## 背景描述
该数据集是由 Machine Learning Repository 基于一个英国电商公司从2010年12月1号到2011年9月12号的真实的交易数据集进行改造的。 该电商主要销售的商品是各类礼品， 主要客户是来自不同国家的的分销商。通过对客户的行为进行分析，从而探索出客户的行为模式，具体指标有客户消费趋势分析（时间序列），客户个体消费分析，客户价值RFM分析，复购率和回购率分析，聚类分析？？？
## 数据说明
### 字段含义
InvoiceNo  发票号码

StockCode  货物代码

Description  货物描述

Quantity  数量

InvoiceDate  发票日期

UnitePrice  单价

CustomerID  客户账号

Country  客户所在国家

### 数据来源
根据UCI机器学习知识库，这些数据由公共分析小组主任陈大庆博士提供。
Director: Public Analytics group. chend '@' lsbu.ac.uk, School of Engineering, London South Bank University, London SE1 0AA, UK.

## 数据清洗
缺失值处理

数据一致性处理：日期格式处理

新增购买金额price一列

异常值处理：df.describe()观察平均值与四分位数比较，观察是否有异常值存在
## 数据分析
### 客户消费趋势分析

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/1.png)

根据图表显示，2010.12-2011.7，销售金额较低，趋势波动，从2011.7以后销售金额逐月上涨，2011.11月达到峰值，12月又降下来

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/2.png)

根据图表显示，销售金额逐季度呈上升趋势，第四季度达到峰值

**客户采购量分析**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/3.png)

根据图表显示，2010.12-2011.7，客户采购量较低，趋势波动，从2011.6月以后销售金额逐月上涨，2011.11月达到峰值，12月又降下来，和采购金额趋势相近

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/4.png)

根据图表显示，客户采购数量逐季度呈上升趋势，第二极度以后上升较快，第四季度达到峰值

**采购客户数分析**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/5.png)

前9个月用户数量在1000以下呈波动趋势，9月到11月用户增长较快，12月下降到最低值

**每月平均一个用户消费的金额**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/6.png)

根据图表可知：客户四月份的消费金额最低，12月份的消费金额最高

**每月用户消费的平均次数**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/7.png)

有图可知消费前九个月的每月消费次数在28左右，9月到11月消费次数增长加快，11月为最高值，消费了39次，12月下降到平均值

总结论：

### 用户个体消费分析
**客户消费商品数与消费总金额的描述统计**
这是一张图片
根据图表得：平均数与中位数和分位数比较，客户的采购数量和采购金额的平均值都要高于中位数，说明数据有极大值的干扰。

**客户消费金额与消费商品数的散点图**（是否呈线性相关，线性方程）

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/8.png)

有异常值干扰，我们可以去除异常值消费金额大于20000再进行分析

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/9.png)

**客户消费金额的分布图**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/10.png)

根据图表可知，用户的消费金额绝大部分集中在一定范围之内，有小部分异常值

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/11.png)

**客户消费次数的分布图**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/12.png)

根据图表可知，客户消费次数主要集中在1000次以下

**用户累计消费金额占比**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/13.png)

根据图表可知，3000名的用户近75%的用户占了接近20%的销售额

**用户累计消费次数占比**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/14.png)

根据图表可知，3000名的用户近75%的用户占了接近20%的销售额，大致符合二八法则，公司维护好这部分用户，销售就有了保障。

### 用户消费行为

用户第一次消费时间，用户最后一次消费，新老客户消费比，用户分层，用户购买周期，用户生命周期

**用户第一次消费时间**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/15.png)

根据图表可知，客户第一次消费的时间在2010.12月人数最多，之后呈波荡下降趋势，客户第一次消费时间在2011.12月人数最少

**用户最后一次消费时间**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/16.png)

根据图表可知，客户最后一次消费时间大都集中在2011.8月以后四个月内，比较两张表，商家的忠诚客户较多

**新老客户消费比**

34%的用户只进行了一次采购

可以看看一次采购的消费金额与消费数量，可能是大单，然后想办法留住客户

**用户分层RFM**

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/17.png)

重要保持的客户的金额远高于其他类型的客户，所以公司要维持好这部分客户，降低这部分客户的流失。

**计算每个月每个用户的消费次数**

根据月份间客户的消费次数的比较来区分用户状态：未注册unreg、新客new、活跃用户active、不活跃用户unactive、回流用户return
做一年之内用户分层的面积图？？？
如购买一次的客户为新客户，购买两次的客户为潜力客户，购买三次的客户为老客户，购买四次的客户为成熟客户，购买五次及以上则为忠实客户。其诀窍在于让消费者一直顺着阶梯往上爬，把销售想象成是要将两次购买的顾客往上推成三次购买的顾客，把一次购买者变成两次的。
![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/18.png)

**用户购买周期（按订单）？？？**

### 复购率和回购率分析

复购率：自然月内，购买多次的用户占比，购买次数大于1次的人/所有购买过的人

![](https://github.com/sunandflowering/E-CommerceData/raw/master/pic/19.png)

根据图标得，客户的复购率在97%左右波动，客户数量比较稳定

回购率：曾经购买过的用户在某一时间内的再次购买的占比？？

