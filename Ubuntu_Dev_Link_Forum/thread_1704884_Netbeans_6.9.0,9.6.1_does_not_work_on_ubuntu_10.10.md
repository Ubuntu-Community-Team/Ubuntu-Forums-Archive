---
title: "Netbeans 6.9.0,9.6.1 does not work on ubuntu 10.10"
date: 2011-03-11
forum: Ubuntu Dev Link Forum
---

### Post by norelpy on 2011-03-11
Hi folks,
I installed netbeans 6.9.1 manuel sometimes ago. I could run the program  and write some code perfectly. But I could not open the ide yesterday. I  do not know why. I reinstalled the program the result is same. Then I  totaly removed the ide and installed netbeans from synaptic manager. I  the result is same. Could not open it. When I click the netbeans icon it  is appearing on the task bar and disappear again. Then I tried to open  it in terminal by typing > netbeans.
It showed below errors:
```
Exception in thread "main" java.lang.NoClassDefFoundError: org/openide/util/Utilities
    at org.netbeans.JarClassLoader$JarURLStreamHandler.openConnection(JarClassLoader.java:853)
    at org.netbeans.JarClassLoader$JarURLStreamHandler.openConnection(JarClassLoader.java:831)
    at java.net.URL.openConnection(URL.java:945)
    at java.net.URL.openStream(URL.java:1010)
    at org.netbeans.MainImpl$BootClassLoader.searchBuildNumber(MainImpl.java:270)
    at org.netbeans.MainImpl$BootClassLoader.<init>(MainImpl.java:238)
    at org.netbeans.MainImpl.execute(MainImpl.java:170)
    at org.netbeans.MainImpl.main(MainImpl.java:81)
    at org.netbeans.Main.main(Main.java:78)
Caused by: java.lang.ClassNotFoundException: org.openide.util.Utilities
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
    ... 9 more

```What is the problem?
My main question is that I could run the program but today I can not. Why?
Thank you

---

### Post by Coalwater on 2011-12-05
I know it's been quite a while, but i just had this problem and i finally fixed it after like 2 hours of installing and uninstalling, and i even reisntalled java it self,
the error is created after some packages are updated, i fixed it by deleting the files in ~/netbeans/6.9.1 or w/e your version is.

---

