---
title: "Dual Boot: Windows XP &amp; Ubuntu (Studio)"
date: 2011-04-20
forum: Ubuntu Studio
---

### Post by SullaQ on 2011-04-20
Hello Everyone,

As a complete newbie to Linux I would like to ask a few questions before proceeding with the installation.

I've used Ubuntu, OpenSuse and Mint in the past with mixed results but recently installed Ubuntu again on a spare machine and really enjoyed it so I am getting ready to make the jump on my main machine and I need to be certain it will work since this computer cannot fail or fail to boot in Windows xp as my work depends on it.

Here is what I would like to know:

During Ubuntu installation I have the option to install it side by side with Windows however I have already partitioned my drive and decided the amount I want to allocate to each OS. The slider option in Ubuntu installation will not work (I think) because my HD is divided as follow.

150GB Windows Xp

150GB (other OS) Ubuntu Studio preferably.

700GB Free space for media files.

In order to maintain this configuration what option should I choose? 

Also note that this partitions were created in Windows so they are all NTFS. I am sure the installer will convert the right one to a Linux partition no problem. 

So, if I do not select the side by side option with the slider, will my boot grub (loader menu) still have both OS on it for me to choose from?

Please note this, my knowledge of the terminal is almost nonexistent and I don't know my way around it at all but I've got to grow a pair and make the move, Microsoft and Apple are just too unethical to have me as an accomplice.

Any help would be greatly appreciated.

Thank you in advance.

---

### Post by oldfred on 2011-04-20
Welcome to the forums.

I do not know what differences Sudio has.

You really want to use manual install. The NTFS partitions are confusing the auto installer.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

You want to convert your install partition(s) to an extended partition and have your install in logical partitions inside the extended. You can put your data in a logical also but cannot easily convert a primary partition to a logical.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Shared NTFS partition - You can also use links
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by trulan on 2011-04-20
I would choose the "Set up partitions manually" option, the only catch there is that you will need to be able to tell the difference between your XP partition and your desired Ubuntu partition.  I usually boot up with a live Ubuntu Desktop cd (not Studio, so I can have the desktop environment) and browse around with GParted (menu/sytem/administration) to figure out which partition number is which. (sda1, sda5, sda6, etc.)  It's a good idea to write down those numbers so you're sure you get it right.

You'll also want a swap partition for Ubuntu (2 to 4Gb probably).  That will make four partitions, the maximum you can have, so it would make sense to set up your Ubuntu partition as an extended partition with two logical partitions:  a big ext3 or ext4 partition for your system and a small linux-swap partition.  Personally, I just find it easiest to set up the partitions first from the live CD, then during the installation all I need to do is point the installer to the correct root partition (mount point '/') and swap partition.

Of course it's a good idea to do a good round of backups before partitioning or installing, because if you accidentally tell Ubuntu to install itself to your XP partition, well, you know...

Good luck!

---

### Post by Learning Linux 2011 on 2011-04-20
Do you actually have data on all the partitions?

If you just have data (Windows) on the Windows partition and nothing else, you could simply delete the 150 gig partition allocated for Linux and the 700 Gig partition, then let Linux create the 150GB partition and leave the 700 GB free for now.  Then later you can create the 700 GB partition after Linux and Windows are set up and running the way you want.

---

### Post by SullaQ on 2011-04-20
Thank you guys.

The only partition that has data is the 150GB partition with Windows Xp on it. The others are empty ...I've only created them in "preparation" for the new Ubuntu install. 

I've used GParted in the past and am fairly familiar with it.

I'm still a bit confused. 

My idea was to use the second 150gb partition to install Linux, Linux swap and whatever is necessary to make it run like a charm :-) but now I am learning from trulan that I can have a maximum of four partitions on an HD so I can have Windows, Ubuntu, Linux swap and a data/media partition. Would this work?

