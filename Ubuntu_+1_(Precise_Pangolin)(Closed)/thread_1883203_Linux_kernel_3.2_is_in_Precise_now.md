---
title: "Linux kernel 3.2 is in Precise now"
date: 2011-11-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-18
You don't need to wonder any longer will  Precise ship linux kernel 3.2.
Linux 3.2 rc2 is in Precise repos, building in Launchpad now.


Here:
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-1.1](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-1.1)

> 
Changelog          linux (3.2.0-1.1) precise;
urgency=low

[ Andy Whitcroft ]
* armhf -- enable armhf and create the first flavours
* SAUCE: ensure root is ready before running usermodehelpers in it
* [Config] enforcer -- ensure CONFIG_FAT_FS is built-in on arm

[ Leann Ogasawara ]
* Temporarily ignore module check
* [Config] Enable PCI_IOV on powerpc
* [Config] Temporarily disable CONFIG_PASEMI_MAC on powerpc
* rebase to v3.2-rc2
* SAUCE: include <linux/export.h> for cpuidle34xx arm build
* SAUCE: include <linux/kernel.h> for linux/mtd/map.h arm build
* SAUCE: include <linux/printk.h> and <stdarg.h> for mmc_core arm build
* SAUCE: select ARM_AMBA if OMAP3_EMU
* [Config] updateconfigs after select ARM_AMBA
* [Config] Temporarily disable CONFIG_KVM_BOOK3S_32 on powerpc
* [Config] Enable CONFIG_EXT2_FS=m
* [Config] Build in CONFIG_SATA_AHCI=y
* Resolve linux-image-extra's install dependency    

[ Seth Forshee ]
* [Config] Enable EVENT_POWER_TRACING_DEPRECATED=y for powertop
* SAUCE: (drop after 3.2) Input: ALPS - move protocol information to     Documentation
* SAUCE: (drop after 3.2) Input: ALPS - add protocol version field in     alps_model_info
* SAUCE: (drop after 3.2) Input: ALPS - remove assumptions about packet     size
* SAUCE: (drop after 3.2) Input: ALPS - add support for protocol versions     3 and 4
* SAUCE: (drop after 3.2) Input: ALPS - add semi-MT support for v3     protocol
* SAUCE: (drop after 3.2) Input: ALPS - add documentation for protocol     versions 3 and 4 

[ Stefan Bader ]
* [Config] Built-in xen-netfront and xen-blkfront
* Fix build of dm-raid45 and re-enable it 

