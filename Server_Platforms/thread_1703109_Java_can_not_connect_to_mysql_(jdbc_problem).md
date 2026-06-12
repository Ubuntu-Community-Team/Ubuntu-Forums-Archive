---
title: "Java can not connect to mysql (jdbc problem)"
date: 2011-03-08
forum: Server Platforms
---

### Post by Phil2812 on 2011-03-08
Hey there!
 I'm currently moving my server to another computer.
 Everything works fine but I want an java program to use MySQL instead of SQLite.
 My OS is Ubuntu 10.10 Server Edition (64Bit). I'm accessing the server via SSH.
 When I start the server it tells me that it fails to load the java program.
 

 Stacktrace:
 ```
2011-03-08 20:28:35 [SEVERE] [BBROTHER] MySQL SQLException on Creation
 com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure
 

 Last packet sent to the server was 0 ms ago.
         at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
         at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
         at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
         at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
         at com.mysql.jdbc.Util.handleNewInstance(Util.java:406)
         at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1074)
         at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2103)
         at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:718)
         at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:46)
         at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
         at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
         at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
         at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
         at com.mysql.jdbc.Util.handleNewInstance(Util.java:406)
         at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:302)
         at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:282)
         at java.sql.DriverManager.getConnection(DriverManager.java:620)
         at java.sql.DriverManager.getConnection(DriverManager.java:200)
         at me.taylorkelly.bigbrother.datasource.ConnectionService.getConnection(ConnectionService.java:77)
         at me.taylorkelly.bigbrother.datasource.JDCConnectionDriver.connect(JDCConnectionDriver.java:41)
         at java.sql.DriverManager.getConnection(DriverManager.java:620)
         at java.sql.DriverManager.getConnection(DriverManager.java:222)
         at me.taylorkelly.bigbrother.datasource.ConnectionManager.createConnection(ConnectionManager.java:27)
         at me.taylorkelly.bigbrother.BigBrother.onEnable(BigBrother.java:95)
         at org.bukkit.plugin.java.JavaPlugin.setEnabled(JavaPlugin.java:140)
         at org.bukkit.plugin.java.JavaPluginLoader.enablePlugin(JavaPluginLoader.java:426)
         at org.bukkit.plugin.SimplePluginManager.enablePlugin(SimplePluginManager.java:187)
Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure
 
```(It's a plugin of our minecraft game server.)
(I already posted in the plugin related forums but it doesn't seem that someone will answer my post. And because I think it looks like a more general problem I thought I might get a solution here.)

 

 It seems to me that jdbc does not work.
 

 **I am able to connect to mysql via PHP without any problems.**
 

 I already installed *libmysql-java* but it didn't change anything.
 

 *mysql my.cnf:*
 ```
...
 port = 3306
 bind-address = 127.0.0.1
 ...
``` *java program properties:*
 ```
MySQL = true   #If true, uses MySQL. If false, uses Sqlite
 [...]
 mysqlDB = jdbc:mysql://localhost:3306/dbbb   #DB for MySQL (if applicable)
 engine = INNODB   #Engine for the Database (INNODB is recommended)
 [...]
 mysqlPass = ****...   #Password for MySQL db (if applicable)
 mysqlUser = ****...   #Username for MySQL db (if applicable)
 ...
``` I already tried to change *'localhost'* to *'127.0.0.1'* but it didn't make a difference.
 

 The database *'dbbb'* exists and the user has all rights on it.
 

 I'm not using *sun-java6* beacause there doesn't seem to be a headless version of it.
 I'm using OpenJDK.
 

 *java -version *output*:*
 ```
java version "1.6.0_20"
 OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1)
 OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)
```

EDIT: I tried to do the same with a simple java program.
On Windows it works, on ubuntu server it doesn't.
It produces the same error as the plugin.

EDIT 2: I added the classpath thing (*'CLASSPATH=".:/usr/share/java/mysql.jar"'*) to *'/etc/environment*' but when I *'echo $CLASSPATH' *it returns nothing.

Any help is appreciated.
 Thanks in advance,
 Phil

---

### Post by Phil2812 on 2011-03-09
/push

No one?
Any idea? :(

---

### Post by BattousaiX on 2011-07-07
Hope you didn't give up.

[http://ubuntuforums.org/showthread.php?p=11020148#post11020148](http://ubuntuforums.org/showthread.php?p=11020148#post11020148)

---

