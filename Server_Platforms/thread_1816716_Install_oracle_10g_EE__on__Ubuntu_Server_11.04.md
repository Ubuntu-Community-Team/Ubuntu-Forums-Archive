---
title: "Install oracle 10g EE  on  Ubuntu Server 11.04"
date: 2011-08-02
forum: Server Platforms
---

### Post by gouravgargg on 2011-08-02
[SIZE=4]Help me to install oracle Enterprise Edition on Ubuntu Server 11.04 [/SIZE]

natty@nnattyBase:~/Downloads/database$ ./runInstaller 
Starting Oracle Universal Installer...

Checking installer requirements...

Checking operating system version: must be redhat-3, SuSE-9, redhat-4, UnitedLinux-1.0, asianux-1 or asianux-2
                                      Failed <<<<

Exiting Oracle Universal Installer, log for this session can be found at /tmp/OraInstall2011-08-02_07-59-02PM/installActions2011-08-02_07-59-02PM.log

---

### Post by Gyokuro on 2011-08-02
Hi,

this guide should help you: [http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/](http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/)

---

### Post by gouravgargg on 2011-08-02
[LEFT]I wan to install [SIZE=4]Oracle 10 g[/SIZE] not [SIZE=4]Oracle 11g [/SIZE]and it's 32bit OS 

Please help to resolve the issue for Oracle 10g Enterprise Edition on Ubuntu 11.04 Server 32 OS

Thanks !!!!
[/LEFT]

---

### Post by gouravgargg on 2011-08-03
[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)

