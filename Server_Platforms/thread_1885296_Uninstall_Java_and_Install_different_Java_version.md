---
title: "Uninstall Java and Install different Java version?"
date: 2011-11-22
forum: Server Platforms
---

### Post by MutinyCraft on 2011-11-22
I will admit I am pretty new to Ubuntu and installing applications and packages from the command line is very new to me.  I currently have ```
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
```
installed on a dedicated server with Ubuntu 10.04 server OS.  I have been running a Java application (minecraft) and I keep getting major errors from Java.  How can I uninstall Java and re-install Java:
```
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.8) (6b20-1.9.8-0ubuntu1~10.04.1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)

```
because I know this version works as I have it on another dedicated server.  

I realize this is probably something simple and I have searched for hours with no luck.  I apologize if this isn't the correct place to post this and if you can point me in the right direction or answer my question I would very much appreciate it.

Thank You :)

---

### Post by maverickaddicted on 2011-11-23
You can search all the jre package in your system by running this command
```
sudo aptitude search jre
```

Remove it using this command 
```
sudo apt-get remove sun-java6-jre sun-java6-plugin sun-java6-fonts
```

You can also try this command to remove all the java files in your system 

```
sudo aptitude remove '~njava'
``` 

Then you can install it using this command -

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

If you want more information, then you can visit here
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by hawkmage on 2011-11-23
In general I don't really care about the default installed java version.  Most applications and servers use the environment variable JAVA_HOME and the PATH.  I manage Tomcat servers that are in a shared environment with dozens of applications each of which can use a different version of java by setting the JAVA_HOME variable for the application.

---

