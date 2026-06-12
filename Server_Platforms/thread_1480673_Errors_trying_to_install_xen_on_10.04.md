---
title: "Errors trying to install xen on 10.04"
date: 2010-05-11
forum: Server Platforms
---

### Post by wxman on 2010-05-11
I'm trying to install any version of xen on a new install of Ubuntu 10.04 server. I set up the drive for LVM, but I don't think that matters here. I followed the advice on [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Xen](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Xen) and ran ```
aptitude install xen-hypervisor xen-docs convirt
```
I get through the install, then reboot all without any troubles. After reboot I tried "xm info" and I get:
```
root@server2:~# xm info
ERROR Internal error: Could not obtain handle on privileged command interface (2 = No such file or directory)
Traceback (most recent call last):
  File "/usr/sbin/xm", line 8, in <module>
    from xen.xm import main
  File "/usr/lib/python2.6/dist-packages/xen/xm/main.py", line 61, in <module>
    xc = xen.lowlevel.xc.xc()
xen.lowlevel.xc.Error: (1, 'Internal error', 'Could not obtain handle on privileged command interface (2 = No such file or directory)')
```
I've tried reinstalling, but got the same results. Has anyone run into this?

---

### Post by erogevets on 2010-05-11
Basically same error as this [http://lists.xensource.com/archives/html/xen-users/2005-06/msg00481.html](http://lists.xensource.com/archives/html/xen-users/2005-06/msg00481.html)

Did you boot into a xen kernel?

---

### Post by wxman on 2010-05-12
> **erogevets said:**
> Basically same error as this [http://lists.xensource.com/archives/html/xen-users/2005-06/msg00481.html](http://lists.xensource.com/archives/html/xen-users/2005-06/msg00481.html)

Did you boot into a xen kernel?

I did see that one, but they gave no solution. I don't understand what's missing, and how to get it.

---

### Post by wxman on 2010-05-13
So far I've even tried to install it using manual build methods, and they never work either. Is there something different with this version of the server? I never had these kind of problems before.

---

