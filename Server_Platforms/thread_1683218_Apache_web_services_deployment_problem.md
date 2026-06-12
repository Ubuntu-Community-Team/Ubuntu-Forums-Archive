---
title: "Apache web services deployment problem"
date: 2011-02-07
forum: Server Platforms
---

### Post by redforece.bala on 2011-02-07
Hi all

     I am using apache axis web services,tomcat 7,Intellij 10 and ant build. I wrote the ant build for deploying the axis web services.When i try to deploy it i am getting error like this

AxisFault
 faultCode: {http://schemas.xmlsoap.org/soap/envelope/}Server.userException
 faultSubcode: 
 faultString: java.net.SocketTimeoutException: Read timed out
 faultActor: 
 faultNode: 
 faultDetail: 
    {http://xml.apache.org/axis/}stackTrace:java.net.SocketTimeoutException: Read timed out
    at java.net.SocketInputStream.socketRead0(Native Method)
    at java.net.SocketInputStream.read(SocketInputStream.java:129)
    at java.io.BufferedInputStream.fill(BufferedInputStream.java:218)
    at java.io.BufferedInputStream.read(BufferedInputStream.java:237)
    at org.apache.axis.transport.http.HTTPSender.readHeadersFromSocket(HTTPSender.java:583)
    at org.apache.axis.transport.http.HTTPSender.invoke(HTTPSender.java:143)
    at org.apache.axis.strategies.InvocationStrategy.visit(InvocationStrategy.java:32)
    at org.apache.axis.SimpleChain.doVisiting(SimpleChain.java:118)
    at org.apache.axis.SimpleChain.invoke(SimpleChain.java:83)
    at org.apache.axis.client.AxisClient.invoke(AxisClient.java:165)
    at org.apache.axis.client.Call.invokeEngine(Call.java:2784)
    at org.apache.axis.client.Call.invoke(Call.java:2767)
    at org.apache.axis.client.Call.invoke(Call.java:1792)
    at org.apache.axis.client.AdminClient.process(AdminClient.java:439)
    at org.apache.axis.client.AdminClient.process(AdminClient.java:404)
    at org.apache.axis.client.AdminClient.process(AdminClient.java:410)
    at org.apache.axis.client.AdminClient.process(AdminClient.java:320)
    at org.apache.axis.tools.ant.axis.AdminClientTask.executeInCurrentVM(AdminClientTask.java:356)
    at org.apache.axis.tools.ant.axis.AdminClientTask.execute(AdminClientTask.java:316)
    at org.apache.tools.ant.UnknownElement.execute(UnknownElement.java:291)
    at sun.reflect.GeneratedMethodAccessor6.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.apache.tools.ant.dispatch.DispatchUtils.execute(DispatchUtils.java:106)
    at org.apache.tools.ant.Task.perform(Task.java:348)
    at org.apache.tools.ant.Target.execute(Target.java:390)
    at org.apache.tools.ant.Target.performTasks(Target.java:411)
    at org.apache.tools.ant.Project.executeSortedTargets(Project.java:1397)
    at org.apache.tools.ant.Project.executeTarget(Project.java:1366)
    at org.apache.tools.ant.helper.DefaultExecutor.executeTargets(DefaultExecutor.java:41)
    at org.apache.tools.ant.Project.executeTargets(Project.java:1249)
    at org.apache.tools.ant.Main.runBuild(Main.java:801)
    at org.apache.tools.ant.Main.startAnt(Main.java:218)
    at org.apache.tools.ant.launch.Launcher.run(Launcher.java:280)
    at org.apache.tools.ant.launch.Launcher.main(Launcher.java:109)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.intellij.rt.ant.execution.AntMain2.main(AntMain2.java:32)
    {http://xml.apache.org/axis/}hostname:RVS-Ubu


The same thing is working well in windows platform.Any body knows about it please help me.I need this urgently..

---

