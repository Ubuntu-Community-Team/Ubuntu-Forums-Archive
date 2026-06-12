---
title: "Ubuntu Server No Linux Headers."
date: 2012-01-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by donniezazen on 2012-01-27
Hello,

I installed the daily build of precise server. I am trying to manually install Nvidia drivers. Their are no linux headers for the installed kernel.

```
sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-headers-3.2.0-10-generic-pae
E: Couldn't find any package by regex 'linux-headers-3.2.0-10-generic-pae'
```

```
sudo apt-get install linux-headers
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-3.2.0-11-virtual 3.2.0-11.19
  linux-headers-3.2.0-11-generic-pae 3.2.0-11.19
  linux-headers-3.2.0-11-generic 3.2.0-11.19
  linux-headers-3.2.0-11 3.2.0-11.19
You should explicitly select one to install.

E: Package 'linux-headers' has no installation candidate
```

Thanks.

---

### Post by cariboo on 2012-01-27
Update the kernel to the latest, you are one release behind.

---

### Post by effenberg0x0 on 2012-01-27
This is unusual. I can see linux-headers-3.2.0-10-generic-pae normally. Maybe check your /etc/apt/sources.list and apt-get update? Or clear a broken apt cache?

```
[09:23 PM][ahsl:AL-DESK:~]
$ sudo apt-cache search linux-headers
linux-headers-3.2.0-10 - Header files related to Linux kernel version 3.2.0
linux-headers-3.2.0-10-generic - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-3.2.0-10-virtual - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-generic - Generic Linux kernel headers
linux-headers-server - Linux kernel headers on Server Equipment.
linux-headers-virtual - Linux kernel headers for virtual machines
linux-libc-dev - Linux Kernel Headers for development
linux-source-3.2.0 - Linux kernel source for version 3.2.0 with Ubuntu patches
**linux-headers-3.2.0-10-generic-pae - Linux kernel headers for version 3.2.0 on x86**
linux-headers-generic-pae - Generic Linux kernel headers
linux-libc-dev-armel-cross - Linux Kernel Headers for development (for cross-compiling)
linux-libc-dev-armhf-cross - Linux Kernel Headers for development (for cross-compiling)
linux-headers-3.2.0-9-generic - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-3.2.0-8-generic - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-3.2.0-030200rc7 - Header files related to Linux kernel version 3.2.0
linux-headers-3.2.0-030200rc7-generic - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-3.2.0-6-generic - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-3.2.0-4 - Header files related to Linux kernel version 3.2.0
linux-headers-3.2.0-7 - Header files related to Linux kernel version 3.2.0
linux-headers-3.2.0-6 - Header files related to Linux kernel version 3.2.0
linux-headers-3.2.0-9 - Header files related to Linux kernel version 3.2.0
linux-headers-3.2.0-8 - Header files related to Linux kernel version 3.2.0
linux-headers-3.2.0-4-generic - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-3.2.0-7-generic - Linux kernel headers for version 3.2.0 on x86/x86_64
```

---

### Post by donniezazen on 2012-01-27
> **cariboo907 said:**
> Update the kernel to the latest, you are one release behind.
How do I do that? System is already updated.

```
Linux ubuntu 3.2.0-10-generic-pae #18-Ubuntu SMP Tue Jan 24 17:58:07 UTC 2012 i686 i686 i386 GNU/Linux
```
```
The following packages have been kept back:
  linux-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```
```
linux-headers-3.2.0-11 - Header files related to Linux kernel version 3.2.0
linux-headers-3.2.0-11-generic - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-3.2.0-11-virtual - Linux kernel headers for version 3.2.0 on x86/x86_64
linux-headers-generic - Generic Linux kernel headers
linux-headers-server - Linux kernel headers on Server Equipment.
linux-headers-virtual - Linux kernel headers for virtual machines
linux-libc-dev - Linux Kernel Headers for development
linux-source-3.2.0 - Linux kernel source for version 3.2.0 with Ubuntu patches
linux-headers-3.2.0-11-generic-pae - Linux kernel headers for version 3.2.0 on x86
linux-headers-generic-pae - Generic Linux kernel headers
linux-libc-dev-armel-cross - Linux Kernel Headers for development (for cross-compiling)
linux-libc-dev-armhf-cross - Linux Kernel Headers for development (for cross-compiling)
```
```
cat /etc/apt/sources.list
#

# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Alpha i386 (20120127)]/ precise main restricted

#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Alpha i386 (20120127)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main

```

This is a clean installed and upgraded system. No changes what so ever.

---

### Post by donniezazen on 2012-01-27
> **cariboo907 said:**
> Update the kernel to the latest, you are one release behind.

I installed linux-image-3.2.0.11-generic-pae and then headers. It went through. I will mark this thread solved as soon as i get nvidia installed.

Thanks.

---

### Post by donniezazen on 2012-01-27
Screen is garbled but nvidia did get installed. I have a big blob of white screen.

---

