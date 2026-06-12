---
title: "[SOLVED] Uninstalling mordor errors"
date: 2007-06-17
forum: Server Platforms
---

### Post by duckmannz on 2007-06-17
Hi

A while back I installed mordor for a laugh and now that we're all done playing it I want to uninstall it. When I try to uninstall I get the following:

```
duckmannz@server:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B/1076kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 58355 files and directories currently installed.)
Preparing to replace mordor 6.66a-7 (using .../mordor_6.66a-7_i386.deb) ...
Unpacking replacement mordor ...
Undefined argument in option spec
dpkg: warning - old post-removal script returned error exit status 255
dpkg - trying script from the new package instead ...
Undefined argument in option spec
dpkg: error processing /var/cache/apt/archives/mordor_6.66a-7_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 255
Undefined argument in option spec
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 255
Errors were encountered while processing:
 /var/cache/apt/archives/mordor_6.66a-7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
duckmannz@server:~$

```

How can I fix this?

Mnay thanks in advance!

---

### Post by duckmannz on 2007-07-02
*bump* Anyone have an idea?

---

### Post by duckmannz on 2007-07-25
Finally figured it out. The perl file /usr/sbin/deluser has a problem with the new perl. You need to change $ to \$ in deluser line 84 to read:
            "conf=s" => \$configfile,

Now it uninstalls fine! I picked up the tip from [here]("http://lists.alioth.debian.org/pipermail/adduser-devel/2006-March.txt.gz").

---

