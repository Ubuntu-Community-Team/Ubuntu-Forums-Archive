---
title: "Messed up Java (Ubuntu 8.04)"
date: 2009-11-04
forum: Server Platforms
---

### Post by primaxx on 2009-11-04
I have managed to mess up my Java installation, and have no clue how to reset it again. I believe the reason for why it's broke is that I started fumbling with the ***export $JAVA_HOME*** command. How do I reset this? I have tried to completely remove Sun-Java and then reinstall it again, but I still get this error-message:```
manager@server:~$ java version
Exception in thread "main" java.lang.NoClassDefFoundError: version
Caused by: java.lang.ClassNotFoundException: version
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)

```

I also have this:```
manager@server:~$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun/jre

```

Are there anyone who can guide me in the right direction here!
Thanks! :)

---

### Post by andrewc6l on 2009-11-04
That error is correct if you're trying to run a class called version (no package) in your current directory, and version.class doesn't exist there. You might instead mean to be running:

java -version

which will print the version of the Java VM you're using.

---

