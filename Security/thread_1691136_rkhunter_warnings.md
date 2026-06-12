---
title: "rkhunter warnings"
date: 2011-02-19
forum: Security
---

### Post by werty2010 on 2011-02-19
so i updated rkhunter and ran a check.it gave me this warnings:

```

..
/bin/dmesg                                               [ Warning ]
..
 /bin/login                                               [ Warning ]
..
/bin/more                                                [ Warning ]
    /bin/mount                                               [ Warning ]
..
    /bin/su                                                  [ Warning ]
..
 /usr/bin/lastlog                                         [ Warning ]
    /usr/bin/ldd                                             [ Warning ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ Warning ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ Warning ]
    /usr/bin/passwd                                          [ Warning ]
..
    /usr/bin/rpm                                             [ Warning ]
..
    /usr/bin/whereis                                         [ Warning ]
..
    /sbin/init                                               [ Warning ]
..
    /sbin/runlevel                                           [ Warning ]
..
    /usr/sbin/groupadd                                       [ Warning ]
    /usr/sbin/groupdel                                       [ Warning ]
    /usr/sbin/groupmod                                       [ Warning ]
    /usr/sbin/grpck                                          [ Warning ]
    /usr/sbin/nologin                                        [ Warning ]
    /usr/sbin/pwck                                           [ Warning ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/useradd                                        [ Warning ]
    /usr/sbin/userdel                                        [ Warning ]
    /usr/sbin/usermod                                        [ Warning ]
    /usr/sbin/vipw                                           [ Warning ]
...
Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

```

some help please
should i be concerned?

---

### Post by howefield on 2011-02-19
Thread moved to "*Security Discussions*"

---

### Post by werty2010 on 2011-02-20
bump

---

### Post by werty2010 on 2011-02-23
anyone???

---

### Post by uRock on 2011-02-23
RKHunter is full of false positives to the extent that it is unusable, unless you know what you are looking for.

---

### Post by werty2010 on 2011-02-23
> **uRock said:**
> RKHunter is full of false positives to the extent that it is unusable, unless you know what you are looking for.

thank you
besides the most common false positives are there any of those i should consider?
could you recommend me any other software i can use instead of rkhunter?

---

### Post by uRock on 2011-02-23
Most anti-viruses look for root kits. I recommend BitDefender.

---

### Post by cariboo on 2011-02-23
Unless you really suspect your system has been rooted, there really isn't a reason to run the tool.

---

### Post by werty2010 on 2011-02-23
> **cariboo907 said:**
> Unless you really suspect your system has been rooted, there really isn't a reason to run the tool.

actually this is the reason
and since im a beginner in linux i would appreciate any help that could show me any info

---

### Post by cariboo on 2011-02-23
What make you think your system has been cracked?

---

### Post by tjwoosta on 2011-02-23
How does rkhunter actually work anyway? 

Ive been reading up on it and apparently the main feature is it compares the md5sums of all your system files against those of known "safe" system files in the rkhunter database, but wouldnt the md5sums be different for files with different compilations and such? Like if I (or whichever distrobution) compiled certain system files against different versions of libraries or other dependencies wouldnt the md5sums be different than those in the rkhunter database?

Or does it perhaps use each seperate distrobutions repositories for building tailored md5sum databases? In which case werty's issue could be that the rkhunter database is out of date, right? Im confused..

There seems to be an amazing lack of information on how this actually works, even on the rkhunter website.

---

