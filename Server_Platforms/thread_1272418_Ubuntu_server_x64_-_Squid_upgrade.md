---
title: "Ubuntu server x64 - Squid upgrade"
date: 2009-09-22
forum: Server Platforms
---

### Post by swappa on 2009-09-22
Hello
I have been assigned the task of upgrading Squid on all of our Ubuntu Intrepid x64 servers. We are currently running Squid 3.0.STABLE7-1 and I will be upgrading to 3.0.STABLE 19-1 amd64. The thing is that I cant use apt-get since it cant find any suitable packages. I know that the person that installed the servers (doesn't work for the company anymore) did it in a very minimalistic way - just the necessary tools/packages where installed (I guess this is a good thing in general). 

I downloaded the deb package and wanted to do dpkg -i <package> but there are a lot of dependencies missing. When I  try to install these separately they cant be found in the repositories.

Is there a "default server sources.lst" I can download and my problem will be solved or do I need to go about this problem in a different way? 

Btw, here is my sources.lst 


deb [http://mirror.xmission.com/ubuntu](http://mirror.xmission.com/ubuntu) hardy main restricted universe multiverse
deb [http://mirror.xmission.com/ubuntu](http://mirror.xmission.com/ubuntu) hardy-updates main restricted universe multiverse
deb [http://mirror.xmission.com/ubuntu](http://mirror.xmission.com/ubuntu) hardy-security main restricted universe multiverse
deb [http://mirror.xmission.com/ubuntu](http://mirror.xmission.com/ubuntu) intrepid main restricted universe multiverse
deb [http://mirror.xmission.com/ubuntu](http://mirror.xmission.com/ubuntu) intrepid-updates main restricted universe multiverse
deb [http://mirror.xmission.com/ubuntu](http://mirror.xmission.com/ubuntu) intrepid-security main restricted universe multiverse

Thank you

---

### Post by JonRohan on 2009-09-22
Have you run "apt-get upate" prior to installing squid? 

Jon

---

### Post by swappa on 2009-09-23
> **JonRohan said:**
> Have you run "apt-get upate" prior to installing squid? 

Jon

Yes - that works, but when doing the apt-get upgrade I get the following;


Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  squid3: Depends: libgssapi-krb5-2 (>= 1.6.dfsg.2) but it is not installed
          Depends: libk5crypto3 (>= 1.6.dfsg.2) but it is not installed
          Depends: libkrb5-3 (>= 1.6.dfsg.2) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by drave99 on 2009-09-23
this being open source, when push comes to shove, use the source luke. i just had a quick look and it didnt mention a list of dependencies, just the usual configure then make.

by the way "on all of our Ubuntu Intrepid x64 servers" ? unless you have a gazillion users, isnt 1 enough ?

dave

---

### Post by swappa on 2009-09-23
> **drave99 said:**
> this being open source, when push comes to shove, use the source luke. i just had a quick look and it didnt mention a list of dependencies, just the usual configure then make.

by the way "on all of our Ubuntu Intrepid x64 servers" ? unless you have a gazillion users, isnt 1 enough ?

dave

Thanks for your feedback. Will try the source option.
We do have a lot of squids as we host a lot of different Online services for quite a few companies.

---

### Post by eugenevdm on 2009-12-02
I have a similar question. I couldn't find any .DEB so I downloaded the source.

The first problem appeared to be that Squid is referring to /usr/local/squid instead of the default Ubuntu install location.

I then found more info that if you do:
squid -v you get default 64-bit options:

configure options:  '--build=x86_64-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=${prefix}/lib/squid3' '--disable-maintainer-mode' '--disable-dependency-tracking' '--srcdir=.' '--datadir=/usr/share/squid3' '--sysconfdir=/etc/squid3' '--mandir=/usr/share/man' '--with-cppunit-basedir=/usr' '--enable-inline' '--enable-async-io=8' '--enable-storeio=ufs,aufs,coss,diskd,null' '--enable-removal-policies=lru,heap' '--enable-delay-pools' '--enable-cache-digests' '--enable-underscores' '--enable-icap-client' '--enable-follow-x-forwarded-for' '--enable-auth=basic,digest,ntlm' '--enable-basic-auth-helpers=LDAP,MSNT,NCSA,PAM,SASL,SMB,YP,getpwnam,multi-domain-NTLM' '--enable-ntlm-auth-helpers=SMB' '--enable-digest-auth-helpers=ldap,password' '--enable-external-acl-helpers=ip_user,ldap_group,session,unix_group,wbinfo_group' '--with-filedescriptors=65536' '--with-default-user=proxy' '--enable-epoll' '--enable-linux-netfilter' 'build_alias=x86_64-linux-gnu' 'CC=cc' 'CFLAGS=-g -O2 -g -Wall -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXX=g++' 'CXXFLAGS=-g -O2 -g -Wall -O2' 'FFLAGS=-g -O2'

I tried make and got GCC error, so I did:
apt-get install build-essential

ERROR: Neither SASL nor SASL2 found
Solution: apt-get install libsasl2-dev

ERROR: Cannot find cppunit at /usr
Solution: apt-get install libcppunit-dev

COSS Error, refer here:
[https://bugs.launchpad.net/ubuntu/+source/squid3/+bug/303869](https://bugs.launchpad.net/ubuntu/+source/squid3/+bug/303869)

Tried removing COSS.

Next I got LDAP error, and tried removing LDAP from the configuration file (there are three references).

Next I got PAM errors, and tried removing PAM from the configuration file.

Then I got:
squid_session.c:51:20: error: db_185.h: No such file or directory

I can't solve this problem, and this advice tells me to use packaged software:
[http://packages.debian.org/source/lenny-backports/squid3](http://packages.debian.org/source/lenny-backports/squid3)

Please help because I would really like to upgrade my 64-bit Squid to latest version.

---

