---
title: "JacORB bug"
date: 2009-12-11
forum: The Cafe
---

### Post by nishant10010 on 2009-12-11
I am a newbie and currently need to work on CORBA using JacORB. I have downloaded and installed everything, but when I am trying to execute a demo program, I am getting the following error:
############################
C:\JacORB\demo\hello>ant
Buildfile: build.xml
Warning: 'file:../../etc/common.xml' in C:\JacORB\demo\hello\build.xml should be
 expressed simply as '../../etc/common.xml' for compliance with other XML tools

base-init:

set-architecture:

init:

hello.init:

load-taskdef:

BUILD FAILED
C:\JacORB\etc\common.xml:108: taskdef class org.jacorb.idl.JacIDL cannot be found

Total time: 0 seconds
#############################

My Paths and Classpaths are:
set ANT_HOME = C:\apache-ant-1.7.1
set JACORB_HOME =C:\Jacorb-2.3.1
set JAVA-HOME= C:\Program Files\Java\jdk1.6.0_11
set PATH=%PATH%;%ANT_HOME%\bin

Awaiting for your reply.This is for your necessary action please.
Thanking you..

---

### Post by flib- on 2009-12-17
> **nishant10010 said:**
> I am a newbie and currently need to work on CORBA using JacORB. I have downloaded and installed everything, but when I am trying to execute a demo program, I am getting the following error:
############################
C:\JacORB\demo\hello>ant
Buildfile: build.xml
Warning: 'file:../../etc/common.xml' in C:\JacORB\demo\hello\build.xml should be
 expressed simply as '../../etc/common.xml' for compliance with other XML tools

base-init:

set-architecture:

init:

hello.init:

load-taskdef:

BUILD FAILED
C:\JacORB\etc\common.xml:108: taskdef class org.jacorb.idl.JacIDL cannot be found

Total time: 0 seconds
#############################

My Paths and Classpaths are:
set ANT_HOME = C:\apache-ant-1.7.1
set JACORB_HOME =C:\Jacorb-2.3.1
set JAVA-HOME= C:\Program Files\Java\jdk1.6.0_11
set PATH=%PATH%;%ANT_HOME%\bin

Awaiting for your reply.This is for your necessary action please.
Thanking you..
Hi Nishant,

your email seems off-topic, seems you are using Windows platform. Maybe you should try user mailing list at [www.jacorb.org](www.jacorb.org)

If you want to install JacORB for Ubuntu 9.04 (jaunty), you can install from launchpad

[https://launchpad.net/~debian-icoup-consulting/+archive/ppa](https://launchpad.net/~debian-icoup-consulting/+archive/ppa)

---

