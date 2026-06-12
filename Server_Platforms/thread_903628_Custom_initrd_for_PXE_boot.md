---
title: "Custom initrd for PXE boot"
date: 2008-08-28
forum: Server Platforms
---

### Post by Moepi on 2008-08-28
Hello,
First I would like to tell you a bit about what I'm doing:

I try to create a platform consisting of a server and multiple (identical) clients. The clients should be able to boot via PXE. After booting a minimal Linux a selection should be shown (e.g. bash script) to offer options like:
1) Boot from local hard drive
2) Reinstall image from server
3) Reset image
4) Boot something else... (:

The idea is to automatically boot a minimal Linux from the network and show these options. Depending on the option choosen the local hard drive should be mounted as root (1), the hard drive should be formatted and filled with data downloaded from the server (2) and so on.
My problem is currently finding a suitable minimal Linux. It should be loaded entirely from the TFTP server. Up to now I created a custom image which I can successfully load into a RAM drive and mount it. The problem is, that no hardware is recognized.
Another try was to modify the standard initrd delivered with Ubuntu. If I create an image of the initrd and mount it as root file system, no hardware is recognized too. If a simply start the kernel with the unmodified initrd it hangs when it comes to the point where it should mount the root file syste (of course, since it must not mount the local hard drive but a ramdisk).

Are there any tutorials around which cover similar scenarios? Can anyone tell me how I can fill the /dev/ folder of my ramdisk?


Thanks in advance!

---

### Post by promodus on 2008-08-29
> **Moepi said:**
> Hello,
First I would like to tell you a bit about what I'm doing:

I try to create a platform consisting of a server and multiple (identical) clients. The clients should be able to boot via PXE. After booting a minimal Linux a selection should be shown (e.g. bash script) to offer options like:
1) Boot from local hard drive
2) Reinstall image from server
3) Reset image
4) Boot something else... (:


I do something very similar with pxelinux & this simple menu system.
[http://syslinux.zytor.com/wiki/index.php/Menu](http://syslinux.zytor.com/wiki/index.php/Menu)

I network install Ubuntu, XP, and soon Vista.
Also have a linux setup, but rather than doing everything in initrd, I use NFS... Why? Well, I don't have to update the initrd, I simply use aptitude to do all of that. If a machine couldn't handle NFS for whatever reason, I don't want to see it anyway.

> 
The idea is to automatically boot a minimal Linux from the network and show these options. Depending on the option choosen the local hard drive should be mounted as root (1), the hard drive should be formatted and filled with data downloaded from the server (2) and so on.
My problem is currently finding a suitable minimal Linux. It should be loaded entirely from the TFTP server. Up to now I created a custom image which I can successfully load into a RAM drive and mount it. The problem is, that no hardware is recognized.
Another try was to modify the standard initrd delivered with Ubuntu. If I create an image of the initrd and mount it as root file system, no hardware is recognized too. If a simply start the kernel with the unmodified initrd it hangs when it comes to the point where it should mount the root file syste (of course, since it must not mount the local hard drive but a ramdisk).

Are there any tutorials around which cover similar scenarios? Can anyone tell me how I can fill the /dev/ folder of my ramdisk?


Thanks in advance!

If you really must, use busybox.
Take a look at the way knoppix does their boot system. It will operate independently if it can not find the KNOPPIX cloop image. Maybe study their initrd? A thought. I have no tutorials. :(

---

### Post by Moepi on 2008-08-30
Thanks for your hints. I'll give them a try. I spent this Saturday with LFS hoping to get a better understanding of the boot process and how to modify it...

A last resort is using a minimal Ubuntu Server install bootet via NFS. This solution provides all functions needed but is a bit slow ):

---

### Post by promodus on 2008-09-01
How fast do you need it to boot?

From the NFS perspective, it's easier to program and get what you want.
After you got whatever menu's you wish to provide, you can then optimize.

Having said that,if you're backing up and restoring disk images you need to store it somewhere? if you have NFS, you're connected to storage already...

---

### Post by Moepi on 2008-09-01
It is not a matter of setting up the NFS server. The minimal Linux should effectively replace the boot loader and is thus started every time the system is powered on. For this reason it is very important that the minimal Linux starts as fast as possible. Providing a "full minimal Ubuntu" via NFS takes to long :(

I successfully set up a busybox or alternatively booted from the standard initrd of Ubuntu (which also has a busybox ready) and mounted /dev/ram0  as root. The problem here is, that the system does not recognize the hardware. In effect I only need the hard drives and paritions including LVM and the primary network interface.
I'm currently a bit unsure if the kernel does not recognize the disks at all or is only unable to create the device nodes. The latter one should normally be done by udev which is of course not available in my initrds. Copying the device nodes from an installation (on the same hardware) was unsuccessul.
Another problem is, that the ramdrive is read only (CRAMFS). Up to now I didn't care about it. It should be possible to resolve this with UnionFS...

---

### Post by promodus on 2008-09-02
```
user@mybox:/home/user #time mount 1.0.0.1:/var/www www

real    0m0.029s
user    0m0.004s
sys     0m0.004s
```
Mounting a NFS share on my network is quick...

Will this configuration require network access?

In my example with NFS the added time would be the starting of additional services... those can be disabled. From booting the kernel to a shell can be done in maybe 12 seconds?

Do you have a time constraint? What is the desired time to have this system booted? or is this more an exercise in customizing initrd?

---

