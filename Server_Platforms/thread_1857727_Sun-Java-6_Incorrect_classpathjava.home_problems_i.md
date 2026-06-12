---
title: "Sun-Java-6 Incorrect classpath/java.home problems in finding tools.jar"
date: 2011-10-10
forum: Server Platforms
---

### Post by peter.depasquale@gmail.co on 2011-10-10
I installed sun-java6-jdk and sun-java6-jre (and likely other related java6 packages such as fonts) for a project running on a Ubuntu 11.04 server distribution. Our project programmatically calls Javadoc from within our running executable. To do so, we obviously need to know the location of the tools.jar file which is part of the JDK distribution, but not the JRE distribution. The packages were installed into /usr/lib/jvm/java-6-sun-1.6.0.26/ and there are bin and other directories under the two areas (JDK/JRE) which provide the various standard binaries.

Whenever we execute a java program (via the java binary), the internal java.home variable seems to overwrite any JAVA_HOME environment variable provided. We have concluded that the binary thus derives its java.home from the path of the binary. The java binary under the jdk really is a link to the jre version. Thus, no matter which one you 'execute', you are always getting the jre version, and thus the java.home directory is defined to be /usr/lib/jvm/java-6-sun-1.6.0.26/jre

As such, any running executable can not seem to find the tools.jar file, and even passing the "-cp /usr/lib/jvm/java-6-sun-1.6.0.26/jdk/lib/tools.jar" option does not help. We're hoping that someone can help shed some light on how we can correctly access the tools.jar file enabling us to correctly be able to call the com.sun.tools.javadoc.Main.execute method.

Example execution:

```
java -cp /usr/lib/jvm/java-6-sun/lib/tools.jar -jar comtor.jar -sourcepath .
Exception in thread "main" java.lang.NoClassDefFoundError: com/sun/tools/javadoc/Main
    at comtor.Comtor.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: com.sun.tools.javadoc.Main
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
    ... 1 more

```

---

