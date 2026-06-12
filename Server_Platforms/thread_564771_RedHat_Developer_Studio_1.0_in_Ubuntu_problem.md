---
title: "RedHat Developer Studio 1.0 in Ubuntu problem"
date: 2007-10-01
forum: Server Platforms
---

### Post by ismakun on 2007-10-01
Im currently working in a project for my Database class using mysql, JSP and servlets. I was using RedHat Developer Studio 1.0 on XP but decided to change to linux Ubuntu. I went through all the hassles but managed to install the program but the integrated JBOSS server wont work. I tried exadel and had the same problem. Maybe there is something in ubuntu blocking the server. Has anyone tried this program or had the same problem and repaired it? Im driving my self mad, I need to start on the second phase of my project soon. I think Jboss runs on apache so exadel. Any bit of help is apreciated.

Thanks in advance,
Ismael

---

### Post by ismakun on 2007-10-01
This is what I get at the console:

log4j:ERROR Failed to create directory structure: /usr/local/rhdevstudio/jboss-eap/jboss-as/server/default/log
log4j:ERROR setFile(null,false) call failed.
java.io.FileNotFoundException: /usr/local/rhdevstudio/jboss-eap/jboss-as/server/default/log/boot.log (No such file or directory)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:102)
	at org.apache.log4j.FileAppender.setFile(FileAppender.java:289)
	at org.apache.log4j.FileAppender.activateOptions(FileAppender.java:163)
	at org.apache.log4j.config.PropertySetter.activate(PropertySetter.java:256)
	at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:132)
	at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:96)
	at org.apache.log4j.PropertyConfigurator.parseAppender(PropertyConfigurator.java:654)
	at org.apache.log4j.PropertyConfigurator.parseCategory(PropertyConfigurator.java:612)
	at org.apache.log4j.PropertyConfigurator.configureRootCategory(PropertyConfigurator.java:509)
	at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:415)
	at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:441)
	at org.apache.log4j.helpers.OptionConverter.selectAndConfigure(OptionConverter.java:470)
	at org.apache.log4j.LogManager.<clinit>(LogManager.java:122)
	at org.jboss.logging.Log4jLoggerPlugin.init(Log4jLoggerPlugin.java:63)
	at org.jboss.logging.Logger.getDelegatePlugin(Logger.java:338)
	at org.jboss.logging.Logger.<init>(Logger.java:96)
	at org.jboss.logging.Logger.getLogger(Logger.java:309)
	at org.jboss.system.server.ServerImpl.doInit(ServerImpl.java:166)
	at org.jboss.system.server.ServerImpl.init(ServerImpl.java:147)
	at org.jboss.Main.boot(Main.java:197)
	at org.jboss.Main$1.run(Main.java:508)
	at java.lang.Thread.run(Thread.java:619)

---

### Post by ismakun on 2007-10-04
No one has Red Hat Developer Studio in Ubuntu or knows why the integrated server does not work???? Does ubuntu fiesty have those ports blocked. I need help :(

Thanks in advance,
Ismakun

---

### Post by primski on 2007-10-04
I am not aware of this application suite, but judging by the error u provided,

log4j:ERROR Failed to create directory structure: /usr/local/rhdevstudio/jboss-eap/jboss-as/server/default/log

perhaps a permission issue?

And no, ports are not blocked....that is if you haven't changed default settings about firewall.

---

### Post by ismakun on 2007-10-04
Yes as you said it was a privilege issue. The program works perfectly including the server if i execute the file from nautilus which is log as root. So maybe the problem can be solved for any user by adding the user to the admin or root group? But at least the problem has been solved partially. Thanks for pointing to the right direction.

---

### Post by primski on 2007-10-05
Yes you can add user to the admin group, or you could also adjust permissions on that folder, maybe change owner of the dir.

glad u got it working.

---

### Post by frankliu on 2007-12-18
Hi, I met problem when I install the redhat developer studio in ubuntu 7.10. When it asked me to choose the jre directory, I chose the jdk directory. But it says that the directory does not contain the JVM. Then I chose the jre directory, and I got the same result. I have installed the jdk1.6 in ubuntu.

I don't know the reason. Can anybody help me? 

Thanks a lot.

---

