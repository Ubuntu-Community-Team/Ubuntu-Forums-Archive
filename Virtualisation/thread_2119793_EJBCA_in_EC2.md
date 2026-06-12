---
title: "EJBCA in EC2"
date: 2013-02-24
forum: Virtualisation
---

### Post by jasoncallaway on 2013-02-24
Apologies ahead of time if this is the wrong forum.

Has anybody been able to successfully install EJBCA in Amazon EC2?  I seem to be having trouble with the Elastic IP NATing with regard to JNDI naming.

I'm using the 12.04 LTS AMI (ami-3fec7956 in the Eastern region), and I'm using EJBCA 4.0.14 and JBoss 5.1.0.GA (which seems to be the latest version supported by ejbca.org).

[FONT=Courier New]ant bootstrap[/FONT] completes without errors.

Relevant failure from [FONT=Courier New]ant install[/FONT]:

[FONT=Courier New]     [java] Initalizing Temporary Authorization Module with caid=-996733751 and superadmin CN 'TempSuperAdmin'.
     [java] 
     [java] javax.naming.NameNotFoundException: ejbca not bound
     [java]     at org.jnp.server.NamingServer.getBinding(NamingServer.java:771)
     [java]     at org.jnp.server.NamingServer.getBinding(NamingServer.java:779)
     [java]     at org.jnp.server.NamingServer.getObject(NamingServer.java:785)
     [java]     at org.jnp.server.NamingServer.lookup(NamingServer.java:396)
     [java]     at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
     [java]     at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
     [java]     at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
     [java]     at java.lang.reflect.Method.invoke(Method.java:616)
     [java]     at sun.rmi.server.UnicastServerRef.dispatch(UnicastServerRef.java:322)
     [java]     at sun.rmi.transport.Transport$1.run(Transport.java:177)
     [java]     at java.security.AccessController.doPrivileged(Native Method)
     [java]     at sun.rmi.transport.Transport.serviceCall(Transport.java:173)
     [java]     at sun.rmi.transport.tcp.TCPTransport.handleMessages(TCPTransport.java:553)
     [java]     at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run0(TCPTransport.java:808)
     [java]     at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run(TCPTransport.java:667)
     [java]     at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1146)
     [java]     at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)
     [java]     at java.lang.Thread.run(Thread.java:679)
     [java]     at sun.rmi.transport.StreamRemoteCall.exceptionReceivedFromServer(StreamRemoteCall.java:273)
     [java]     at sun.rmi.transport.StreamRemoteCall.executeCall(StreamRemoteCall.java:251)
     [java]     at sun.rmi.server.UnicastRef.invoke(UnicastRef.java:160)
     [java]     at org.jnp.server.NamingServer_Stub.lookup(Unknown Source)
     [java]     at org.jnp.interfaces.NamingContext.lookup(NamingContext.java:726)
     [java]     at org.jnp.interfaces.NamingContext.lookup(NamingContext.java:686)
     [java]     at javax.naming.InitialContext.lookup(InitialContext.java:409)
     [java]     at org.ejbca.core.ejb.JndiHelper.getRemoteSession(JndiHelper.java:57)
     [java]     at org.ejbca.core.model.util.EjbRemoteHelper.getAdminGroupSession(EjbRemoteHelper.java:94)
     [java]     at org.ejbca.ui.cli.ca.BaseCaAdminCommand.initAuthorizationModule(BaseCaAdminCommand.java:161)
     [java]     at org.ejbca.ui.cli.ca.CaInitCommand.execute(CaInitCommand.java:207)
     [java]     at org.ejbca.ui.cli.EjbcaEjbCli.executeCommand(EjbcaEjbCli.java:118)
     [java]     at org.ejbca.ui.cli.EjbcaEjbCli.main(EjbcaEjbCli.java:80)
     [java] Could not run execute method for class class org.ejbca.ui.cli.ca.CaInitCommand
     [java] org.ejbca.ui.cli.ErrorAdminCommandException: java.lang.NullPointerException
     [java]     at org.ejbca.ui.cli.ca.CaInitCommand.execute(CaInitCommand.java:312)
     [java]     at org.ejbca.ui.cli.EjbcaEjbCli.executeCommand(EjbcaEjbCli.java:118)
     [java]     at org.ejbca.ui.cli.EjbcaEjbCli.main(EjbcaEjbCli.java:80)
     [java] Caused by: java.lang.NullPointerException
     [java]     at org.ejbca.ui.cli.ca.BaseCaAdminCommand.initAuthorizationModule(BaseCaAdminCommand.java:161)
     [java]     at org.ejbca.ui.cli.ca.CaInitCommand.execute(CaInitCommand.java:207)
     [java]     ... 2 more
