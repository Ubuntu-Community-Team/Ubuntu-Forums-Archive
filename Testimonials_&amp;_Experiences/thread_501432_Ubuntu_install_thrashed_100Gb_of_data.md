---
title: "Ubuntu install thrashed 100Gb of data"
date: 2007-07-15
forum: Testimonials &amp; Experiences
---

### Post by DeltaZero on 2007-07-15
I suspected you can't correctly resize NTFS partition this fast!

[http://ubuntuforums.org/showthread.php?t=501359](http://ubuntuforums.org/showthread.php?t=501359)

If your installer can't resize NTFS disks correctly, why doesn't it say so? Now I have to re-install the system completely.
I surely won't be trusting open sauce with such critical tasks in the future!

---

### Post by Gausian on 2007-07-15
Its not open sources fault that you didnt back things up before doing system changes, is it?

---

### Post by wolfen69 on 2007-07-15
blame yourself,not the software.

---

### Post by Ralob on 2007-07-15
All software, be it commercial or open source, has imperfections. That being said ANYTIME you make drastic changes to your system (like installing a new OS, partitioning, restoring, etc) you need to backup to a safe location. Live and learn, eh?

---

### Post by Wim Sturkenboom on 2007-07-15
It's not our installer. It's the installer that we use. And I have resized NTFS partitions without problems (can't remember which tool (gparted?)).

Sorry for the loss (RIP)

---

### Post by tmonte on 2007-07-15
Sorry to hear that, but my install worked without problems on the resize, and dual booting into Vista with GRUB works great too.   I haven't heard this too much, but maybe yours was a case of bad luck...and as others have said, critical data needs backups.  Still doesn't account for rebuild time though... :(


Tom

---

### Post by Paul820 on 2007-07-15
If you make ANY modifications to your hard disk you should always back-up, it's just common sense. Blaming Ubuntu for your lack of it is not going to cut it with anyone on these forums. Sorry!

---

### Post by Old Pink on 2007-07-15
Unlucky, but without a backup you were kind of asking for it, I guess. :) 

Instead of looking on this as a negative outcome, why not look on it as a positive and reformat to a 100% Ubuntu install? That's what I did when I lost 30Gb+ of Windows installation and personal files to partitioning without a backup. :D

---

### Post by zero244 on 2007-07-15
I agree nothing is for sure.
Before I installed Ubuntu I tried to create a ext3 partition using Paragon 6.5 Disk Manager...........I paid  165 dollars for this software.
I was running it in XP and have used the software several times without problem. Well this time it failed to create the ext3 partitions correctly and messed up my XP partition to the point I had to restore it.
After I had everything restored when I booted up two partitions were missing which werent involved in the creation process.
Fortunately I was able to undelete the two missing partitions manually.
So trying to create two partitions at the end of my harddrive almost ruined all my data.
This is from a company like Paragon who has been in business for a couple of decades.
I upgraded to the latest version and that bug was apparently fixed.
So you really never know for sure and should always be backed up before doing something risky.

Sorry you had the problem.

---

### Post by xzero1 on 2007-07-16
Try the linux system rescue disk, you may be able to find the original partitions.  It could be only your partition table is corrupted -- the data could still be there.
[http://www.sysresccd.org/Download]("http://www.sysresccd.org/Download")

---

### Post by 3rdalbum on 2007-07-17
Partitioning was designed back in the 1970s, with the intention that partitions would not be resized.

Fat32 and NTFS were designed with the intention that the partitions they would describe would never be resized.

It's a miracle that resizing works most of the time. But still, it's common sense and mentioned in all dual-boot howtos, that you back up all your data before messing around with the partition table. As for your assertion that "you'll never trust open sauce software with critical tasks again", I can point to many examples of people losing their data when trying to mess with their disks using proprietry software.

I've lost data with proprietry software, and with open-source software. It's the nature of the beast. Get over it, and next time remember to back up before doing anything low-level with your data.

---

### Post by weblordpepe on 2007-07-18
OK everyone its time to sing the gparted liveCD song!

Gparted live CD rules
...gee parted live see dee ruuules!!!
....ddanannananaaaa......
[URL="http://gparted.sourceforge.net/livecd.php"]
http://gparted.sourceforge.net/livecd.php[/URL]

---

### Post by marsmissionaries on 2007-07-18
open...sauce?

---

### Post by weblordpepe on 2007-07-18
Open Sauce witih a capital S

---

### Post by jonathonblake on 2007-07-21
Whenever changes to either the system configuration, or hard drive are being made you have to do two things:

* Backup your data;
* Verify on another system that your data backup was successful;

Ideally, your system is configured to do an automatic backup either daily, or weekly. 

xan

jonathon

---

### Post by Wiebelhaus on 2007-07-21
Anyone who has been around computers for awhile knows that ANY KIND of partition manipulation is highly dangerous and all elementary precautions should be taken...

---

### Post by bodycoach2 on 2007-07-21
Other than immediate use files, I didn't realize anyone stored data on the same hard drive as the OS anymore. That's just so 1990's. 

The partitioning has worked perfectly on every dual boot installation I've done. The mistake usually is made in not defragging before installing Ubuntu.

In the future, I recommend keeping your stored files on a completely different disk than the OS, no matter what OS you use (Windows, OSX, Linux). With any OS, something goes wrong, or an update goes beserk, or little two year old Timmy just happens to bang the right sequence of keys, deleting everything, and completely erasing the internet too.

> **DeltaZero said:**
> I suspected you can't correctly resize NTFS partition this fast!

[http://ubuntuforums.org/showthread.php?t=501359](http://ubuntuforums.org/showthread.php?t=501359)

If your installer can't resize NTFS disks correctly, why doesn't it say so? Now I have to re-install the system completely.
I surely won't be trusting open sauce with such critical tasks in the future!

---

### Post by weblordpepe on 2007-07-22
Erase the internet?? Oh noes.
U hav scared me enough. I mus download windows defendor and savee the inmnternet.

Actually though. You may be right. But I have always been a big fan of having a single volume. I hate having to manage multiple amounts of free space.

One solution that I found though was to just have all my documents/movies etc - over the network. To releve the burden of having a huge hard drive and upgrading it in the same box as my gaming-inspired upgrades. Or just general sillybuggers with the operating system.

And if you're over the internet you can use SSHfs. Or Orb if it worked in Linux :(

My main machine has XP on it. Its a desktop. And I dont use it much. But it has a huge hard disk so it stores all my videos & documents. My laptop with linux on it is just rigged to get the files etc from my desktop computer over Samba or SSHfs if Im not at home.

---

