---
title: "Raid 1 array malfunctioning, most likely simple"
date: 2008-09-18
forum: Server Platforms
---

### Post by exutable on 2008-09-18
Hey guys,

I am running Debian Etch 4.0 on a new build that I just did, well I have always done raids through hardware(Intel Matrix Storage Manager) but this time I decided I was going to try out a linux software raid.  So when I initially installed the OS I partitioned two 500 gb hard drives identically and created the raid array in the OS setup.  Well I decided I was going to test my little creation by unplugging each of the hard drives individually.  One obviously boots to the OS and the other does nothing.  One thing that I have noticed when I turn off the comp it says md0 array fails to stop(I am guessing it was never started). 

Anyways is there anyway to fix the array now without having to reinstall the OS?


Thanks in advance.

---

### Post by anderswestrup on 2008-09-18
You can re-assemble a RAID array with the "mdadm --assemble" command. It is best to do this from a live CD, you don't want to have any filesystem from the disks mounted.

---

### Post by Krupski on 2008-09-18
> **exutable said:**
> Hey guys,

I am running Debian Etch 4.0 on a new build that I just did, well I have always done raids through hardware(Intel Matrix Storage Manager) but this time I decided I was going to try out a linux software raid.  So when I initially installed the OS I partitioned two 500 gb hard drives identically and created the raid array in the OS setup.  Well I decided I was going to test my little creation by unplugging each of the hard drives individually.  One obviously boots to the OS and the other does nothing.  One thing that I have noticed when I turn off the comp it says md0 array fails to stop(I am guessing it was never started). 

Anyways is there anyway to fix the array now without having to reinstall the OS?


Thanks in advance.

Try setting up GRUB to use FALLBACK. That is, it will first try to boot from the "first" drive, then if it fails it will try the "second" drive (which, for RAID-1, are both identical).

Read this: [http://www.gnu.org/software/grub/manual/html_node/Booting-fallback-systems.html#Booting-fallback-systems](http://www.gnu.org/software/grub/manual/html_node/Booting-fallback-systems.html#Booting-fallback-systems)

I know it seems like a work-around... but think about it... the master boot record (MBR) is stored on a physical drive and the system knows nothing about MDADM until it's loaded. If the drive with the MBR you boot from isn't there, the system has nowhere to go!

I built a few file server boxes and I anticipated that this might be a problem, so I purposely setup the machines to boot from a small, single 4GB COMPACT FLASH camera memory card. Linux lives on the card, and the hard drives are SOLELY for data storage.

Pull out any drive from the array and the system still boots (of course!) and the stored data is also still there (because MDADM gets a chance to load and do it's thing).

Consider using a compact flash card and a CF-to-IDE adapter in your computer.

Alternatively, if you have a modern motherboard that supports USB booting, simply install Linux to a USB stick, set GRUB to install it's bootloader to the USB stick and then run right from the stick.

You can always setup ANOTHER Linux install on the RAID array and then, after booting from the USB stick or Compact Flash, CHROOT to the RAID array's install and run from there.

Even if the RAID array totally fails, only the CHROOT will fail and you will still be in a working Linux environment!

---

### Post by exutable on 2008-09-19
Thank you for referring me to that link on the fallback system, that is a really good idea and is awesome.  I actually have the fallback system set up now but there is only one problem I still can't boot off of disk 2, I get this error when I try to. The weird part is that both of my harddrives have the same used space and everything as if the raid works.

Error 30: Invalid argument

This is my config

default saved
timeout 10
fallback 1 2

title       1
root        (hd0, 0)
kernel      /boot/vmlinuz-2.6.18-6-686 root=/dev/md0 ro
initrd      /boot/initrd.img-2.6.18-6-686
savedefault fallback



title       2
root        (hd1, 0)
kernel      /boot/vmlinuz-2.6.18-6-686 root=/dev/md1 ro
initrd      /boot/initrd.img-2.6.18-6-686
savedefault fallback

Thanks

---

