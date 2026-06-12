---
title: "Tomcat6 + Apache 2.2 + OpenEJB not working"
date: 2009-07-16
forum: Server Platforms
---

### Post by C-King on 2009-07-16
I'm trying to get OpenEJB to work on my Ubuntu server. I have Apache 2.2 installed, Tomcat6 and mod_jk to connect them to eachother. To add EJB support to Tomcat, I found [OpenEJB]("http://openejb.apache.org"), also by the Apache Group. 

And then it started to fail. I followed the instructions on the OpenEJB website (1. deploy openejb.war. 2. go to <tomcat_url>/openejb/installer 3. follow instructions). Step 1 was no problem at all. Then I tried step two and I got an error about the Installer class, which could not be found.

output: ```
exception 
javax.servlet.ServletException: Wrapper cannot find servlet class org.apache.openejb.tomcat.installer.InstallerServlet or a class it depends on
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.jk.server.JkCoyoteHandler.invoke(JkCoyoteHandler.java:190)
	org.apache.jk.common.HandlerRequest.invoke(HandlerRequest.java:291)
	org.apache.jk.common.ChannelSocket.invoke(ChannelSocket.java:769)
	org.apache.jk.common.ChannelSocket.processConnection(ChannelSocket.java:698)
	org.apache.jk.common.ChannelSocket$SocketConnection.runIt(ChannelSocket.java:891)
	org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:690)
	java.lang.Thread.run(Thread.java:619)


root cause 
java.lang.ClassNotFoundException: org.apache.openejb.tomcat.installer.InstallerServlet
	org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1387)
	org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1233)
	java.security.AccessController.doPrivileged(Native Method)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.jk.server.JkCoyoteHandler.invoke(JkCoyoteHandler.java:190)
	org.apache.jk.common.HandlerRequest.invoke(HandlerRequest.java:291)
	org.apache.jk.common.ChannelSocket.invoke(ChannelSocket.java:769)
	org.apache.jk.common.ChannelSocket.processConnection(ChannelSocket.java:698)
	org.apache.jk.common.ChannelSocket$SocketConnection.runIt(ChannelSocket.java:891)
	org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:690)
	java.lang.Thread.run(Thread.java:619)
```

When I try Tomcat6 bundled with NetBeans, it works perfectly, also a standalone Tomcat6 server. But not on the Tomcat6 server from the Ubuntu repositories. 

Does anyone have an idea how to fix this?

---

### Post by michalkocian on 2009-09-20
Please, can anyone tell me how to fix this problem?

---

