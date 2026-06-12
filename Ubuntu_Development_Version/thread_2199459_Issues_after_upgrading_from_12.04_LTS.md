---
title: "Issues after upgrading from 12.04 LTS"
date: 2014-01-14
forum: Ubuntu Development Version
---

### Post by povlhp on 2014-01-14
I just upgraded from 12.04 LTS, hoping to get 13.10, but got to 14.04 instead :-(
Lost my zfs volumes.

Have some issues. ATI binary drivers does not work, so I downloaded kernel 3.8 from 13.04.

What is the correct way to install zfs-on-linux on an older kernel in Ubuntu ? 

With 12.04 I followed the instructions and did a:
> deb [http://ppa.launchpad.net/zfs-native/stable/ubuntu](http://ppa.launchpad.net/zfs-native/stable/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/zfs-native/stable/ubuntu](http://ppa.launchpad.net/zfs-native/stable/ubuntu) precise main
And then installed the packages. But they do not support 14.04 yet.

---

### Post by povlhp on 2014-01-14
Guess the solution is to follow the generic deb, and make kernel specific modules:
[http://zfsonlinux.org/generic-deb.html](http://zfsonlinux.org/generic-deb.html)

Working on that right now.

---

### Post by kansasnoob on 2014-01-14
What method did you use to upgrade?

---

### Post by dannyboy79 on 2014-01-16
the AMD binary driver doesn't work most likely because you have to install it for your new kernel you're running

---

