---
title: "Just started in Ubuntu"
date: 2015-09-16
forum: Ubuntu, Linux and OS Chat
---

### Post by kc110 on 2015-09-16
Having been frustrated by Windows for a long time, the Windows 10 scenario finally prompted me to switch.

Just successfully dual booted Ubuntu (Windows 7) on my HP laptop. This was a bit of a hassle partly due to having 4 primary partitions on the laptop. 

Anyway, now that I have started, the next step is to install Ubuntu on the main desktop PC. (Dual boot also as I want to use FSX, and not yet sure how effective "Wine" will be).

Then home network set up. I am determined never to install or buy another Windows PC. Windows update has been switched off on both my machines.

Cheers

Kevin

---

### Post by Bucky Ball on 2015-09-16
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Moved here as the area you posted in is a support area and you seem to be doing just fine for the moment! :)

Just a tip with the four partition limitation. This leads me to believe you are using legacy mode to install rather than EFI. That is fine, but yes, you are limited to four partitions, primary or otherwise. The way around this is to use an extended partition instead of one of the primary partitions inside which you can put as many logical drives (or virtual partitions) as you like. Think of the extended partition as a container for other partitions. Four partition limit problem solved. 

For instance, you can have three primary partitions and one extended partition inside which you could, in theory, install Ubuntu on three virtual partitions. In essence and for all intents and purposes, you have seven partitions (three primary, one extended, three virtual inside the extended). Hope that makes sense.

Thought this might help for your next install. If you hit any brick walls with that, post a new thread in the most suitable support area (***Installation and Upgrades*** might be the go). 

All the best and good luck with it.

PS: One other tip: If you need to resize the Windows partition, boot to Windows and use Win software to do so. DON'T use Gparted or any other Linux software to do it. This can screw the Win boot. For Linux resizing, use Linux software. ;)

---

### Post by kc110 on 2015-09-16
Thanks for that.

I read lots of different pages and tutorials, all of which added to my knowledge and helped the process.

I deleted the "HP Tools" partition after creating a repair disc and that allowed the new partition.

I'll bear in mind your comments for the next install, but am hoping for an easier ride as the main PC is my own build and has "space" for more partitions.

Thanks again

kc

---

### Post by Bucky Ball on 2015-09-16
Good luck again. Further note: If you are using EFI mode for install rather than legacy (newer motherboards/BIOS) there is no partition limitation. You can have (theoretically) as many as you like. If Windows is installed in EFI (which it generally is on 'off-the-shelf' computers) then Ubuntu should be installed in UEFI also. 

As you created this desktop beast, you possibly used legacy, though. Four partitions (primary OR extended). If it is legacy, doesn't matter how much free space you have on the disk, you can still only have four partitions. 

Boot to Windows, shrink the Windows install to what it needs (probably about 30-40Gb), create an extended partition with the rest and put everything else (including the Ubuntu install) inside that is one of the many options. Make a mud-map of a plan of attack always a good idea. 

Win won't read/write native Linux EXT partitions so good idea to make an NTFS partition, large, for personal data if you are going to share it between Windows and Ubuntu. 

Hope that helps along a bit more. :)

(Final note: Windows can only be installed on a primary partition. Ubuntu doesn't care. Primary or logical inside an extended.)

---

### Post by Sweet_Baby_Jamie on 2015-09-16
Another new user, yaaaay!  ):P  Welcome! 

You'll love it.  I'm using an Ubuntu "flavor" derivative that keeps my 13-year-old hand-me-old computer running faster than it did when it was new running Windows XP! (according to my parents, anyway - I was a baby when they got this computer) and I do all my school stuff and social, music lessons, and everything on it.  Trouble free and simple.

No more Windows for me either!

---

### Post by Mike_Walsh on 2015-09-17
Welcome to the Forums. :)

> **Bucky Ball said:**
> Win won't read/write native Linux EXT partitions so good idea to make an NTFS partition, large, for personal data if you are going to share it between Windows and Ubuntu. 

In actual fact, there **is** a way to do it. Look here:-

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

The ext2fs Project has developed a way for Windows (up to Win 8, at any rate.....I don't know about 8.1 or 10) to access Linux ext2/3/4 partitions.

I know somebody who has done this; it appears to work very efficiently. You apparently need to remount each drive (or partition) that you wish to access, write the config changes to the hard drive, and after that, the Linux partition access is auto-started at boot. (Haven't tried it myself, as I no longer have any form of Windows in the house...)

Just a little bit more info for you!

Bucky's right, though; if you make an NTFS partition for stuff you want to access from both machines, it avoids the need for this to some extent, as almost all Linux distros I've come across have ntfs-utils installed from the word go.


Regards,

Mike. ;)

---

### Post by kc110 on 2015-09-18
Hi,

Thanks to all for the welcome and advice.

At the moment I am trawling the forums for help on partitioning. "!" ntfsprogs ntfs-3g. Despite having run chkdsk twice it is still not fixed.

Thanks

---

### Post by Bucky Ball on 2015-09-18
You're best to post a new thread in a support area and sure we can help. This is not a support area. Good luck. :)

(Have a quick check of the third link in my signature prior to posting and that should help you get a speedy resolution.)

---

