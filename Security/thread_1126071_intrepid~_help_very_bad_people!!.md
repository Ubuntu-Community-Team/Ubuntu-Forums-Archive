---
title: "intrepid~ help very bad people!!"
date: 2009-04-15
forum: Security
---

### Post by KEE on 2009-04-15
someone is changing my harddisk permission remotely =/ I had too go into fdisk and /mbr three times this week =/ there should be more security on ubuntu. they keep changing my usb removable hard disk to fat32?!? now it wont save because perrmissions are "undetermined". how do you  undo this in terminal? so i wont have to reboot and adjusting through a mbr disk over and over again. i had it working for three days never thought it would happen this many times. please help and thank you

---

### Post by KEE on 2009-04-15
forgot to mention that i also keep geting "superblock" on drives that worked before =/ i changed it sometimes through /mbr but its very annoying stuff man =/

---

### Post by Svensk023 on 2009-04-15
well first I would unplug your internet from your computer, then just to be super thorough, re-install ubuntu, because if someone has gotten into your computer and is either manually vandalizing it or has left behind a program to do it, they have probably also left behind different "road blocks" to keep you from getting them out.
but after your fresh install make sure to download a firewall, such as firestarter, and keep all unnecessary ports closed, also check to make sure your router's firewall is up and running correctly.

if your opposed to a re-installation, then I am sure you can find the help you need otherwise, but that route may be an uphill battle.  

Also be sure to encrypt any sensitive data that you send over the internet or a network, doing otherwise is just foolish nowadays.

-Good Luck

---

### Post by The Cog on 2009-04-15
I think it's unlikely to be someone with remote access messing you around (though I can't rule it out entirely). I think it's more likely that you are having local configuration issues. But let's try to find out.

You say they are changing the external disk to fat32. What do you think it should be, and how are you changing it back again? 

How do you tell it's changed back to fat32?

Do you plug it into any other computer, or change operating systems in between times?

Why are you doing fdisk /mbr?

Lots of questions I know, but they should help understand what's going on.

---

### Post by KEE on 2009-04-16
> **The Cog said:**
> I think it's unlikely to be someone with remote access messing you around (though I can't rule it out entirely). I think it's more likely that you are having local configuration issues. But let's try to find out.

You say they are changing the external disk to fat32. What do you think it should be, and how are you changing it back again? 

How do you tell it's changed back to fat32?

Do you plug it into any other computer, or change operating systems in between times?

Why are you doing fdisk /mbr?

Lots of questions I know, but they should help understand what's going on.
i have a disk.my external usb drive used for data storage and is it meant to be in fat32? and is ubuntu making this "undetermined" so i cant use with frostwire? also it has something do with snort i think =/ I cant add anymore programs or update intrepid anymore. once changed i check to see once in a while i use ```
sudo fdisk -l
``` to see if anything changed. more about my issue with snort go here [http://ubuntuforums.org/showthread.php?p=7075320#post7075320](http://ubuntuforums.org/showthread.php?p=7075320#post7075320)

---

### Post by KEE on 2009-04-16
oh and ,**The Cog** uh if i added "superblock" in /mbr then i wouldnt be able to boot ubuntu at all so its not me =/

---

### Post by bodhi.zazen on 2009-04-16
Well my guess would also be a hardware failure.

some people have reported re-formatting the usb device may help. Also when using the device, be sure to remove it safely.

---

### Post by KEE on 2009-04-17
> **bodhi.zazen said:**
> Well my guess would also be a hardware failure.

some people have reported re-formatting the usb device may help. Also when using the device, be sure to remove it safely.
i guess thats possible but my drives are fairly new  Western digital's which is the best from what I heard =/  I believe something like a program is causing it. I remember geting a "autorun" (.)something on the drive. I never allowed it to install or whatever it was intention to do because of fear to wipe my drive. i tried opening it in text first to see what is was about but it would not show the contents.

---

### Post by cariboo on 2009-04-17
Just to be sure your hard drive is in good condition, I would suggest you go to the [Western Digital]("http:///support.wdc.com/product/download.asp?wdc_lang=en") web site and download the diagnostic tools and run them on the hard drive.

Jim

---

### Post by KEE on 2009-04-17
> **cariboo907 said:**
> Just to be sure your hard drive is in good condition, I would suggest you go to the [Western Digital]("http:///support.wdc.com/product/download.asp?wdc_lang=en") web site and download the diagnostic tools and run them on the hard drive.

Jim

thanks =) i found no disk errors ..... = program =(

---

### Post by SigmaSanti on 2009-04-17
Most western digital drives have extra software on them for backups and other free features - I have a several external WD's.
When I bought mine I reformatted it just to get ride of that software, I'm sure you don't have to do that to make it work with ubuntu, and in any case you can remove/rename the autorun file on the drive to get ride of that message.

---

