#MyBatis 分页插件 - PageHelper

[English](https://github.com/pagehelper/Mybatis-PageHelper/blob/master/README.md)

如果你也在用 MyBatis，建议尝试该分页插件，这一定是<b>最方便</b>使用的分页插件。

分页插件支持任何复杂的单表、多表分页，部分特殊情况请看[重要提示](https://github.com/pagehelper/Mybatis-PageHelper/blob/master/wikis/zh/Important.md)。

想要使用分页插件？请看[如何使用分页插件](https://github.com/pagehelper/Mybatis-PageHelper/blob/master/wikis/zh/HowToUse.md)。

##物理分页

该插件目前支持以下数据库的<b>物理分页</b>:

 1. `Oracle`
 2. `Mysql`
 3. `MariaDB`
 4. `SQLite`
 5. `Hsqldb`
 6. `PostgreSQL`
 7. `DB2`
 8. `SqlServer(2005,2008)`
 9. `Informix`
 10. `H2`
 11. `SqlServer2012`
 12. `Derby`

分页插件默认会检测当前的数据库链接，自动选择对应的数据库分页。

你可以配置`helperDialect`属性来指定分页插件使用哪种方言。配置时，可以使用下面的缩写值：

`oracle`,`mysql`,`mariadb`,`sqlite`,`hsqldb`,`postgresql`,`db2`,`sqlserver`,`informix`,`h2`,`sqlserver2012`,`derby`

<b>特别注意：</b>使用 SqlServer2012 数据库时，需要手动指定为 `sqlserver2012`，否则会使用 SqlServer2005 的方式进行分页。

##MyBatis 工具网站:[http://mybatis.tk](http://www.mybatis.tk)

##分页插件支持 MyBatis 3.1.0+(支持最新版本)

##分页插件 5.0

由于分页插件 5.0 版本和 4.2.x 实现完全不同，所以 master 分支为 5.x 版本，4.2 作为一个分支存在，如果有针对 4.2 的 PR，请注意提交到分支版本。

##分页插件最新快照版本为 5.0.0-SNAPSHOT

##分页插件最新版本为 4.2.1

###Maven 坐标

```xml  
<dependency>
    <groupId>com.github.pagehelper</groupId>
    <artifactId>pagehelper</artifactId>
    <version>4.2.1</version>
</dependency>
```  

##最近的更新日志

###4.2.1

- 解决`SimpleCache`类遗留问题导致的错误 [#143](http://git.oschina.net/free/Mybatis_PageHelper/issues/143) fix by [dhhua](https://github.com/dhhua)

###4.2.0

- 使用新的方式进行分页，4.2版本是从5.0版本分离出来的一个特殊版本，这个版本兼容4.x的所有功能，5.0版本时为了简化分页逻辑，会去掉部分功能，所以4.2是4.x的最后一个版本。
- 支持 MyBatis 3.1.0+ 版本
- 增加对 Derby 数据库的支持
- 对除 informix 外的全部数据库进行测试，全部通过
- PageHelper增加手动清除方法`clearPage()`
- 解决 SqlServer 多个`with(nolock)`时出错的问题
- 对CountMappedStatement 进行缓存，配置方式见BaseSqlUtil 319行
- 由于SqlServer的sql处理特殊，因此增加了两个SQL缓存，具体配置参考SqlServerDialect类
- 添加 sqlserver 别名进行排序功能，在解析sql时，会自动将使用的别名转换成列名 by panmingzhi
- 新增`sqlCacheClass`参数，该参数可选，可以设置sql缓存实现类，默认为`SimpleCache`，当项目包含guava时，使用`GuavaCache`，也可以通过参数`sqlCacheClass`指定自己的实现类，有关详情看`com.github.pagehelper.cache`包。
- 解决#135，增加/*keep orderby*/注解，SQL中包含该注释时，count查询时不会移出order by
- sqlserver没有orderby时，使用`order by rand()` #82 #118

##项目文档：  

###1. [如何使用分页插件](https://github.com/pagehelper/Mybatis-PageHelper/blob/master/wikis/zh/HowToUse.md)

如果要使用分页插件，这篇文档一定要看，看完肯定没有问题。

如果和 Spring 集成不熟悉，可以参考下面两个 MyBatis 和 Spring 集成的框架

<b>只有基础的配置信息，没有任何现成的功能，作为新手入门搭建框架的基础</b>

- [集成 Spring 3.x](https://github.com/abel533/Mybatis-Spring/tree/spring3.x)
- [集成 Spring 4.x](https://github.com/abel533/Mybatis-Spring)

这两个集成框架集成了 PageHelper 和 [通用 Mapper](https://github.com/abel533/Mapper)。

###2. 使用 RowBounds 和 PageRowBounds 方式

###3. 实现自己的分页插件
- helperDialect 方式
- dialect 方式

##[更新日志](https://github.com/pagehelper/Mybatis-PageHelper/blob/master/wikis/zh/Changelog.md)

包含全部的详细的更新日志。

##[重要提示](https://github.com/pagehelper/Mybatis-PageHelper/blob/master/wikis/zh/Important.md)

提示很重要，建议一定看一遍！

##提交 BUG
- [提交到 github](https://github.com/pagehelper/Mybatis-PageHelper/issues/new)
- [提交到 gitosc](http://git.oschina.net/free/Mybatis_PageHelper/issues/new?issue%5Bassignee_id%5D=&issue%5Bmilestone_id%5D=)

##相关链接

作者博客：http://blog.csdn.net/isea533

作者邮箱： abel533@gmail.com  

MyBatis QQ 群： <a target="_blank" href="http://shang.qq.com/wpa/qunwpa?idkey=29e4cce8ac3c65d14a1dc40c9ba5c8e71304f143f3ad759ac0b05146e0952044"><img border="0" src="http://pub.idqqimg.com/wpa/images/group.png" alt="MyBatis" title="MyBatis"></a>

本项目在 github 的项目地址：https://github.com/pagehelper/Mybatis-PageHelper

本项目在 gitosc 的项目地址：http://git.oschina.net/free/Mybatis_PageHelper

##MyBatis-3
- 项目：https://github.com/mybatis/mybatis-3
- 文档：http://mybatis.github.io/mybatis-3/zh/index.html  

MyBatis 专栏： 
- [MyBatis示例](http://blog.csdn.net/column/details/mybatis-sample.html)
- [MyBatis问题集](http://blog.csdn.net/column/details/mybatisqa.html)  