[http://www.makina-corpus.org/blog/how-install-oracle-10g-full-64-bits-version-not-xe-and-tora-gnu-linux-ubuntu-karmic-910-64-bits](http://www.makina-corpus.org/blog/how-install-oracle-10g-full-64-bits-version-not-xe-and-tora-gnu-linux-ubuntu-karmic-910-64-bits)

[http://web.archive.org/web/20060506141220/http://dizwell.com/main/content/view/96/144/1/3/](http://web.archive.org/web/20060506141220/http://dizwell.com/main/content/view/96/144/1/3/)

[http://revtech0.ash.com/blog.html](http://revtech0.ash.com/blog.html)

[http://www.excession.org.uk/blog/installing-oracle-on-ubuntu-karmic-64-bit.html](http://www.excession.org.uk/blog/installing-oracle-on-ubuntu-karmic-64-bit.html)

[SIZE=4][COLOR=Red]Still the same issue [/COLOR][/SIZE]

:(

---

### Post by Gyokuro on 2011-08-03
Run installer via: ./runinstaller -ignoreSysPrereqs

---

### Post by gouravgargg on 2011-08-03
[SIZE=4]**natty@nattyserver:/home/oracle/database$ ./runInstaller -ignoreSysPrereqs**[/SIZE]
Starting Oracle Universal Installer...

Checking installer requirements...

Checking operating system version: must be redhat-3, SuSE-9, redhat-4, UnitedLinux-1.0, asianux-1 or asianux-2
                                      Passed


All installer requirements met.

Preparing to launch Oracle Universal Installer from /tmp/OraInstall2011-08-03_12-45-12PM. Please wait ...natty@nattyserver:/home/oracle/database$ Oracle Universal Installer, Version 10.2.0.1.0 Production
Copyright (C) 1999, 2005, Oracle. All rights reserved.

Exception java.lang.UnsatisfiedLinkError: /tmp/OraInstall2011-08-03_12-45-12PM/jre/1.4.2/lib/i386/libawt.so: libXtst.so.6: cannot open shared object file: No such file or directory occurred..
java.lang.UnsatisfiedLinkError: /tmp/OraInstall2011-08-03_12-45-12PM/jre/1.4.2/lib/i386/libawt.so: libXtst.so.6: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.loadLibrary0(Unknown Source)
    at java.lang.System.loadLibrary(Unknown Source)
    at sun.security.action.LoadLibraryAction.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
    at sun.awt.DebugHelper.<clinit>(Unknown Source)
    at java.awt.Component.<clinit>(Unknown Source)
    at oracle.sysman.oii.oiif.oiifm.OiifmGraphicInterfaceManager.<init>(OiifmGraphicInterfaceManager.java:222)
    at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.createInterfaceManager(OiicSessionInterfaceManager.java:193)
    at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.getInterfaceManager(OiicSessionInterfaceManager.java:202)
    at oracle.sysman.oii.oiic.OiicInstaller.getInterfaceManager(OiicInstaller.java:436)
    at oracle.sysman.oii.oiic.OiicInstaller.runInstaller(OiicInstaller.java:926)
    at oracle.sysman.oii.oiic.OiicInstaller.main(OiicInstaller.java:866)
Exception in thread "main" java.lang.NoClassDefFoundError
    at oracle.sysman.oii.oiif.oiifm.OiifmGraphicInterfaceManager.<init>(OiifmGraphicInterfaceManager.java:222)
    at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.createInterfaceManager(OiicSessionInterfaceManager.java:193)
    at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.getInterfaceManager(OiicSessionInterfaceManager.java:202)
    at oracle.sysman.oii.oiif.oiifm.OiifmAlert.<clinit>(OiifmAlert.java:151)
    at oracle.sysman.oii.oiic.OiicInstaller.runInstaller(OiicInstaller.java:984)
    at oracle.sysman.oii.oiic.OiicInstaller.main(OiicInstaller.java:866)

---

### Post by gouravgargg on 2011-08-03
[SIZE=4][COLOR=Red]I am using Ubuntu 11.04 Desktop for host machine and Ubuntu 11.04 server for guest machine in Virtual Box 4.1.0

I am trying this on Ubuntu server 11.04 without GUI[/COLOR][/SIZE]


All of are 32 bit OS

---

### Post by gouravgargg on 2011-08-03
[SIZE=3][COLOR=SeaGreen]by Using this link [http://www.excession.org.uk/blog/installing-oracle-on-ubuntu-karmic-64-bit.html](http://www.excession.org.uk/blog/installing-oracle-on-ubuntu-karmic-64-bit.html)

Now I am trying to install my host machine i.e. Ubuntu 11.04 Desktop 
 [/COLOR][/SIZE][SIZE=3]
Now i got an error during installation : 

[/SIZE][SIZE=3][COLOR=Red]
Exception Name: MakefileException
Exception String: Error in invoking target 'all_no_orcl ihsodbc' of makefile '/home/natty/oracle/product/10.2.0/db_1/rdbms/lib/ins_rdbms.mk'. See '/home/natty/oraInventory/logs/installActions2011-08-03_01-13-56PM.log' for details.
Exception Severity: 1[/COLOR][/SIZE]

---

### Post by Gyokuro on 2011-08-03
Ok,

why you do not use the deb package from Oracle?? ([http://oss.oracle.com/debian/dists/unstable/non-free/binary-i386/oracle-xe-universal_10.2.0.1-1.1_i386.deb](http://oss.oracle.com/debian/dists/unstable/non-free/binary-i386/oracle-xe-universal_10.2.0.1-1.1_i386.deb))

to get it running:

1.) sudo apt-get install bc

2.) sudo dpkg i oracle-xe_10.2.0.1-1.0_i386.deb

3.) sudo /etc/init.d/oracle-xe configure

4.) sudo export ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server && 
export ORACLE_SID=XE &&
export PATH=$ORACLE_HOME/bin:$PATH

5.) sudo /etc/init.d/oracle-xe start

6.) voila! Have fun!

---

### Post by gouravgargg on 2011-08-03
[SIZE=3][COLOR=Red]I Need Enterprise Edition not an Express / Standard Edition [/COLOR][/SIZE][SIZE=3]

I have Microsoft Server now want to shift on Ubuntu Linux 


So right now i am verifying things [/SIZE]

---

### Post by gouravgargg on 2011-08-04
[http://www.excession.org.uk/blog/ins...ic-64-bit.html]("http://www.excession.org.uk/blog/installing-oracle-on-ubuntu-karmic-64-bit.html")


by following this tutorial on Ubuntu 11.04 Desktop



[SIZE=4]SOLVED[/SIZE] 


 :)

---

### Post by manojankk on 2011-12-03
This article clearly describes installation of Oracle 11g release 2 on Ubuntu desktop (Posted on 03-December-2011)
[http://sqlandplsql.blogspot.com/2011/12/installing-oracle-11g-on-ubuntu.html](http://sqlandplsql.blogspot.com/2011/12/installing-oracle-11g-on-ubuntu.html)

---

