---
title: "Ubuntu failed me"
date: 2007-10-03
forum: Testimonials &amp; Experiences
---

### Post by Richard Hunt on 2007-10-03
Having read that Ububtu was a Linux version that had 'come of age' to the extent that Dell now offer it as a pre-load, I thought I would try it out.

I regret to announce that Ubuntu, while looking good, and apparently full of capability to provide access to many applications, failed in its first task to gain me access to the internet, and in so doing messed up my primary hard disk in spectacular manner.

I run an AMD64 Atlon 3500+ machine with Windows XP and many applications and much data on 2 x 200GB fixed disks.  I needed therefore a dual boot environment.  This I managed to set up.  However Ubuntu refused to connect to my USR 5462 wireless router with the USR 5422 wireless adapter I had. After USR told me it was incompatible with all flavours of Linux eventually I managed to find a Ralink USB adapter that claimed to work with Ubuntu. This was with the help of this forum.

Well, the first step was to make it work under Windows.  The manufacturer's CD turned out to be useless and nothing worked.  I managed to get it working by downloading the latest XP driver from the Ralink website.  Strangely, I had also to enter the device's MAC code to my router (which is configured to filer access by MAC code).

While I am new to Linux, I have some experience with PCs including many installs of OS/2 in the late 80s.  The instructions that came with the device from the vendor on how to install the Linux drivers were complex, and I think, not particularly user friendly.  I managed, I thought, to effect installation after several attempts, and proceeded to re-boot.

Ubuntu then failed to start, and appeared to stop when it reached the point of starting the network.  I assumed that the driver installation had corrupted the system, so ran a new install.

That worked, but on booting into Windows, received a "Disk read error" return.  This is a serious Windows error requiring re-partitioning of the disk, reformatting and re-installation to correct.

The pocess of doing this took several attempts as Windows refused to recognise the partitions on the disk. I used the Gnome partition editor on the Live Ubuntu CD to delete the disk partitions, and lastly I resorted to using a Windows 98 boot floppy and FDISK to repeat the deletions before the Windows XP system CD would recognise what was there.  I then performed a full format and restore by file which ran overnight.

My conclusions from this are that:

1. Ubuntu is not sufficiently developed to recognise devices in the same Plug ‘n Play manner as Windows and from a simple user perspective is therefore deficient. 
2. I shall not repeat this experiment for some time as a 2 day recovery is not huge fun. 

While I may have made mistakes through lack of knowledge of Linux, the impact on my PC has been too drastic and fundamental for me to risk any form of migration away from Windows until I can see that Linux has matured even more.  

With regrets, goodbye for now.

---

### Post by conehead77 on 2007-10-03
> **Richard Hunt said:**
> 
1. Ubuntu is not sufficiently developed to recognise devices in the same Plug ‘n Play manner as Windows and from a simple user perspective is therefore deficient. 
When it comes to wireless, you may be right. Theres still research about the hardware to do before installing Ubuntu. But most of the other devices are easy to use. I installed Ubuntu on 2 Desktops and 1 Laptop and everything just worked out of the box (no wireless though).
> **Richard Hunt said:**
> 
2. I shall not repeat this experiment for some time as a 2 day recovery is not huge fun. 
Did you run the live-CD first? If you run into troubles with it, you may try another Distribution of Linux.
The harddrive errors you got seem strange to me. Wish i could help, but i dont have any experience with this kind of stuff.

Good luck with your OS in future, maybe you will try Ubuntu again somewhen (be sure to browse the forums and look if your wireless card works then).
Btw did you use 7.04 or 7.10 beta?

---

### Post by K.Mandla on 2007-10-03
Thanks for the comments. I think your post was well-intentioned, but I have to counter a couple of issues in your conclusions.

> **Richard Hunt said:**
> 1. Ubuntu is not sufficiently developed to recognise devices in the same Plug &#8216;n Play manner as Windows and from a simple user perspective is therefore deficient. 
"Deficient" is a bit harsh. Deficient implies ingrained failure, and considering that there are literally millions more people who are successful with Linux -- some possibly with identical hardware to what you use -- that cannot be the case. I think this time you have made an error by generalizing your own experience and using it to lambast the entire project, without taking into account that for many, many more people, it is working. 

> **Richard Hunt said:**
> 2. I shall not repeat this experiment for some time as a 2 day recovery is not huge fun. 
Fair enough, but don't wait so long that the effort you expended cannot be built upon, making the entire adventure a learning experience, instead of a failure. Remember that in most cases, adults learn through repetition and correction, and for most of us, many, many attempts were necessary before learning how Linux works. 

> **Richard Hunt said:**
> While I may have made mistakes through lack of knowledge of Linux, the impact on my PC has been too drastic and fundamental for me to risk any form of migration away from Windows until I can see that Linux has matured even more.  
Again, since this is a learning experience, it might be that you need to mature more (which is not to imply that you are immature; I'm just using the same term you used). Give it a month or two, reflect upon your experience, and then try again. Many, many people from different and even less technophilic backgrounds have found success with Linux and more are added every day. 

Cheers and good luck. :)

---

### Post by Richard Hunt on 2007-10-03
Thank you all for your messages.  I accept your well meaning criticisms of my post, but if Ubuntu had found and automatically installed my original wireles adapter the first time I would not have dug holes for myself!  In that respect, I would still say it is lacking.

I think you are right though. I may well try again in a few months.  The OS I saw has, as one landscape gardener put it, "capability".

Au revoir, perhaps rather than goodbye...[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by |Eric| on 2007-10-03
i have to comment becose i totaly disagree with your conclusion exept the point where you **may** lack technical expertise to yourself to do the kind of setup you tried here is why & what i propose to you :

on the first note i have to say that multi-boot systems with diffrent OS especialy in the combination of Linux/windows & the reason for that is that WINDOWS does not recognise the bootloader of linux & refuse to implement any kind of facility to be able to load both system that said you should know it is possible to install linux & windows & use lilo as a loader for linux:
 just copy the loader into a file (installing in partition boot record instead of the MBR & then use dd utility to copy it to a file) also seams to work with grub. 

also as far as drivers go in windows its the manufacturer who programs the drivers why would it be the fault of linux if a driver isnt available for your hardware ? 

For wireless hardware  linux seams to be boycoted by wireless chipset companys ie: broadcom & such.Im pretty shure if your windows did not come with its drivers it would be a pain in the a** as much to find a devloper who whants to program for it freely.

so its not all linux's fault ... you have to understand that its not all companys that are friendly to this OS versus windows which is widely accepted for its "simplicity" (wich isnt the case realy if you compare apples with apples) 

personal note: ubuntu recongnised my wireless card even if it wasent supported (a broadcom) so as far as windows who cant tell who from who i think its way better in linux

---

### Post by LaRoza on 2007-10-03
Installing a new OS can be daunting, but try not to blame the OS or yourself. If somewhere were to set it up for you, and get everything working, I doubt you would have the same opinion. Also, if you had to set up Windows instead of buying it pre-installed, you would have (most likely) more complaints than you had about Linux (Ubuntu). 

You might want to try another distro, like Pardus, or Gutsy.

---

