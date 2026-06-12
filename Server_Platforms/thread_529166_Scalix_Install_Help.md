---
title: "Scalix Install Help"
date: 2007-08-18
forum: Server Platforms
---

### Post by chaser001 on 2007-08-18
Hello, 
I'm trying to get scalix installed on my dapper box.  I'm getting an error that something to do with kerberos, but I'm not sure how to fix it.  Please Help. 

ps-

This is what happens when i run make with_java



> 
apt-get install apache2 libapache2-mod-jk gawk krb5-config krb5-doc krb5-user libkadm55 libkrb53 libglib2.0-0 \
        libstdc++2.10-glibc2.2 libxml2 sgml-base xml-core libsasl2-modules libsasl2-gssapi-mit sendmail elinks
Reading package lists... Done
Building dependency tree... Done
libkrb53 is already the newest version.
libglib2.0-0 is already the newest version.
libxml2 is already the newest version.
sgml-base is already the newest version.
xml-core is already the newest version.
libsasl2-modules is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  krb5-user: Depends: libkrb53 (= 1.4.3-5) but 1.4.3-5ubuntu0.4 is to be installed
             Depends: libkadm55 (= 1.4.3-5) but 1.4.3-5ubuntu0.4 is to be installed
E: Broken packages
make: *** [dubidu_depends] Error 100 

---

### Post by psifry on 2007-08-29
Hi,

I have an identical problem, my LAMP installation of dapper is only a few hours old and I have so far only attempted to install Scalix.  Any help would be appreciated.

sifly

---

### Post by gfowler on 2007-08-30
Any particular reason you are compling java.  I've installed Scalix to a couple of Ubuntu distros but just used apt-get install sun-java5-jre.

Buried in the Scalix forum (~ May 2007) there is a script someone contributed that will install Scalix on a FF server distro.  I have used it to install Scalix 11.1.0 to Edgy.  Worked 5X5, you need to change the script to get the 11.1.0 Scalix distrobution, and you need to have the server set with hosts, hostname, etc configured pre-Scalix install and it will give you a close to turnkey install.

This doesn't address your specific issue tho, so no umbrage if you click 'N" and keep moving....

Jerry

> **chaser001 said:**
> Hello, 
I'm trying to get scalix installed on my dapper box.  I'm getting an error that something to do with kerberos, but I'm not sure how to fix it.  Please Help. 

ps-

This is what happens when i run make with_java

---

