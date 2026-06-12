---
title: "Virtualisation beginner"
date: 2007-12-09
forum: Virtualisation
---

### Post by Charlie Chick on 2007-12-09
Hello Everybody,

I'm a complete beginner to this idea and would like to run Windoze XP inside 7.10 for certain things that I can't do in Ubuntu. Do I need to install Vmware? Player, server or workstation? Or is there an open source program that will do the job? Once installed, how do I install Windoze into it?

My PC has a P4 3Mz, 2Gb of RAM and a 160Gb HDD.

Thanks!

---

### Post by Joeb454 on 2007-12-09
Search the repo's for Virtual Box :)

---

### Post by donnonotin on 2007-12-09
You need to install a program called wine. It allows ubuntu to run .exe programs just like it were windows. (works a hell of a lot better than virtualization)

First you need to go into System>Administration>Software Sources and make sure you have all the universe and multiverse software enabled.

[Then follow the rest of this guide. It's what I used.]("http://www.psychocats.net/ubuntu/wine")

---

### Post by Charlie Chick on 2007-12-09
Interesting. I've been told that virtualisation works better than Wine. I've found a program called Virtualbox which I installed from Add/Remove Programs. I installed it but it's asking for an ISO image and Windoze doesn't come as one so I'm stuck.

---

### Post by pebo on 2007-12-09
> **Charlie Chick said:**
> Interesting. I've been told that virtualisation works better than Wine. I've found a program called Virtualbox which I installed from Add/Remove Programs. I installed it but it's asking for an ISO image and Windoze doesn't come as one so I'm stuck.

Mount your windows cd and then ```
dd if=/dev/cdrom of=windows.iso
```or equivalent. Then you have your iso.

The thing about virtualisation is that you can get all your windows programs working (except maybe the most resource hungry) not just the limited ones supported in wine.

---

### Post by mosaic2s on 2007-12-09
have installed virtual box on xp and then installed ubuntu 7.10 within it.
it works great - little slower. but it is in a window and it does not take on full display. can it be rectified?

will it be the same if have ubuntu as host and xp as guest?

---

### Post by lil_B on 2007-12-11
Charlie, you need to mount your CD-ROM with the windows CD into VirtualBox. I assume you allready created a virtual machine to install into with a virtual hard disk.

You can add the CD-ROM by selecting the OS in the virtual box menu, click on settings then go to the CD/DVD tab. Check off Mount CD/DVD and select the drive you want to use.

Then start the virtual machine with a bootable windows CD in the drive and install.

---

### Post by Charlie Chick on 2007-12-14
> **lil_B said:**
> Charlie, you need to mount your CD-ROM with the windows CD into VirtualBox. I assume you allready created a virtual machine to install into with a virtual hard disk.

You can add the CD-ROM by selecting the OS in the virtual box menu, click on settings then go to the CD/DVD tab. Check off Mount CD/DVD and select the drive you want to use.

Then start the virtual machine with a bootable windows CD in the drive and install.

I have already made a virtual m/c and mounted the the CDROM drive but when I put the Windoze CD in, nothing happens. Do I need to make an iso version of it first?

Thanks!

---

### Post by AndyCooll on 2007-12-14
No, it shouldn't be necessary.

You may need to check your VM's settings/properties, and specifically the CD drive section. Does it have the CD-drive loaded, is it set as the first boot device, and is setup correctly? For instance it may be set to /dev/cdrom0 when your CD-drive is seen by Ubuntu as /dev/cdrom.

:cool:

---

### Post by chestnut1969 on 2007-12-14
Hi,

I run Ubuntu 7.10, with an Windows XP Pro guest on Vmware Workstation 6. Vmware 6 is the only virtualisation product where I can get USB 2 devices running correctly.

Unfortunately my Canon LIDE 70 scanner does not work under Linux, but under XP/Vmware 6 Workstation it does. I have simply set up a Samba share folder to share scans between Windows XP and Linux. 

Works a treat until such time that drivers are available - I live in hope ;)

Cheers

---

### Post by Charlie Chick on 2007-12-17
> **AndyCooll said:**
> No, it shouldn't be necessary.

You may need to check your VM's settings/properties, and specifically the CD drive section. Does it have the CD-drive loaded, is it set as the first boot device, and is setup correctly? For instance it may be set to /dev/cdrom0 when your CD-drive is seen by Ubuntu as /dev/cdrom.

:cool:

Thanks for the advice. I checked VirtualBox's settings and the CDROM is seen correctly. However, there is nothing to make the CDROM actually run. 

Charlie

---

### Post by AndyCooll on 2007-12-17
The CD should run when you power your virtual machine up (you put your CD in your main machines drive, start VirtualBox if it isn't already started and then start your virtual machine. It should be as straightforward as that). It should work just like it would do if you started a normal box/laptop up with a Windows CD in. 

This of course is assuming that the CD-drive is set as the first boot device.

Another thought. If you highlight your virtual machine, and click on the CD/DVD-ROM section, is there a cross in the box against "Mount CD/DVD drive"?

:cool:

---

