---
title: "jvm java not found"
date: 2010-06-07
forum: Server Platforms
---

### Post by 007casper on 2010-06-07
I have updated the ubuntu from from 9.04, to 9.10 to Ubuntu 10.04 LTS.  Then, somehow I think java-6-sun is a gonner. I tried to find it in synaptic.  I couldnt figure out what is going on... what to pick etc?

this may seem really ignorant, but what does this mean?
/usr/lib/jvm/java-6-sun/bin/java: not found

please, advise thank you

---

### Post by arrrghhh on 2010-06-07
Sun's java is no longer in the normal repo.  It's been moved to the partner repo.  Enable that if you *need* Sun's java - OpenJDK is now the 'preferred' package.

---

### Post by 007casper on 2010-06-07
what is the difference between Sun's java vs. OpenJDK?

Thank you

---

### Post by arrrghhh on 2010-06-08
One is community supported & the 'official' java package for Ubuntu (OpenJDK).

The other is supported by Sun and is not preferred for OSS reasons.

---

### Post by 007casper on 2010-06-08
>>not preferred for OSS reasons.

what is OSS stands for?  Is it political because oracle bought sun?

I did read about OpenJDK on wikipedia, however I wonder why one is preferred over the other.

thank you

---

### Post by arrrghhh on 2010-06-08
OSS = Open Source Software.

I'm pretty sure that's the reason Sun's java was demoted.  Don't quote me on that, but I believe OpenJDK follows the OSS 'rules' if you will so Ubuntu can include it without issue.

---

### Post by 007casper on 2010-06-09
>>It's been moved to the partner repo
I have all the repos checked main, universe, restricted, multiverse
where can I find the download repo for java-6-sun?

I have been trying to set all the paths for OpenJDK and nothing is working out.  Here is my list

> rox@www:~$ ls -l /usr/lib/jvm
total 8
drwxr-xr-x 6 root root 4096 2010-06-06 23:27 java-1.5.0-gcj-4.4
lrwxrwxrwx 1 root root   14 2010-06-06 23:27 java-1.6.0-openjdk -> java-6-openjdk
drwxr-xr-x 5 root root 4096 2010-06-06 23:27 java-6-openjdk
lrwxrwxrwx 1 root root   18 2010-06-06 22:26 java-gcj-4.4 -> java-1.5.0-gcj-4.4
rox@www:~$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8 ) (6b18-1.8-0ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)

---

### Post by arrrghhh on 2010-06-09
Enable the partner repo in your sources.list...

---

### Post by 007casper on 2010-06-09
$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid  partner"
$ sudo apt-get update 

I still have problems

tomcat servlet engine using JRE_HOME /usr/lib/jvm/java-6-openjdk

should I remove openjdk-6-jdk, will that default to java-6-sun?

---

### Post by 007casper on 2010-06-09
rox@www:~$ ls -l /usr/lib/jvm
total 12
drwxr-xr-x 6 root root 4096 2010-06-06 23:27 java-1.5.0-gcj-4.4
lrwxrwxrwx 1 root root 14 2010-06-06 23:27 java-1.6.0-openjdk -> java-6-openjdk
drwxr-xr-x 5 root root 4096 2010-06-06 23:27 java-6-openjdk
lrwxrwxrwx 1 root root 19 2010-06-09 15:01 java-6-sun -> java-6-sun-1.6.0.20
drwxr-xr-x 8 root root 4096 2010-06-09 15:01 java-6-sun-1.6.0.20
lrwxrwxrwx 1 root root 18 2010-06-06 22:26 java-gcj-4.4 -> java-1.5.0-gcj-4.4
rox@www:~$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8 ) (6b18-1.8-0ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode) 

edit
gksudo gedit .bashrc
export $JAVA_HOME=/usr/lib/jvm/java-6-sun

set default
sudo update-java-alternatives -s java-6-sun

gksudo gedit /etc/jvm
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr

java -version
java version "1.6.0_20"
Java (TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)

**********************************
ref> [http://nfolamp.wordpress.com/2010/05/19/howto-install-sun-java-on-ubuntu-10-04-lucid/](http://nfolamp.wordpress.com/2010/05/19/howto-install-sun-java-on-ubuntu-10-04-lucid/)

---

### Post by 007casper on 2010-06-09
purged other packages 
$ sudo apt-get purge openjdk-6-jre openjdk-6-jre-headless

still no luck

---

### Post by 007casper on 2010-06-09
I still get the same error in the logs
> 
SEVERE: StandardServer.await: create[8005]: 
java.net.BindException: Address already in use
SEVERE: StandardServer.await: create[8005]: 
java.net.BindException: Address already in use
	at java.net.PlainSocketImpl.socketBind(Native Method)
	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:336)
	at java.net.ServerSocket.bind(ServerSocket.java:336)
	at java.net.ServerSocket.<init>(ServerSocket.java:202)
	at org.apache.catalina.core.StandardServer.await(StandardServer.java:373)
	at org.apache.catalina.startup.Catalina.await(Catalina.java:642)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:602)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:413)

then whole thing shuts it self off

---

### Post by 007casper on 2010-06-09
after updating TOMCAT server from 9.04, to 9.10 to Ubuntu 10.04 LTS.  

Ubuntu split the user into two, and one of the user is tomcat.  I cant login to this user.  

When I tried to start an app under regular user I get java.net.BindException: Address already in use.  I thought the problem was jre/jdk.  I purged all the other java alternatives.

I tried to find what the problem is.  It comes out that another Tomcat process is running at the same time on the same port.

on the terminal 
netstat -anp | grep 8080
unix 3 [ ]  STREAM CONNECTED 8080 1464/bonobo-activat

it doesnt look like another tomcat is running.

please, advise.  Thank you so much.

I tried restarting the server, and even fully shutdown and turn it back on after two minutes... no luck same problem

---

