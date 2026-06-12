---
title: "Packages not getting upgraded?"
date: 2008-09-27
forum: Server Platforms
---

### Post by DWizzard on 2008-09-27
Hi there,

When I run apt-get update, then apt-get install on my 8.04 server I get this

Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.


So, how come it didn't upgrade them? Is there some special reason?
How can I make it so they are upgraded, and is there some security reason not to?

Thanks :D

---

### Post by hansdown on 2008-09-27
Hi DWizzard.

It's because there are no upgrades to add.

This is normal.

---

### Post by keithweddell on 2008-09-27
> **hansdown said:**
> Hi DWizzard.

It's because there are no upgrades to add.

This is normal.

This advice is incorrect.  Have you run apt-get upgrade or if you want to be more conservative apt-get --show-upgraded?  The apt-get manpage has more options that might be useful.

Keith

---

### Post by koenn on 2008-09-27
> **DWizzard said:**
> Hi there,

When I run apt-get update, then apt-get install on my 8.04 server I get this

Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.


So, how come it didn't upgrade them? Is there some special reason?
How can I make it so they are upgraded, and is there some security reason not to?

Thanks :D
use apt-get upgrade to upgrade, not apt-get install.

The result may be the same in this case, but 'install' is for installing new packgs, upgrade is to upgrade software you have already installed.

"(number) not upgraded" indicates a number of packages have newer versions available, but couldn't be upgraded.
reasons for that are usually
a/ the packages require a dist-upgrade 
b/ generel dependency trouble.

most likely, its a/
try this to see if dist-upgrade would make a difference :
```
 
sudo apt-get update
sudo apt-get -s dist-upgrade

```

---

### Post by DWizzard on 2008-09-27
Hi there,

Thanks, but why does it say
23 not upgraded?

---

### Post by koenn on 2008-09-27
"(number) not upgraded" indicates a number of packages have newer versions available, but couldn't be upgraded.
reasons for that are usually
a/ the packages require a dist-upgrade
b/ generel dependency trouble.

---

### Post by lykwydchykyn on 2008-09-27
Can you post the entire output of the command:
```
apt-get dist-upgrade
```

---

### Post by DWizzard on 2008-09-27
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  base-files bash bsdutils cpp dpkg eject initramfs-tools iproute klibc-utils libc6 libdbus-1-3 libgnutls13 libklibc libldap-2.4-2 libpam-modules
  libpam-runtime libpam0g libssl0.9.8 mount pciutils procps python2.5 python2.5-minimal tzdata util-linux util-linux-locales x11-common
27 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.1MB of archives.
After this operation, 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]?


What is odd is, I just installed this machine 2 weeks ago, I thought I wouldn't have to do a dist upgrade....

---

### Post by lykwydchykyn on 2008-09-27
"dist-upgrade" just means it is going to upgrade all packages even if it means removing some things or installing some extra things.  It's not a version upgrade, if that's what you mean.  Normal "upgrade" (or "safe-upgrade" which is the new syntax) will only upgrade packages that don't require extra modifications.

---

### Post by cariboo on 2008-09-27
Instead of dist-upgrade, you may want to use:

```
sudo aptitude safe-upgrade
```

This will not delete any packages on which the dependecies are not met.

Jim

---

