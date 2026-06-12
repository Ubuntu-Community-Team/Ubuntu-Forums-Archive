---
title: "The package system is broken"
date: 2014-08-13
forum: Ubuntu Development Version
---

### Post by pixelro on 2014-08-13
Hi, i'm on Ubuntu 14.10 with the last update i get this error "The package system is broken"

this is the updates [http://i.imgur.com/P3NreCH.png](http://i.imgur.com/P3NreCH.png)
this is the error message [http://i.imgur.com/W2s1hCc.png](http://i.imgur.com/W2s1hCc.png)

running apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libllvm3.4:i386 libmirprotobuf-dev libmirprotobuf0 mircommon-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmircommon-dev
The following NEW packages will be installed:
  libmircommon-dev
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/20,3 kB of archives.
After this operation, 240 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 380889 files and directories currently installed.)
Preparing to unpack .../libmircommon-dev_0.6.0+14.10.20140811-0ubuntu1_amd64.deb ...
Unpacking libmircommon-dev:amd64 (0.6.0+14.10.20140811-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libmircommon-dev_0.6.0+14.10.20140811-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/mircommon/mir/graphics/native_buffer.h', which is also in package mircommon-dev:amd64 0.5.1+14.10.20140728-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/libmircommon-dev_0.6.0+14.10.20140811-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

bug reports here [https://bugs.launchpad.net/ubuntu/+source/mir/+bug/1356186](https://bugs.launchpad.net/ubuntu/+source/mir/+bug/1356186)
[https://bugs.launchpad.net/mir/+bug/1348515](https://bugs.launchpad.net/mir/+bug/1348515)

---

### Post by pixelro on 2014-08-13
fixed. 

how can i close this thread? :D

---

### Post by varunendra on 2014-08-13
> **pixelro said:**
> how can i close this thread? :D

You can't, only mods and admins can, and they do it only when necessary.

What you can, and should do is to mark the thread as [SOLVED] using "Thread Tools" link above the top post. :)

---

### Post by pixelro on 2014-08-13
thanks :>

---

### Post by portugalthephilosoph on 2015-05-03
I'm having this same issue. What was the solution you found?

---

### Post by Bashing-om on 2015-05-03
portugalthephilosoph; Hi ! Welcome to the forum.

This thread a very old, your post is not likely to get much notice;
May I suggest that you start your own new thread and in this new thread include the outputs - Between Code Tags -  of terminal commands:
```

sudo apt-get update
sudo apt-gt upgrade

```

[INDENT][INDENT]help is what we do
[/INDENT][/INDENT]

---

### Post by cariboo on 2015-05-03
Please post your question in General Help, as this thread is closed.

---

