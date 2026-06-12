---
title: "Can't Boot Windows from Pendrive FAT32"
date: 2015-09-18
forum: Windows
---

### Post by nick220 on 2015-09-18
Hi. 

I've got a virus, now my computer is screwed. I launched ubuntu from live usb, formatted everything with cfdisk now i have an empty patrition sda1 and i can't create ntfs filesystem. I used mkntfs but in the end it says it's Linux Filesystem. I have a recovery image for my surface pro, and an ms-dos filesystem, but i cant boot to it, only the live-linux. Altouhgh when i'm in Ubuntu it cant read the win pendrives..

I'm really tired.. Been trying over 3 days and cant make it work.

---

### Post by Bucky Ball on 2015-09-18
Welcome. You don't need to create any partitions if you are installing Windows and removing Ubuntu. Boot from the Ubuntu live USB, launch Gparted, delete the partitions on the drive. You may need to write the partition table after that, I'm not sure. You can do that in Gparted also.

When you install Windows partition the free space however you like. It is best to create the Win partition with Win software during the install rather than with Gparted. Just make free space with that and do the rest with Windows.

Keep in mind that if you want help with Win issues when installing this is not the best place to post. We do have a Windows area of the support forum, but there are much more active ones about. :)

Good luck.

---

### Post by nick220 on 2015-09-18
I tried it booting with MS-DOS and the recovery windows image, now i'm creating a win 10 usb, to see if it works. None did so far.

//Also it says in gparted : "The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes."

---

### Post by Bucky Ball on 2015-09-18
*Thread moved to **Windows**.*

Did you follow the advice in my last post? Windows will not read/write or really recognise EXT filesystem partitions as anything but 'healthy'. Get rid of it.

---

### Post by nick220 on 2015-09-18
I'm on it right now, but even gparted says free spcace, along with it there is a warning: [COLOR=#000000]The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes[/COLOR]

---

### Post by Bucky Ball on 2015-09-18
How did you create the bootable Windows USB and is it a licensed copy? Which version of Windows?

---

### Post by nick220 on 2015-09-18
I'm creating it with the [MediaCreationToolx64.exe]("file:///C:/Users/Nick/Downloads/MediaCreationToolx64.exe") form microsoft's website. I had this version updated from Win8.1 on my Surface pro. I have no image from win 8 only an official recovery image for the surface pro, but it is not booting .

---

### Post by nick220 on 2015-09-18
My God It's working. The Win 10 installer just booted. Did the same thing that i did before writing a topic and creating a partition. Dont know what have changed. Thank you for your help, I will mark this solved, as soon it's working properly.

---

