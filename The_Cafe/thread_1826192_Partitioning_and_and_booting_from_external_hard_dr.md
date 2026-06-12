---
title: "Partitioning and and booting from external hard drives"
date: 2011-08-16
forum: The Cafe
---

### Post by u-noob-tu on 2011-08-16
the hard drive in question isnt an external one, just an internal one with a USB dock, but id still like to know how to do this. my grandfather just gave me a 200gb hard drive and a USB dock. so far i have just used it for backups but id like to try out other types of Linux, but i dont really want to put them on my laptops hard drive. i just want ubuntu as my primary, but ive been thinking of trying Kubuntu and others lately. is there any way to partition the hard drive to use 50gb for backups and the rest for an OS?

---

### Post by sanderd17 on 2011-08-16
It seems rather dangerous to put backups on a disk that you use to test OS. But yes that is possible. Just use Gparted.

And when you install an other OS. Make sure that the bootloader gets installed to that hard disk and not to the internal hard disk. Than you can boot from that hard disk like you boot from an USB stick.

---

### Post by beew on 2011-08-16
You just boot to a live usb or cd, connect the external drive and install it like you would normally, except that make sure you install with the Advanced Mode (or called "Something Else" in Natty) so you can choose where to put the bootloader, make sure that you install the bootloader in the external drive (say sdb) rather than the internal one, if you install the bootloader in the internal harddrive you won't be able to boot your PC without the external drive attached. 

If you do multiboot on the external drive, you need only one OS to control grub, --say Ubuntu11.04 whose root partition is on sdb1. 

When you add a new OS, choose either not to install bootloader if the option exists (e.g. Fedora) or install the bootloader in the partition rather than the drive if the option of not installing bootloader is not available (as in different flavours of Buntus) , so for example if you install Kubuntu11.04 (actually its root partition) in sdb5, you should install the bootloader in sdb5 instead of sdb. After the installation is complete, boot into the OS that controls grub (in our example it would be Ubuntu 11.04 whose root partition is in sdb1) and run ```
sudo update-grub
``` This would add the new OS to the boot menu (I assume that an OS which uses grub2 such as a version of Ubuntu is controlling grub here)

---

### Post by u-noob-tu on 2011-08-17
thanks for the detailed info. burning a cd of kubuntu 11.04 right now. cant wait to try it,

---

### Post by u-noob-tu on 2011-08-17
i have a question about grub. i successfully booted into Kubuntu on the external hard drive, but grub seems to disappear after only a few seconds, giving me little time to choose what OS i want. plus, i would like grub to show up every time i boot. how would i do that?

---

