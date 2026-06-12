---
title: "Minecraft (jar) start fails. Java error. Please help"
date: 2015-03-31
forum: Server Platforms
---

### Post by Jan_Scholz_ on 2015-03-31
Hello, I have Ubuntu server 14 LTS installed on my machine and when I tried to launch Minecraft with Java (openjdk-6-jre) it fails. Same with the 7 version.
Thank you for your help!

Here is the console output:
root@server:~# java -jar /home/server/minecraft/forge.jar nogui
A problem occurred running the Server launcher.java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:622)
        at cpw.mods.fml.relauncher.ServerLaunchWrapper.run(ServerLaunchWrapper.java:43)
        at cpw.mods.fml.relauncher.ServerLaunchWrapper.main(ServerLaunchWrapper.java:12)
Caused by: java.lang.NoClassDefFoundError: org/apache/logging/log4j/Level
        at net.minecraft.launchwrapper.Launch.launch(Launch.java:94)
        at net.minecraft.launchwrapper.Launch.main(Launch.java:28)
        ... 6 more
Caused by: java.lang.ClassNotFoundException: org.apache.logging.log4j.Level
        at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
        ... 8 more

---

### Post by ian-weisser on 2015-04-01
Do you get the same error if you run as a different user (instead of root)?
Do you get the same error if you run a different flavor of Minecraft?

---

