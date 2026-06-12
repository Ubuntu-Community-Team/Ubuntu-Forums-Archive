---
title: "Promise raid array manager install"
date: 2009-05-08
forum: Server Platforms
---

### Post by njmarine2001 on 2009-05-08
Ladies and Gentlemen,
I have a promise VTrak j610s array that i am trying to make work on ubuntu (9.04 server).

So far, i have verified that the x libraries are installed and that these libraries that i see listed in the stack trace are present. 

Both are present in /usr/lib
I have verified that JRE is set up and configured (at least to the best of my knowledge)

```
root@wphxwsc01:/cdrom/CLI/Linux# java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)

```

The problem that i encounter is 


```
root@wphxwsc01:/cdrom/CLI/Linux# sh CLI_Installer_3_12_0000_00_linux.bin           
Preparing to install...                                                            
Extracting the JRE from the installer archive...                                   
Unpacking the JRE...                                                               
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.6434/Linux/resource/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open sharedobject file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
        at java.lang.Runtime.load0(Runtime.java:769)
        at java.lang.System.load(System.java:968)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:545)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA10*..)
        at com.zerog.ia.installer.LifeCycleManager.h(DashoA10*..)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA10*..)
        at com.zerog.ia.installer.Main.main(DashoA10*..)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.zerog.lax.LAX.launch(DashoA10*..)
        at com.zerog.lax.LAX.main(DashoA10*..)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
```

Hardware: IBM X3400 2x3.0GHZ intel quad, 4GB, 250GB.
Promise supertrak EX8658 SAS card /w Promise array listed above.
Intel dual port GB nic

The software i have tried to install is the management utility for this array / card.

I receive the exact same errors whether installing the CLI or the GUI tool.

---

