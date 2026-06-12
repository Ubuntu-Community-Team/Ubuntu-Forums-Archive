---
title: "Media Direct - Linux Equivalent"
date: 2006-05-25
forum: The Cafe
---

### Post by blakegrover on 2006-05-25
I have noticed that HP, Dell and other computer manufacturers are inculding a seperate partition on the hard drive for a "mediadirect" program.  Where the computer takes 2-3 seconds to boot into a gui screen where they can browse their ntfs/fat32 drivers for media and play dvds.  

Does anyone know of a linux equivalent.  I would like to boot a kernel/linux distrubution to do this.  Any help would be appreciated.

Thanks
Blake

---

### Post by colo on 2006-05-25
Afaik, those Solutions are actually based on GNU/Linux most of the time. Medion, Gericom or Targa (at least one of the three) made it into the headlines of computer-realted publications in Germany because of violating the GPL by doing so, but not including any notices about the software's license, if I recall correctly.

I don't know a pre-packaged distro for that purpose, though.

---

### Post by ThirdWorld on 2006-05-25
[QUOTE=colo]Afaik, those Solutions are actually based on GNU/Linux most of the time. Medion, Gericom or Targa (at least one of the three) made it into the headlines of computer-realted publications in Germany because of violating the GPL by doing so, but not including any notices about the software's license, if I recall correctly.

I don't know a pre-packaged distro for that purpose, though.[/QUOTE]


This is so ilogic. Those programs are based on Linux, but linux itself doesnt have them? so what about the GPL? some guy the other day said that stuff like this will never happend, im afraid  he was wrong.

---

### Post by mostwanted on 2006-05-25
[QUOTE=ThirdWorld]This is so ilogic. Those programs are based on Linux, but linux itself doesnt have them? so what about the GPL? some guy the other day said that stuff like this will never happend, im afraid  he was wrong.[/QUOTE]

It's possible to make proprietary programs for Linux you know. You don't have to GPL everything just because it's for Linux.

---

### Post by blakegrover on 2006-05-25
Is there any howtos out there to add another boot option in grub so it could do something similar?

---

### Post by blakegrover on 2006-05-26
Ok, now I would like to know is there a way I could write a bash script to check what actual kernel file I am booting from?  I know I can use uname -r to grab the kernel version but is there a command I could tell what the the name of the kernel file?  I am thinking of trying to build a mini music player in an xwindows enviroment.  I plan to build my own kernel but have the majority of the drivers turned off.  I just want my hard driver and dvd player working and my soundcard.  The rest like network and etc are not needed.  I would then write a bash script to be ran every time the computer boots up and then check to see if I booted into the special kernel or not.  I am a little worried about using the uname to detect just the version number of the kernel but maybe if I do a custom kernel it would be sufficiently different to seperate it from the same kernel # on ubuntu.  Then this program would start just the minimal programs also and minimal startup programs/services and then have some sort of a xwindows manager.  It might be easiest also just to create another partition about 50MB like dell and HP do and just have a seperate partition with all those changes.

I also did some playing around with a friend's laptop he just got and I noticed the first time you boot into it it takes a couple of minutes and then when you turn it off it does the same screen for hibernating in windows.  Then every time you go in it takes the 2-3 seconds.   So maybe just by installing a small linux distro or minimal ubuntu you could resume from hibernating each time.

The bad news about hibernating is you need to store all the memory to the hard drive.  Even though the partition I would need could be 50mb I have 1 GB of ram so I would need to have 1GB of hard drive space to hibernate each time for it.

If anyone wants to help contribute I really would like to dedicate my little free time I have to start working on this project.  Any help would be appreciated.  I just think if it can be done for windows we should be able to have something similar.

By the way I know there might be some who think that the media direct features or whatever they are called on the laptops aren't that great and I shouldn't devote to much time but it would be nice to have it bootup in under 3-10 seconds and turn off in the same amount.

---

