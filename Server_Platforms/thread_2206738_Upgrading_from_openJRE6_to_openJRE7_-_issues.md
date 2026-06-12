---
title: "Upgrading from openJRE6 to openJRE7 - issues"
date: 2014-02-20
forum: Server Platforms
---

### Post by Eric_Snyder on 2014-02-20
I have installed OpenJRE7 and it shows that it is installed. Version 7 is just not the default JRE. When I execute the command:
>  sudo update-alternatives --config java
I get:
> There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      manual mode




When I check the default java version I get:
> java -version

java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.6) (6b27-1.12.6-1ubuntu0.12.04.4)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)



If I try:
> sudo update-java-alternatives -s java-1.7.0-openjdk-amd64
I get:
> update-alternatives: error: no alternatives for appletviewer.update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for jcmd.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jcmd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/bin/xjc
update-alternatives: error: alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/policytool for policytool not registered, not setting.
update-java-alternatives: plugin alternative does not exist: /usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so


What to do???

---

### Post by ajgreeny on 2014-02-20
Uninstall openjdk-6-jre perhaps?

You don't really need both, I suspect, so why not get rid of the older version of all the openjdk-6 packages and add the openjdk-7 versions, though it sounds as if you already have the 7 version.

---

