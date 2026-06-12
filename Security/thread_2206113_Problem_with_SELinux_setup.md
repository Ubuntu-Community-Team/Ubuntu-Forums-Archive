---
title: "Problem with SELinux setup"
date: 2014-02-17
forum: Security
---

### Post by Gohar on 2014-02-17
Hi!
I install selinux-basics and selinux-policy-default in ubuntu server 13.04 as described in [here]("https://wiki.debian.org/SELinux/Setup"), but when i run ```
check-selinux-installation
```, I get the following message:
```
Postfix init script is syncing the chroots.
udev will create node labeled not correctly 
```
How I can fix this?

Then I tried to set SELinux in enforcing mode with ```
selinux-config-enforcing
``` command, but when i reboot, my system doesn't boot up and I get following error:

```
mountall: mount /run/lock [424] terminated with status 32
mountall: Filesystem could not be mounted: /run/lock
mountall: mount /run/shm [426] terminated with status 32
mountall: Filesystem could not be mounted: /run/shm
mountall: mount /run/usr [427] terminated with status 32
mountall: Filesystem could not be mounted: /run/usr

An error occured while mounting /run/lock
```

How I can fix these problems?

---

### Post by linuxyogi on 2014-02-21
I dont know anyone who has successfully configured selinux under Ubuntu. 

By default Ubuntu uses apparmor. 

If you want to run selinux use Fedora.

I tried Fedora 20 but unfortunately my experience was very bad.

I tried installing selinux under Ubuntu and messed up my installation. I just reinstalled.

---

### Post by mmueller44 on 2014-02-24
SELinux in Ubuntu is broken:

[http://translate.google.de/translate?sl=de&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&u=http%3A%2F%2Fforum.kubuntu-de.org%2Findex.php%3Ftopic%3D17463.0](http://translate.google.de/translate?sl=de&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&u=http%3A%2F%2Fforum.kubuntu-de.org%2Findex.php%3Ftopic%3D17463.0)

Even with Fedora 20 it's tricky and not perfect, see link to Fedora-forum via page above . . .

---

