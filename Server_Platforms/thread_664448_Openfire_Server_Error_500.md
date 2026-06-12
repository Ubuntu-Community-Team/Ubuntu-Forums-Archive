---
title: "Openfire Server Error 500"
date: 2008-01-11
forum: Server Platforms
---

### Post by Awayne on 2008-01-11
I've been trying to install Openfire for a more secure and private system for me and some friends. When I installed it on my server it refused to work, spitting out an "Error 500". I've tried everything I can think of to solve this including use both Java 1.5 and 1.6 versions, and using 2 versions of Openfire. Not being well versed in Java I can't make any sense out of the error and Google doesn't seem to have any answers. Any help would be greatly appreciated. Thanks.

> HTTP ERROR: 500

INTERNAL_SERVER_ERROR

RequestURI=/index.jsp
Caused by:

java.lang.NullPointerException
	at org.jivesoftware.openfire.filetransfer.proxy.FileTransferProxy.isProxyEnabled(FileTransferProxy.java:240)
	at org.jivesoftware.openfire.admin.index_jsp._jspService(index_jsp.java:528)
	at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	at org.mortbay.jetty.servlet.ServletHolder.handle(ServletHolder.java:491)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1074)
	at com.opensymphony.module.sitemesh.filter.PageFilter.parsePage(PageFilter.java:118)
	at com.opensymphony.module.sitemesh.filter.PageFilter.doFilter(PageFilter.java:52)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1065)
	at org.jivesoftware.util.LocaleFilter.doFilter(LocaleFilter.java:65)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1065)
	at org.jivesoftware.util.SetCharacterEncodingFilter.doFilter(SetCharacterEncodingFilter.java:41)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1065)
	at org.jivesoftware.admin.PluginFilter.doFilter(PluginFilter.java:69)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1065)
	at org.jivesoftware.admin.AuthCheckFilter.doFilter(AuthCheckFilter.java:98)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1065)
	at org.mortbay.jetty.servlet.ServletHandler.handle(ServletHandler.java:365)
	at org.mortbay.jetty.security.SecurityHandler.handle(SecurityHandler.java:185)
	at org.mortbay.jetty.servlet.SessionHandler.handle(SessionHandler.java:181)
	at org.mortbay.jetty.handler.ContextHandler.handle(ContextHandler.java:689)
	at org.mortbay.jetty.webapp.WebAppContext.handle(WebAppContext.java:391)
	at org.mortbay.jetty.handler.ContextHandlerCollection.handle(ContextHandlerCollection.java:146)
	at org.mortbay.jetty.handler.HandlerCollection.handle(HandlerCollection.java:114)
	at org.mortbay.jetty.handler.HandlerWrapper.handle(HandlerWrapper.java:139)
	at org.mortbay.jetty.Server.handle(Server.java:285)
	at org.mortbay.jetty.HttpConnection.handleRequest(HttpConnection.java:457)
	at org.mortbay.jetty.HttpConnection$RequestHandler.headerComplete(HttpConnection.java:751)
	at org.mortbay.jetty.HttpParser.parseNext(HttpParser.java:500)
	at org.mortbay.jetty.HttpParser.parseAvailable(HttpParser.java:209)
	at org.mortbay.jetty.HttpConnection.handle(HttpConnection.java:357)
	at org.mortbay.io.nio.SelectChannelEndPoint.run(SelectChannelEndPoint.java:329)
	at org.mortbay.thread.BoundedThreadPool$PoolThread.run(BoundedThreadPool.java:475)


---

### Post by zozobra on 2008-02-21
I am having the same issue.

**Output from Openfire after hitting continue on the Administrator Account set up page:**
```
HTTP ERROR: 500

INTERNAL_SERVER_ERROR

RequestURI=/setup/setup-finished.jsp
Caused by:

java.lang.NullPointerException
	at org.jivesoftware.openfire.admin.setup.setup_002dfinished_jsp._jspService(setup_002dfinished_jsp.java:74)
	at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:820)
	at org.mortbay.jetty.servlet.ServletHolder.handle(ServletHolder.java:487)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1093)
	at com.opensymphony.module.sitemesh.filter.PageFilter.parsePage(PageFilter.java:118)
	at com.opensymphony.module.sitemesh.filter.PageFilter.doFilter(PageFilter.java:52)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.jivesoftware.util.LocaleFilter.doFilter(LocaleFilter.java:65)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.jivesoftware.util.SetCharacterEncodingFilter.doFilter(SetCharacterEncodingFilter.java:41)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.jivesoftware.admin.PluginFilter.doFilter(PluginFilter.java:69)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.jivesoftware.admin.AuthCheckFilter.doFilter(AuthCheckFilter.java:98)
	at org.mortbay.jetty.servlet.ServletHandler$CachedChain.doFilter(ServletHandler.java:1084)
	at org.mortbay.jetty.servlet.ServletHandler.handle(ServletHandler.java:360)
	at org.mortbay.jetty.security.SecurityHandler.handle(SecurityHandler.java:216)
	at org.mortbay.jetty.servlet.SessionHandler.handle(SessionHandler.java:181)
	at org.mortbay.jetty.handler.ContextHandler.handle(ContextHandler.java:726)
	at org.mortbay.jetty.webapp.WebAppContext.handle(WebAppContext.java:405)
	at org.mortbay.jetty.handler.ContextHandlerCollection.handle(ContextHandlerCollection.java:206)
	at org.mortbay.jetty.handler.HandlerCollection.handle(HandlerCollection.java:114)
	at org.mortbay.jetty.handler.HandlerWrapper.handle(HandlerWrapper.java:139)
	at org.mortbay.jetty.Server.handle(Server.java:324)
	at org.mortbay.jetty.HttpConnection.handleRequest(HttpConnection.java:505)
	at org.mortbay.jetty.HttpConnection$RequestHandler.headerComplete(HttpConnection.java:828)
	at org.mortbay.jetty.HttpParser.parseNext(HttpParser.java:514)
	at org.mortbay.jetty.HttpParser.parseAvailable(HttpParser.java:205)
	at org.mortbay.jetty.HttpConnection.handle(HttpConnection.java:380)
	at org.mortbay.io.nio.SelectChannelEndPoint.run(SelectChannelEndPoint.java:395)
	at org.mortbay.thread.BoundedThreadPool$PoolThread.run(BoundedThreadPool.java:450)

Powered by Jetty://
```

**Java version check:**
```
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)
```

**Mysql version check:**
```
mysql> select version();
+------------------------------+
| version()                    |
+------------------------------+
| 5.0.45-Debian_1ubuntu3.1-log |
+------------------------------+
1 row in set (0.00 sec)
```

---

### Post by Lorrim on 2008-03-31
Posted for posterity since a resolution was not posted in a timely manner.

I ran into this myself this afternoon.  Check the permissions on the Openfire files and directories.  Specifically the logs directory and the openfire.xml file need to be writable by the user account under which Openfire runs.  This is identical to what happened to me today and what it ended up being was that I created a openfire.xml file as root and forgot to reset the permissions.  I blame sleep deprivation, but whatever works for you.  :)

---

