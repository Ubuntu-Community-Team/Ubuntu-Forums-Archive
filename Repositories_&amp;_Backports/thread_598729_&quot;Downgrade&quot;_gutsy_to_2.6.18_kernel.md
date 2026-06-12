---
title: "&quot;Downgrade&quot; gutsy to 2.6.18 kernel?"
date: 2007-10-31
forum: Repositories &amp; Backports
---

### Post by djm1021 on 2007-10-31
For various reasons, I would like to build a 2.6.18 kernel from source but still run Gutsy on top of it.  Is this possible?  I've succesfully built and booted a 2.6.23 kernel under a fresh Gutsy install by using the "Master Kernel Thread" instructions ([http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)) and followed the same instructions for 2.6.18, but the resulting 2.6.18 kernel/initrd failed to boot, tested on two different systems, both times unable to read the root disk and falling back to an ash prompt.  I have booted both machines with a 2.6.18 kernel and another (RH-based) distro so it is not that the machines cannot boot 2.6.18 at all.  I've scanned config files without spotting anything either.  Anybody know if 1) this is possible at all and 2) if so, what the magic incantations might be to get this to work?      

Thanks,
Dan

---

### Post by sledgeas on 2007-11-07
Same problem here, I am in a dire need to get BeWAN ADSL USB modem running because of the internet connection I am using; thus is it possible to have 2.6.18 under Gutsy?

Please respond, guys, waiting there..

---

### Post by wadageek on 2007-11-08
I'm running Gutsy but with the feisty kernel (2.6.20).  I did this inorder to fix the problem with ATI fglrx driver and suspend to RAM.  The process I used was quite simple.  I just downloaded the kernel files from the official Ubuntu/feisty repositories and then installed the deb files (and prayed :-k )

    * linux-image-2.6.20-16-generic
    * linux-headers-2.6.20-16
    * linux-headers-2.6.20-16-generic
    * linux-restricted-modules-2.6.20-16-generic
    * linux-source-2.6.20

Once installed, I modified grub (menu.lst)to load the new kernel

Change the _default_ value to new kernel.  ***Remember the menu starts at 0

Not sure if this will work for 2.6.18 but hopefully this will lead you in the right direction

---

### Post by don_eros on 2007-11-15
Hi,

I'm trying to downgrade to 2.6.20 too (not sure what's wrong with my laptop, but it ran smoothly with feisty, so I'm willing to explore the kernel angle).

Where did you find the old kernel exactly? I've tried having a look at the repository in:

[http://it.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-di-i386-2.6](http://it.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-di-i386-2.6)

but is's empty, I also tried looking in the linux-source-2.6.20 dir but it's a real mess in there, there are a gozillion files  with almost identical names and I'm not sure which one I should download (what does "di" stand for anyway?)

Any help would be greatly appreciated, given the crappy performance of my linux system I'm back to using Windows these days, and it's really affecting my karma... ;-)

---

### Post by bigbang on 2008-03-29
In case it is still any help, this is where you can find the packages:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Use the search box at the bottom of the page but remember to select "Distribution: Any".
hope that helped.

---

