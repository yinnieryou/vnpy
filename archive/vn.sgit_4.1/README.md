# vn.sgit

### 简介
飞鼠接口的Python封装，主要用于期货和黄金T+D的高频交易。

### 说明
和金仕达黄金接口类似，尽管看起来很像CTP，细节实现有很多区别。

飞鼠接口的委托数据更新是分散在多个推送里的：

1. 下单后，通过onRtnOrder通知是否成功，没有ErrorID说明委托到了交易所

2. 后续的成交状态，通过onRtnTrade通知，用户自行累加

3. 撤单的确认，通过onRspOrderAction通知

为了获取实时的委托状态，需要用户自行把这三个数据合并起来。

飞鼠的撤单需要使用交易所代码+交易所的系统委托号，因此要实现CTP的OrderRef撤单需要用户自行实现一个异步撤单的设计。

如果打算自己开发建议参考vn.trader里的sgitGateway，可以少踩点坑。

### API版本

日期：2016-01-06

名称：SgitApi-4.1-20160106仿真接口

来源：招金投资技术部门提供