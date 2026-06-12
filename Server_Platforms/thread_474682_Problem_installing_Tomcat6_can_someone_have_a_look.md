---
title: "Problem installing Tomcat6: can someone have a look at this catalina.out log ?"
date: 2007-06-15
forum: Server Platforms
---

### Post by gisaalter on 2007-06-15
Hi, I'd like to run Apache Tomcat on my machine, however startup fails. When I have a look at my log file this comes up:


15-jun-2007 16:25:20 org.apache.catalina.core.AprLifecycleListener init
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib
15-jun-2007 16:25:20 org.apache.coyote.http11.Http11Protocol init
INFO: Initializing Coyote HTTP/1.1 on http-8080
15-jun-2007 16:25:20 org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 486 ms
15-jun-2007 16:25:20 org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
15-jun-2007 16:25:20 org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/6.0.13
15-jun-2007 16:25:20 org.apache.coyote.http11.Http11Protocol start
INFO: Starting Coyote HTTP/1.1 on http-8080
15-jun-2007 16:25:20 org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8009
15-jun-2007 16:25:20 org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/22  config=null
15-jun-2007 16:25:20 org.apache.catalina.startup.Catalina start
INFO: Server startup in 750 ms
15-jun-2007 16:25:20 org.apache.catalina.core.StandardServer await
SEVERE: StandardServer.await: create[8005]: 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:359)
	at java.net.ServerSocket.bind(ServerSocket.java:319)
	at java.net.ServerSocket.<init>(ServerSocket.java:185)
	at org.apache.catalina.core.StandardServer.await(StandardServer.java:373)
	at org.apache.catalina.startup.Catalina.await(Catalina.java:630)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:590)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:413)
15-jun-2007 16:25:20 org.apache.coyote.http11.Http11Protocol pause
INFO: Pausing Coyote HTTP/1.1 on http-8080
15-jun-2007 16:25:21 org.apache.catalina.core.StandardService stop
INFO: Stopping service Catalina
15-jun-2007 16:25:21 org.apache.coyote.http11.Http11Protocol destroy
INFO: Stopping Coyote HTTP/1.1 on http-8080

I'm running an apache-http server on port 8888, however when I stop this apache I get the same
message...
Can someone point me out how to fix this ?

Thanks !

---