[/FONT]
Thanks!

---

### Post by jasoncallaway on 2013-02-24
Sorry that last error was not representative of what I normally see.  This is more like it:

[FONT=Courier New]     [java] Initalizing Temporary Authorization Module with caid=-996733751 and superadmin CN 'TempSuperAdmin'.
     [java] 
     [java] javax.naming.NameNotFoundException: AdminGroupSessionRemote not bound
     [java]     at org.jnp.server.NamingServer.getBinding(NamingServer.java:771)
     [java]     at org.jnp.server.NamingServer.getBinding(NamingServer.java:779)
     [java]     at org.jnp.server.NamingServer.getObject(NamingServer.java:785)
     [java]     at org.jnp.server.NamingServer.lookup(NamingServer.java:443)
     [java]     at org.jnp.server.NamingServer.lookup(NamingServer.java:399)
     [java]     at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
     [java]     at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
     [java]     at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
     [java]     at java.lang.reflect.Method.invoke(Method.java:616)
     [java]     at sun.rmi.server.UnicastServerRef.dispatch(UnicastServerRef.java:322)
     [java]     at sun.rmi.transport.Transport$1.run(Transport.java:177)
     [java]     at java.security.AccessController.doPrivileged(Native Method)
     [java]     at sun.rmi.transport.Transport.serviceCall(Transport.java:173)
     [java]     at sun.rmi.transport.tcp.TCPTransport.handleMessages(TCPTransport.java:553)
     [java]     at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run0(TCPTransport.java:808)
     [java]     at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run(TCPTransport.java:667)
     [java]     at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1146)
     [java]     at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)
     [java]     at java.lang.Thread.run(Thread.java:679)
     [java]     at sun.rmi.transport.StreamRemoteCall.exceptionReceivedFromServer(StreamRemoteCall.java:273)
     [java]     at sun.rmi.transport.StreamRemoteCall.executeCall(StreamRemoteCall.java:251)
     [java]     at sun.rmi.server.UnicastRef.invoke(UnicastRef.java:160)
     [java]     at org.jnp.server.NamingServer_Stub.lookup(Unknown Source)
     [java]     at org.jnp.interfaces.NamingContext.lookup(NamingContext.java:726)
     [java]     at org.jnp.interfaces.NamingContext.lookup(NamingContext.java:686)
     [java]     at javax.naming.InitialContext.lookup(InitialContext.java:409)
     [java]     at org.ejbca.core.ejb.JndiHelper.getRemoteSession(JndiHelper.java:57)
     [java]     at org.ejbca.core.model.util.EjbRemoteHelper.getAdminGroupSession(EjbRemoteHelper.java:94)
     [java]     at org.ejbca.ui.cli.ca.BaseCaAdminCommand.initAuthorizationModule(BaseCaAdminCommand.java:161)
     [java]     at org.ejbca.ui.cli.ca.CaInitCommand.execute(CaInitCommand.java:207)
     [java]     at org.ejbca.ui.cli.EjbcaEjbCli.executeCommand(EjbcaEjbCli.java:118)
     [java]     at org.ejbca.ui.cli.EjbcaEjbCli.main(EjbcaEjbCli.java:80)
     [java] Could not run execute method for class class org.ejbca.ui.cli.ca.CaInitCommand
     [java] org.ejbca.ui.cli.ErrorAdminCommandException: java.lang.NullPointerException
     [java]     at org.ejbca.ui.cli.ca.CaInitCommand.execute(CaInitCommand.java:312)
     [java]     at org.ejbca.ui.cli.EjbcaEjbCli.executeCommand(EjbcaEjbCli.java:118)
     [java]     at org.ejbca.ui.cli.EjbcaEjbCli.main(EjbcaEjbCli.java:80)
     [java] Caused by: java.lang.NullPointerException
     [java]     at org.ejbca.ui.cli.ca.BaseCaAdminCommand.initAuthorizationModule(BaseCaAdminCommand.java:161)
     [java]     at org.ejbca.ui.cli.ca.CaInitCommand.execute(CaInitCommand.java:207)
     [java]     ... 2 more
[/FONT]

---

### Post by jasoncallaway on 2013-02-26
Solved by EJBCA support folks.  See [https://sourceforge.net/p/ejbca/discussion/123123/thread/71db197e/](https://sourceforge.net/p/ejbca/discussion/123123/thread/71db197e/).

---

### Post by jeby6372 on 2013-12-12
I have the same problem with Ubuntu 12.04 / openjdk-6-amd64. When lauching the ant install it fails as mentioned. The link provided above refers to the installation sequence that I stritcly followed step by step. It doesn't solve the problem.
Many similar issues exists on the web and I've never found any valuable answer. It's very disapointed

---