Despite knowing Ubuntu only need 10GB to work fine I want it to have 100GB on the OS partition because as I start working with media (i.e. non-linear video editing) even though I keep the source material on separate HDs sometime in Windows the user folders get pretty fat with data.

I am going to look at the articles oldfred suggested and educate myself a little more.

As far as distinguishing the partitions when I install, my trick was to make the Windows one 150gb and the Linux one 145GB (which is what I did). A silly trick but I could never take the risk of erasing Windows by mistake right now.

My machine has 6gb of memory so I intend to have a Linux swap partition ...which according from what I have just learned from you guys should also be 6gb in size. Is that correct?

To make things less complicated I could install regular Ubuntu and then upgrade to studio inside the OS. But now if I were to chose the side by side install Ubuntu would install next to Windows on the 150GB, is that correct? (I don't want that, even though Windows and my docs on it are only taking up half of that partition, one never knows)

Due to my lack of knowledge on the subject I think I may be making things sound more complicated than they are but if I'm going to take control of my computer once and for all I want it to do exactly what I want :-)

Thanks again guys for helping me sort this out.

---

### Post by oldfred on 2011-04-20
Side by side is dangerous in 10.10, I think it is ok in other versions.

Only if you plan on hibernating do you need swap of 6GB. Some with that much memory do not have swap as it is almost never used. You have to have many large applications or editing video to use that much memory. Having some swap others still recommend for slightly faster boot or just in case, so it does not just crash on the rare chance you use all 6GB.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

The 4 partition limit is primary partitions, but one primary can be converted to an extended partition that can hold many logical partitions. Windows will not boot from a logical but will read NTFS partitions in a logical and all of Ubuntu works just fine in logical partitions. So most use one or two primaries for windows, one for the extended and keep one primary available for future.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
Above does have an error - you cannot share /home with windows and should not share with another install.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by trulan on 2011-04-20
Sorry, I should have been more clear.  Put all your linux-related partitions (root, swap, and any more you may decide you want) in logical partitions inside one extended partition, that way you can avoid running up against the four primary partition limit.  The two NTFS partitions can stay as they are, primary partitions.

Actually the 150Gb/145Gb trick was a very good idea, not silly at all.  Smart thinking!

---

### Post by sgx on 2011-04-21
Don't install linux on the hard-disk of your work computer. Buy a usb/firewire hardisk, or enclosure to use a disk you now own. That being said, you should have a current system backup image, AND full data backed up, with daily backup on every entry of significance.

The price of a hard-disk is trivial. Old P4 systems are cheap.
Preserve your business against needless risk.
Cheers

---

### Post by Sylos on 2011-04-21
> **oldfred said:**
> 
Above does have an error - you cannot share /home with windows and should not share with another install.


Hello oldfred - Just happened upon this thread and wondered if you could elaborate on why you shouldnt share a /home partition between Ubuntu installs. I ask because I currently do share a partition of my disk between my standard Ubuntu and my ubuntu studio installs. Its not the /home its a separate one. Are configs or other such details stored in /home?

Cheers (sorry for jacking the thread a little).

---

### Post by oldfred on 2011-04-21
If your versions of Ubuntu are identical, it may work. The use of separate /home is for clean installs on upgrading and separating system from data which has other advantages.

Even different versions of Ubuntu are running differnet versions of software and have some settings that are different. Most software is designed to upgrade from old settings but older version may find a new setting and not know what to do with it.

I find the actual /home settings in Ubuntu are very small. My /home is 1GB and three quarters of that is .wine which I have not yet moved to my /data partition. I promote /data partitions, but it is more advanced so I try not to over promote /data for new users. But if dual booting with Debian based systems /data works very well. Even a data parttion can have issues with other distributions as UID & GID may not start at 1000.

I move all data folders into /data and mount it at /mnt/data. Change owership and permissions and link every folder back into /home so my system looks & acts like a standard /home.

I have posted details several times, but have changed a few things. My most recent post with some details. I actually use a bash script for the details so each install is easy to set up.
[http://ubuntuforums.org/showthread.php?t=1734233](http://ubuntuforums.org/showthread.php?t=1734233)

---

### Post by SullaQ on 2011-04-21
@trulan: I think I understand now. You are suggesting to turn the partition I had destined for Linux into a logical partition and then put all of Linux related partitions in there. How do I turn a primary partition into a logical partition? (Is GParted the solution?) I don't even know what a logical partition is so I've got some reading to do :-)

@sgx, I was getting ready to write that I want both OS on the same hard drive and don't see why I should not be able to make that happen since that is what I want but your answer actually thought me one important thing I did not know and that is that you can install Ubuntu on an external hard drive of which I already have several hooked up. But how would my computer be able to give me the boot menu so that I can choose between each OS each team I boot? If this involves any unplugging it won't work for me ...also if it involves use of the terminal I'll be at a loss unless someone guides me step by step. Can you elaborate on your suggestion?

@oldfred, thank you for the link I'll look into it.

---

### Post by trulan on 2011-04-21
Yes, that's what I was trying to say.  Use GParted, I think the easiest way would be to delete your (currently empty) Linux partition and create an extended partition in the empty space.  Then you can create your linux-swap partition and your ext4 system partition as logical partitions inside that.  Write down those partition numbers (probably sda6 and sda7) and then you can pick them manually when installing.

You can also install Ubuntu on an external drive as was suggested.  The easiest way to do that is to set the BIOS to boot first from USB (assuming you're using a USB external drive and your computer supports booting from USB).  Then, do the Ubuntu install to the USB drive.  Whenever you reboot and your Ubuntu system USB drive is plugged in, you'll be able to choose between booting into Ubuntu or into Windows.  If the USB drive is not plugged in, it will just boot into Windows.

You could also install Ubuntu on an external drive (even if you can't set the BIOS to boot from the external drive) and install grub to the MBR of your Windows drive; but then you wouldn't be able to boot into Windows unless your external drive was hooked up, as the actual menu would be on the external drive.  So that would be a bad idea IMO.  There may be a way to install grub or another bootloader menu directly in Windows to avoid this problem, I don't know if that's possible or not.

---

### Post by sgx on 2011-04-21
> **SullaQ said:**
> @trulan: I think I understand now. You are suggesting to turn the partition I had destined for Linux into a logical partition and then put all of Linux related partitions in there. How do I turn a primary partition into a logical partition? (Is GParted the solution?) I don't even know what a logical partition is so I've got some reading to do :-)

@sgx, I was getting ready to write that I want both OS on the same hard drive and don't see why I should not be able to make that happen since that is what I want but your answer actually thought me one important thing I did not know and that is that you can install Ubuntu on an external hard drive of which I already have several hooked up. But how would my computer be able to give me the boot menu so that I can choose between each OS each team I boot? If this involves any unplugging it won't work for me ...also if it involves use of the terminal I'll be at a loss unless someone guides me step by step. Can you elaborate on your suggestion?

@oldfred, thank you for the link I'll look into it.
Hi, Your computer will have an 'early boot' option, one of the F keys,
Tap it as your computer starts, when you want to boot from other devices. The bios offers boot priority, grub can be utilized to list external drives, but the early boot option minimizes problems, while not effecting usage of storage media. You can choose usbsticks, dvd/cd, external drives, whatever is on you system when turned on.

I would use another spare or cheap pc to experiment on, and get
acquainted with partition managers, and achieving your ultimate goals.
Cheers

---

### Post by SullaQ on 2011-04-23
Thank you guys. I'll have to do some experimenting but I think I got the gist of it.

I won't deny I am scared to adventure down this path but now that  Lighworks Beta has planed a Linux release there is no excuse for me to  stay on Windows forever so I'll see what I can figure out.

Of course once Linux is up and running getting my sound card to work is  going to be a whole other new adventure but I'll be ready then.

---

