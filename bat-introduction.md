title: BAT 介绍
speaker: 薛梦飞
theme: blue
transition: zoomin

[slide]
# BAT
## UI 单元测试框架

[slide]
## BAT能做什么
* UI 单元测试
* 提供出错信息
* 提供操作截图

[slide]
## 为什么要用BAT
* 减少人工测试成本
* 减少bug
* 模拟操作（房源发布）

[slide]
## BAT有哪些功能/API
功能 | API | 备注
:---|:---|:---
case分组 | bat.test | 区分不同流程case
打开url | bat.open |
选择元素 | bat.dom | 普通css选择器
触发事件 | bat.dom('x').on('click') | 触发基础DOM事件及自定义事件
表单赋值 | bat.dom('x').value('123') |
验证文本匹配 | bat.dom('x').content('123') |

[slide]
## Demo
```javascript
bat.test("预约看房流程", function(){
  bat.open('http://www.cjia.com/'); // 打开城家首页

  bat.dom('.searchbox').on('click'); // 打开城市列表
  bat.dom('.searchlist li[id="228"]').on('click'); // 选择广州
  bat.dom('button.cursor').on('click'); // 立即找房

  bat.dom('.list .item:nth-child(2) a').on('click'); // 选择 广州火车东站公寓房型C
  bat.dom('#room-list .chapter-content .content-paragraph:nth-child(4) a').on('click'); // 选择 812

  bat.dom('#info_lookatroom_date').value('2015-11-8'); // 填入看房日期
  bat.dom('#timeRangeName').on('click'); // 打开时间列表
  bat.dom('#timeRangeName~ul li[currentindex="1"]').on('click'); // 选择下午
  bat.dom('#input_name').value('xxx'); // 填入联系人
  bat.dom('#input_mobile').value('xxx'); // 填入手机号

  bat.dom('#save_reservations').on('click'); // 提交预约单

  bat.dom('.f-16.fgreen.inblock.width70p').content('看房预约成功'); // 验证是否预约成功
});
```

[slide]
## Show Time

[slide]
## BAT 架构概览
<style type="text/css">
  .section {
    max-width: 450px;
    margin: 0 auto;
    text-align: left;
  }
  .small {
    font-size: .8rem;
  }
  .line {
    height: 0;
    border-bottom: 2px dashed #fff;
  }
</style>
<section class="section">
  <p>BAT.js <span class="small">(Beacon)</span></p>
  <p class="line"></p>
  <p>caseLoader.js <span class="small">(Node, 解析、执行bat及case)</span></p>
  <p>PhantomJS <span class="small">(WebKit)</span></p>
  <p>NodeJS</p>
</style>

[slide]
## Links
* [BAT](https://github.com/baishuiz/bat)
* [Beacon](https://github.com/baishuiz/beacon)
* [PhantomJS](http://phantomjs.org/)



[slide]
## THANK YOU!
