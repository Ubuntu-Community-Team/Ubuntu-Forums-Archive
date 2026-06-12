---
title: "Jaunty To Karmic Upgrade is broken due to grub2"
date: 2011-01-11
forum: Server Platforms
---

### Post by electroteque on 2011-01-11
Hi there, i havent really had a chance to ask this for a while, but im in a bit of a bind. im trying to do a release upgrade of 9.04 through to 10.10. I'm stuck at getting karmic to reboot because of a grub problem. I keep getting "error 15" file not found. Not one single forum post has helped for some reason which is strange. Release upgrades have always worked even though not recommended, but this one of all has been the worst of the lot and totally insane. 

Im testing in a vmware before i do this for real on the production server, I am using a raid1 setup and boot partitions set to md0.

my fstab after the upgrade before i reboot looked like this

# / was on /dev/md1 during installation
UUID=######################## /               reiserfs relatime        0       1
# /boot was on /dev/md0 during installation
UUID=#########################/boot           reiserfs notail,relatime 0       2
# /vz was on /dev/md2 during installation
UUID=######################### /vz             reiserfs relatime        0       2
# swap was on /dev/md3 during installation
UUID=######################### none            swap    sw              0       0

My grub looked like this after

kernel  /vmlinuz-2.6.31-22-server  root/dev/md1
initrd  /initrd.img-2.6.31-22-server


etc

I tried to first install grub2, i confirmed it installed and worked perfect, and therefore removed grub legacy. 

Ran do-release-upgrade , it completely uninstalled grub2, and it also fails at building /initrd.img-2.6.31-22-server and adding into the grub menu therefore the upgrade fails with this error. I reinstalled grub2, the menu came up fine but trying to load a kernel gave me something like 

alert ! /dev/disk/by-uid/############## does not exist. 

What is the go with this ? Ive been trying to make this work off and on for 6 months :D

---

### Post by Thirtysixway on 2011-01-11
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2")
does this guide help at all?

---

### Post by electroteque on 2011-01-11
A live cd isn't going to help me if I run into this on my production server unless I gain access to the data centre so rather not. 

Grub 2 installs and works perfectly, the release upgrade breaks something somewhere, and removed grub2 in the process like grub-pc and upgrade-grub was not on the system anymore.  Its a problem with the upgrade not grub2 I think or a problem with both especially when it throws an error at creating the image and adding to the grub menu but with no information what the problem is.

---

### Post by electroteque on 2011-01-11
Im testing in a vmware btw have have to keep reverting to a snapshot and starting all over again its the most painful update ever as yet. a fresh install of the server id rather not because id also have to gain access to the data centre and spend ages there. 

the uuid matches whats in fstab btw but it keeps complaining it can't find it when trying to boot. 

If I dont install grub2 before hand it complains about being unable to find a kernel to boot , they show up as /boot/vmlinuz#### in grub and its /vmlinuz#### in the origina menu.lst

---

### Post by electroteque on 2011-01-11
Its decided to not break after installing grub first, removing legacy, doing a dist-upgrade, then a do-release-upgrade. taken me 6 months to keep coming back and trying !

---

### Post by Thirtysixway on 2011-01-11
> **electroteque said:**
> Its decided to not break after installing grub first, removing legacy, doing a dist-upgrade, then a do-release-upgrade. taken me 6 months to keep coming back and trying !

Glad you found a solution. I was doing some searching around, couldn't find anything

---

### Post by electroteque on 2011-01-12
Exactly there is no usable information. 

Unfortunately the upgrade to grub2 and removing legacy after confirming it booted fine, has made the server fail to boot. Simply got a loading stage 1.5 and error 15 error. I run two drives in raid 1 , switched the order around, server booted. rebooted and get a grub console. 

I must say this is totally flakey.

---

### Post by electroteque on 2011-01-12
Confirmed the grub console happens on both disks on my RAID1 system. I had to fix the 15 error by reinstalling grub on the second disk. Both disks come up with a grub console now, and I have to manually load linux

insmod raid
set root=(md0)
linux /vmlinuz-version root=/dev/md1 ro quiet splash
initrd  /initrd.img-version
boot

I'm stuck for answers, what a nightmare, grub == crap :)

---

