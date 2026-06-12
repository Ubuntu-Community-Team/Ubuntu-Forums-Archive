---
title: "Another java problem"
date: 2009-06-03
forum: System76 Support
---

### Post by Bulli2010 on 2009-06-03
Hi,

starting the program jbidwatcher i get following error message:

[COLOR=Blue]Exception in thread "main" java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.simontuffs.onejar.Boot.run(Boot.java:306)
    at com.simontuffs.onejar.Boot.main(Boot.java:159)
Caused by: java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
    at com.jbidwatcher.app.JBidWatch.loadConfig(JBidWatch.java:166)
    at com.jbidwatcher.app.JBidWatch.main(JBidWatch.java:384)
    ... 6 more[/COLOR]

I'm nearly sure installing a plugin for viewing DVD's created the problem but what is it and how to solve it? Every hint is very much appreciated.
Thanks in advance.

---

### Post by theDaveTheRave on 2009-06-03
> **Bulli2010 said:**
> Hi,


I'm nearly sure installing a plugin for viewing DVD's created the problem 

Surely you aren't suggesting that this worked before you added the plugin for viewing DVD's are you? Was this plugin for firefox or something else?

Ok some stupid suggestions...

Have you tried disabling / removing this plugin to see if the error disappears?

I'm affraid that is the limit of my suggestions currently.

sorry

David

---

### Post by thomasaaron on 2009-06-03
It sounds like you need to install sun's java to make it work correctly. Run these commands...

sudo apt-get install sun-java6-jre
sudo update-alternatives --config java

After that second command, you must choose the version that has "sun" in it, not the open java.

Reboot.

---

### Post by Bulli2010 on 2009-06-04
Thanks for your hints. This was the solution: :p

sudo update- java-alternatives -s java-6-sun

---

