# thrift-demo

学习thrift

**thrift学习教程**：[thrift官网](https://thrift.apache.org/)

## 项目目的

模拟一个多服务的游戏匹配系统，具体业务逻辑如下图：

![image-20211210125800627](https://gitee.com/pxlsdz/blogImage/raw/master/img/202112101258703.png)

## 准备工作

1. 创建项目文件夹`thrift_demo`

2. `游戏系统节点`，创建`game`文件夹；

   `匹配系统节点`，创建`match_system`文件夹；

      `thrift`相关文件,创建`thrift`文件夹
         ![image-20211210132628478](https://gitee.com/pxlsdz/blogImage/raw/master/img/202112101326507.png)

### thrift简单语法介绍

#### 0.开发流程

         1. 对接口进行描述
         2. 使用`thrift`将接口的描述文件编译成对应语言的版本

#### 1.命名空间

         `thrift`文件命名一般都是以`.thrift`作为后缀：`XXX.thrift`，可以在该文件的开头为该文件加上命名空间限制，格式为：

             namespace 语言名称 名称


             例如对c++来说，有：

                 namespace cpp match_service


#### 2.数据类型

                 大小写敏感，它共支持以下几种基本的数据类型：

                 > 1.  `string`， 字符串类型，注意是全部小写形式；
                 > 2.  `i16`, 16位整形类型，
                 > 3.  `i32`，32位整形类型，对应C/C++/java中的int类型；
                 > 4.  `i64`，64位整形，对应C/C++/java中的long类型；
                 > 5.  `byte`，8位的字符类型，对应C/C++中的char，java中的byte类型
                 > 6.  `bool`, 布尔类型，对应C/C++中的bool，java中的boolean类型；
                 > 7.  `double`，双精度浮点类型，对应C/C++/java中的double类型；
                 > 8.  `void`，空类型，对应C/C++/java中的void类型；该类型主要用作函数的返回值，
                 >
                 > 除上述基本类型外，ID还支持以下类型：
                 >
                 > 1.  `map`，map类型，例如，定义一个map对象：map\[HTML\_REMOVED\] newmap;
                 > 2.  `set`，集合类型，例如，定义set\[HTML\_REMOVED\]对象：set\[HTML\_REMOVED\] aSet;
                 > 3.  `list`，链表类型，例如，定义一个list\[HTML\_REMOVED\]对象：list\[HTML\_REMOVED\] aList;

                 struct，自定义结构体类型，在IDL中可以自己定义结构体，对应C中的struct，c++中的struct和class，java中的class。例如：

                     struct User{
                                   1: i32 id,
                                                    2: string name,
                                                              3: i32 score
                                                                      }

**注意，在struct定义结构体时需要对每个结构体成员用序号标识：“序号: ”。**