[ Tim Gardner ]
* [Config] CONFIG_USB_XHCI_HCD=y     - LP: [#886167]("https://launchpad.net/bugs/886167")
* [Config] CONFIG_R6040=m     - LP: [#650899]("https://launchpad.net/bugs/650899")
* SAUCE: Add a new entry (413c:8197) to Bluetooth USB device ID table     - LP: [#854399]("https://launchpad.net/bugs/854399")
* [Config] Consolidated amd64 server flavour into generic
* [Config] updateconfigs after rebase to 3.2-rc1
* [Config] Disabled dm-raid4-5
* [Config] Disabled ndiswrapper
* [Config] Disable vt6656
* [Config] exclude ppp-modules for virtual flavour
* [Config] CONFIG_MEMSTICK_R592=m     - LP: [#238208]("https://launchpad.net/bugs/238208")

[ Upstream Kernel Changes ]
* CHROMIUM: seccomp_filter: new mode with configurable syscall filters     - LP: [#887780]("https://launchpad.net/bugs/887780")
* CHROMIUM: seccomp_filter: add process state reporting     - LP: [#887780]("https://launchpad.net/bugs/887780")
* CHROMIUM: seccomp_filter: Document what seccomp_filter is and how it     works.     - LP: [#887780]("https://launchpad.net/bugs/887780")
* CHROMIUM: x86: add HAVE_SECCOMP_FILTER and seccomp_execve     - LP: [#887780]("https://launchpad.net/bugs/887780")
* CHROMIUM: arm: select HAVE_SECCOMP_FILTER     - LP: [#887780]("https://launchpad.net/bugs/887780")
* CHROMIUM: seccomp_filters: move to btrees
* CHROMIUM: enable CONFIG_BTREE
* CHROMIUM: seccomp_filter: kill NR_syscall references
* CHROMIUM: seccomp_filters: guard all ftrace wrapper code
* CHROMIUM: seccomp_filters: clean up warnings; kref mistake
* CHROMIUM: seccomp_filter: remove "skip" from copy and add drop helper
* CHROMIUM: seccomp_filter: allow CAP_SYS_ADMIN management of execve
* CHROMIUM: seccomp_filter: inheritance documentation
* CHROMIUM: seccomp_filter: make inherited filters composable
* CHROMIUM: Fix seccomp_t compile error     - LP: [#887780]("https://launchpad.net/bugs/887780") 
* CHROMIUM: Fix kref usage     - LP: [#887780]("https://launchpad.net/bugs/887780")
* CHROMIUM: enable CONFIG_SECCOMP_FILTER and CONFIG_HAVE_SECCOMP_FILTER
* rebase to v3.2-rc2

-- Leann Ogasawara <email address hidden>   Mon, 31 Oct 2011 09:24:39 -0400


---

### Post by zika on 2011-11-18
What I need is CONFIG_SATA_PMP=N ... ;)
I'm sure, not only me... ;)

---

### Post by Harry33 on 2011-11-18
Now we are waiting to find out will mesa 7.12 ( 8.0 ) arrive in Precise.

---

### Post by VinDSL on 2011-11-20
> **Harry33 said:**
> You don't need to wonder any longer will  Precise ship linux kernel 3.2.
Linux 3.2 rc2 is in Precise repos, building in Launchpad now.
I just installed 3.2.0-1.1

Running fine (for the past 14m 38s).  ;)

This is what peaked my curiosity...


SOURCE:  [http://voices.canonical.com/kernelteam/](http://voices.canonical.com/kernelteam/)
> _Status: Precise Development Kernel_

We have uploaded the 3.1.0-2.3 Ubuntu kernel which was based on the upstream v3.1 kernel. Upstream is in the early -rc releases of the v3.2 kernel, ie currently v3.2-rc1. **[COLOR="Blue"]Given a higher likelihood for instability with an early -rc, we will hold off doing the first 3.2.0-1.1 upload until we rebase onto upstream v3.2-rc2. I would anticipate this prior to Alpha 1 (Thurs Dec 1). If there are any patches which need to land in the 12.04 kernel, submit them now so that they receive adequate testing and feedback.[/COLOR]**

It's got to be good, yes?  LoL!  :D

---

### Post by Harry33 on 2011-11-20
I have one setup with AMD HD2600 Pro graphics card, I use open source x dricer xserver-sorg-video-ati. This all from Precise repos setup.

Now, I noticed that this new rc2 kernel 3.2 will hang when rebooting or shutting down.
It say "will now restart" or "will now halt", but nothings happens, it just hangs there.
Kernel 3.1 (release version) works well.

---

### Post by kaldor on 2011-11-20
> **Harry33 said:**
> Now we are waiting to find out will mesa 7.12 ( 8.0 ) arrive in Precise.

It should. It's due out a few months before 12.04 is released. If it doesn't make it in time, I suspect it'll be there by 12.04.1.

---

### Post by VinDSL on 2011-11-20
> **Harry33 said:**
> Now, I noticed that this new rc2 kernel 3.2 will hang when rebooting or shutting down.[...]
Interesting!

3.2.0-1.1 worked a treat, last night, before going to bed.  And, again, this morning, when I awoke.

When I got home from church and cold booted, my network service wasn't working.  So, I attempted a warm boot.  No dice!  Hanging on shutdown, like you said.

Cold booted.  Everything came up, but when the desktop loaded, the upper panel looked janky, for a moment or two - colors were wrong - generic Gnome 3 icon set was being used instead of indicators, blah, blah, blah - then, Unity kicked in.

That hesitation rang a bell for me...

I went into my x-server settings and did the ol' IgnoreABI trick.

Tried a warm boot.  Nothing.  Had to manually power-off again.

Next cold boot (ignoreABI now in effect) everything looks/works fine, e.g. so far, so good.

I'll try a warm boot now, after I submit this post.  BBL

**Edit**

Alrighty, then...

Warm boot/restart worked, but when I got back to the desktop, the network service wasn't working, again.  And, it hung on shutdown, too.  LoL!

So, I judge 3.2.0-1.1 to be a crapshoot, at this time.

As Dirty Harry would say, "Are you feeling lucky today, punk?  Well, are you?"  :D

**Edit-2**

Hangs on "Log Out" too...

---

### Post by Harry33 on 2011-11-21
> **VinDSL said:**
> Interesting!

3.2.0-1.1 worked a treat, last night, before going to bed.  And, again, this morning, when I awoke.

When I got home from church and cold booted, my network service wasn't working.  So, I attempted a warm boot.  No dice!  Hanging on shutdown, like you said.

Cold booted.  Everything came up, but when the desktop loaded, the upper panel looked janky, for a moment or two - colors were wrong - generic Gnome 3 icon set was being used instead of indicators, blah, blah, blah - then, Unity kicked in.

That hesitation rang a bell for me...

I went into my x-server settings and did the ol' IgnoreABI trick.

Tried a warm boot.  Nothing.  Had to manually power-off again.

Next cold boot (ignoreABI now in effect) everything looks/works fine, e.g. so far, so good.

I'll try a warm boot now, after I submit this post.  BBL

**Edit**

Alrighty, then...

Warm boot/restart worked, but when I got back to the desktop, the network service wasn't working, again.  And, it hung on shutdown, too.  LoL!

So, I judge 3.2.0-1.1 to be a crapshoot, at this time.

As Dirty Harry would say, "Are you feeling lucky today, punk?  Well, are you?"  :D

**Edit-2**

Hangs on "Log Out" too...

This is a 3.2 kernel issue, because with kernel 3.1 everything works well.
So something about acpid or power management has changed into worse direction.
Perhaps kernel and some mobo's do not work together too well.

Anyway, I have noticed this only with my setup with ATI drivers, not with Intel nor with Nvidia setup.

---

### Post by dino99 on 2011-11-21
confirm that its ok with nvidia 290 here.

---

### Post by ventrical on 2011-11-21
The last time I installed a kernel there were 3 files. Now there is a tar.gz file at the link mentioned. How do install this kernel. /

thanks

---

### Post by Harry33 on 2011-11-21
First from the right, select your achitecture.
Then you can see the list of all built deb files.
Select these three from there: (note that the first one is same to both architectures)

32-bit:
[linux-headers-3.2.0-1_3.2.0-1.1_all.deb]("http://launchpadlibrarian.net/85437159/linux-headers-3.2.0-1_3.2.0-1.1_all.deb")
[linux-headers-3.2.0-1-generic_3.2.0-1.1_i386.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-1.1/+build/2936593/+files/linux-headers-3.2.0-1-generic_3.2.0-1.1_i386.deb")
[linux-image-3.2.0-1-generic_3.2.0-1.1_i386.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-1.1/+build/2936593/+files/linux-image-3.2.0-1-generic_3.2.0-1.1_i386.deb")

64-bit:
[linux-headers-3.2.0-1_3.2.0-1.1_all.deb]("http://launchpadlibrarian.net/85437159/linux-headers-3.2.0-1_3.2.0-1.1_all.deb")
[linux-headers-3.2.0-1-generic_3.2.0-1.1_amd64.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-1.1/+build/2936591/+files/linux-headers-3.2.0-1-generic_3.2.0-1.1_amd64.deb") 
[linux-image-3.2.0-1-generic_3.2.0-1.1_amd64.deb]("https://launchpad.net/ubuntu/+source/linux/3.2.0-1.1/+build/2936591/+files/linux-image-3.2.0-1-generic_3.2.0-1.1_amd64.deb")

---

### Post by ventrical on 2011-11-21
Thanks a million harry33. it's working good here. I'll try a re-boot shutdown.

---

### Post by ventrical on 2011-11-21
Ok .. no issues. I am using this VIA MoBo with P42.80GHz running Cairo-Dock with a ATI Technologies Inc Rage 128 Pro Ultra TF.

When I run Unity 2D (even in oldOneiric) there seemed to be some kind of kernel panic .. or system resources jumped really high.

  I'll load up my GIGAbyte mobo with that new kernel. Hmmmm.. I think I'll go down to the local parts store and barter for some old nvidia cards.

sheesh .. :)

---

### Post by ventrical on 2011-11-21
I did get a system hang, video capped it and then tried to use my USB device to copy it do desktop so I could upload it to youtube and got these errors:

EDIT**  OK [B]What I think happened was that I installed the kernel without having my sources list set for precise -so the new kernel was actually running in Oneiric. That being resolved now. Not sure  if this will affect anything ..but it looks good so far.

 Precise is a masterpiece.

thanks..

[/B]

---

### Post by xyzzyman on 2011-11-22
Works great on Oneiric. Not sure why but took 5 seconds off my stock 3.0.0-13 kernel. Compiled from [https://launchpadlibrarian.net/85642192/linux_3.2.0-1.2.tar.gz](https://launchpadlibrarian.net/85642192/linux_3.2.0-1.2.tar.gz), optimized for core2 and stripped lots of junk out and added some drivers into the kernel instead of a module, and got another 2 seconds off down to 24.91s! Which is good for me as a few months back I couldn't get under 40 seconds on Natty and while testing Oneirc I was a minute 20.

[[img]http://s9.postimage.org/exq43i4yz/Aspire_6930_G_oneiric_20111122_2.jpg[/img]](http://postimage.org/image/exq43i4yz/)

---

### Post by matt_symes on 2011-11-22
It's working alright here as well (Precise). It actually fixed another minor issue i had. 

The only thing i have seen is that i lose my mouse every once in a while This is an X problem as dropping to a console and restarting X fixes it - as you would expect. I don't think it's due to the kernel but other updates. I will investigate at some point.

The only thing i could not get working at the new catalyst drivers no matter how hard i tried. I suppose that's not too much of a surprise though.

---

### Post by effenberg0x0 on 2011-11-22
Just tested, seems alright. As usual, no luck on dkms for nvidia-proprietary and virtualbox, had to manually invoke kernel build. Also vmware, which need some tweaking to its defs/ifdefs in tars. It's slower than my previous one though (but that was built with cpu specific march/mtune and config was set to preempt/low-latency).

---

### Post by ventrical on 2011-11-22
After I did an update on one of my machines the 'Restart' indicator came on BEFORE the sudo apt-get upgrade was done. Of course I lost my mouse and a few other bugs .. but when I went back to terminal and tried to run - sudo apt-get upgrade it came back with some thing to the effect to try and run:

sudo **dpkg** -i --configure -a

and it started to install  the unistalled packages that were terminated when I clicked on the restart indicator.

 So... I think perhaps that the early *restart* indicator is a bug because by using it - packages that are in the process of being installed are broken - but can be recovered by  the above command.

---

### Post by zika on 2011-11-22
> **ventrical said:**
> After I did an update on one of my machines the 'Restart' indicator came on BEFORE the sudo apt-get upgrade was done. Of course I lost my mouse and a few other bugs .. but when I went back to terminal and tried to run - sudo apt-get upgrade it came back with some thing to the effect to try and run:

sudo dkms -i --configure -a

and it started to install  the unistalled packages that were terminated when I clicked on the restart indicator.

 So... I think perhaps that the early *restart* indicator is a bug because by using it - packages that are in the process of being installed are broken - but can be recovered by  the above command.
You mean **sudo dpkg -i --configure -a** :)... ?

---

### Post by ventrical on 2011-11-22
> **zika said:**
> You mean **sudo dpkg -i --configure -a** :)... ?

 I got seven machines going  :) but .. thats no excuse for bad code. Thanks for the correction.

---

### Post by ventrical on 2011-11-24
I am just curious as to how this got installed into the ointment all of a sudden..

linux-image-3.2.0-1-generic_3.2.0-1.1_i386.deb.part

---

