---
title: "JSPWiki redirects remote users to localhost"
date: 2007-02-28
forum: Server Platforms
---

### Post by DNA_Boss on 2007-02-28
Hola Folks,

So I'm in the process of setting up an Ubuntu Dapper machine to run an internal wiki.

The Setup so far

Apache2
Tomcat5
JSPWiki
Java 1.5.0

The Issue:
So the wiki itself is running, and other users are able to browse the wiki. However, whenever a user attempts to comment or create a new page the address goes to localhost instead of the server. The changes are saved to the wiki though.

An example to help clarify the issue:
User goes to the wiki
clicks on a link to a topic named "Phone directory"
clicks add comment, and types in the comment.
clicks save - it's at this point that the issue occurs
Instead of going to [http://SERVERNAME.net:8180/JSPWiki/phonedir](http://SERVERNAME.net:8180/JSPWiki/phonedir)...
it goes to [http://LOCALHOST:8180/JSPWiki/phonedir](http://LOCALHOST:8180/JSPWiki/phonedir)...
and results in a page not found error.

I'm pretty positive the issue is somewhere in tomcat5, but i can't figure out where. I've edited the virtualhost information in the server.xml file, which it doesn't seem to pay attention to. The only thing I've found that may be related is an error recorded in my localhost logs whenever i startup the tomcat service.

---------------------------------------------
2007-02-27 16:03:39 StandardContext[/balancer]Exception starting filter BalancerFilter
java.lang.NoClassDefFoundError: org/apache/commons/digester/Digester
        at org.apache.webapp.balancer.RulesParser.createDigester(RulesParser.java:65)
        at org.apache.webapp.balancer.RulesParser.<init>(RulesParser.java:43)
        at org.apache.webapp.balancer.BalancerFilter.init(BalancerFilter.java:79)
        at org.apache.catalina.core.ApplicationFilterConfig.getFilter(ApplicationFilterConfig.java:225)
        at org.apache.catalina.core.ApplicationFilterConfig.setFilterDef(ApplicationFilterConfig.java:308)
        at org.apache.catalina.core.ApplicationFilterConfig.<init>(ApplicationFilterConfig.java:79)
        at org.apache.catalina.core.StandardContext.filterStart(StandardContext.java:3702)
        at org.apache.catalina.core.StandardContext.start(StandardContext.java:4329)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:823)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:807)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:595)
        at org.apache.catalina.core.StandardHostDeployer.install(StandardHostDeployer.java:277)
        at org.apache.catalina.core.StandardHost.install(StandardHost.java:832)
        at org.apache.catalina.startup.HostConfig.deployDirectories(HostConfig.java:701)
        at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:432)
        at org.apache.catalina.startup.HostConfig.start(HostConfig.java:983)
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:349)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1091)
        at org.apache.catalina.core.StandardHost.start(StandardHost.java:789)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1083)
        at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:478)
        at org.apache.catalina.core.StandardService.start(StandardService.java:480)
        at org.apache.catalina.core.StandardServer.start(StandardServer.java:2313)
        at org.apache.catalina.startup.Catalina.start(Catalina.java:556)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:287)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:425)
-------------------------------------------

So ladies and gents any help would be most appreciated because at this point I'm clueless.

---

### Post by mrf on 2007-03-01
The error stack trace will probably be because you're missing an apache commons jar file. You can download it from: [http://jakarta.apache.org/commons/digester/](http://jakarta.apache.org/commons/digester/)

Getting redirected back to localhost will be because the html form the comment editor is in has something like action="http://localhost:8180/xxx" in it. There will be a configuration some where to set the domain jspwiki thinks it's running on, so it generates a action="http://<sitename>/xxx". No idea where thou, never used it.

---

