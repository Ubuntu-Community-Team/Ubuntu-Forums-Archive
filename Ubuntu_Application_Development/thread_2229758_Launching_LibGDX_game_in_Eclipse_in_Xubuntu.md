---
title: "Launching LibGDX game in Eclipse in Xubuntu"
date: 2014-06-15
forum: Ubuntu Application Development
---

### Post by ViliX64 on 2014-06-15
I am trying to launch my LibGDX game in Eclipse on Xubuntu, but I always get this error:
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: Native Library /usr/lib/jvm/java-7-openjdk-i386/jre/lib/i386/libawt.so already loaded in another classloader    at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1931)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1890)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1872)
    at java.lang.Runtime.loadLibrary0(Runtime.java:849)
    at java.lang.System.loadLibrary(System.java:1088)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1650)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1672)
    at org.lwjgl.LinuxSysImplementation.<clinit>(LinuxSysImplementation.java:50)
    at org.lwjgl.Sys.createImplementation(Sys.java:126)
    at org.lwjgl.Sys.<clinit>(Sys.java:111)
    at org.lwjgl.openal.AL.<clinit>(AL.java:59)
    at com.badlogic.gdx.backends.lwjgl.audio.OpenALAudio.<init>(OpenALAudio.java:72)
    at com.badlogic.gdx.backends.lwjgl.LwjglApplication.<init>(LwjglApplication.java:82)
    at com.badlogic.gdx.backends.lwjgl.LwjglApplication.<init>(LwjglApplication.java:64)
    at cz.vilix.main.Desktop.main(Desktop.java:30)

```

Line 30 in my game is this one:
```
new LwjglApplication(game = new Game(), config);
```

I don't know what's wrong even exported LibGDX jars don't work in here (and everything works on Ubuntu with the same Java version).
This is my Java version:

```
java version "1.7.0_55"OpenJDK Runtime Environment (IcedTea 2.4.7) (7u55-2.4.7-1ubuntu1)
OpenJDK Server VM (build 24.51-b03, mixed mode)
``` 

The question is, how to make it run. Thanks for any anwsers.

---

### Post by ViliX64 on 2014-06-16
I have messed around with Java versions (but still have the openjdk-7) and it started working. I am sorry that I cannot provide solution to this, but installing different versions and then back the OpenJDK one works.

---

