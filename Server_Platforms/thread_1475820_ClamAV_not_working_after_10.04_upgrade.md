---
title: "ClamAV not working after 10.04 upgrade"
date: 2010-05-07
forum: Server Platforms
---

### Post by PeterK2003 on 2010-05-07
```
 * Starting ClamAV daemon clamd 
WARNING: Ignoring deprecated option MailFollowURLs at line 33
ERROR: Can't initialize the internal logger
ERROR: Can't open /var/log/clamav/clamav.log in append mode (check permissions!).
   ...fail!

```

```
peterk2003@dungeon:/var/log/clamav$ ls -lh
total 140K
-rw-r----- 1 syslog adm    0 2010-05-02 06:34 clamav.log
-rw-r----- 1 syslog adm 9.9K 2010-04-25 06:48 clamav.log.0
-rw-r----- 1 syslog adm 7.9K 2010-04-29 18:18 clamav.log.1
-rw-r----- 1 clamav adm 1.2K 2010-02-28 06:53 clamav.log.10.gz
-rw-r----- 1 clamav adm 1.3K 2010-02-21 06:40 clamav.log.11.gz
-rw-r----- 1 clamav adm 1.7K 2010-02-14 06:27 clamav.log.12.gz
-rw-r----- 1 clamav adm  12K 2010-04-18 06:50 clamav.log.2
-rw-r----- 1 syslog adm   20 2010-04-25 06:47 clamav.log.2.gz
-rw-r----- 1 clamav adm 1.6K 2010-04-11 06:26 clamav.log.5.gz
-rw-r----- 1 clamav adm 1.2K 2010-03-28 06:44 clamav.log.6.gz
-rw-r----- 1 clamav adm 1.2K 2010-03-21 06:40 clamav.log.7.gz
-rw-r----- 1 clamav adm 1.7K 2010-03-14 06:46 clamav.log.8.gz
-rw-r----- 1 clamav adm 1.6K 2010-03-07 06:35 clamav.log.9.gz
-rw-r----- 1 syslog adm    0 2010-05-02 06:34 freshclam.log
-rw-r----- 1 syslog adm  12K 2010-04-25 06:48 freshclam.log.0
-rw-r----- 1 syslog adm  11K 2010-04-29 17:40 freshclam.log.1
-rw-r----- 1 clamav adm  884 2010-02-28 06:53 freshclam.log.10.gz
-rw-r----- 1 clamav adm 1.1K 2010-02-21 06:40 freshclam.log.11.gz
-rw-r----- 1 clamav adm 1.1K 2010-02-14 06:27 freshclam.log.12.gz
-rw-r----- 1 clamav adm  12K 2010-04-18 06:50 freshclam.log.2
-rw-r----- 1 syslog adm   20 2010-04-25 06:47 freshclam.log.2.gz
-rw-r----- 1 clamav adm 1.1K 2010-04-11 06:26 freshclam.log.5.gz
-rw-r----- 1 clamav adm  830 2010-03-28 06:44 freshclam.log.6.gz
-rw-r----- 1 clamav adm  900 2010-03-21 06:40 freshclam.log.7.gz
-rw-r----- 1 clamav adm 1.2K 2010-03-14 06:46 freshclam.log.8.gz
-rw-r----- 1 clamav adm 1.1K 2010-03-07 06:35 freshclam.log.9.gz
peterk2003@dungeon:/var/log/clamav$

```

i have changed nothing other than upgrading to 10.04.   I am not a linux expert but the permissions look reasonable.  Any suggestions?

---

### Post by PeterK2003 on 2010-05-07
i deleted the logs and it fixed the problem.  The permissions are now:

```
peterk2003@dungeon:/var/log/clamav$ ls -lh
total 12K
-rw-r----- 1 clamav clamav 1.6K 2010-05-07 13:27 clamav.log
-rw-r----- 1 clamav clamav 1.8K 2010-05-07 13:27 freshclam.log

```

Not sure why that broke during the upgrade?

---

### Post by PeterK2003 on 2010-06-29
The permissions got fubared again.  Anyone know why?

---

### Post by glenstewart on 2010-09-07
You will want to fix the cause of that WARNING too.  See [http://ubuntuforums.org/showthread.php?p=9818318#post9818318](http://ubuntuforums.org/showthread.php?p=9818318#post9818318)

---

### Post by marl30 on 2010-09-07
Why not use the gui version, Clamtk. It's found in the software center. The latest version can be downloaded here: [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

---

### Post by AlexanderDGreat on 2010-10-13
Hi, how do you UPGRADE clamAV?

I typed, sudo freshclam but it says:

ClamAV update process started at Wed Oct 13 23:36:17 2010
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.96.1 Recommended version: 0.96.3
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd is up to date (version: 52, sigs: 704727, f-level: 44, builder: sven)
daily.cld is up to date (version: 12134, sigs: 139810, f-level: 53, builder: ccordes)
bytecode.cld is up to date (version: 80, sigs: 10, f-level: 53, builder: edwin)

Can anyone help?

---

