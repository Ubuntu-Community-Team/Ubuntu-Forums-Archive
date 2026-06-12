---
title: "libapache2-svn: subprocess post-installation script returned error exit status 1"
date: 2007-09-08
forum: Server Platforms
---

### Post by prabhakaran on 2007-09-08
Hi All,
               While I am Installing libapache2-svn, I have encountered this error, 
**libapache2-svn: subprocess post-installation script returned error exit status 1,**

due to this error, apache2 service is not restarted. 

can any one please help me.

---

### Post by sopordave on 2007-09-19
I think I'm having the same problem. Here is the error, in full:

```
nostromo:~$ sudo apt-get install libapache2-svn
Reading package lists... Done
Building dependency tree
Reading state information... Done
libapache2-svn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libapache2-svn (1.4.3dfsg1-1ubuntu1) ...
This module does not exist!
dpkg: error processing libapache2-svn (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by shermanx on 2007-10-01
Hey, anyone have clue how to fix this? I got the same problem too! :(

---

### Post by l0b0 on 2008-07-14
Ditto - I tried completely removing libapache2-svn and apache2, but still no go. Anyone?

---

