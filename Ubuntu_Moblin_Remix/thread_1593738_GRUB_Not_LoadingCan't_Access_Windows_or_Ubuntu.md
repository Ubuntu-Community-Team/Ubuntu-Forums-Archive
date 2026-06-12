---
title: "GRUB Not Loading/Can't Access Windows or Ubuntu"
date: 2010-10-11
forum: Ubuntu Moblin Remix
---

### Post by JGeZau on 2010-10-11
I have Windows 7 and Ubuntu as dual boot on my Acer Netbook. Windows partition got corrupted so I did a Windows restore, now the computer does not want to load either of the OSs.

When I turn on the computer, the Acer logo appears, then it tries to load grub, but it just boots again and keeps doing that over and over. Refer to video below.

[[IMG]http://i44.photobucket.com/albums/f48/JGeZau/th_video-2010-10-11-16-42-00-1.jpg[/IMG]](http://s44.photobucket.com/albums/f48/JGeZau/?action=view&current=video-2010-10-11-16-42-00-1.mp4)

So I made a live USB and tried to install Ubutnu again, or delete the ubutnu partition and keeps telling me that there is no OS in the Live USB.

[IMG]http://i44.photobucket.com/albums/f48/JGeZau/2010-10-11164320.jpg[/IMG]

What should I do?

Thanks

---

### Post by albertcolin on 2010-10-14
When you install Windows upon Linux Grub file is lost, you can restore it using the installation CD for Red Hat, in rescue mode press R when booting the installation CD and after installing the image of system read / write mode and run the following commands

chroot /mnt/sysimage i.e. to mount system image and the install grub by running ->

grub-install /dev/sda as in whatever is you Hard Drive's name i.e. maybe /dev/sda or sdb .....

---

### Post by sqr47 on 2010-10-26
I have a similar problem here, GRUB not loading, just in the same constant loop any way to fix without Red Hat livecd? I've been able to boot my computer fine since I upgraded Ubuntu to 10.10, this just happened after I ran Windows Updater

---

### Post by drs305 on 2010-10-26
The constantly rebooting issue is normally caused by Grub being loaded on the Windows partition rather than in the drive's MBR. Normally this issue is resolved by restoring the Windows MBR.

Forum member *meierfra* created a page about it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by sqr47 on 2010-10-26
Apparantly I'm suffering from a different problem, and the backup boot sector might be corrupted, and I need to run "fixboot" from a Windows CD. I don't have a Windows CD, am I totally screwed?

---

### Post by drs305 on 2010-10-26
> **sqr47 said:**
> Apparantly I'm suffering from a different problem, and the backup boot sector might be corrupted, and I need to run "fixboot" from a Windows CD. I don't have a Windows CD, am I totally screwed?


Take a look at posts 7 & 9. There are various Windows links, including a Windows repair CD:
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

---

### Post by sqr47 on 2010-10-26
Yeah I ran "bootrec.exer /fixmub" in the CMD on the startup repair disk, it booted straight into windows, but at least that's a start.

---

### Post by drs305 on 2010-10-26
> **sqr47 said:**
> Yeah I ran "bootrec.exer /fixmub" in the CMD on the startup repair disk, it booted straight into windows, but at least that's a start.

That was the intent. Now you can try to restore Grub if you want. Boot the LiveCD, mount your Ubuntu partition, and then install Grub2. Substitute the X and Y values, and don't use the Y value in the second command (e.g. sda and not sda1)
```
sudo mount /dev/sdXY
sudo grub-install --root-directory=/mnt /dev/sdX
```

The above should restore Grub if your Grub files are intact. If they aren't, you are going to end up back where you started (no Ubuntu and no Windows). 

It would be best if you started your own thread, run the boot info script from the following link, and post the contents of RESULTS.txt in your first post.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by fireflower on 2010-10-27
I had to deal with the same problem. It was a bit of a harsh introduction. Basically this is what you need to do: Install GRUB from the LiveCD.

Step 1: Enter BIOS. This can be done during startup by pressing DEL or F1 or something similar, it depends on your BIOS. Happily the BIOS itself should display a message declaring what button during the abortive startup process you're seeing over and over.

Step 2: Change the boot up priority list to put your CD-ROM drive first. Not the DVD drive! Even if they're physically the same!

Step 3: Insert the LiveCD (the disc on which you slow-burned the .iso of Ubuntu) and pres butan to start the computer. This will allow the computer to boot, in Ubuntu, but it is reading the OS from the disc, not the hard drive.

Step 4: Install GRUB to the hard drive from the LiveCD. This is the scary part that involves the use of the terminal. The following is the method I used based on [[color=red]this information[/color]](https://help.ubuntu.com/community/Grub2). First click Applications, then Accessories, then Terminal.
```
sudo fdisk -l
sudo mount /dev/sdXX /mnt
``` (Substitute the correct partition: sda1, sdb5, etc.) ```
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
update-grub
grub-install /dev/sdX
``` (Substitute the correct device - sda, sdb, etc. Do not specify a partition number.) ```
sudo grub-install --recheck /dev/sdX
```(For example sda. Do not specify a partition) ```
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/boot
sudo umount /mnt/usr
sudo umount /mnt
sudo reboot
```

---

