#velocity study note

##Velocity is a Java-based template engine. It permits web page designers to reference methods defined in Java code. Web designers can work in parallel with Java programmers to develop web sites according to the Model-View-Controller (MVC) model, meaning that web page designers can focus solely on creating a well-designed site, and programmers can focus solely on writing top-notch code.

  1、声明:#set ($var=XXX)<br>
　　左边可以是以下的内容<br>
　　Variable reference <br>
　　String literal <br>
　　Property reference <br>
　　Method reference <br>
　　Number literal #set ($i=1)<br> 
　　ArrayList #set ($arr=["yt1","t2"])<br>
　　算术运算符<br>

2、注释:
　　单行## XXX<br>
　　多行#* xxx<br>
　　xxxx<br>
　　xxxxxxxxxxxx*#<br>

　　References 引用的类型<br>
3、变量 Variables <br>
　　以 "$" 开头，第一个字符必须为字母。character followed by a VTL Identifier. (a .. z or A .. Z).<br>
　　变量可以包含的字符有以下内容：<br>
　　alphabetic (a .. z, A .. Z) <br>
　　numeric (0 .. 9) <br>
　　hyphen ("-") <br>
　　underscore ("_") <br>

4、Properties <br>
　　$Identifier.Identifier<br>
　　$user.name<br>
　　hashtable user中的的name值.类似：user.get("name")<br>

5、Methods <br>
　　object user.getName() = $user.getName()<br>
　　also can get Properties by Methods,by get{Name}()<br>

6、Formal Reference Notation <br>
　　用{}把变量名跟字符串分开 <br>

　　如<br>
　　#set ($user="csy"}<br>
　　${user}name <br>
　　返回csyname<br>

　　$username<br>
　　$!username<br>
　　$与$!的区别<br>
　　当找不到username的时候，$username返回字符串"$username"，而$!username返回空字符串""<br> 

7、双引号 与 引号 <br>
　　#set ($var="helo")<br>
　　test"$var" 返回testhello<br>
　　test'$var' 返回test'$var'<br>
　　可以通过设置 stringliterals.interpolate=false改变默认处理方式<br>

8、条件语句<br>
　　#if( $foo )<br> 
　　 <strong>Velocity!</strong><br>
　　#end<br>
　　#if($foo)<br>
　　#elseif()<br>
　　#else<br>
　　#end<br>
　　当$foo为null或为Boolean对象的false值执行.<br>

9、逻辑运算符:== && || !<br>

10、循环语句#foreach($var in $arrays ) // 集合包含下面三种Vector, a Hashtable or an Array<br>
#end<br>
　　#foreach( $product in $allProducts )<br>
　　 <li>$product</li><br>
　　#end<br>

　　#foreach( $key in $allProducts.keySet() )<br>
　　 <li>Key: $key -> Value: $allProducts.get($key)</li><br>
　　#end<br>

　　#foreach( $customer in $customerList )<br>
　　 <tr><td>$velocityCount</td><td>$customer.Name</td></tr><br>
　　#end<br>

11、velocityCount变量在配置文件中定义<br>
　　# Default name of the loop counter<br>
　　# variable reference.<br>
　　directive.foreach.counter.name = velocityCount<br>
　　# Default starting value of the loop<br>
　　# counter variable reference.<br>
　　directive.foreach.counter.initial.value = 1<br>

12、包含文件 <br>
　　#include( "one.gif","two.txt","three.htm" )<br>

13、Parse导入脚本<br>
　　#parse("me.vm" )<br>

14、#stop 停止执行并返回<br> 

15、定义宏Velocimacros ,相当于函数 支持包含功能<br>
　　#macro( d )<br>
　　 <tr><td></td></tr><br>
　　#end<br>
　　调用 <br>
　　#d()<br>

16、带参数的宏<br>
　　#macro( tablerows $color $somelist )<br>
　　#foreach( $something in $somelist )<br>
　　 <tr><td bgcolor=$color>$something</td></tr><br>
　　#end<br>
　　#end<br>

17、Range Operator <br>
　　#foreach( $foo in [1..5] )<br>
