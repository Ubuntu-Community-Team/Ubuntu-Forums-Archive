---
title: "Missing libtdsodbc.so in freetds-dev"
date: 2007-05-05
forum: Repositories &amp; Backports
---

### Post by dkasak on 2007-05-05
Greetings.

I've just installed Ubuntu ( long-time Gentoo user ) and I'm trying to set up DBD::ODBC to talk to SQL Server via FreeTDS. I've installed the freetds-dev package, but it sets up a broken symlink:

```
root@Ubuntu:/usr/lib# ls -l libtds*
-rw-r--r-- 1 root root 313170 2007-03-05 17:45 libtds.a
-rw-r--r-- 1 root root    788 2007-03-05 17:45 libtds.la
-rw-r--r-- 1 root root 431148 2007-03-05 17:45 libtdsodbc.a
-rw-r--r-- 1 root root    876 2007-03-05 17:45 libtdsodbc.la
lrwxrwxrwx 1 root root     19 2007-05-05 14:24 [COLOR="Red"]libtdsodbc.so [/COLOR]-> libtdsodbc.so.0.0.0
lrwxrwxrwx 1 root root     15 2007-05-05 14:24 libtds.so -> libtds.so.4.0.0
lrwxrwxrwx 1 root root     15 2007-05-05 13:57 libtds.so.4 -> libtds.so.4.0.0
-rw-r--r-- 1 root root 203280 2007-03-05 17:45 libtds.so.4.0.0
-rw-r--r-- 1 root root 329868 2007-03-05 17:45 libtdssrv.a
-rw-r--r-- 1 root root    809 2007-03-05 17:45 libtdssrv.la
lrwxrwxrwx 1 root root     18 2007-05-05 14:24 libtdssrv.so -> libtdssrv.so.2.0.0
lrwxrwxrwx 1 root root     18 2007-05-05 13:57 libtdssrv.so.2 -> libtdssrv.so.2.0.0
-rw-r--r-- 1 root root 213172 2007-03-05 17:45 libtdssrv.so.2.0.0
root@Ubuntu:/usr/lib# 
```

What happened to libtdsodbc.so.0.0.0?

---

### Post by dkasak on 2007-05-21
Hmmmmm. Back to Gentoo?

---

### Post by WW on 2007-05-22
Looks like this is pretty old bug: [https://bugs.launchpad.net/ubuntu/+source/freetds/+bug/68239](https://bugs.launchpad.net/ubuntu/+source/freetds/+bug/68239)

Add your comments to the bug report so the developers know the bug is still there.

---

### Post by glenndavy on 2007-09-20
hey there dkasak - dunno if this helps - installing the  tdsodbc package got me around the bug as it puts that file in the right place.

---

### Post by eborchardt on 2007-09-21
how did you go about installing the tdsodbc package? Could you please elaborate a little for us dummies?

Oh, I see it is in the Synaptic Package Manager! I'll give this a shot and let you know if it works on Ubuntu Server.

---

### Post by glenndavy on 2007-09-21
good luck - i dont see why not - i should mention im using gutsy

---

### Post by eborchardt on 2007-09-21
Well, I got my Ubuntu Server (feisty) communicating with my MS SQL server. While trying to install the package in Synaptic, it kept locking up for some reason. Using apt-get in the terminal worked perfectly. Once I installed this package, the rest of the setup was not difficult. Thanks for your help.

---

### Post by Hellman on 2008-03-04
Hi! I have installed Ubuntu Server 7.10 (gutsy gibbon) and need to run PHP with MS SQL. I have the same damn problem ... no libtdsodbc.so on the whole server... since two days i'm tyring to get this work!

i just have the OS in text mode...so no Synaptic Package Manager will run... help me out! :(

---

### Post by Hellman on 2008-03-04
Ok i think i just worked it out:

The file libtdsodbc.so in the package freetds-dev is damaged.

i extracted the functional libtdsodbc.so from the package tdsodbc (!) and substituted it with the damaged file in /usr/lib/

Extraction is easy with midnight commander (mc) ...

---

### Post by jschmitz on 2008-06-30
> **Hellman said:**
> 

i extracted the functional libtdsodbc.so from the package tdsodbc (!) and substituted it with the damaged file in /usr/lib/


I'm having the same issue but I'm not sure I'm grabbing the undamaged file.  Could you provide the exact location you got the undamaged file from?

---

### Post by Hellman on 2008-07-01
> **jschmitz said:**
> I'm having the same issue but I'm not sure I'm grabbing the undamaged file.  Could you provide the exact location you got the undamaged file from?

i took the file directly from the Ubuntu Download Section:

1) Download - [http://packages.ubuntu.com/hardy/i386/tdsodbc/download](http://packages.ubuntu.com/hardy/i386/tdsodbc/download)

2) Extract libtdsodbc.so from the downloaded tdsodbc_0.63-3.2ubuntu1_i386.deb file

3) replace the damaged file in /usr/lib

hope this helps! :guitar:

---

### Post by erikvw on 2008-07-06
libtdsodbc.so
with freeTDS (freetds-dev, tdsodbc), you can either edit the path in the odbcinst.ini file for the [FreeTDS] driver section OR cp the /usr/lib/odbc/libtdsodbc.so into /usr/lib/libtdsodbc.so. 

either way works when accessing mssql from the prompt

isql -v $dsn $user $passwd 

i found this to be useful 

[http://www.unixodbc.org/doc/FreeTDS.html#Configuration](http://www.unixodbc.org/doc/FreeTDS.html#Configuration)

---

