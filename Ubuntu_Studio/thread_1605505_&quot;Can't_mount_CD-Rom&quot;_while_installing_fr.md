---
title: "&quot;Can't mount CD-Rom&quot; while installing from USB."
date: 2010-10-25
forum: Ubuntu Studio
---

### Post by Linux_FTW on 2010-10-25
There isn't much to this story, my DVD drive is not working so my only option right now is using the USB.

I used the Universal USB Installer and used the option "unlisted distribution" 

is there anyway to fix this, or should i just install ubuntu and upgrade it?

---

### Post by mikeh789 on 2010-10-25
you could try [https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller](https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller)

but, i would probably just do the standard install and add whatever studio packages i want to that install

---

### Post by Tweedle on 2010-12-11
i think i read somewhere that the usb's mount point was /cdrom after someone installed to a usb with the ubuntu usb installer thing from in windows. so that would mean that the usb was format to an ext type file system and not a fat system. so maybe if it is formated to an ext3 and the mountpoint for it was set to /cdrom ,  then the installer would automaticly think that the usb is really the cdrom.

ive been trying for over a month to get this to work because i dont have any blank dvd's left and i don't want to upgrade. well, until about 15 minutes ago i didnt want to upgrade. so i installed ubuntu 8.04 64-bit and im currently waiting for the upgrade to work (i used the command you listed here) but the server is sooooo slow, it's runiing at about 150kb/s and it's gonna take a while. but in the mean time i'm going to reformat the usb stick to ext3 and set it to /cdrom (if i can find a way to do this in ubuntu) and then copy the files from the iso after i mount it. then im going to change isolinux to syslinux and blah blah blah. hopefully it will work, it should in theory, but u know how they pan out in linux...

lol, i probably wont even need to do this after the upgrade finishes, i dont know why i didn't want to do it this way in the first place. maybe i could find a way to write a script to fix this (if it really works) and i'll post it.

i'll let you know how it all turns out, if i find a way to format and set the mountpoint, but i know that this can be done in the ubuntu installer when you boot to the cd (in the partition settings) 

good luck ;)

---

