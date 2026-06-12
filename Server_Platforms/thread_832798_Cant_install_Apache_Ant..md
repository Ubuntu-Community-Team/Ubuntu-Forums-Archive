---
title: "Cant install Apache Ant."
date: 2008-06-18
forum: Server Platforms
---

### Post by marbo on 2008-06-18
I try to install Apache Ant with this howto: [http://osflash.org/red5/debian](http://osflash.org/red5/debian)

But then i copy/paste this line ```
/usr/local/ant/bin/ant
```
in this folder: /red5-trunk, then come this error:

```
root@kotiservu:~/red5-trunk# /usr/local/ant/bin/ant                             Buildfile: build.xml

clean:
   [delete] Deleting directory /home/marbo/red5-trunk/bin
   [delete] Deleting directory /home/marbo/red5-trunk/dist
   [delete] Deleting directory /home/marbo/red5-trunk/cluster

-library.check:
     [echo] Java: java.home is /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre and the target version is 1.5
     [echo] Ant: ant.home is /usr/local/ant and the target version is Apache Ant version 1.7.0 compiled on December 13 2006

-java6.check:
     [echo] Using Java 1.5

prepare:
    [mkdir] Created dir: /home/marbo/red5-trunk/bin
    [mkdir] Created dir: /home/marbo/red5-trunk/dist
    [mkdir] Created dir: /home/marbo/red5-trunk/cluster
    [mkdir] Created dir: /home/marbo/red5-trunk/cluster/origin
    [mkdir] Created dir: /home/marbo/red5-trunk/cluster/edge
    [mkdir] Created dir: /home/marbo/red5-trunk/bin/testcases
    [mkdir] Created dir: /home/marbo/red5-trunk/bin/testcases/testreports

compile:
     [echo] javac version: 1.5
     [echo] Not using the Eclipse IDE
     [echo] Compiler adapter name: modern

compile_core:

compile_core_compatibility:

retrieve:
[ivy:settings] :: Ivy 2.0.0-beta2 - 20080225093827 :: http://ant.apache.org/ivy/ ::
[ivy:settings] :: loading settings :: file = /home/marbo/red5-trunk/ivysettings.xml
     [echo] Ivy conf name: java5
[ivy:resolve] :: resolving dependencies :: red5#server;working@kotiservu
[ivy:resolve]   confs: [java5]
[ivy:resolve]   found tomcat#jasper;6.0.16 in googlecode
[ivy:resolve]   found tomcat#jasper-jdt;6.0.16 in googlecode
[ivy:resolve]   found tomcat#jasper-el;6.0.16 in googlecode
[ivy:resolve]   found tomcat#tomcat-juli;6.0.16 in googlecode
[ivy:resolve]   found tomcat#tomcat-juli-adapters;6.0.16 in googlecode
[ivy:resolve]   found tomcat#el-api; in googlecode
[ivy:resolve]   found javax#jsp-api;2.1 in googlecode
[ivy:resolve]   found javax#servlet-api;2.5 in googlecode
[ivy:resolve]   found javax#ejb3-persistence; in googlecode
[ivy:resolve]   found red5#naming-factory; in googlecode
[ivy:resolve]   found red5#naming-resources; in googlecode
[ivy:resolve]   found spring#spring-aop;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#spring-orm;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#spring-beans;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#spring-context;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#spring-core;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#spring-web;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#aopalliance; in googlecode
[ivy:resolve]   found tomcat#catalina;6.0.16 in googlecode
[ivy:resolve]   found tomcat#tomcat-coyote;6.0.16 in googlecode
[ivy:resolve]   found tomcat#annotations-api; in googlecode
[ivy:resolve]   found commons#commons-modeler;2.0.1 in googlecode
[ivy:resolve]   found jetty#jetty;6.1.9 in googlecode
[ivy:resolve]   found jetty#jetty-util;6.1.9 in googlecode
[ivy:resolve]   found jetty#jetty-xbean;6.1.9 in googlecode
[ivy:resolve]   found red5#slf4j-api;1.5.2 in googlecode
[ivy:resolve]   found red5#jcl-over-slf4j;1.5.2 in googlecode
[ivy:resolve]   found red5#log4j-over-slf4j;1.5.2 in googlecode
[ivy:resolve]   found red5#jul-to-slf4j;1.5.2 in googlecode
[ivy:resolve]   found red5#logback-core;0.9.9 in googlecode
[ivy:resolve]   found red5#logback-classic;0.9.9 in googlecode
[ivy:resolve]   found cglib#cglib-nodep;2.1_3 in googlecode
[ivy:resolve]   found commons#commons-beanutils;1.8.0-BETA in googlecode
[ivy:resolve]   found commons#commons-codec;1.3 in googlecode
[ivy:resolve]   found commons#commons-collections;3.2.1 in googlecode
[ivy:resolve]   found commons#commons-httpclient;3.1 in googlecode
[ivy:resolve]   found commons#commons-lang;2.4 in googlecode
[ivy:resolve]   found commons#commons-pool;1.3 in googlecode
[ivy:resolve]   found javax#jpda; in googlecode
[ivy:resolve]   found red5#quartz;1.5.2 in googlecode
[ivy:resolve]   found javax#jta;1.0.1B in googlecode
[ivy:resolve]   found red5#ehcache;1.4.1 in googlecode
[ivy:resolve]   found red5#xercesImpl;2.9.0 in googlecode
[ivy:resolve]   found red5#xml-apis;2.9.0 in googlecode
[ivy:resolve]   found red5#xmlrpc;2.0.1 in googlecode
[ivy:resolve]   found javax#activation;1.1 in googlecode
[ivy:resolve]   found jmx#jmxremote; in googlecode
[ivy:resolve]   found jmx#jmxtools; in googlecode
[ivy:resolve]   found jmx#rmissl; in googlecode
[ivy:resolve]   found mina#mina-core;1.1.7 in googlecode
[ivy:resolve]   found mina#mina-filter-ssl;1.1.7 in googlecode
[ivy:resolve]   found mina#mina-integration-spring;1.1.7 in googlecode
[ivy:resolve]   found mina#mina-integration-jmx;1.1.7 in googlecode
[ivy:resolve]   found asm#asm;2.2.3 in googlecode
[ivy:resolve]   found asm#asm-commons;2.2.3 in googlecode
[ivy:resolve]   found antlr#antlr;2.7.6 in googlecode
[ivy:resolve]   found red5#bsh;2.0b4 in googlecode
[ivy:resolve]   found red5#groovy;1.0 in googlecode
[ivy:resolve]   found red5#jruby;1.0.3 in googlecode
[ivy:resolve]   found red5#jython;2.2 in googlecode
[ivy:resolve]   found spring#spring-context-support;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#spring-webmvc;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#spring-tx;2.5.5-20080609 in googlecode
[ivy:resolve]   found spring#spring-jdbc;2.5.5-20080609 in googlecode
[ivy:resolve]   found commons#standard;1.1.2 in googlecode
[ivy:resolve]   found spring#spring-security-core;2.0.2 in googlecode
[ivy:resolve]   found red5#derby;10.4.1.3 in googlecode
[ivy:resolve]   found rhino#js;1.6R7 in googlecode
[ivy:resolve]   found red5#jsr173_1.0_api; in googlecode
[ivy:resolve]   found red5#jsr-223;1.0 in googlecode
[ivy:resolve]   found red5#js-engine; in googlecode
[ivy:resolve]   found red5#jython-engine; in googlecode
[ivy:resolve]   found red5#groovy-engine; in googlecode
[ivy:resolve]   found red5#jruby-engine; in googlecode
[ivy:resolve] :: resolution report :: resolve 2287ms :: artifacts dl 532ms
[ivy:resolve]   :: evicted modules:
[ivy:resolve]   red5#jruby;1.0.1 by [red5#jruby;1.0.3] in [java5]
        ---------------------------------------------------------------------
        |                  |            modules            ||   artifacts   |
        |       conf       | number| search|dwnlded|evicted|| number|dwnlded|
        ---------------------------------------------------------------------
        |       java5      |   75  |   0   |   0   |   1   ||   74  |   0   |
        ---------------------------------------------------------------------
[ivy:retrieve] :: retrieving :: red5#server
[ivy:retrieve]  confs: [java5]
[ivy:retrieve]  0 artifacts copied, 74 already retrieved (0kB/132ms)
    [javac] Compiling 478 source files to /home/marbo/red5-trunk/bin
    [javac] Note: Some input files use or override a deprecated API.
    [javac] Note: Recompile with -Xlint:deprecation for details.
    [javac] Note: Some input files use unchecked or unsafe operations.
    [javac] Note: Recompile with -Xlint:unchecked for details.

compile_demos:
     [echo] Webapps dir: webapps
     [echo] Webapps build dir: dist/webapps
     [copy] Copying 23 files to /home/marbo/red5-trunk/dist/webapps/root
     [copy] Copying 23 files to /home/marbo/red5-trunk/dist/webapps/root
    [mkdir] Created dir: /home/marbo/red5-trunk/dist/webapps/admin/WEB-INF/classes
    [mkdir] Created dir: /home/marbo/red5-trunk/dist/webapps/admin/WEB-INF/lib
    [javac] Compiling 13 source files to /home/marbo/red5-trunk/dist/webapps/admin/WEB-INF/classes
    [javac] /home/marbo/red5-trunk/webapps/admin/WEB-INF/src/org/red5/webapps/admin/client/AuthClientRegistry.java:79: cannot find symbol
    [javac] symbol  : variable Red5
    [javac] location: class org.red5.webapps.admin.client.AuthClientRegistry
    [javac]             masterScope = Red5.getConnectionLocal().getScope();
    [javac]                               ^
    [javac] Note: Some input files use unchecked or unsafe operations.
    [javac] Note: Recompile with -Xlint:unchecked for details.
    [javac] 1 error

BUILD FAILED
/home/marbo/red5-trunk/build.xml:245: The following error occurred while executing this line:
/home/marbo/red5-trunk/build.xml:339: The following error occurred while executing this line:
/home/marbo/red5-trunk/build.xml:284: Compile failed; see the compiler error output for details.
```

How i can install apache ant with red5 ?

ps. im so sorry for my bad english.

---

### Post by windependence on 2008-06-18
Can you post the contents of /home/marbo/red5-trunk/build.xml as an attachment here?

-Tim

---

### Post by marbo on 2008-06-18
> **windependence said:**
> Can you post the contents of /home/marbo/red5-trunk/build.xml as an attachment here?

-Tim

Here u are. [http://on.dy.fi/build.xml](http://on.dy.fi/build.xml)

---

### Post by windependence on 2008-06-18
> **marbo said:**
> Here u are. [http://on.dy.fi/build.xml](http://on.dy.fi/build.xml)

You're gonna have to give me some time on this one. :) I would like to find the offending lines in this XML file.

-Tim

---

### Post by marbo on 2008-06-18
i delete this fail. i solved my problem.

---

### Post by matthewboh on 2008-06-27
Oh, I wish you could have posted how you fixed it.  I'm installing it on a headless 8.04 server.

I'm plowing through the install - found it best to install tomcat5.5 using ```
sudo apt-get update
sudo apt-get install tomcat5.5 tomcat5.5-admin tomcat5.5-webapps
```
Then changing over to the tomcat5.5 configuration files by typing ```
cd /etc/tomcat5.5
```
then adding in two lines into tomcat-users.xml by using nano ```
sudo nano tomcat-users.xml
```.  They two lines are: ```
<role rolename="admin"/>
  <user username="admin" password="supersecretpassword" roles="standard,manager,admin"/>
``` and you can place them in the middle of the file.

I then re-started the Tomcat server with ```
sudo /etc/init.d/tomcat5.5 restart
``` and then I was able to go to localhost:8180 and use apt-get to install ant ```
sudo apt-get install ant
```
Now I'm just trying to get ivy running and configured to point to googlecode.com instead of maven.

---

