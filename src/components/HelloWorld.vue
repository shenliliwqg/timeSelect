<template>
  <div class="hello">
    <div class="title text-center">
      机时预约时间选择插件
    </div>
    <div class="container">
      <span>预约规则：</span>
      <table width="100%">
        <tr>
          <td width="15%">
            允许预约时间范围
          </td>
          <td width="35%">{{data.afterDays}}天</td>
          <td width="15%">
            最小预约时间
          </td>
          <td width="35%">{{data.minTime}}</td>
        </tr> <tr>
          <td>
            需提前预约时间
          </td>
          <td>{{data.ahead}}</td>
          <td>
          </td>
          <td></td>
        </tr>
      </table>
      <p >{{data.address}}</p>
      <div>
        <div class="flex openDay">
          <p class="item openTitle">
            <span>开放时间</span>
          </p>
          <p class="prev"><span><</span></p>
          <p v-for="item in data.openTimeList" :class="['item',{'table-disabled':item.state=='disableb'},{'table-able':item.state=='able'},{'table-full':item.state=='full'}]">
            <span>{{item.date}}</span>
            <b>已约满</b>
            <u>不开放</u>
          </p>
          <p class="next"><span>></span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      data:{
        address:'江苏省苏州市吴中工业区3号楼602',
        afterDays:'15',
        minTime:'0.5h',
        ahead:'2h',
        openTimeList:[
          {
            day:'2018-11-1',
            state:'disableb',
            date:'星期',
          },
          {
            day:'2018-11-2',
            state:'disableb',
            date:'星期',
          },
          {
            day:'2018-11-3',
            date:'星期',
            state:'full',
          },
          {
            day:'2018-11-4',
            date:'星期',
            state:'disableb',
          },
          {
            day:'2018-11-5',
            date:'星期',
            state:'disableb',
          },
          {
            day:'2018-11-6',
            date:'星期',
            state:'able',
          },
          {
            day:'2018-11-7',
            date:'星期',
            state:'able',
          }
        ]
      }
    }
  },
  methods:{

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
  @import "../style/mixin.less";
  .title{
    .font(24px,30px,'Microsoft YaHei');
    padding:20px 0 ;
  }
  table{
    border-collapse: collapse;
    margin: 15px 0;
    td{
      border: 1px solid #ddd;
      height: 30px;
      padding: 0 20px;
    }
  }
  .flex{
    .fj(flex-start );
    border-right: 1px solid #ddd;
    text-align: center;
    margin: 15px 0;
    .common{
      border: 1px solid #ddd;
      border-right: none;
      cursor: pointer;
      padding: 10px 0;
    }
    .item{
      flex: 1;
      .common;
      span{
        display: block;
      }
      u,b{
        display: none;
        .font(12px,14px);
        color: #fff;
      }
      &.table-full{
        background: #f60;
        cursor: not-allowed;
        span{
          color: #fff;
        }
        b{
          display: block;
        }
      }
      &.table-disabled{
        background: #ddd;
        cursor: not-allowed;
        u{
          display: block;
        }
      }
    }
    .next,.prev{
      width: 20px;
      vertical-align: middle;
      background: lighten(#ccc,10%);
      &:hover{
        background: #ccc;
      }
      .common;
    }
    .openTitle{
      cursor: default;
    }
    .next,.prev,.openTitle{
      .fj(flex-start );
      span{
        flex: 1;
        align-self: center;
        .font(14px,20px)
      }
    }
  }
</style>
