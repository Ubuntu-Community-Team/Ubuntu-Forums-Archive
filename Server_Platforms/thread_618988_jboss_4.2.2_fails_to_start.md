---
title: "jboss 4.2.2 fails to start"
date: 2007-11-21
forum: Server Platforms
---

### Post by cybergalvez on 2007-11-21
I am trying to install jboss 4.2.2 on gutsy.  I downloaded the zip file extracted, set JAVA_HOME to the sun java1/5 jdk and when I run run.sh I get the error below.  Does anyone have any help to offer I would really like to be able to get jboss running on this machine

```

21:54:57,276 INFO  [Server] Starting JBoss (MX MicroKernel)...
21:54:57,278 INFO  [Server] Release ID: JBoss [Trinity] 4.2.2.GA (build: SVNTag=JBoss_4_2_2_GA date=200710221139)
21:54:57,278 DEBUG [Server] Using config: org.jboss.system.server.ServerConfigImpl@2e8f4fb3
21:54:57,279 DEBUG [Server] Server type: class org.jboss.system.server.ServerImpl
21:54:57,279 DEBUG [Server] Server loaded through: org.jboss.system.server.NoAnnotationURLClassLoader
21:54:57,279 DEBUG [Server] Boot URLs:
21:54:57,279 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/endorsed/xalan.jar
21:54:57,279 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/endorsed/xercesImpl.jar
21:54:57,279 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/endorsed/serializer.jar
21:54:57,280 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/jboss-jmx.jar
21:54:57,280 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/concurrent.jar
21:54:57,280 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/log4j-boot.jar
21:54:57,280 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/jboss-common.jar
21:54:57,280 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/jboss-system.jar
21:54:57,280 DEBUG [Server]   file:/home/jc/jboss-4.2.2.GA/lib/jboss-xml-binding.jar
21:54:57,280 INFO  [Server] Home Dir: /home/jc/jboss-4.2.2.GA
21:54:57,281 INFO  [Server] Home URL: file:/home/jc/jboss-4.2.2.GA/
21:54:57,281 DEBUG [Server] Library URL: file:/home/jc/jboss-4.2.2.GA/lib/
21:54:57,283 INFO  [Server] Patch URL: null
21:54:57,283 INFO  [Server] Server Name: default
21:54:57,283 INFO  [Server] Server Home Dir: /home/jc/jboss-4.2.2.GA/server/default
21:54:57,284 INFO  [Server] Server Home URL: file:/home/jc/jboss-4.2.2.GA/server/default/
21:54:57,284 INFO  [Server] Server Log Dir: /home/jc/jboss-4.2.2.GA/server/default/log
21:54:57,285 DEBUG [Server] Server Data Dir: /home/jc/jboss-4.2.2.GA/server/default/data
21:54:57,285 INFO  [Server] Server Temp Dir: /home/jc/jboss-4.2.2.GA/server/default/tmp
21:54:57,285 DEBUG [Server] Server Config URL: file:/home/jc/jboss-4.2.2.GA/server/default/conf/
21:54:57,286 DEBUG [Server] Server Library URL: file:/home/jc/jboss-4.2.2.GA/server/default/lib/
21:54:57,286 INFO  [Server] Root Deployment Filename: jboss-service.xml
21:54:57,296 DEBUG [Server] Starting General Purpose Architecture (GPA)...
21:54:57,709 DEBUG [Server] Created MBeanServer: org.jboss.mx.server.MBeanServerImpl@5210f6d3[ defaultDomain='jboss' ]
21:54:57,763 DEBUG [Server] Boot url list: [file:/home/jc/jboss-4.2.2.GA/server/default/conf/]
21:54:57,764 DEBUG [Server] Creating loader for URL: file:/home/jc/jboss-4.2.2.GA/server/default/conf/
21:54:57,768 DEBUG [RepositoryClassLoader] setRepository, repository=org.jboss.mx.loading.UnifiedLoaderRepository3@2fdb7df8, cl=org.jboss.mx.loading.UnifiedClassLoader3@732b3d53{ url=file:/home/jc/jboss-4.2.2.GA/server/default/conf/ ,addedOrder=0}
21:54:57,768 DEBUG [RepositoryClassLoader] setRepository, repository=org.jboss.mx.loading.UnifiedLoaderRepository3@2fdb7df8, cl=org.jboss.mx.loading.UnifiedClassLoader3@732b3d53{ url=file:/home/jc/jboss-4.2.2.GA/server/default/conf/ ,addedOrder=0}
21:54:57,768 DEBUG [UnifiedLoaderRepository3] Adding org.jboss.mx.loading.UnifiedClassLoader3@732b3d53{ url=file:/home/jc/jboss-4.2.2.GA/server/default/conf/ ,addedOrder=0}
21:54:57,865 DEBUG [Server] Failed to create xmbean for: org.jboss.system.server.ServerInfo
21:54:57,891 INFO  [ServerInfo] Java version: 1.5.0_13,Sun Microsystems Inc.
21:54:57,891 INFO  [ServerInfo] Java VM: Java HotSpot(TM) 64-Bit Server VM 1.5.0_13-b05,Sun Microsystems Inc.
21:54:57,891 INFO  [ServerInfo] OS-System: Linux 2.6.22-14-generic,amd64
21:54:57,891 DEBUG [ServerInfo] Full System Properties Dump
21:54:57,892 DEBUG [ServerInfo]     java.vendor: Sun Microsystems Inc.
21:54:57,892 DEBUG [ServerInfo]     sun.java.launcher: SUN_STANDARD
21:54:57,892 DEBUG [ServerInfo]     sun.management.compiler: HotSpot 64-Bit Server Compiler
21:54:57,892 DEBUG [ServerInfo]     os.name: Linux
21:54:57,892 DEBUG [ServerInfo]     sun.boot.class.path: /home/jc/jboss-4.2.2.GA/lib/endorsed/xalan.jar:/home/jc/jboss-4.2.2.GA/lib/endorsed/xercesImpl.jar:/home/jc/jboss-4.2.2.GA/lib/endorsed/serializer.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/rt.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i18n.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/sunrsasign.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/jsse.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/jce.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/charsets.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/classes
21:54:57,892 DEBUG [ServerInfo]     sun.desktop: gnome
21:54:57,892 DEBUG [ServerInfo]     java.vm.specification.vendor: Sun Microsystems Inc.
21:54:57,892 DEBUG [ServerInfo]     java.runtime.version: 1.5.0_13-b05
21:54:57,892 DEBUG [ServerInfo]     user.name: jc
21:54:57,893 DEBUG [ServerInfo]     jboss.bind.address: 127.0.0.1
21:54:57,893 DEBUG [ServerInfo]     jboss.home.dir: /home/jc/jboss-4.2.2.GA
21:54:57,893 DEBUG [ServerInfo]     user.language: en
21:54:57,893 DEBUG [ServerInfo]     sun.boot.library.path: /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/amd64
21:54:57,893 DEBUG [ServerInfo]     jboss.home.url: file:/home/jc/jboss-4.2.2.GA/
21:54:57,893 DEBUG [ServerInfo]     java.version: 1.5.0_13
21:54:57,893 DEBUG [ServerInfo]     user.timezone: GMT-08:00
21:54:57,894 DEBUG [ServerInfo]     java.net.preferIPv4Stack: true
21:54:57,894 DEBUG [ServerInfo]     jboss.server.home.dir: /home/jc/jboss-4.2.2.GA/server/default
21:54:57,894 DEBUG [ServerInfo]     sun.arch.data.model: 64
21:54:57,894 DEBUG [ServerInfo]     java.endorsed.dirs: /home/jc/jboss-4.2.2.GA/lib/endorsed
21:54:57,894 DEBUG [ServerInfo]     jboss.server.home.url: file:/home/jc/jboss-4.2.2.GA/server/default/
21:54:57,894 DEBUG [ServerInfo]     sun.cpu.isalist: 
21:54:57,894 DEBUG [ServerInfo]     sun.jnu.encoding: UTF-8
21:54:57,894 DEBUG [ServerInfo]     file.encoding.pkg: sun.io
21:54:57,894 DEBUG [ServerInfo]     file.separator: /
21:54:57,894 DEBUG [ServerInfo]     java.specification.name: Java Platform API Specification
21:54:57,894 DEBUG [ServerInfo]     java.class.version: 49.0
21:54:57,894 DEBUG [ServerInfo]     jboss.server.config.url: file:/home/jc/jboss-4.2.2.GA/server/default/conf/
21:54:57,894 DEBUG [ServerInfo]     user.country: US
21:54:57,894 DEBUG [ServerInfo]     java.home: /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre
21:54:57,894 DEBUG [ServerInfo]     java.vm.info: mixed mode
21:54:57,894 DEBUG [ServerInfo]     jboss.lib.url: file:/home/jc/jboss-4.2.2.GA/lib/
21:54:57,894 DEBUG [ServerInfo]     os.version: 2.6.22-14-generic
21:54:57,894 DEBUG [ServerInfo]     path.separator: :
21:54:57,894 DEBUG [ServerInfo]     java.vm.version: 1.5.0_13-b05
21:54:57,894 DEBUG [ServerInfo]     java.protocol.handler.pkgs: org.jboss.net.protocol
21:54:57,894 DEBUG [ServerInfo]     java.awt.printerjob: sun.print.PSPrinterJob
21:54:57,894 DEBUG [ServerInfo]     sun.io.unicode.encoding: UnicodeLittle
21:54:57,894 DEBUG [ServerInfo]     jboss.server.temp.dir: /home/jc/jboss-4.2.2.GA/server/default/tmp
21:54:57,894 DEBUG [ServerInfo]     sun.rmi.dgc.client.gcInterval: 3600000
21:54:57,894 DEBUG [ServerInfo]     user.home: /home/jc
21:54:57,895 DEBUG [ServerInfo]     java.specification.vendor: Sun Microsystems Inc.
21:54:57,895 DEBUG [ServerInfo]     java.library.path: /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/amd64/server:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/amd64:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/../lib/amd64
21:54:57,895 DEBUG [ServerInfo]     java.vendor.url: http://java.sun.com/
21:54:57,895 DEBUG [ServerInfo]     program.name: run.sh
21:54:57,895 DEBUG [ServerInfo]     java.vm.vendor: Sun Microsystems Inc.
21:54:57,895 DEBUG [ServerInfo]     sun.rmi.dgc.server.gcInterval: 3600000
21:54:57,895 DEBUG [ServerInfo]     java.runtime.name: Java(TM) 2 Runtime Environment, Standard Edition
21:54:57,895 DEBUG [ServerInfo]     java.class.path: /home/jc/jboss-4.2.2.GA/bin/run.jar:/usr/lib/jvm/java-1.5.0-sun/lib/tools.jar
21:54:57,895 DEBUG [ServerInfo]     jboss.server.log.dir: /home/jc/jboss-4.2.2.GA/server/default/log
21:54:57,895 DEBUG [ServerInfo]     jbossmx.loader.repository.class: org.jboss.mx.loading.UnifiedLoaderRepository3
21:54:57,895 DEBUG [ServerInfo]     java.vm.specification.name: Java Virtual Machine Specification
21:54:57,895 DEBUG [ServerInfo]     java.vm.specification.version: 1.0
21:54:57,895 DEBUG [ServerInfo]     sun.cpu.endian: little
21:54:57,895 DEBUG [ServerInfo]     sun.os.patch.level: unknown
21:54:57,895 DEBUG [ServerInfo]     jboss.server.lib.url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/
21:54:57,895 DEBUG [ServerInfo]     java.io.tmpdir: /tmp
21:54:57,895 DEBUG [ServerInfo]     java.vendor.url.bug: http://java.sun.com/cgi-bin/bugreport.cgi
21:54:57,895 DEBUG [ServerInfo]     jboss.server.data.dir: /home/jc/jboss-4.2.2.GA/server/default/data
21:54:57,895 DEBUG [ServerInfo]     java.rmi.server.hostname: 127.0.0.1
21:54:57,895 DEBUG [ServerInfo]     os.arch: amd64
21:54:57,895 DEBUG [ServerInfo]     java.awt.graphicsenv: sun.awt.X11GraphicsEnvironment
21:54:57,895 DEBUG [ServerInfo]     java.ext.dirs: /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/ext
21:54:57,895 DEBUG [ServerInfo]     user.dir: /home/jc/jboss-4.2.2.GA/bin
21:54:57,895 DEBUG [ServerInfo]     line.separator: 

21:54:57,895 DEBUG [ServerInfo]     java.vm.name: Java HotSpot(TM) 64-Bit Server VM
21:54:57,896 DEBUG [ServerInfo]     jboss.server.base.dir: /home/jc/jboss-4.2.2.GA/server
21:54:57,896 DEBUG [ServerInfo]     jboss.server.base.url: file:/home/jc/jboss-4.2.2.GA/server/
21:54:57,896 DEBUG [ServerInfo]     javax.management.builder.initial: org.jboss.mx.server.MBeanServerBuilderImpl
21:54:57,896 DEBUG [ServerInfo]     file.encoding: UTF-8
21:54:57,896 DEBUG [ServerInfo]     java.specification.version: 1.5
21:54:57,896 DEBUG [ServerInfo]     jboss.server.name: default
21:54:57,901 DEBUG [Server] Created system MBean: jboss.system:type=ServerInfo
21:54:57,909 DEBUG [Server] Failed to create xmbean for: org.jboss.system.ServiceController
21:54:57,935 DEBUG [ServiceController] Controller MBean online
21:54:57,936 DEBUG [Server] Created system MBean: jboss.system:service=ServiceController
21:54:58,075 DEBUG [Server] Created system XMBean: jboss.system:service=MainDeployer
21:54:58,076 DEBUG [ServiceController] Creating service jboss.system:service=MainDeployer
21:54:58,083 DEBUG [MainDeployer] Creating jboss.system:service=MainDeployer
21:54:58,106 DEBUG [Files] Failed to delete dir: /home/jc/jboss-4.2.2.GA/server/default/tmp/deploy
21:54:58,108 DEBUG [MainDeployer] Created jboss.system:service=MainDeployer
21:54:58,108 DEBUG [ServiceController] Creating dependent components for: jboss.system:service=MainDeployer dependents are: []
21:54:58,108 DEBUG [ServiceController] starting service jboss.system:service=MainDeployer
21:54:58,109 DEBUG [MainDeployer] Starting jboss.system:service=MainDeployer
21:54:58,109 DEBUG [MainDeployer] Started jboss.system:service=MainDeployer
21:54:58,109 DEBUG [ServiceController] Starting dependent components for: jboss.system:service=MainDeployer dependent components: []
21:54:58,110 DEBUG [Server] Shutdown hook added
21:54:58,215 DEBUG [Server] Created system XMBean: jboss.system:service=JARDeployer
21:54:58,215 DEBUG [ServiceController] Creating service jboss.system:service=JARDeployer
21:54:58,216 DEBUG [JARDeployer] Creating jboss.system:service=JARDeployer
21:54:58,246 DEBUG [JARDeployer] Created jboss.system:service=JARDeployer
21:54:58,246 DEBUG [ServiceController] Creating dependent components for: jboss.system:service=JARDeployer dependents are: []
21:54:58,246 DEBUG [ServiceController] starting service jboss.system:service=JARDeployer
21:54:58,246 DEBUG [JARDeployer] Starting jboss.system:service=JARDeployer
21:54:58,247 DEBUG [MainDeployer] Adding deployer: org.jboss.deployment.JARDeployer@6076ab2f
21:54:58,247 DEBUG [SuffixOrderHelper] Static suffix exists; ignoring request for adding enhanced suffix: 700:.jar
21:54:58,247 DEBUG [JARDeployer] Started jboss.system:service=JARDeployer
21:54:58,248 DEBUG [ServiceController] Starting dependent components for: jboss.system:service=JARDeployer dependent components: []
21:54:58,279 DEBUG [Server] Created system XMBean: jboss.system:service=ServiceDeployer
21:54:58,280 DEBUG [ServiceController] Creating service jboss.system:service=ServiceDeployer
21:54:58,280 DEBUG [SARDeployer] Creating jboss.system:service=ServiceDeployer
21:54:58,296 DEBUG [SARDeployer] Created jboss.system:service=ServiceDeployer
21:54:58,296 DEBUG [ServiceController] Creating dependent components for: jboss.system:service=ServiceDeployer dependents are: []
21:54:58,296 DEBUG [ServiceController] starting service jboss.system:service=ServiceDeployer
21:54:58,296 DEBUG [SARDeployer] Starting jboss.system:service=ServiceDeployer
21:54:58,297 DEBUG [MainDeployer] Adding deployer: org.jboss.deployment.SARDeployer@546c585a
21:54:58,410 DEBUG [SARDeployer] Started jboss.system:service=ServiceDeployer
21:54:58,410 DEBUG [ServiceController] Starting dependent components for: jboss.system:service=ServiceDeployer dependent components: []
21:54:58,410 INFO  [Server] Core system initialized
21:54:58,511 DEBUG [MainDeployer] Starting deployment of package: file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:54:58,511 DEBUG [MainDeployer] Starting deployment (init step) of package at: file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:54:58,511 DEBUG [MainDeployer] Copying file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml -> /home/jc/jboss-4.2.2.GA/server/default/tmp/deploy/tmp32163jboss-service.xml
21:54:58,520 DEBUG [MainDeployer] using deployer org.jboss.deployment.SARDeployer@546c585a
21:54:58,558 DEBUG [SARDeployer] Found classpath element: [classpath: null]
21:54:58,562 DEBUG [SARDeployer] codebase URL is file:/home/jc/jboss-4.2.2.GA/server/default/lib/
21:54:58,562 DEBUG [SARDeployer] listing codebase for archives matching *
21:54:58,565 DEBUG [SARDeployer] URLLister class is org.jboss.net.protocol.file.FileURLLister
21:54:58,572 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossts-common.jar
21:54:58,572 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbosssx.jar
21:54:58,572 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossws-spi.jar
21:54:58,572 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossws-jboss42.jar
21:54:58,572 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/bindingservice-plugin.jar
21:54:58,572 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/mail.jar
21:54:58,572 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossjta.jar
21:54:58,572 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jsr88.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/xmlentitymgr.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/hibernate-annotations.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/servlet-api.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/antlr.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-management.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-serialization.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/hsqldb-plugin.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-saaj.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/bsh-deployer.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossmq.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-common-jdbc-wrapper.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/joesnmp.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jaxen.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/log4j.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/bcel.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-vfs.jar
21:54:58,573 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/hsqldb.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-transaction.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/hibernate3.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jaxrpc.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/commons-codec.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossws-framework.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/quartz.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-srp.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jca.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jsp-api.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossjta-integration.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-remoting-int.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jaxws.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/commons-logging.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/properties-plugin.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/cglib.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/scheduler-plugin-example.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/commons-collections.jar
21:54:58,574 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/el-api.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-ejb3x.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jnpserver.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/activation.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-remoting.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/mail-plugin.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jsr77.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-cache-jdk50.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/bsf.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/autonumber-plugin.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/ejb3-persistence.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/scheduler-plugin.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jpl-pattern.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/javassist.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/commons-httpclient.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-hibernate.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jmx-adaptor-plugin.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/dom4j.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossws-common.jar
21:54:58,575 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-j2ee.jar
21:54:58,576 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jpl-util.jar
21:54:58,576 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/log4j-snmp-appender.jar
21:54:58,576 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/hibernate-entitymanager.jar
21:54:58,576 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-monitoring.jar
21:54:58,576 DEBUG [SARDeployer] deployed classes for file:/home/jc/jboss-4.2.2.GA/server/default/lib/bsh.jar
21:54:58,576 DEBUG [SARDeployer] about to copy 0 local directories
21:54:58,577 DEBUG [SARDeployer] looking for nested deployments in : file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:54:58,579 DEBUG [DeploymentInfo] createLoaderRepository from config: LoaderRepositoryConfig(repositoryName: JMImplementation:service=LoaderRepository,name=Default, repositoryClassName: null, configParserClassName: null, repositoryConfig: null)
21:54:58,579 DEBUG [RepositoryClassLoader] setRepository, repository=org.jboss.mx.loading.UnifiedLoaderRepository3@2fdb7df8, cl=org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=0}
21:54:58,579 DEBUG [RepositoryClassLoader] setRepository, repository=org.jboss.mx.loading.UnifiedLoaderRepository3@2fdb7df8, cl=org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=0}
21:54:58,579 DEBUG [UnifiedLoaderRepository3] Adding org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=0}
21:54:58,581 DEBUG [ClassLoaderUtils] Multiple class loaders found for pkg: 
21:54:58,587 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossts-common.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,691 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbosssx.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,700 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossws-spi.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,706 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossws-jboss42.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,708 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/bindingservice-plugin.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,746 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/mail.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,794 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossjta.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,800 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jsr88.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,801 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/xmlentitymgr.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:58,936 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/hibernate-annotations.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,088 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,094 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/servlet-api.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,122 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/antlr.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,135 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-management.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,141 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-serialization.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,142 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/hsqldb-plugin.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,144 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-saaj.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,145 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/bsh-deployer.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,177 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossmq.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,182 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-common-jdbc-wrapper.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,186 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/joesnmp.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,198 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jaxen.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,216 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/log4j.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,240 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/bcel.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,252 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-vfs.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,282 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/hsqldb.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,287 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-transaction.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,390 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/hibernate3.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,392 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jaxrpc.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,395 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/commons-codec.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,399 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossws-framework.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,418 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/quartz.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,421 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-srp.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,431 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jca.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,437 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jsp-api.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,452 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossjta-integration.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,455 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-remoting-int.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,460 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jaxws.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,463 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/commons-logging.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,464 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/properties-plugin.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,480 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/cglib.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,481 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/scheduler-plugin-example.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,509 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/commons-collections.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,511 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/el-api.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,523 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-ejb3x.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,526 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jnpserver.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,530 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/activation.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,572 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-remoting.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,573 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/mail-plugin.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,575 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-jsr77.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,672 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-cache-jdk50.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,682 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/bsf.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,683 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/autonumber-plugin.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,687 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/ejb3-persistence.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,689 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/scheduler-plugin.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,693 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jpl-pattern.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,720 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/javassist.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,730 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/commons-httpclient.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,741 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-hibernate.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,744 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jmx-adaptor-plugin.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,757 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/dom4j.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,759 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jbossws-common.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,779 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-j2ee.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,780 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jpl-util.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,781 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/log4j-snmp-appender.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,787 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/hibernate-entitymanager.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,790 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/jboss-monitoring.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,800 DEBUG [RepositoryClassLoader] Added url: file:/home/jc/jboss-4.2.2.GA/server/default/lib/bsh.jar, to ucl: org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:54:59,801 DEBUG [MainDeployer] found 0 subpackages of file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:54:59,801 DEBUG [MainDeployer] Watching new file: file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:54:59,801 DEBUG [MainDeployer] create step for deployment file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:54:59,801 DEBUG [SARDeployer] Deploying SAR, create step: url file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:54:59,801 DEBUG [SARDeployer] Registering service UCL=jmx.loading:UCL=716925b0
21:54:59,805 DEBUG [ServiceCreator] About to create bean: jboss.management.local:j2eeType=J2EEDomain,name=Manager with code: org.jboss.management.j2ee.LocalJBossServerDomain
21:54:59,972 DEBUG [ServiceCreator] Created bean: jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:54:59,975 DEBUG [ServiceConfigurator] MainDeployer set to jboss.system:service=MainDeployer in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:54:59,977 DEBUG [ServiceConfigurator] SARDeployer set to jboss.system:service=ServiceDeployer in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:54:59,978 DEBUG [ServiceConfigurator] EARDeployer set to jboss.j2ee:service=EARDeployer in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:54:59,979 DEBUG [ServiceConfigurator] EJBDeployer set to jboss.ejb:service=EJBDeployer in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:54:59,980 DEBUG [ServiceConfigurator] RARDeployer set to jboss.jca:service=RARDeployer in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,038 DEBUG [ServiceConfigurator] CMDeployer set to jboss.jca:service=ConnectionFactoryDeployer in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,040 DEBUG [ServiceConfigurator] WARDeployer set to jboss.web:service=WebServer in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,041 DEBUG [ServiceConfigurator] CARDeployer set to jboss.j2ee:service=ClientDeployer in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,042 DEBUG [ServiceConfigurator] MailService set to jboss:service=Mail in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,043 DEBUG [ServiceConfigurator] JMSService set to jboss.mq:service=DestinationManager in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,045 DEBUG [ServiceConfigurator] JNDIService set to jboss:service=Naming in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,046 DEBUG [ServiceConfigurator] JTAService set to jboss:service=TransactionManager in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,048 DEBUG [ServiceConfigurator] UserTransactionService set to jboss:service=ClientUserTransaction in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,049 DEBUG [ServiceConfigurator] RMI_IIOPService set to jboss:service=CorbaORB in jboss.management.local:j2eeType=J2EEDomain,name=Manager
21:55:00,050 DEBUG [ServiceCreator] About to create xmbean object: jboss:service=AttributePersistenceService with code: org.jboss.system.pm.AttributePersistenceService with descriptor: resource:xmdesc/AttributePersistenceService-xmbean.xml
21:55:00,146 DEBUG [ModelMBeanInvoker] Loaded persistence mgr: org.jboss.mx.persistence.ObjectStreamPersistenceManager
21:55:00,146 DEBUG [ObjectStreamPersistenceManager] load, resource:org.jboss.system.pm.AttributePersistenceService@6f649b44
21:55:00,146 DEBUG [ObjectStreamPersistenceManager] Store file is: /home/jc/jboss-4.2.2.GA/server/default/data/xmbean-attrs/AttributePersistenceService.ser
21:55:00,146 DEBUG [ServiceCreator] Created bean: jboss:service=AttributePersistenceService
21:55:00,147 DEBUG [ServiceCreator] About to create bean: jboss.system:service=ThreadPool with code: org.jboss.util.threadpool.BasicThreadPool
21:55:00,171 DEBUG [ServiceCreator] Created bean: jboss.system:service=ThreadPool
21:55:00,172 DEBUG [ServiceConfigurator] Name set to JBoss System Threads in jboss.system:service=ThreadPool
21:55:00,173 DEBUG [ServiceConfigurator] ThreadGroupName set to System Threads in jboss.system:service=ThreadPool
21:55:00,181 DEBUG [ServiceConfigurator] KeepAliveTime set to 60000 in jboss.system:service=ThreadPool
21:55:00,181 DEBUG [ServiceConfigurator] MaximumPoolSize set to 10 in jboss.system:service=ThreadPool
21:55:00,182 DEBUG [ServiceConfigurator] MaximumQueueSize set to 1000 in jboss.system:service=ThreadPool
21:55:00,184 DEBUG [ServiceConfigurator] BlockingMode set to run in jboss.system:service=ThreadPool
21:55:00,184 DEBUG [ServiceCreator] About to create xmbean object: jboss.system:type=Log4jService,service=Logging with code: org.jboss.logging.Log4jService with descriptor: resource:xmdesc/Log4jService-xmbean.xml
21:55:00,226 DEBUG [ServiceCreator] Created bean: jboss.system:type=Log4jService,service=Logging
21:55:00,227 DEBUG [ServiceConfigurator] ConfigurationURL set to resource:jboss-log4j.xml in jboss.system:type=Log4jService,service=Logging
21:55:00,228 DEBUG [ServiceConfigurator] Log4jQuietMode set to true in jboss.system:type=Log4jService,service=Logging
21:55:00,228 DEBUG [ServiceConfigurator] RefreshPeriod set to 60 in jboss.system:type=Log4jService,service=Logging
21:55:00,229 DEBUG [ServiceCreator] About to create bean: jboss.rmi:type=RMIClassLoader with code: org.jboss.util.property.jmx.SystemPropertyClassValue
21:55:00,237 DEBUG [ServiceCreator] Created bean: jboss.rmi:type=RMIClassLoader
21:55:00,238 DEBUG [ServiceConfigurator] Property set to java.rmi.server.RMIClassLoaderSpi in jboss.rmi:type=RMIClassLoader
21:55:00,238 DEBUG [ServiceConfigurator] ClassName set to org.jboss.system.JBossRMIClassLoader in jboss.rmi:type=RMIClassLoader
21:55:00,239 DEBUG [ServiceCreator] About to create bean: jboss:service=WebService with code: org.jboss.web.WebService
21:55:00,262 DEBUG [ServiceCreator] Created bean: jboss:service=WebService
21:55:00,263 DEBUG [ServiceConfigurator] BindAddress set to 127.0.0.1 in jboss:service=WebService
21:55:00,264 DEBUG [ServiceConfigurator] Port set to 8083 in jboss:service=WebService
21:55:00,265 DEBUG [ServiceConfigurator] Host set to 127.0.0.1 in jboss:service=WebService
21:55:00,266 DEBUG [ServiceConfigurator] DownloadServerClasses set to true in jboss:service=WebService
21:55:00,266 DEBUG [ServiceConfigurator] DownloadResources set to false in jboss:service=WebService
21:55:00,267 DEBUG [ServiceController] recording that jboss:service=WebService depends on jboss.system:service=ThreadPool
21:55:00,267 DEBUG [ServiceConfigurator] considering ThreadPool with object name jboss.system:service=ThreadPool
21:55:00,298 DEBUG [ServiceCreator] About to create xmbean object: jboss:service=NamingBeanImpl with code: org.jnp.server.NamingBeanImpl with descriptor: resource:xmdesc/NamingBean-xmbean.xml
21:55:00,320 DEBUG [ServiceCreator] Created bean: jboss:service=NamingBeanImpl
21:55:00,320 DEBUG [ServiceCreator] About to create xmbean object: jboss:service=Naming with code: org.jboss.naming.NamingService with descriptor: resource:xmdesc/NamingService-xmbean.xml
21:55:00,372 DEBUG [ModelMBeanInvoker] Ignoring obsolete legacy interceptor: org.jboss.mx.interceptor.PersistenceInterceptor2
21:55:00,372 DEBUG [ModelMBeanInvoker] Ignoring obsolete legacy interceptor: org.jboss.mx.interceptor.ModelMBeanInterceptor
21:55:00,372 DEBUG [ModelMBeanInvoker] Ignoring obsolete legacy interceptor: org.jboss.mx.interceptor.ObjectReferenceInterceptor
21:55:00,374 DEBUG [ServiceCreator] Created bean: jboss:service=Naming
21:55:00,374 DEBUG [ServiceConfigurator] CallByValue set to false in jboss:service=Naming
21:55:00,376 DEBUG [ServiceConfigurator] Port set to 1099 in jboss:service=Naming
21:55:00,387 DEBUG [ServiceConfigurator] BindAddress set to 127.0.0.1 in jboss:service=Naming
21:55:00,388 DEBUG [ServiceConfigurator] RmiPort set to 1098 in jboss:service=Naming
21:55:00,389 DEBUG [ServiceConfigurator] RmiBindAddress set to 127.0.0.1 in jboss:service=Naming
21:55:00,390 DEBUG [ServiceController] recording that jboss:service=Naming depends on jboss.system:service=ThreadPool
21:55:00,390 DEBUG [ServiceConfigurator] considering LookupPool with object name jboss.system:service=ThreadPool
21:55:00,522 DEBUG [ServiceController] recording that jboss:service=Naming depends on jboss:service=NamingBeanImpl
21:55:00,522 DEBUG [ServiceConfigurator] considering Naming with object name jboss:service=NamingBeanImpl
21:55:00,526 DEBUG [ServiceCreator] About to create xmbean object: jboss:service=JNDIView with code: org.jboss.naming.JNDIView with descriptor: resource:xmdesc/JNDIView-xmbean.xml
21:55:00,574 DEBUG [ServiceCreator] Created bean: jboss:service=JNDIView
21:55:00,575 DEBUG [ServiceConfigurator] HANamingService set to jboss:service=HAJNDI in jboss:service=JNDIView
21:55:00,576 DEBUG [ServiceCreator] About to create bean: jboss.security:service=SecurityConfig with code: org.jboss.security.plugins.SecurityConfig
21:55:00,590 DEBUG [ServiceCreator] Created bean: jboss.security:service=SecurityConfig
21:55:00,591 DEBUG [ServiceConfigurator] LoginConfig set to jboss.security:service=XMLLoginConfig in jboss.security:service=SecurityConfig
21:55:00,592 DEBUG [ServiceCreator] About to create bean: jboss.security:service=XMLLoginConfig with code: org.jboss.security.auth.login.XMLLoginConfig
21:55:00,603 DEBUG [ServiceCreator] Created bean: jboss.security:service=XMLLoginConfig
21:55:00,603 DEBUG [ServiceConfigurator] ConfigResource set to login-config.xml in jboss.security:service=XMLLoginConfig
21:55:00,604 DEBUG [ServiceCreator] About to create bean: jboss.security:service=JaasSecurityManager with code: org.jboss.security.plugins.JaasSecurityManagerService
21:55:00,639 DEBUG [ServiceCreator] Created bean: jboss.security:service=JaasSecurityManager
21:55:00,639 DEBUG [ServiceConfigurator] ServerMode set to true in jboss.security:service=JaasSecurityManager
21:55:00,640 DEBUG [ServiceConfigurator] SecurityManagerClassName set to org.jboss.security.plugins.JaasSecurityManager in jboss.security:service=JaasSecurityManager
21:55:00,641 DEBUG [ServiceConfigurator] DefaultUnauthenticatedPrincipal set to anonymous in jboss.security:service=JaasSecurityManager
21:55:00,641 DEBUG [ServiceConfigurator] DefaultCacheTimeout set to 1800 in jboss.security:service=JaasSecurityManager
21:55:00,641 DEBUG [ServiceConfigurator] DefaultCacheResolution set to 60 in jboss.security:service=JaasSecurityManager
21:55:00,642 DEBUG [ServiceConfigurator] DeepCopySubjectMode set to false in jboss.security:service=JaasSecurityManager
21:55:00,642 DEBUG [JaasSecurityManagerService] setDeepCopySubjectMode=false
21:55:00,642 DEBUG [ServiceCreator] About to create bean: jboss:service=XidFactory with code: org.jboss.tm.XidFactory
21:55:00,845 DEBUG [ServiceCreator] Created bean: jboss:service=XidFactory
21:55:00,846 DEBUG [ServiceCreator] About to create bean: jboss:service=TransactionManager with code: com.arjuna.ats.jbossatx.jta.TransactionManagerService
21:55:01,081 DEBUG [ServiceCreator] Created bean: jboss:service=TransactionManager
21:55:01,081 DEBUG [ServiceConfigurator] TransactionTimeout set to 300 in jboss:service=TransactionManager
21:55:01,082 DEBUG [ServiceConfigurator] ObjectStoreDir set to /home/jc/jboss-4.2.2.GA/server/default/data/tx-object-store in jboss:service=TransactionManager
21:55:01,082 DEBUG [ServiceCreator] About to create xmbean object: jboss:service=ClientUserTransaction with code: org.jboss.tm.usertx.server.ClientUserTransactionService with descriptor: resource:xmdesc/ClientUserTransaction-xmbean.xml
21:55:01,110 DEBUG [ServiceCreator] Created bean: jboss:service=ClientUserTransaction
21:55:01,111 DEBUG [ServiceCreator] About to create bean: jboss:service=proxyFactory,target=ClientUserTransactionFactory with code: org.jboss.invocation.jrmp.server.JRMPProxyFactory
21:55:01,124 DEBUG [ServiceCreator] Created bean: jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,125 DEBUG [ServiceConfigurator] InvokerName set to jboss:service=invoker,type=jrmp in jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,132 DEBUG [ServiceConfigurator] TargetName set to jboss:service=ClientUserTransaction in jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,133 DEBUG [ServiceConfigurator] JndiName set to UserTransactionSessionFactory in jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,135 DEBUG [ServiceConfigurator] ExportedInterface set to interface org.jboss.tm.usertx.interfaces.UserTransactionSessionFactory in jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,141 DEBUG [ServiceConfigurator] ClientInterceptors set to [interceptors: null] in jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,144 DEBUG [JRMPProxyFactory] added interceptor type: class org.jboss.proxy.ClientMethodInterceptor
21:55:01,201 DEBUG [JRMPProxyFactory] added interceptor type: class org.jboss.invocation.InvokerInterceptor
21:55:01,202 DEBUG [ServiceController] recording that jboss:service=proxyFactory,target=ClientUserTransactionFactory depends on jboss:service=invoker,type=jrmp
21:55:01,202 DEBUG [ServiceConfigurator] considering <anonymous> with object name jboss:service=invoker,type=jrmp
21:55:01,202 DEBUG [ServiceController] recording that jboss:service=ClientUserTransaction depends on jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,203 DEBUG [ServiceConfigurator] considering <anonymous> with object name jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,203 DEBUG [ServiceCreator] About to create bean: jboss:service=proxyFactory,target=ClientUserTransaction with code: org.jboss.invocation.jrmp.server.JRMPProxyFactory
21:55:01,207 DEBUG [ServiceCreator] Created bean: jboss:service=proxyFactory,target=ClientUserTransaction
21:55:01,208 DEBUG [ServiceConfigurator] InvokerName set to jboss:service=invoker,type=jrmp in jboss:service=proxyFactory,target=ClientUserTransaction
21:55:01,209 DEBUG [ServiceConfigurator] TargetName set to jboss:service=ClientUserTransaction in jboss:service=proxyFactory,target=ClientUserTransaction
21:55:01,211 DEBUG [ServiceConfigurator] ExportedInterface set to interface org.jboss.tm.usertx.interfaces.UserTransactionSession in jboss:service=proxyFactory,target=ClientUserTransaction
21:55:01,214 DEBUG [ServiceConfigurator] ClientInterceptors set to [interceptors: null] in jboss:service=proxyFactory,target=ClientUserTransaction
21:55:01,214 DEBUG [JRMPProxyFactory] added interceptor type: class org.jboss.proxy.ClientMethodInterceptor
21:55:01,214 DEBUG [JRMPProxyFactory] added interceptor type: class org.jboss.invocation.InvokerInterceptor
21:55:01,214 DEBUG [ServiceController] recording that jboss:service=proxyFactory,target=ClientUserTransaction depends on jboss:service=invoker,type=jrmp
21:55:01,214 DEBUG [ServiceConfigurator] considering <anonymous> with object name jboss:service=invoker,type=jrmp
21:55:01,215 DEBUG [ServiceController] recording that jboss:service=ClientUserTransaction depends on jboss:service=proxyFactory,target=ClientUserTransaction
21:55:01,215 DEBUG [ServiceConfigurator] considering TxProxyName with object name jboss:service=proxyFactory,target=ClientUserTransaction
21:55:01,215 DEBUG [ServiceCreator] About to create bean: jboss:service=invoker,type=unified with code: org.jboss.invocation.unified.server.UnifiedInvoker
21:55:01,230 DEBUG [ServiceCreator] Created bean: jboss:service=invoker,type=unified
21:55:01,231 DEBUG [ServiceController] recording that jboss:service=invoker,type=unified depends on jboss:service=TransactionManager
21:55:01,231 DEBUG [ServiceConfigurator] considering <anonymous> with object name jboss:service=TransactionManager
21:55:01,231 DEBUG [ServiceController] recording that jboss:service=invoker,type=unified depends on jboss.remoting:service=Connector,transport=socket
21:55:01,231 DEBUG [ServiceConfigurator] considering <anonymous> with object name jboss.remoting:service=Connector,transport=socket
21:55:01,231 DEBUG [ServiceCreator] About to create bean: jboss:service=invoker,type=jrmp with code: org.jboss.invocation.jrmp.server.JRMPInvoker
21:55:01,245 DEBUG [ServiceCreator] Created bean: jboss:service=invoker,type=jrmp
21:55:01,245 DEBUG [ServiceConfigurator] RMIObjectPort set to 4444 in jboss:service=invoker,type=jrmp
21:55:01,247 DEBUG [ServiceConfigurator] ServerAddress set to 127.0.0.1 in jboss:service=invoker,type=jrmp
21:55:01,248 DEBUG [ServiceController] recording that jboss:service=invoker,type=jrmp depends on jboss:service=TransactionManager
21:55:01,248 DEBUG [ServiceConfigurator] considering <anonymous> with object name jboss:service=TransactionManager
21:55:01,248 DEBUG [ServiceCreator] About to create bean: jboss:service=invoker,type=local with code: org.jboss.invocation.local.LocalInvoker
21:55:01,253 DEBUG [ServiceCreator] Created bean: jboss:service=invoker,type=local
21:55:01,253 DEBUG [ServiceController] recording that jboss:service=invoker,type=local depends on jboss:service=TransactionManager
21:55:01,253 DEBUG [ServiceConfigurator] considering <anonymous> with object name jboss:service=TransactionManager
21:55:01,254 DEBUG [ServiceCreator] About to create bean: jboss:service=invoker,type=pooled with code: org.jboss.invocation.pooled.server.PooledInvoker
21:55:01,274 DEBUG [ServiceCreator] Created bean: jboss:service=invoker,type=pooled
21:55:01,274 DEBUG [ServiceConfigurator] NumAcceptThreads set to 1 in jboss:service=invoker,type=pooled
21:55:01,274 DEBUG [ServiceConfigurator] MaxPoolSize set to 300 in jboss:service=invoker,type=pooled
21:55:01,275 DEBUG [ServiceConfigurator] ClientMaxPoolSize set to 300 in jboss:service=invoker,type=pooled
21:55:01,275 DEBUG [ServiceConfigurator] SocketTimeout set to 60000 in jboss:service=invoker,type=pooled
21:55:01,276 DEBUG [ServiceConfigurator] ServerBindAddress set to 127.0.0.1 in jboss:service=invoker,type=pooled
21:55:01,276 DEBUG [ServiceConfigurator] ServerBindPort set to 4445 in jboss:service=invoker,type=pooled
21:55:01,277 DEBUG [ServiceConfigurator] ClientConnectAddress set to 127.0.0.1 in jboss:service=invoker,type=pooled
21:55:01,278 DEBUG [ServiceConfigurator] ClientConnectPort set to 0 in jboss:service=invoker,type=pooled
21:55:01,279 DEBUG [ServiceConfigurator] ClientRetryCount set to 1 in jboss:service=invoker,type=pooled
21:55:01,279 DEBUG [ServiceConfigurator] EnableTcpNoDelay set to false in jboss:service=invoker,type=pooled
21:55:01,280 DEBUG [ServiceController] recording that jboss:service=invoker,type=pooled depends on jboss:service=TransactionManager
21:55:01,280 DEBUG [ServiceConfigurator] considering TransactionManagerService with object name jboss:service=TransactionManager
21:55:01,280 DEBUG [ServiceCreator] About to create bean: jboss.remoting:service=NetworkRegistry with code: org.jboss.remoting.network.NetworkRegistry
21:55:01,475 WARN  [BasicMBeanRegistry] javax.management.MBeanRegistrationException: preRegister() failed: [ObjectName='jboss.remoting:service=NetworkRegistry', Class=org.jboss.remoting.network.NetworkRegistry (org.jboss.remoting.network.NetworkRegistry@f8622f3)]
21:55:01,477 DEBUG [ServiceController] removing service: jboss:service=invoker,type=pooled
21:55:01,477 DEBUG [ServiceController] removing already unregistered jboss:service=invoker,type=pooled from server
21:55:01,478 DEBUG [ServiceController] removing service: jboss:service=invoker,type=local
21:55:01,478 DEBUG [ServiceController] removing already unregistered jboss:service=invoker,type=local from server
21:55:01,478 DEBUG [ServiceController] removing service: jboss:service=invoker,type=jrmp
21:55:01,478 DEBUG [ServiceController] no need to remove jboss:service=invoker,type=jrmp from server
21:55:01,478 DEBUG [ServiceController] removing service: jboss:service=invoker,type=unified
21:55:01,478 DEBUG [ServiceController] Removing context for nonexistent service it is no longer recording dependencies: ObjectName: jboss.remoting:service=Connector,transport=socket
  State: NOTYETINSTALLED

21:55:01,478 DEBUG [ServiceController] removing already unregistered jboss:service=invoker,type=unified from server
21:55:01,478 DEBUG [ServiceController] removing service: jboss:service=proxyFactory,target=ClientUserTransaction
21:55:01,479 DEBUG [ServiceController] no need to remove jboss:service=proxyFactory,target=ClientUserTransaction from server
21:55:01,479 DEBUG [ServiceController] removing service: jboss:service=proxyFactory,target=ClientUserTransactionFactory
21:55:01,479 DEBUG [ServiceController] Removing context for nonexistent service it is no longer recording dependencies: ObjectName: jboss:service=invoker,type=jrmp
  State: NOTYETINSTALLED

21:55:01,479 DEBUG [ServiceController] no need to remove jboss:service=proxyFactory,target=ClientUserTransactionFactory from server
21:55:01,479 DEBUG [ServiceController] removing service: jboss:service=ClientUserTransaction
21:55:01,479 DEBUG [ServiceController] Removing context for nonexistent service it is no longer recording dependencies: ObjectName: jboss:service=proxyFactory,target=ClientUserTransactionFactory
  State: NOTYETINSTALLED

21:55:01,479 DEBUG [ServiceController] Removing context for nonexistent service it is no longer recording dependencies: ObjectName: jboss:service=proxyFactory,target=ClientUserTransaction
  State: NOTYETINSTALLED

21:55:01,479 DEBUG [ServiceController] removing already unregistered jboss:service=ClientUserTransaction from server
21:55:01,479 DEBUG [ServiceController] removing service: jboss:service=TransactionManager
21:55:01,480 DEBUG [ServiceController] removing already unregistered jboss:service=TransactionManager from server
21:55:01,480 DEBUG [ServiceController] removing service: jboss.security:service=JaasSecurityManager
21:55:01,480 DEBUG [ServiceController] removing already unregistered jboss.security:service=JaasSecurityManager from server
21:55:01,480 DEBUG [ServiceController] removing service: jboss.security:service=XMLLoginConfig
21:55:01,480 DEBUG [ServiceController] removing already unregistered jboss.security:service=XMLLoginConfig from server
21:55:01,480 DEBUG [ServiceController] removing service: jboss.security:service=SecurityConfig
21:55:01,480 DEBUG [ServiceController] removing already unregistered jboss.security:service=SecurityConfig from server
21:55:01,481 DEBUG [ServiceController] removing service: jboss:service=JNDIView
21:55:01,481 DEBUG [ServiceController] removing already unregistered jboss:service=JNDIView from server
21:55:01,481 DEBUG [ServiceController] removing service: jboss:service=Naming
21:55:01,481 DEBUG [ServiceController] removing already unregistered jboss:service=Naming from server
21:55:01,483 DEBUG [ServiceController] removing service: jboss:service=WebService
21:55:01,483 DEBUG [ServiceController] removing already unregistered jboss:service=WebService from server
21:55:01,483 DEBUG [ServiceController] removing service: jboss.system:type=Log4jService,service=Logging
21:55:01,483 DEBUG [ServiceController] removing already unregistered jboss.system:type=Log4jService,service=Logging from server
21:55:01,495 DEBUG [ServiceController] removing service: jboss:service=AttributePersistenceService
21:55:01,495 DEBUG [ServiceController] removing already unregistered jboss:service=AttributePersistenceService from server
21:55:01,498 DEBUG [NestedThrowable] org.jboss.util.NestedThrowable.parentTraceEnabled=true
21:55:01,498 DEBUG [NestedThrowable] org.jboss.util.NestedThrowable.nestedTraceEnabled=false
21:55:01,498 DEBUG [NestedThrowable] org.jboss.util.NestedThrowable.detectDuplicateNesting=true
21:55:01,499 DEBUG [SARDeployer] create operation failed for package file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
org.jboss.deployment.DeploymentException: - nested throwable: (java.lang.reflect.InvocationTargetException)
	at org.jboss.system.ServiceConfigurator.install(ServiceConfigurator.java:196)
	at org.jboss.system.ServiceController.install(ServiceController.java:226)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:86)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.util.MBeanProxyExt.invoke(MBeanProxyExt.java:210)
	at $Proxy4.install(Unknown Source)
	at org.jboss.deployment.SARDeployer.create(SARDeployer.java:249)
	at org.jboss.deployment.MainDeployer.create(MainDeployer.java:969)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:818)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:782)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:766)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.interceptor.AbstractInterceptor.invoke(AbstractInterceptor.java:133)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.interceptor.ModelMBeanOperationInterceptor.invoke(ModelMBeanOperationInterceptor.java:142)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.util.MBeanProxyExt.invoke(MBeanProxyExt.java:210)
	at $Proxy5.deploy(Unknown Source)
	at org.jboss.system.server.ServerImpl.doStart(ServerImpl.java:482)
	at org.jboss.system.server.ServerImpl.start(ServerImpl.java:362)
	at org.jboss.Main.boot(Main.java:200)
	at org.jboss.Main$1.run(Main.java:508)
	at java.lang.Thread.run(Thread.java:595)
Caused by: java.lang.reflect.InvocationTargetException
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1451)
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1350)
	at org.jboss.mx.server.MBeanServerImpl.createMBean(MBeanServerImpl.java:345)
	at org.jboss.system.ServiceCreator.install(ServiceCreator.java:157)
	at org.jboss.system.ServiceConfigurator.internalInstall(ServiceConfigurator.java:451)
	at org.jboss.system.ServiceConfigurator.install(ServiceConfigurator.java:171)
	... 36 more
Caused by: javax.management.MBeanException
	at org.jboss.mx.interceptor.ReflectedDispatcher.handleInvocationExceptions(ReflectedDispatcher.java:180)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:163)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.interceptor.AbstractInterceptor.invoke(AbstractInterceptor.java:133)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.interceptor.ModelMBeanOperationInterceptor.invoke(ModelMBeanOperationInterceptor.java:142)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.server.MBeanServerImpl$3.run(MBeanServerImpl.java:1422)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1417)
	... 41 more
Caused by: javax.management.MBeanRegistrationException: preRegister() failed: [ObjectName='jboss.remoting:service=NetworkRegistry', Class=org.jboss.remoting.network.NetworkRegistry (org.jboss.remoting.network.NetworkRegistry@f8622f3)]
	at org.jboss.mx.server.registry.BasicMBeanRegistry.invokePreRegister(BasicMBeanRegistry.java:713)
	at org.jboss.mx.server.registry.BasicMBeanRegistry.registerMBean(BasicMBeanRegistry.java:211)
	at sun.reflect.GeneratedMethodAccessor1.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	... 51 more
Caused by: java.lang.RuntimeException: Exception creating identity: phoenix: phoenix
	at org.jboss.remoting.ident.Identity.get(Identity.java:211)
	at org.jboss.remoting.network.NetworkRegistry.preRegister(NetworkRegistry.java:268)
	at org.jboss.mx.server.AbstractMBeanInvoker.invokePreRegister(AbstractMBeanInvoker.java:966)
	at org.jboss.mx.modelmbean.ModelMBeanInvoker.invokePreRegister(ModelMBeanInvoker.java:489)
	at org.jboss.mx.server.AbstractMBeanInvoker.preRegister(AbstractMBeanInvoker.java:654)
	at org.jboss.mx.server.registry.BasicMBeanRegistry.invokePreRegister(BasicMBeanRegistry.java:697)
	... 56 more
21:55:01,503 DEBUG [SARDeployer] Unregistering service UCL=jmx.loading:UCL=716925b0
21:55:01,503 DEBUG [UnifiedLoaderRepository3] UnifiedLoaderRepository removed(true) org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:55:01,510 ERROR [MainDeployer] Could not create deployment: file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
org.jboss.deployment.DeploymentException: - nested throwable: (java.lang.reflect.InvocationTargetException)
	at org.jboss.system.ServiceConfigurator.install(ServiceConfigurator.java:196)
	at org.jboss.system.ServiceController.install(ServiceController.java:226)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:86)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.util.MBeanProxyExt.invoke(MBeanProxyExt.java:210)
	at $Proxy4.install(Unknown Source)
	at org.jboss.deployment.SARDeployer.create(SARDeployer.java:249)
	at org.jboss.deployment.MainDeployer.create(MainDeployer.java:969)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:818)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:782)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:766)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.interceptor.AbstractInterceptor.invoke(AbstractInterceptor.java:133)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.interceptor.ModelMBeanOperationInterceptor.invoke(ModelMBeanOperationInterceptor.java:142)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.util.MBeanProxyExt.invoke(MBeanProxyExt.java:210)
	at $Proxy5.deploy(Unknown Source)
	at org.jboss.system.server.ServerImpl.doStart(ServerImpl.java:482)
	at org.jboss.system.server.ServerImpl.start(ServerImpl.java:362)
	at org.jboss.Main.boot(Main.java:200)
	at org.jboss.Main$1.run(Main.java:508)
	at java.lang.Thread.run(Thread.java:595)
Caused by: java.lang.reflect.InvocationTargetException
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1451)
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1350)
	at org.jboss.mx.server.MBeanServerImpl.createMBean(MBeanServerImpl.java:345)
	at org.jboss.system.ServiceCreator.install(ServiceCreator.java:157)
	at org.jboss.system.ServiceConfigurator.internalInstall(ServiceConfigurator.java:451)
	at org.jboss.system.ServiceConfigurator.install(ServiceConfigurator.java:171)
	... 36 more
Caused by: javax.management.MBeanException
	at org.jboss.mx.interceptor.ReflectedDispatcher.handleInvocationExceptions(ReflectedDispatcher.java:180)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:163)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.interceptor.AbstractInterceptor.invoke(AbstractInterceptor.java:133)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.interceptor.ModelMBeanOperationInterceptor.invoke(ModelMBeanOperationInterceptor.java:142)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.server.MBeanServerImpl$3.run(MBeanServerImpl.java:1422)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1417)
	... 41 more
Caused by: javax.management.MBeanRegistrationException: preRegister() failed: [ObjectName='jboss.remoting:service=NetworkRegistry', Class=org.jboss.remoting.network.NetworkRegistry (org.jboss.remoting.network.NetworkRegistry@f8622f3)]
	at org.jboss.mx.server.registry.BasicMBeanRegistry.invokePreRegister(BasicMBeanRegistry.java:713)
	at org.jboss.mx.server.registry.BasicMBeanRegistry.registerMBean(BasicMBeanRegistry.java:211)
	at sun.reflect.GeneratedMethodAccessor1.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	... 51 more
Caused by: java.lang.RuntimeException: Exception creating identity: phoenix: phoenix
	at org.jboss.remoting.ident.Identity.get(Identity.java:211)
	at org.jboss.remoting.network.NetworkRegistry.preRegister(NetworkRegistry.java:268)
	at org.jboss.mx.server.AbstractMBeanInvoker.invokePreRegister(AbstractMBeanInvoker.java:966)
	at org.jboss.mx.modelmbean.ModelMBeanInvoker.invokePreRegister(ModelMBeanInvoker.java:489)
	at org.jboss.mx.server.AbstractMBeanInvoker.preRegister(AbstractMBeanInvoker.java:654)
	at org.jboss.mx.server.registry.BasicMBeanRegistry.invokePreRegister(BasicMBeanRegistry.java:697)
	... 56 more
21:55:01,513 DEBUG [Server] Failed to start
org.jboss.deployment.DeploymentException: - nested throwable: (java.lang.reflect.InvocationTargetException)
	at org.jboss.system.ServiceConfigurator.install(ServiceConfigurator.java:196)
	at org.jboss.system.ServiceController.install(ServiceController.java:226)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:86)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.util.MBeanProxyExt.invoke(MBeanProxyExt.java:210)
	at $Proxy4.install(Unknown Source)
	at org.jboss.deployment.SARDeployer.create(SARDeployer.java:249)
	at org.jboss.deployment.MainDeployer.create(MainDeployer.java:969)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:818)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:782)
	at org.jboss.deployment.MainDeployer.deploy(MainDeployer.java:766)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.interceptor.AbstractInterceptor.invoke(AbstractInterceptor.java:133)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.interceptor.ModelMBeanOperationInterceptor.invoke(ModelMBeanOperationInterceptor.java:142)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.util.MBeanProxyExt.invoke(MBeanProxyExt.java:210)
	at $Proxy5.deploy(Unknown Source)
	at org.jboss.system.server.ServerImpl.doStart(ServerImpl.java:482)
	at org.jboss.system.server.ServerImpl.start(ServerImpl.java:362)
	at org.jboss.Main.boot(Main.java:200)
	at org.jboss.Main$1.run(Main.java:508)
	at java.lang.Thread.run(Thread.java:595)
Caused by: java.lang.reflect.InvocationTargetException
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1451)
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1350)
	at org.jboss.mx.server.MBeanServerImpl.createMBean(MBeanServerImpl.java:345)
	at org.jboss.system.ServiceCreator.install(ServiceCreator.java:157)
	at org.jboss.system.ServiceConfigurator.internalInstall(ServiceConfigurator.java:451)
	at org.jboss.system.ServiceConfigurator.install(ServiceConfigurator.java:171)
	... 36 more
Caused by: javax.management.MBeanException
	at org.jboss.mx.interceptor.ReflectedDispatcher.handleInvocationExceptions(ReflectedDispatcher.java:180)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:163)
	at org.jboss.mx.server.Invocation.dispatch(Invocation.java:94)
	at org.jboss.mx.interceptor.AbstractInterceptor.invoke(AbstractInterceptor.java:133)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.interceptor.ModelMBeanOperationInterceptor.invoke(ModelMBeanOperationInterceptor.java:142)
	at org.jboss.mx.server.Invocation.invoke(Invocation.java:88)
	at org.jboss.mx.server.AbstractMBeanInvoker.invoke(AbstractMBeanInvoker.java:264)
	at org.jboss.mx.server.MBeanServerImpl.invoke(MBeanServerImpl.java:659)
	at org.jboss.mx.server.MBeanServerImpl$3.run(MBeanServerImpl.java:1422)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.jboss.mx.server.MBeanServerImpl.registerMBean(MBeanServerImpl.java:1417)
	... 41 more
Caused by: javax.management.MBeanRegistrationException: preRegister() failed: [ObjectName='jboss.remoting:service=NetworkRegistry', Class=org.jboss.remoting.network.NetworkRegistry (org.jboss.remoting.network.NetworkRegistry@f8622f3)]
	at org.jboss.mx.server.registry.BasicMBeanRegistry.invokePreRegister(BasicMBeanRegistry.java:713)
	at org.jboss.mx.server.registry.BasicMBeanRegistry.registerMBean(BasicMBeanRegistry.java:211)
	at sun.reflect.GeneratedMethodAccessor1.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.jboss.mx.interceptor.ReflectedDispatcher.invoke(ReflectedDispatcher.java:155)
	... 51 more
Caused by: java.lang.RuntimeException: Exception creating identity: phoenix: phoenix
	at org.jboss.remoting.ident.Identity.get(Identity.java:211)
	at org.jboss.remoting.network.NetworkRegistry.preRegister(NetworkRegistry.java:268)
	at org.jboss.mx.server.AbstractMBeanInvoker.invokePreRegister(AbstractMBeanInvoker.java:966)
	at org.jboss.mx.modelmbean.ModelMBeanInvoker.invokePreRegister(ModelMBeanInvoker.java:489)
	at org.jboss.mx.server.AbstractMBeanInvoker.preRegister(AbstractMBeanInvoker.java:654)
	at org.jboss.mx.server.registry.BasicMBeanRegistry.invokePreRegister(BasicMBeanRegistry.java:697)
	... 56 more
21:55:01,678 INFO  [Server] Runtime shutdown hook called, forceHalt: true
21:55:01,679 INFO  [Server] JBoss SHUTDOWN: Undeploying all packages
21:55:01,679 DEBUG [MainDeployer] Undeploying file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml, isShutdown=true
21:55:01,679 DEBUG [SARDeployer] undeploying document file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:55:01,679 DEBUG [RepositoryClassLoader] Unregistering cl=org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:55:01,679 DEBUG [UnifiedLoaderRepository3] UnifiedLoaderRepository removed(false) org.jboss.mx.loading.UnifiedClassLoader3@716925b0{ url=null ,addedOrder=2}
21:55:01,680 DEBUG [DeploymentInfo] Cleaned Deployment: file:/home/jc/jboss-4.2.2.GA/server/default/tmp/deploy/tmp32163jboss-service.xml
21:55:01,680 DEBUG [MainDeployer] Undeployed file:/home/jc/jboss-4.2.2.GA/server/default/conf/jboss-service.xml
21:55:01,680 DEBUG [MainDeployer] Undeployed 1 deployed packages
21:55:01,680 DEBUG [Server] Shutting down all services
21:55:01,680 DEBUG [ServiceController] Stopping 9 services
21:55:01,680 DEBUG [ServiceController] stopping service: jboss.system:service=ServiceDeployer
21:55:01,680 DEBUG [ServiceController] stopping dependent services for: jboss.system:service=ServiceDeployer dependent services are: []
21:55:01,681 DEBUG [SARDeployer] Stopping jboss.system:service=ServiceDeployer
21:55:01,681 DEBUG [MainDeployer] Removing deployer: org.jboss.deployment.SARDeployer@546c585a
21:55:01,681 DEBUG [SARDeployer] Stopped jboss.system:service=ServiceDeployer
21:55:01,681 DEBUG [ServiceController] destroying service: jboss.system:service=ServiceDeployer
21:55:01,681 DEBUG [ServiceController] destroying dependent services for: jboss.system:service=ServiceDeployer dependent services are: []
21:55:01,681 DEBUG [SARDeployer] Destroying jboss.system:service=ServiceDeployer
21:55:01,681 DEBUG [SARDeployer] Destroyed jboss.system:service=ServiceDeployer
21:55:01,682 DEBUG [ServiceController] removing service: jboss.system:service=ServiceDeployer
21:55:01,682 DEBUG [ServiceController] removing jboss.system:service=ServiceDeployer from server
21:55:01,682 DEBUG [ServiceController] stopping service: jboss.system:service=JARDeployer
21:55:01,682 DEBUG [ServiceController] stopping dependent services for: jboss.system:service=JARDeployer dependent services are: []
21:55:01,682 DEBUG [JARDeployer] Stopping jboss.system:service=JARDeployer
21:55:01,682 DEBUG [JARDeployer] Stopped jboss.system:service=JARDeployer
21:55:01,682 DEBUG [ServiceController] destroying service: jboss.system:service=JARDeployer
21:55:01,682 DEBUG [ServiceController] destroying dependent services for: jboss.system:service=JARDeployer dependent services are: []
21:55:01,682 DEBUG [JARDeployer] Destroying jboss.system:service=JARDeployer
21:55:01,682 DEBUG [JARDeployer] Destroyed jboss.system:service=JARDeployer
21:55:01,683 DEBUG [ServiceController] removing service: jboss.system:service=JARDeployer
21:55:01,683 DEBUG [ServiceController] removing jboss.system:service=JARDeployer from server
21:55:01,683 DEBUG [ServiceController] stopping service: jboss.system:service=MainDeployer
21:55:01,683 DEBUG [ServiceController] stopping dependent services for: jboss.system:service=MainDeployer dependent services are: []
21:55:01,683 DEBUG [MainDeployer] Stopping jboss.system:service=MainDeployer
21:55:01,683 DEBUG [MainDeployer] Stopped jboss.system:service=MainDeployer
21:55:01,683 DEBUG [ServiceController] destroying service: jboss.system:service=MainDeployer
21:55:01,683 DEBUG [ServiceController] destroying dependent services for: jboss.system:service=MainDeployer dependent services are: []
21:55:01,683 DEBUG [MainDeployer] Destroying jboss.system:service=MainDeployer
21:55:01,683 DEBUG [MainDeployer] Destroyed jboss.system:service=MainDeployer
21:55:01,683 DEBUG [ServiceController] removing service: jboss.system:service=MainDeployer
21:55:01,684 DEBUG [ServiceController] removing jboss.system:service=MainDeployer from server
21:55:01,684 DEBUG [ServiceController] Stopped 3 services
21:55:01,684 DEBUG [Server] Deleting server tmp/deploy directory
21:55:01,685 INFO  [Server] Shutdown complete

```

---

### Post by cybergalvez on 2007-11-23
Anyone out there know jboss?  Can anyone help me with this?
Jose

---

### Post by cybergalvez on 2007-11-26
I got the answer from the jboss folks, apparently my /etc/hosts file did not have my computer name in it, which was preventing jboss from binding correctly
Jose

---

### Post by sivlardemalle on 2008-01-12
Solution confirmed!!! :-) Thanks

---

### Post by sivlardemalle on 2008-01-12
also, try to run jboss with -c minimal. That should work without the hosts solution (if that doesn't work it might point you to another solution)

---

