#一、议题#

1. 对后台服务的代码进行讲评

#二、会议内容#

会议主要是对cde-oauth2-client服务和cde-account-service服务通过代码逐行查看讲解的方式对代码风格、结构、命名规范、异常的处理、类型处理等相关问题进行了讲评。也通过规范代码展示的方式对一些编码规则进行讲解。这些问题的指出以及编码应遵守的规则主要是保证代码的可读性和可维护性，以下是本次会议中发现的问题：
##2.1 系统中主要出现的问题
1. 对于配置文件中自定义的属性应该加上机构名称（cde）作为前缀，再接上服务的名称，最后是自定义属性的具体名称。
2. 对于程序中的异常的处理。第一，一般不会出现运行时异常的异常定义情况；第二，异常应该使用日志记录下来。这里的日志指的是日志服务。
3. 成员变量不需要初始化。除了一些特殊的情况，比如说永远不返回null的list、map等。其次就是为了区分成员变量，在使用的时候应该加上this关键字。
4. 代码中不应该出现用来测试的方法，其中可以通过两种途径来进行解决：第一，使用日志记录；第二，写测试用例。
5. 对于一些特殊的不可变的类型，应该定义为没有set方法。创建对象可以通过构造函数和Builder的方式实现，其中构造函数的方式不适用于属性较多的方式。
6. 在程序中对于map的使用，应该当成一种数据类型来使用，一般就在本类中或是本方法中使用，不暴露给外界。
7. 在注入Bean的情况下，Spring一般默认是单例的情况，对于可变的对象，应该采用工厂的方式来创建对象。
8. 所有的URL不应该出现大写形式（除了是变量的情况），使用“-”符号进行分割。
9. 对前端数据应该采用完全不信任的情况，这是作为一个后台服务必须要遵守的规则，为了自身安全做保障。
10. 对cde-account-service系统的设计进行讲评。mobile和email不应该存到数据库表中，应该属于account的属性作为存储。
11. 对于错误码的设计，为了以后更方便扩展，错误码应该分为服务码和具体的错误码，进行组合。
12. 接口与model应该独立出来（还没有理解其中的意思）。
13. application.yml,mongdb:url 支持集群写法。
14. 开发工具尽量使用IntelliJ。并且需要加入代码检查。

##2.2 代码中主要出现的问题
1. cde-oauth2-client，RequestConfiguration中两个@Bean问题
2. 对于Java8 新语法，应该多进行关注，节省代码量。
3. controller endpoint 名称应该统一。
4. 成员变量message问题，由于该变量在并发的时候后造成严重的影响，一定要避免。
5. 返回值全部Object，Service层要处理异常，只有当正常的时候返回结果，其他的时候必须对异常进行处理。
6. 代码缩进问题，不能使用tab建。
7. 没有resultmodel，domain拼写错误
8. 方法名称不应该与业务存在联系，如checkEmailbyEmailName方法名称就是不规范的。


#三、会议遗留问题

1. 对于代码格式以及规范检查是使用google的还是原来zyeeda修改过的。并添加到开发工具中。

#四、下阶段工作计划
1. 修改以上指出的存在的错误
2. 添加配置服务与日志服务









		






