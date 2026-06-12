---
title: "Upgrading a customized distribution"
date: 2009-11-30
forum: Ubuntu Customization Guide
---

### Post by baggachipz on 2009-11-30
Greetings folks,

I've been given a customized Ubuntu distribution, modified using [the LiveCD guide]("https://help.ubuntu.com/community/LiveCDCustomization?action=show").  It was based on Jaunty.  I extracted the .iso and chrooted into the environment, then ran do-release-upgrade to go to Karmic.  It worked well, save for some complaints that stemmed from many default packages being removed in the previous custom version.  

In any event, I noticed that in listing installed packages after the upgrade, there are now two versions of linux-headers and linux-image: the generic ones based on the new kernel used in Karmic, and ones named after the custom distribution whose name implies that they were constructed from the previous kernel version.  I'm assuming that means that a custom kernel was compiled for the custom distribution, right?  If that's the case, is there any way I can determine what was (or was not) included in the old kernel version to duplicate the effort in compiling a custom kernel based on the one Karmic uses?  Or, is there any harm in having both versions of the linux-image and linux-headers packages installed in my new version?  

As you can probably tell, I know enough to be dangerous but not enough to really roll my sleeves up and know what really needs to be done.  ANY help you can provide would be very greatly appreciated!

---

### Post by Ibidem on 2010-01-01
> **baggachipz said:**
> Greetings folks,


In any event, I noticed that in listing installed packages after the upgrade, there are now two versions of linux-headers and linux-image: the generic ones based on the new kernel used in Karmic, and ones named after the custom distribution whose name implies that they were constructed from the previous kernel version.  I'm assuming that means that a custom kernel was compiled for the custom distribution, right?  If that's the case, is there any way I can determine what was (or was not) included in the old kernel version to duplicate the effort in compiling a custom kernel based on the one Karmic uses?  Or, is there any harm in having both versions of the linux-image and linux-headers packages installed in my new version?  

As you can probably tell, I know enough to be dangerous but not enough to really roll my sleeves up and know what really needs to be done.  ANY help you can provide would be very greatly appreciated!

I don't know as much as many others here, but I know this much:
Having 2 kernels (or 5, for that matter) installed on the same system is safe, as long as you don't end up using completely different ones like one with tuxonice and one without (startup scripts may be troublesome then). 
/boot/config-[kernel-version-build]  is your kernel configuration.
If it has the distro name, it's probably custom; you might check the distro  for updates.


Hope this helps,
Ibidem

---

