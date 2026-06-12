---
title: "how do I move windows installation file to usb back disc ?"
date: 2020-01-06
forum: Windows
---

### Post by wolftrax on 2020-01-06
I just got a new computer which has windows 10 preinstalled .  the installation media is on a file on the harddrive and is too big to burn to disc and too big to be moved to a external hardrive. 
it has windows 10 pro and a refistration key which allows me to re-install it as many times as I wish but I dont know how to get the iso file copied to a USB device for back up . 

how do I go about this ?

---

### Post by wolftrax on 2020-01-07
I think I know why.  its because the pen drives are always formatten in FAT32 which cant handle that large a file.  however it does not help me just copying the file I also need to make a bootable if I need to reinstall windows again.  which I don't know how to do either :)

---

### Post by oldfred on 2020-01-07
New Windows has  a .win file that exceeds the FAT32 size limit.

I have seen suggestions to use exFAT, but do not know if UEFI can boot from that or not as UEFI always says FAT32.

And I have seen somewhere where the boot files are still in a FAT32 partition, but install files in a NTFS partition. Do not know how Windows boot then can find another partition. Probably need Windows install tools to create that. It probably is some sort of modification of BCD as that is how it knows partitions.

---

### Post by wolftrax on 2020-01-09
I bought a 8 gigabyte USB drive and downloaded the program RUFUS which should be able to make a bootable USB pen drive to re-install windows from. 

its very hard for me to relate to using windows after so many years and I cant resist the temptation of just installing a *NIX of some sort on it. I bought it to experiment with learning how networking works.  both windows and linux , I am not good with internet stuff so learning to create my own network at home with different types of operative systems will be a educational experience and I also want to set up a printer and I am not sure if I can find a printer that works out of the box with linux,.  

so when I got the computer with windows 10 and registration key that I can re-install it as many times as I want I don't want to just delete the file because I might run into a situation where I would like to play with some software that runs windows only in the future. 

have to admit running open indiana on a live CD and it just works made me really itch to just click the installer and get on with it.  hence the question :)

edit: I just tested the USB install media and it works.  so now I can just put the USB pen aside and re-install if need be.  the registration key is on a sticker on the computer so I can install it again if need be.  
I dont really like windows but might as well just keep the option open.

---

### Post by C.S.Cameron on 2020-01-09
Rufus has a **Windows to Go** option that allows installing Windows 10 on an external drive, if you do not want it on your internal drive.
The speed of WTG largely depends on the type of external drive used.
It can take over a day to install.

---

### Post by wolftrax on 2020-01-10
interesting. I noticed the installation is about 30 gigabytes and that is a lot space to use for a single OS to install.  I could buy a external 500 gigabyte storage and install it on that and then just use the internal hardrive for my *NIX which I prefer.

---

