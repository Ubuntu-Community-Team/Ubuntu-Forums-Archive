---
title: "Selinux installation seems incomplete.."
date: 2012-10-02
forum: Security
---

### Post by ninja123 on 2012-10-02
I am trying to download selinux on an Ubuntu 11.04 using apt-get.

when I tried sudo apt-get install selinux: I got the following error: The following packages have unmet dependencies: selinux : PreDepends: grub-pc but it is not installable E: Broken packages

I then downloaded selinux-utils, selinux-basics.
then, I tried setenforce 1 it returns: setenforce: SELinux is disabled

So, I checked for the config file under /etc/selinux which showed that
parameter SELINUX=permissive

However setenforce 0/1 always shows selinux disabled. I even tried to login as root and did: echo '1' > /selinux/enforce (actually under /selinux there were no parameters!!)

I even tried seinfo and it showed an error: Could not find policy file blah blah.

What are the dependencies? what should I download? how can I resolve this?


Pleas help

---

### Post by 2F4U on 2012-10-02
From what I read up until now, SElinux seems to be only marginally supported at Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1978277](http://ubuntuforums.org/showthread.php?t=1978277)
[http://ubuntuforums.org/showthread.php?t=1951847](http://ubuntuforums.org/showthread.php?t=1951847)
[http://ubuntuforums.org/showthread.php?t=1672727](http://ubuntuforums.org/showthread.php?t=1672727)

Ubuntu has AppArmor and if you really want SELinux, it may be better to use Fedora, which has a really well integrated SELinux implementation.

---

### Post by TopQuark_net on 2012-10-09
See [https://bugs.launchpad.net/ubuntu/+source/selinux/+bug/1047099](https://bugs.launchpad.net/ubuntu/+source/selinux/+bug/1047099) for the grub-pc removal issue

As 2F4U said, SELinux support is marginal at best.  However, if you are really interested in it, the most relevant/current documentation is here:
[http://wiki.debian.org/SELinux](http://wiki.debian.org/SELinux)

---

### Post by Hungry Man on 2012-10-09
I really wouldn't use SELinux with Ubuntu. If you're looking for SELinux try Fedora. Otherwise I think Apparmor is very useful for Ubuntu users.

---

### Post by bodhi.zazen on 2012-10-09
> **Hungry Man said:**
> I really wouldn't use SELinux with Ubuntu. If you're looking for SELinux try Fedora. Otherwise I think Apparmor is very useful for Ubuntu users.

+1

I highly advise you select the distro based on what security tools you want.

Apparmor - Ubuntu and SUSE
Selinux - Fedora, RHEL, Centos, Scientific Linux
grsecurity - Gentoo (hardened)

---

