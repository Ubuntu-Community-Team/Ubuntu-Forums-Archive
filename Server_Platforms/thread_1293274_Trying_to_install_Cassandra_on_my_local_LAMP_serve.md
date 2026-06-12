---
title: "Trying to install Cassandra on my local LAMP server"
date: 2009-10-16
forum: Server Platforms
---

### Post by linuxluver on 2009-10-16
I have installed a LAMP server on my Desktop Ubuntu, and I have recently installed MediaWiki successfully. I am looking to install Cassandra(base of Facebook) on my computer to test it out. I have not been able to find any installation instructions anywhere. Thanks in advance,

linuxluver

---

### Post by stlsaint on 2009-10-16
sorry i can provide docs on cassandra but when you do find some i recommend you make a chroot to test out the program before putting it on your main server.

---

### Post by linuxluver on 2009-10-16
Oh, no, it's not like a server on the interwebs, but a local server that I set up as a private sandbox. Did you say you 'can' or you 'can't' provide docs on Cassandra? Me is confuzzled.

---

### Post by ldavison on 2009-10-19
Follow the steps outlined here:

[http://wiki.apache.org/cassandra/GettingStarted](http://wiki.apache.org/cassandra/GettingStarted)

If you download the binary package, it should only take a few minutes to get Cassandra setup to run a single node.

You will know if you don't have the correct JRE when you start Cassandra and get the following output:

```

Listening for transport dt_socket at address: 8888
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)


```

In which case, the following command will sort you out:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts && sudo update-java-alternatives --set java-6-sun
```

---

