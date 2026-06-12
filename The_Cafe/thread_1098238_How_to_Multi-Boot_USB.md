---
title: "How to: Multi-Boot USB"
date: 2009-03-16
forum: The Cafe
---

### Post by EvilRobotDrew on 2009-03-16
read my post, in it's original form on my friend's blog at [http://informationinsecurity.com/](http://informationinsecurity.com/)

This tutorial will guide you through making a USB rescue drive, booting Grub4DOS, and loading Backtrack 3, Damn Small Linux, Belgian Federal Computer Crime Linux, Free DOS, Samurai Linux, Ultimate Boot CD, Ubuntu 8.04, and Darik's Boot and Nuke. You will need a computer able to boot from USB, a computer running Linux (can be the same computer), a large thumb drive (I used a Kingston 16Gb DataTraveller), 2 blank cds, and a lot of time. Follow the steps below, all of them except installing Grub4DOS are optional.

Grub4dos

1. Download Grub4DOS <http://sourceforge.net/projects/grub4dos>
2. Open GParted, and create 2 partitions.
Partition 1 needs to be a primary partition, formatted as FAT32, I made mine 7Gb. this will be where we install Grub4DOS, and being the first partition on the thumb drive will be read by windows as file storage. be sure to label it something you will remember, like "boot", or "first".
Partition 2 needs to be an extended partition. This will contain the logical partitions we need to make for the other Operating systems. no formatting or logical partitions are necessary right now.
3. Install Grub <http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive>
I don't know if it is necessary, but I installed GRUB first. If your bootloader is something other than GRUB, you can try either skipping this step, or doing a quick google search. Using Terminal type "sudo grub-install /dev/(THUMB)" where THUMB is the root of your thumb drive (sdb, not sdb1). Then type "sudo grub" to drop into the GRUB prompt. At the grub prompt, enter the command "root (hdX,Y)" where X is the hard drive number (startng the count at 0, ex. i have 3 Hard drives, after plugging in the thumb drive grub sees 4, so the thumbdrive will be (hd3)), Y is the partition number, it will be )for the first partition on the thumdrive. After successfully entering the root command, we have to setup the drive, "setup (hdX)" and quit grub with "quit". Then copy the contents of your /boot folder onto the drive with "sudo cp -ax /boot /media/(LABEL OF YOUR FIRST PARTITION)" and finally make these files editable by your current user "sudo chmod 777 /media/(LABEL OF YOUR FIRST PARTITION)/boot"
4. Install Grub4DOS
Unzip " grub4dos-0.4.3 " and copy grldr, bootlace.com, and menu.lst onto the first partition of your thumb drive. Navigate to this partition in terminal and run "sudo ./bootlace.com /dev/(THUMB)" where THUMB is the root of your thumb drive (sdb, not sdb1).
5. Reboot
Boot with the thumbdrive, you will see the Menu.lst that came with Grub4DOS.

Backtrack3

1. Download Backtrack 3 USB Version (Extended) < http://www.remote-exploit.org/backtrack_download.html>
2. Make a partition for Backtrack on the Thumbdrive. Make it FAT16, 800Gb large, and label it something you will remember.
3. Using Archive manager, extract the .ISO onto the new partition you made for Backtrack.
4. Edit menu.lst, on the root of your boot partition,and add the following entry

title Backtrack 3 (KDE)
root (hd0,4)
kernel /boot/vmlinuz ramdisk_size=6666 root=/dev/ram0 rw autoexec=xconf;kdm
initrd /boot/initrd.gz

*NOTE* make sure that "root (hd0,4)" points to the partition on your disk that contains Backtrack

Damn Small Linux
1. Download Damn Small Linux dsl-4.4.10-embedded.zip < ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/>
2. Make a partition for DSL on the Thumbdrive. Make it FAT16, 100mb large, and label it something you will remember.
3. Using Archive manager, extract the .ISO onto the new partition you made for DSL.
4. Edit menu.lst, on the root of your boot partition, and add the following entry

title Damn Small Linux
root (hd0,5)
kernel /linux24
initrd /minirt24.gz

*NOTE* make sure that "root (hd0,5)" points to the partition on your disk that contains DSL

Belgan Federal Computer Crime Linux

1. Download FCCU 12.0 <http://www.securitydistro.com/security-distros/40/FCCU/downloads>
2. Make a partition for FCCU on the Thumbdrive. Make it FAT16, 600mb large, and label it something you will remember.
3. Using Archive manager, extract the .ISO onto the new partition you made for FCCU.
4. Edit menu.lst, on the root of your boot partition, and add the following entry

title FCCU Linux
root (hd0,6)
kernel /live/vmlinuz1 boot=live keyb=be noswap username=fccu hostname=fcculive union=aufs
initrd /live/initrd1.img

*NOTE* make sure that "root (hd0,6)" points to the partition on your disk that contains FCCU

FreeDOS

1. Download FreeDOS fdbasecd.iso < http://www.freedos.org/freedos/files/>
2. Make a partition for FreeDOS on the Thumbdrive. Make it FAT16, 62mb large, and label it something you will remember.
3. Copy the .ISO onto the new partition you made for FreeDOS. DON'T EXTRACT IT!
4. Edit menu.lst, on the root of your boot partition, and add the following entry

title Free DOS
find --set-root /fdbasecd.iso
map -mem /fdbasecd.iso (0xFF)
map --hook
root (0xFF)
map --mem /isolinux/data/fdboot.img (fd0)
map --rehook
chainloader (fd0)+1
rootnoverify (fd0)

*NOTE* this should work on any disk that has fdbase.iso on the root of a partition

Samurai Linux

1. Download Samurai Linux <http://sourceforge.net/project/showfiles.php?group_id=235785>
Samurai and Ubuntu both need to be installed live to the USB, they will be persistent. Create a partition that is at least 3 Gb, label it something you will remember. You can also create a separate /home partition for it now. it should be at least 1Gb, and formatted as ext3.
2. Burn the ISO you just downloaded onto a CD, boot from that CD, plug in your USB stick, and use the Samurai installer to install it to the partition you made. If you decided you want a separate /home partition be sure to have the installer mount the partition as /home
DO NOT LET SAMURAI INSTALL A BOOT LOADER! If you do let Samurai install GRUB, you will not only make your USB disk unbootable, but also your COMPUTER!
3. After installation, edit menu.lst on the root of your boot partition, and add the following

title Samurai Web Testing
root (hd0,10)
kernel /boot/initrd.img-2.6.24-23-generic root=UUID=2106-5051 ro quiet splash
initrd /boot/vmlinuz-2.6.24-23-generic

*NOTE* make sure that "root (hd0,10)" points to the partition on your disk that contains Samurai, be sure to change the UUID to the UUID of your Samurai partition.

Ultimate Boot CD

1. Download UBCD 5 beta 12 <http://www.softpedia.com/get/System/Back-Up-and-Recovery/Ultimate-Boot-CD.shtml>
2. Create a partition for UBCD, at least 300mb, formatted as FAT16.
3. Add the following to menu.lst
title Ultimate Boot CD
root (hd0,11)
configfile /ubcd/menus/grub4dos/main.lst

*NOTE* (hd0,11) needs to be changed to reflect your UBCD partition.

Ubuntu 8.04

1. Download Ubuntu (can be any flavor you prefer, Xubuntu, Kubuntu, etc.) <http://www.ubuntu.com/getubuntu/download>
Samurai and Ubuntu both need to be installed live to the USB, they will be persistent. Create a partition that is at least 3 Gb, label it something you will remember. You can also create a separate /home partition for it now. it should be at least 1Gb, and formatted as ext3.
2. Burn the ISO you just downloaded onto a CD, boot from that CD, plug in your USB stick, and use the ubuntu installer to install it to the partition you made. If you decided you want a seperate /home partition be sure to have the installer mount the partition as /home
DO NOT LET UBUNTU INSTALL A BOOTLOADER! If you do let Samurai install GRUB, you will not only make your USB disk unbootable, but also your COMPUTER!
3. After installation, edit menu.lst on the root of your boot partition, and add the following

title Start Ubuntu 8.04 in Graphical Mode
root (hd0,12)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=75332b78-071b-4a02-9562-31895d90f52a ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic

*NOTE* make sure that "root (hd0,10)" points to the partition on your disk that contains Samurai, be sure to change the UUID to the UUID of your Samurai partition.

Boot and Nuke

1. Download Boot and Nuke <http://www.dban.org/download>
2. Put the .ISO into your boot partition, follow the folder names below.
3. Add the following to menu.lst

title Boot and Nuke
map (hd0,0)/boot/floppy/dban.IMA (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

Now you should have a "Super Multi-Boot USB" you can add more bootable images, or live OSes. Please post a reply to this post if you get anything else working on this setup, or encounter any difficulties.

---

### Post by chris4585 on 2009-03-16
There is a tutorial section on the forum.  Alternatively there's this, which IMO I think is easier but thats subjective since I haven't used your tutorial.

[http://ubuntuforums.org/showpost.php?p=6659180&postcount=5]("http://ubuntuforums.org/showpost.php?p=6659180&postcount=5")

---

### Post by EvilRobotDrew on 2009-03-17
i think that my tutorial, and the one you posted are catering to different needs. whereas the other tutorial would work very well for general recovery, i created mine with more of an eye to computer security. I got the idea for this USB when my friend who works at a fortune 500 as a computer security engineer, said one day how he would love a multi-boot usb with samurai, backtrack, and ubcd; he gave up after a couple weeks but being the stubborn SOB i am i worked on it until i got this. 

I am impressed that the other poster was able to multiboot with unetbootin, i tried using that but was never happy and couldn't get the OSes i wanted to multiboot with it. i made a decision early on to use grub, and finally had to use grub4dos to get UBCD, and FreeDOS. 

this is meant to be a template, something that others can add to or subtract from.

---

### Post by dnalexxio on 2009-04-15
doesn't work for me..
i tried to put in backtrack4 beta and dsl.. but the first gives a strange  error just like "this should never happen, try to change scsi device or something", the dsl gives kernel panic (i downloaded the embedded version as written in the tutorial)
i want to try with other distros but these are preferred ones i need to use.. any help? should i be more verbose with the errors i see?
thanx

---

### Post by rbaleksandar on 2009-10-31
Hi :)

  I'm trying this right now but I'm a little bit confused. :D Why do you make your primary partition 7GB? From what you've written, the only thing that will land in there is GRUB4DOS, which is less than 1MB. 8-[ The OSs will be placed in the other partitions so I don't see why one should take 7GB for a GRUB4DOS (again - less than 1MB). Am I right?


EDIT: Forget it. I missed the "will be read by windows as file storage"-part. :P It's all clear now. btw Instead of installing Ubuntu (and having to deal with the bootloader you've mentioned), I think it's better to make it just liveOS and not a full installed OS. Actually I'll try to use the USB Creator Tool that goes with Ubuntu by default and will use it to install on a blank USB stick. Then copy the the files (change this and that of course, to make it work). The cool thing is that the tool enables you to make you liveUbuntu save the settings you've changed (not like a live CD that wipes out everything you've configured). So the most important thing - the system settings - will be there. Don't see why not install a live version. :) One can even install apps and not loose them when shutting down the system. ;)

---

