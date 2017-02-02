# vue-h-datepicker
基于Vue1.x的移动端选择组件

# 版本
1.2
 修复滑动过渡（修复）
 增加自定义回调函数(修复)
 修复字体大小获取(修复)
 增加模式选择（日期和时间双模式）

# Install
    npm install vue-h-datepicker --save

# Usage

    <template>
      <input v-model="dateOption.date" >
      <div @click="showDatePicker">选择日期</div>
      <div class="wrap">
        <app-date-picker :status="dateOption.status" :option="dateOption.option" v-on:confirm="getDate" v-on:cancel="cancelDatePicker"></app-date-picker>
      </div>


      <input v-model="timeOption.time" >
      <div @click="showTimePicker">选择时间</div>
      <div class="wrap">
        <app-date-picker :status="timeOption.status" :option="timeOption.option" v-on:confirm="getTime" v-on:cancel="cancelTimePicker"></app-date-picker>
      </div>
     </template>
    <style>
      html{
        font-size: 10px;
      }
    </style>
    <script>
      import DatePicker from '../src/DatePicker.vue';

    export default {
      data(){
        return {
          dateOption:{
            status:false,
            option:{
              type:'date',//date or time,默认为date
              startDate:{
                year:2001,
                month:11,
                day:12
              },
              yearScope:[1991,2018]//可选,默认为今年前后20年,
            },
            date:'2012-12-12'
          },
          timeOption:{
            status:false,
            option:{
              type:'time',//date or time,默认为date
              startTime:{
                meridiem:'上午',
                hour:3,
                minute:35
              }
            },
            time:'上午 3:35'
          }

        }
      },
      components: {
        'app-date-picker': DatePicker
      },
      methods:{
        showDatePicker:function(){
          this.dateOption.status = true;
        },
        showTimePicker:function(){
          this.timeOption.status = true;
        },
        getDate: function(date){
          this.dateOption.date = date.year+'-'+date.month+'-'+date.day;//选择之后的回调函数
          this.dateOption.status = false
        },
        getTime: function(time){
          this.timeOption.time = time.meridiem+' '+time.hour+':'+time.minute;//选择之后的回调函数
          this.timeOption.status = false
        },
        cancelDatePicker:function(){
          this.dateOption.status = false;//取消之后的回调函数
        },
        cancelTimePicker:function(){
          this.timeOption.status = false;//取消之后的回调函数
        }
      }
    }
    </script>

