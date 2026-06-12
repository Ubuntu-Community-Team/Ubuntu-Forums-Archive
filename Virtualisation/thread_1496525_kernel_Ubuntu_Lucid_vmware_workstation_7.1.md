---
title: "kernel Ubuntu Lucid vmware workstation 7.1"
date: 2010-05-29
forum: Virtualisation
---

### Post by 24jedi on 2010-05-29
I am running Ubuntu 10.04 LTS Lucid Lynx

Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010

I have recently downloaded an upgrade copy of vmware ws7.1, which I own a licensed copy.
vmware has NOT been previously installed on this OS..its clean
I am still trying to figure out how to get the kernel setup, before installing vmware.
The kernel pre-req for vmware ws7 to run on linux, is to have the following enabled.

// --this line does not exist in my system
CONFIG_RTC=y

//-- this line DOES exist in my system
CONFIG_PARPORT_PC=m 

I do not see CONFIG_RTC=y as an optional parameter.
Instead, I see the use of classes.

grep "CONFIG_RTC" /boot/config-$(uname -r)

dude@ubuntu:~$ grep "CONFIG_RTC" /boot/config-$(uname -r)
CONFIG_RTC_LIB=y
CONFIG_RTC_CLASS=y
CONFIG_RTC_HCTOSYS=y
CONFIG_RTC_HCTOSYS_DEVICE="rtc0"
# CONFIG_RTC_DEBUG is not set
CONFIG_RTC_INTF_SYSFS=y
CONFIG_RTC_INTF_PROC=y
CONFIG_RTC_INTF_DEV=y
CONFIG_RTC_INTF_DEV_UIE_EMUL=y
CONFIG_RTC_DRV_TEST=m
CONFIG_RTC_DRV_DS1307=m
CONFIG_RTC_DRV_DS1374=m
 :
 :

So my question is..how do I ensure that this kernel will meet the requirements for vmware to install correctly?

Or..am I good-to-go?

---

### Post by thelastquincy on 2010-05-30
Try it and see wat happens. What's the worst that can happen? lol

---

### Post by 24jedi on 2010-06-02
I am please to report success.

No kernel patches
No vmware patches

Basically, the vmware workstation v7 installed without issue.

Now, I am not certain if this had anything to do with it, but I did download the kernel source tree in advance of having to upgrade the kernel.

by the by.. I don't have a need for bleeding edge, so the autoupdate feature whereby Ubuntu keeps up to date from Conanical only.  No third party sources

Thanks

---

