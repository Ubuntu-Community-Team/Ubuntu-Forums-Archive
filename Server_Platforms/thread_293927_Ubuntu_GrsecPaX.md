---
title: "Ubuntu Grsec/PaX"
date: 2006-11-05
forum: Server Platforms
---

### Post by BobJJ on 2006-11-05
Hi there,

I've recently installed Ubuntu Dapper Drake, and am rather impressed, except for when it comes to security. I would like to upgrade kernel to a most up to date kernel, and also apply grsec patches. I discovered felosi's article on tuxmachines.org, and so far it's been working, but I thought I'd stop and seek clarification before going any further.

The parts which confuse me are highlighted in bold below

[i]gunzip < grsecurity-2.1.9-2.6.17.7-200607261817.patch.gz | patch -p0

mv linux-2.6.17.7 linux-2.6.17.7-grsec

ln -s linux-2.6.17.7-grsec linux

cd linux

**copy your current config over**

do uname -r to see what kernel your running and copy it, example:

cp /boot/config-2.6.15-26-686L .config

***Configure the kernel:**[/i]

What would my current config be? And where would this be located?

Thanks in advance

---

### Post by po0f on 2006-11-05
BobJJ,

This would be the *.config* for your currently running kernel.
```
$ ls -l /boot/config-`uname -r`
```

---

