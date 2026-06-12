---
title: "OpenCMS Setup and Image Processing"
date: 2008-05-15
forum: Server Platforms
---

### Post by Tapsa73 on 2008-05-15
Hello,

I'm installing OpenCMS to Ubuntu 8.04 Server and I'm using instruction from [http://linuxfellaz.net/doku.php?id=debian:opencms](http://linuxfellaz.net/doku.php?id=debian:opencms)

My installation differs on Java, which is in sun-java5-jdk in instruction and Iäm using sun-java6-jdk.

Everything goes thru instruction and I get OpenCMS setupscript running, but then setup tests component it says that image processing is not allowed.

I tried to start tomcat by adding line "JAVA_OPT=-Djava.awt.headless=true" begin to /etc/init.d/tomcat5.5  -file.

How I get this image prosessing to work?

- Tapsa -

---

