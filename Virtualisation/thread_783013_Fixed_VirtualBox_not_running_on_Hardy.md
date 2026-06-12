---
title: "Fixed: VirtualBox not running on Hardy"
date: 2008-05-05
forum: Virtualisation
---

### Post by georgek on 2008-05-05
Just tried to run VirtualBox OSE for the first time since upgrading to Hardy and it didn't work.  I'm in a rush to get some work done so I apologise for not looking up exact commands or package names but this might help someone anyway.

There are a lot of forum threads which are similar but none of the ones I read matched my problem (or solution) that closely.

I got the error message about the kernel module so I went off to Synaptic and installed the relevant virtual package to get the right module - still no good.

/etc/init.d/vboxdrv start wouldn't.  When I didn't find an answer in the forums quickly I tried working manually through the script and luckily didn't have to go far:  modprobe vboxdrv failed.

I knew the module was there (but checked again anyway) and after some head scratching and man page reading I realised that I needed to run depmod.  cd'ed to /lib/modules/`uname -r`, ran depmod and everything is now fine.

HTH
George.

---

### Post by tolginho on 2009-01-10
if you can't starup your vbox driver and it says something like no suitable drivers, try that:

1. type uname -r to get your kernel version.
2. install virtualbox-ose-modules-[kernel version]

eg.

virtualbox-ose-modules-2.6.24-23-openvz if your uname -r returns 2.6.24-23-openvz.

i hope that will helps.

---

