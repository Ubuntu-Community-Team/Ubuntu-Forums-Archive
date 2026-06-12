---
title: "How to install Java in Pop OS?"
date: 2020-02-25
forum: System76 Support
---

### Post by javierdl on 2020-02-25
[COLOR=#DEDCD7][FONT=&quot]Update: I ended up letting Synaptic take care of the installation, I just chose "default-jre" and I agreed with the rest of the associated files Synaptic named.

[/FONT][/COLOR]-----------------------------------------------------------------

According to the Terminal these are my choices:

```
sudo apt install default-jre              # version 2:1.11-72, or
sudo apt install openjdk-11-jre-headless  # version 11.0.5+10-0ubuntu1
sudo apt install openjdk-13-jre-headless  # version 13+33-1
sudo apt install openjdk-14-jre-headless  # version 14~18-1
sudo apt install openjdk-8-jre-headless   # version 8u232-b07-2ubuntu1

```
Notice how the 1st command line ends with "or". Does it mean that installing either "default-jre" or all the 4 other command lines below will yield the same result?


Or is there yet another more suitable way?

Thanks guys,

JDL

------------------------------------------

---

### Post by #&amp;thj^% on 2020-02-25
"or" means as it reads "default-jre"  or "openjdk-11-jre-headless"
The jre/jdk is just the runtime environment.
Now the rest is up to you as to what version you would like.
EG:```
apt search jre
Sorting... Done
Full Text Search... Done
android-platform-tools-base/stable 2.2.2-3 all
  base tools for developing applications for the Android system

default-jre/stable 2:1.11-71+b1 armhf
  Standard Java or Java compatible Runtime

default-jre-headless/stable 2:1.11-71+b1 armhf
  Standard Java or Java compatible Runtime (headless)

docbook-xsl/stable 1.79.1+dfsg-2 all
  stylesheets for processing DocBook XML to various output formats

gcj-4.9-jre/stable 4.9.4-2+rpi1+b19 armhf
  Java runtime environment using GIJ/Classpath

gcj-4.9-jre-headless/stable 4.9.4-2+rpi1+b19 armhf
  Java runtime environment using GIJ/Classpath (headless version)

gcj-4.9-jre-lib/stable 4.9.4-2+rpi1 all
  Java runtime library for use with gcj (jar files)

gcj-5-jre/stable 5.5.0-8 armhf
  Java runtime environment using GIJ/Classpath

gcj-5-jre-headless/stable 5.5.0-8 armhf
  Java runtime environment using GIJ/Classpath (headless version)

gcj-5-jre-lib/stable 5.5.0-8 all
  Java runtime library for use with gcj (jar files)

gcj-6-jre/stable 6.5.0-1+rpi1+b1 armhf
  Java runtime environment using GIJ/Classpath

gcj-6-jre-headless/stable 6.5.0-1+rpi1+b1 armhf
  Java runtime environment using GIJ/Classpath (headless version)

gcj-6-jre-lib/stable 6.5.0-1+rpi1 all
  Java runtime library for use with gcj (jar files)

gcj-jre/stable 4:6.4.0-11+rpi2 armhf
  Java runtime environment using GIJ/Classpath

gcj-jre-headless/stable 4:6.4.0-11+rpi2 armhf
  Java runtime environment using GIJ/Classpath (headless version)

java-package/stable 0.62 all
  Utility for creating Java Debian packages

jaxws/stable 2.3.0.2-1 all
  JAX-WS Reference Implementation (Command Line Tools)

libambix-utils/stable 0.1.1-1 armhf
  AMBIsonics eXchange library (utilities)

libanimal-sniffer-java/stable 1.16-1 all
  JDK/API verification tools

libcommons-exec-java/stable 1.3-1 all
  Java library to reliably execute external processes from within the JVM

libgeronimo-osgi-support-java/stable 1.1-1 all
  Java libraries providing OSGi lookup support for Geronimo projects

libgeronimo-osgi-support-java-doc/stable 1.1-1 all
  Documentation for libgeronimo-osgi-support-java

libhtmlcleaner-java/stable 2.21-5 all
  Java HTML Parser library

libhtmlcleaner-java-doc/stable 2.21-5 all
  Java HTML Parser library (documentation)

libjaxws-api-java/stable 2.3.0-1 all
  Java API for XML-Based Web Services

libjaxws-java/stable 2.3.0.2-1 all
  JAX-WS Reference Implementation (Library)

libjreen-dbg/stable 1.2.0-2 armhf
  powerful Jabber/XMPP library (Qt4 build) - debugging symbols

libjreen-dev/stable 1.2.0-2 armhf
  powerful Jabber/XMPP library (Qt4 build) - development files

libjreen-qt5-1/stable 1.2.0-2 armhf
  powerful Jabber/XMPP library implemented in Qt5/C++

libjreen-qt5-dbg/stable 1.2.0-2 armhf
  powerful Jabber/XMPP library (Qt5 build) - debugging symbols

libjreen-qt5-dev/stable 1.2.0-2 armhf
  powerful Jabber/XMPP library (Qt5 build) - development files

libjreen1/stable 1.2.0-2 armhf
  powerful Jabber/XMPP library implemented in Qt4/C++

libjrexx-java/stable 1.1.1-7 all
  automaton based regular expression API for java

libopenjfx-java/stable,now 11.0.2+1-1 all [installed,automatic]
  JavaFX/OpenJFX - Rich client application platform for Java (Java libraries)

libreoffice/stable,now 1:6.1.5-3+rpi1+deb10u5 armhf [installed,automatic]
  office productivity suite (metapackage)

libsaaj-java/stable 1.4.0-3 all
  SOAP with Attachment API for Java

libtwelvemonkeys-java/stable 3.4.1-1 all
  collection of plugins and extensions for Java's ImageIO

libtwelvemonkeys-java-doc/stable 3.4.1-1 all
  Documentation for libtwelvemonkeys-java

openjdk-10-jre/stable 10.0.2+13-2 armhf
  OpenJDK Java runtime, using Hotspot JIT

openjdk-10-jre-headless/stable 10.0.2+13-2 armhf
  OpenJDK Java runtime, using Hotspot JIT (headless)

openjdk-10-jre-zero/stable 10.0.2+13-2 armhf
  Alternative JVM for OpenJDK, using Zero

openjdk-11-jre/stable,now 11.0.6+10-1~deb10u1 armhf [installed,automatic]
  OpenJDK Java runtime, using Hotspot JIT

openjdk-11-jre-headless/stable,now 11.0.6+10-1~deb10u1 armhf [installed,automatic]
  OpenJDK Java runtime, using Hotspot JIT (headless)

openjdk-8-jre/stable 8u212-b01-1+rpi1 armhf
  OpenJDK Java runtime, using Hotspot JIT

openjdk-8-jre-headless/stable 8u212-b01-1+rpi1 armhf
  OpenJDK Java runtime, using Hotspot JIT (headless)

openjdk-8-jre-zero/stable 8u212/-b01-1+rpi1 armhf
  Alternative JVM for OpenJDK, using Zero/Shark

openjdk-9-jre/stable 9.0.4+12-4 armhf
  OpenJDK Java runtime, using Hotspot JIT

openjdk-9-jre-headless/stable 9.0.4+12-4 armhf
  OpenJDK Java runtime, using Hotspot JIT (headless)

openjdk-9-jre-zero/stable 9.0.4+12-4 armhf
  Alternative JVM for OpenJDK, using Zero

```
As you can see there are plenty of choices depending on your needs/wants.
And my examples are from my RPI4 so you might see differences for your output.
Right now I'm running:
```
$ java -version
openjdk version "11.0.6" 2020-01-14
OpenJDK Runtime Environment (build 11.0.6+10-post-Raspbian-1deb10u1)
OpenJDK Server VM (build 11.0.6+10-post-Raspbian-1deb10u1, mixed mode)

```

---

### Post by johnnyzee on 2020-02-26
Thanks for posting this advice. It was very helpful to me in getting access to Ignition database client.

---

