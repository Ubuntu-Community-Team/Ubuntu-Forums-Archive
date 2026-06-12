---
title: "Open LDAP won't start"
date: 2007-06-22
forum: Server Platforms
---

### Post by dazz5 on 2007-06-22
When I attempt to start LDAP I get this:

```
Starting OpenLDAP: (db4.2_recover not found),  slapd.
```

I had Zimbra installed prev. but I compleatly removed it. (ZImbra used Open LDAP)

now I've installed just open ldap, and i get that error when i try to start it

---

### Post by dazz5 on 2007-06-22
Now I get:

Starting OpenLDAP: (slapd running, no recovery),  slapd.

---

### Post by zaf on 2007-06-24
You'll need to give more information, but then again, if you have nothing in the LDAP directory you actually want (which it sounds like is true), the easiest fix may be to:
```

dpkg --purge slapd
apt-get install slapd

```
Which will totally uninstall Open LDAP server (including all of your OpenLDAP settings, database, etc), then reinstall it with default settings.

---

### Post by lsilver on 2007-06-29
Hello.

I was having similar problems to the originator of this post and so I followed your removal and reinstallation instructions but get the error as per below.  Also, slaptest says the conf file is invalid even though its a default install.  Any suggestions as to what is causing the db4.2_recover not found error?  I'[m running 6.06 on an AMD64 processor.

sudo apt-get install slapd
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  db4.2-util
The following NEW packages will be installed:
  slapd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/961kB of archives.
After unpacking 2646kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package slapd.
(Reading database ... 74940 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.2.26-5ubuntu2.2_amd64.deb) ...
Setting up slapd (2.2.26-5ubuntu2.2) ...
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... done.
Starting OpenLDAP: (db4.2_recover not found),  slapd.


Thanks, Leo.

---

### Post by ethanbrown on 2007-11-09
I was able to solve this problem by installing the db4.2-util package.  I don't know why it's not a dependencyfor the slapd package.  Maybe it's worth filing a bug report.

---

