---
title: "Box with raid card boots to black screen after update"
date: 2015-09-30
forum: Server Platforms
---

### Post by rossguil on 2015-09-30
Good evening everyone!

I am experiencing a problem with my Ubuntu server at home: After the last kernel update, I am unable to boot the server properly.

The server boots "normally" though the POST, until Grub takes over. I see the menu appearing, then, after the ~30 secs it takes to boot the default option, the screen just goes black... I have tried about every trick I could find to make it boot, namely adding some options to the grub boot command (nomodeset, something disabling the graphics driver, etc..), booting from a CD and perform a fsck on the main hard disk, etc...](*,)

The only thing that seems to work is to take the server down, open it, remove the raid card and re-plug the server. Then it will boot normally, and I am able to shut it down smoothly, plug the raid card back and tadaa! It boots again.

I am confused about what to do to prevent this raid card switch-a-roo every time a new update to the system is available, which has been quite frequent over the last week or so....

 I use it mainly as a glorified NAS, so the components are a little bit dated. Maybe it's a possible cause?
Motherboard: Asus A8N32-SLI Deluxe
CPU: AMD Athlon x2 4800+
RAM: 4gb of ram (3.5 detected due to the motherboard)
SSD: 120gb Kingston SSDnow
GPU: Some generic ASUS card
Raid card: DELL LSI Megaraid 9270-8i with 8 disks attached
OS: Ubuntu 15.04

The operating system disk is listed as /dev/sdb and the RAID array is on /dev/sda. That may also be another possible cause.

The operating system *was* working 30 minutes ago, but I had to perform a reboot after compiling and installing ps3mediaserver, its dependencies and a whole bunch of system updates. I just spent the evening debugging my black screen of death by unplugging the raid card and plugging it again, but it seems that the last batch of updates broke whatever setting I was able to fix earlier....

I will gladly provide any information needed to get to the bottom of this issue, feel free to ask any question you think would provide a clue to what could the cause be.

---

### Post by darkod on 2015-09-30
Have you tried booting a previous kernel? You can do that in the grub menu in Previous Versions or something like that?

And another point, but it's too late now. Don't use the normal releases even for a home server. If you are looking for stability, only LTS. They come out every two years and the latest is 14.04. Think of the normal releases as trial and error while developing the LTS. Plus they have only 9 months support compared to 5 yrs for LTS. I'm not saying this is directly related to some update but it could easily be. Give the previous kernels a shot.

---

### Post by rossguil on 2015-09-30
Good morning darkrod,

First of all thanks for the quick reply! Using the 15.04 version was indeed a test. I had to change the raid card for upgradeability and I thought that using a newer version of the Ubuntu distro would be better. If all else fails, I'll try a 14.04 install (I don't have much on the server, so if it can help..).

I did try to boot the other versions of the kernel (It's in the "Advanced options for Ubuntu" menu, right under the regular Ubuntu boot item) but nothing made it past the post-grub black screen. The kernels I tried:
3.19.0-30-generic
3.19.0-28-generic
3.19.0-15-generic

I did try most of their upstart and recovery modes too. When I am confronted to the black screen of death, I can still reboot using the good'ol Ctrl+Alt+Del, so the system is not "frozen" per se. It's more a failure to boot to the hard disk.

Also, I did perform a memtest out of desperation last time I encountered this problem (right befored I discovered the RAID card switch-a-roo technique). The test ran for a straight 26 hours without any error.

Thanks again for any insights

---

### Post by rossguil on 2015-10-01
*bump*

I will perform a re-install of the operating system using 14.04.3 LTS tonight. I have a feeling that the issue will reappear somehow, so I will keep posting updates here.

EDIT: Moar issues!! I am totally unable to re-install Ubuntu. I tried with a burned DVD-RW, but I kept getting an error about how the system was not able to mount /dev/fd0 (there's no such thing as a floppy drive on the server...). I then switched to a bootable USB key, and I am able to "start" the installation process, that is go through the keyboard setup. After that I get a big pause and switching to the debug console (alt + F4) shows me that the installation process is AGAIN having trouble with an imaginary floppy disk drive:
```
blk_update_request: I/O error, dev fd0, sector 0
floppy:error -5 while reading block 0
```
It is beginning to look like the end of the road for this hardware...

---

### Post by rossguil on 2015-10-03
Ok, I am getting somewhere. I managed to install Ubuntu Server version 12.04.5-LTS on the server with the card disconnected, then I got the raid card working with the OS and I am doing a refresh of the backup I had of the data.

I am puzzled as to why an earlier version works so far flawlessly but, hey, new hardware is on the way!

A few questions remain unanswered though:
1) Will the new hardware encounter the same problems as the old one with Ubuntu Server 14.04.3-LTS and the raid card both plugged in at the same time?
2) What could be the source of the original conflict?

To be continued next week when I receive the parts... (Yay! It's christmas early! Kind of...)

---

