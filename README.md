# 基于Springboot2.0的Dubbo入门项目（dubbo-spring-boot-starter）

Dubbo是阿里巴巴公司开源的一个高性能优秀的服务框架，使得应用可通过高性能的 RPC 实现服务的输出和输入功能，可以和Spring框架无缝集成。最近半年来，Dubbo的得到了快速的维护，官方也推出了集成Springboot的jar包，及其贴合时代潮流，那么现在就来讲Springboot2.0如何集成官方Dubbo。

## **一、运行工具与环境**

运行环境：JDK 8，Maven 3.3+
技术栈：SpringBoot 2.0+、Dubbo 2.6+、ZooKeeper 3.3+
工具：IntelliJ IDEA、谷歌浏览器

## **二、Springboot快速集成Dubbo关键的依赖**
```maven
<dependency>
    <groupId>com.alibaba.boot</groupId>
    <artifactId>dubbo-spring-boot-starter</artifactId>
    <version>0.2.0</version>
</dependency>
```

## **三、如何使用**
**1.使用Dubbo要知道服务提供者和消费者概念，而且最好调用的服务要有共同的Api，如下图是我写的入门项目。**

![Dubbo项目目录](http://wx2.sinaimg.cn/large/cf495cdcgy1fss1juop0uj20as0bj74e.jpg)

**2.配置application.properties**

![application.properties配置](http://wx3.sinaimg.cn/large/cf495cdcly1fuu28gq1jqj20zi0htjsv.jpg)

这边用到的注册中心是zookeeper，当然你也可以用其他注册中心，你可以查看[Dubbo管理手册(中文)](http://dubbo.apache.org/books/dubbo-admin-book/)，里面有其他注册中心使用方法。其他一些配置可以去官网查看，这边就不在多说。

**3.服务提供者和消费者**

**共同Api：**

![Dubbo服务提供者](http://wx2.sinaimg.cn/large/cf495cdcly1fuu28fumilj20uv0hq0u4.jpg)

这是服务提供者和消费者共同调用的接口。

**服务提供者：**
![Dubbo服务提供者](http://wx2.sinaimg.cn/large/cf495cdcly1fuu28gcb56j213i0j4gnh.jpg)

简单来说就是将上面接口的实现方法（称之为服用）注册到zookeeper上，并暴露端口供其他消费者消费。@Service里面的一些信息就是服务具体的注册地址。

**服务消费者：**
![Dubbo服务消费者](http://wx1.sinaimg.cn/large/cf495cdcly1fuu28h1ke4j216i0jk0uu.jpg)

如上@Reference的直接表示远程调用，里面最重要的是url，表示要调用的地址，也就是上面服务暴露的地址。

## **四、运行项目**

首先启动服务提供者，在启动服务调用者，打开谷歌浏览器，输入[http://localhost:9091/sayHello/HelloWorld](http://localhost:9091/sayHello/HelloWorld)

![Dubbo浏览器显示结果](http://wx4.sinaimg.cn/large/cf495cdcgy1fss496cbz4j20hu0apdfv.jpg)

## **五、总结**
Dubbo的重新维护，不切实际疯狂维护，给RPC又添加了生机，结合Springboot，也许你会发现，Dubbo入门并没有那么困难，只是你想不想学。

## 项目地址

#### 码云：[https://gitee.com/smirk/dubbo-springboot](https://gitee.com/smirk/dubbo-springboot)

#### github：[https://github.com/xiaoze-smirk/dubbo-springboot](https://github.com/xiaoze-smirk/dubbo-springboot)

------

smirk小泽   
2018 年 06月29日    
