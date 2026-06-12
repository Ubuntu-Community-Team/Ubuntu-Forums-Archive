---
title: "Using javax.comm under Ubuntu"
date: 2009-12-15
forum: Server Platforms
---

### Post by digysol on 2009-12-15
I am trying to use the javax.comm package (Java serial comm under Ubuntu server edition.

I downloaded the package from the Java site and did the following:

1 - copied libLinuxSerialParallel.so to /usr/lib/
2 - copied javax.comm.properties to [JDK-directory]/jre/lib/
3 - copied comm.jar to [JDK-directory]/lib/

I added the following at the top of my Java source:

import javax.comm
.......

The compiler (version 1.6) came back with an error on the import statement saying that javax.comm is an unknown package.

I performed:

jar -tf comm.jar

on the associated jar file and all the javax.comm components were there.

Any suggestions?

---

### Post by jamesstansell on 2009-12-15
Does using [JDK-directory]/bin/javac (or similar) to compile your source work any better?

It is possible that the default javac command doesn't know about the extension directory where you placed the jar, which I why I would try to use the javac associated with the extension directory.

Hope that gets you further along.

-james.

(I prefer to work without extension directories if possible, but they can be a quick way to get started.)

---

### Post by scphan on 2010-01-21
Try reading the documentation that came with the download (in /docs).

Have java.comm.properties in the same directory as comm.jar.

As for the libLinuxSerialParallel.so file, after you'd copied it over to /usr/lib, invoke "ldconfig" as super user.

For the error you've received, the compiler's probably saying it can't find the comm.jar. You need to add to your classpath.. if at runtime with a terminal via "-cp comm.jar:.".

---

