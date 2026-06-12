---
title: "[SOLVED] Strange problem with Ubuntu Server and 2nd SATA drive"
date: 2008-12-11
forum: Server Platforms
---

### Post by [Grevane] on 2008-12-11
Hi all,
I was wondering if anyone could lend me a hand with this slight issue I'm having.
 
Up until now, I've been mostly a "reader" on this forum. Google has been an excellent friend while experimenting with Ubuntu.
 
I recently purchased an HP Pavillion g3100 through work to use as an Ubuntu box at home (day to day IT support gets a little "samey" and so from time to time I like to bury myself in little mini projects at home).
 
I threw my old GF6800Ultra into this Pavillion PC and have had a good month or so of very impressive Ubuntu desktop use. I added a 2nd drive (almost identicle as the 1st) on the desktop variety just for a little more space.
 
I've had it joined to my Win2K8 domain at home (had to edit the source files of Samba 3.2.5 to get Winbind working correctly - had to hard coded my kerberos realm as there was a bug where it would only resolve the domain name but not the suffix), played around with Shorewall, and various other things. all in all, very impressive (love the 3D desktop :p ).
 
Yesterday, I decided to reload and throw the server package onto this PC and I've been absolutely plagued with partitioning problems.
 
This PC has 2 160Gb SATA drives in it.
 
I ran the installer for Ubuntu Server and chose the manual partition option (as I had done previously with the desktop variety) and decided on a simple partition setup.
 
sda
/dev/sda1 - mounted as '/' & size=100% of drive less swap
/dev/sda5 - swap (~4Gb)
 
sdb
/dev/sdb1 - mounted as '/home' & size=20%
/dev/sdb5 - mounted as '/data' & size=80%
 
Anyway, that lot failed to boot. Not because I'd been lazy and not been bothered to define all the partitions (I figured that the drives are big and I'm never going to run out of space) but because the installer didn't install GRUB. I had to run the repair option and force it to install GRUB into hd0.
 
It then did boot but failed to mount the 2nd drive.
 
So I tried again. Same thing.
 
I even went as far as totally trashing the boot record with an old util called Ranish Partition Manager incase it has somehow damaged the boot record. But hte same thing happened again.
 
So...
 
I went back, removed all the partitions again, and just let the installer setup Ubuntu Server on /dev/sda using all the disk space. I didn't bother with any custom partitions. I decided I would do that once it was installed.
 
Also, an important note. I absolutely definitely in every attempt said NO to Ubuntu's wish to activate my drives as RAID devices. It's a cheap HP PC (cost me £120 including a Vista Home license) and definitely not RAID capable.
 
But I am now sat here looking at gpart and it's telling me i have the following devices in my PC...
 
/dev/sda <-- correct
/dev/sdb <-- correct
/dev/mapper/nvidia_behdggie <-- erm, where did you come from?!?!?
 
So I thought I'd just ignore it and format sdb anyway...
 
But it won't let me. It fails to create the ext3 partition when it tries to create the ext3 filesystem.
 
Hmmm, so I though sod it, I'll create the partition on the rogue nvidia_behdggie device because it had blatantly created this fictional device from the 2nd SATA drive.
 
This time it completed successfully.
 
However, there was also a "broken" partition on the sdb device...
 
And even stranger, all of a sudden my PC has grown a 4 drive out of nowhere...
 
My device list was now as follows........
 
/dev/sda <-- correct
/dev/sdb <-- correct
/dev/mapper/nvidia_behdggie
/dev/mapper/nvidia_behdggie1
 
And there you have it, I have no clue what's going on and my friend google has let me down.
 
And the last bit of info I can add to this is that when I delete the broken partition on /dev/sdb both nvidia devices remain. However, if I delete the sdb partition and then delete the nvidia_behdggie partition, the nvidia_behdggie1 device disappears again but for love nor money, I can't get that darn final nvidia device to disappear. As far as I can tell, it's NOT to do with the boot record. It's down to something ubuntu server does during install and I'm a little loath to delete files or edit files with references to them until I've checked with someone who knows the Server package a little better than I do.
 
I'd really like to get back to just 2 plain SATA drives. Does anyone have any clue what's going on? I'm baffled and totally googled out on searching for answers.
 
Thanks in advance for any help

---

### Post by albinootje on 2008-12-11
What about the RAID-options in the BIOS ?
I just looked at these 2 links :
[http://linux.derkeiler.com/Mailing-Lists/Fedora/2006-06/msg03674.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2006-06/msg03674.html)
[http://www.linuxforums.org/forum/linux-newbie/118308-can-i-rename-device-like-dev-mapper-nvidia.html](http://www.linuxforums.org/forum/linux-newbie/118308-can-i-rename-device-like-dev-mapper-nvidia.html)
It sounds like a good idea to turn the hardware RAID off in the BIOS, using plain IDE, and reinstall, making sure that the partitions are not flagged as RAID partitions if there possibly were flagged like that somehow.

---

### Post by [Grevane] on 2008-12-12
hi albinootje,
 
thanks for the reply! ):P
 
that's the really strange thing about this, it doesn't have any raid options.
 
it's just a cheap'n'cheerful office desktop PC.
 
to give you an idea, it has one of those that only has 2 SATA connectors, 1 PATA, and 3 PCI slots and 1 PCI-e slot.
 
Infact, it's made extra odd by the fact that half the inside of the case is back to front (to save space the PSU isn't in the std place etc...)
 
It's **VERY **basic and certainly doesn't have any raid capabilities...
 
And the last really odd thing (which I'm tending to think is something to do with Ubuntu Server rather than the PC) is that GRUB never installs correctly, no matter what. Almost like the Ubu Server installer is a bit "screwy". Never has a problem with Ubu Desktop but everytime I installed the Server build, I had to "repair" and force install GRUB into hd0.
 
I've just gotten to work so I'll take a read of those links you posted once I've dealt with the mornings support calls...
 
Thanks again!
 
[EDIT: if you or anyone else knows how to manually unflag the drives, that would be awesome as overall, I've now got this server running v.sweetly. I'm actually very happy with it overall just need to get this 2nd drive unflagged as a raid device so I can use it as 2 normal SATA drives. I'm guessing this is something to do with the SATA controller and the fact it's a very new HP PC. When I got it, there were "only" Vista drivers available for it on HP's website. Not even any XP ones let alone Linux or any other OS's]
 
[EDIT2: ahhhhhhhh, I think you nudged my thought process along the right line. I "think" I know what's causing this. At the same time I bought this PC I also bought a new server from work. An HP ML115 and I used that drive while I was waiting for my 4x 1Tb drives which went in the server in RAID 0+1 so that 2nd drive IS originally out of a Server that DOES have RAID capability - it has an NVidia Media Shield RAID controller - hence where the Nvidia reference is coming from. That 2nd drive can be removed and has no important data on it so I guess the trick is, how on earth do I unflag that drive for RAID? I'm fairly sure now that your thoughts were corrct about it being flagged but I've trashed all the partitions, trashed the boot record and it still remains flagged. Could anyone shed any light on how to "unflag" it?]

---

### Post by albinootje on 2008-12-12
Hmm, weird.

If you've removed all partitions, then there's nothing to change any existing partition label to.
Also a bit weird to hear that you have so many problems with Grub from the Ubuntu server installations. 
I've done a few Ubuntu server installations and i never had that problem, but that was often with just 1 IDE hdd.
I did one software RAID1 install with Ubuntu dapper with 2 Sata disks, also no Grub problems.

As a good Linux user you should think about reporting this bug, and help to get it fixed ;-)
But if you don't have time for that, try a Debian Etch installation.
I think the semi graphical Debian Etch installation is pretty cool, also for servers and for a minimal installation.
You can also try Debian Lenny, it is still not released, but you can look at the unofficial RC bugs list :
[http://bts.turmzimmer.net/](http://bts.turmzimmer.net/) And then decide. 
I'm happily using Debian Lenny in a VPS since a few months for Nagios, and for some small administrative tasks.
On several servers i'm happily using Debian Etch, but sometimes i had to backport (some perl based packages) from Debian Lenny.

---

### Post by albinootje on 2008-12-12
And perhaps you start a new post asking how to get rid of the /dev/mapper/nvidia_behdggie.
You could do this as a bug-report or question on launchpad.net with the idea that Ubuntu developers will get a chance to reply to you.

---

### Post by [Grevane] on 2008-12-12
hello mate,
 
yeah, historically I'm actually a debian fan (tbh, this love of linux actually stems from Everquest and... *cough cough* ShowEQ "testing" of course ;-) )
 
i love debian, been using it on and off for years and never really had a chance to test Ubuntu.
 
But I've gotta say, I'm very impressed with how Ubuntu are trying to bridge the gap between linux hobbyists. Still a fair way to go but definitely the right direction.
 
I was using debian etch and was happy with that. but then I had a major HD failure containing ALL my data from the last 10years. so i did this overhaul of my IT kit at home and hence I've had time to test etch vs lenny and ubuntu 8.10 desktop and server. (part of why I tried ubuntu was down to how nice lenny was in terms of the GUI... (thinking again along the lines of it becoming more "mainstream").
 
i'm trying at the moment to find exactly how or where the drives are flagged for a RAID. I had tried trashing the boot records but maybe there was somethign left in respect to the RAID flag which was causing GRUB problems (or rather causing the installer problems when installing GRUB). Maybe the flag is stored at the end of the drive rather than in the boot records... Never had much need to look into RAID and how the data is stored on teh drives in this much detail before...

---

### Post by [Grevane] on 2008-12-12
> **albinootje said:**
> And perhaps you start a new post asking how to get rid of the /dev/mapper/nvidia_behdggie.
You could do this as a bug-report or question on launchpad.net with the idea that Ubuntu developers will get a chance to reply to you.
Mmm, good idea mate...
 
heh hehe, no idea whats involved in launchpad.net... will have to look into it. I'd be more than happy to pass on info I find out. I've got around more than enough minor and major bugs to get to where I am now.
 
But this RAID things is just bugging me now. I'm sure if I get rid of whatever data is being stored on the drive that this problem will disappear but I'm damned if I can find anything through google.
 
Sods law, when I search for "remove RAID flag" and similar searches, all I get are World of Warcraft hits...LOL!!! which would be fine if I still played ;-)
 
But thanks again for the replies. Been a pleasure chatting with you.

---

### Post by albinootje on 2008-12-12
Okay, nice to hear that you've already used Debian before. :)

And it was good to talk to you, except that we're not so much further, and i have the impression that i shouldn't have used the word "flag" so often, perhaps "label" is better.
In fdisk you have "change bootable flag". but concerning partitions it's a bit unclear from within fdisk how the labelling of the partitions would be called.

In FreeBSD there's slices and disk labels.

I just looked and didn't see any specific "Linux Raid", there's only Linux and Linux swap for partitions. I wonder how the partition software in the Ubuntu install deals with that.

And do check [https://bugs.launchpad.net/](https://bugs.launchpad.net/) and file a bug.
It can be interesting and fun to talk to the developers and other users.
GL!

---

### Post by albinootje on 2008-12-12
Ah.. I was wrong (of course). 
Linux Raid Auto is there in fdisk as "fd".

---

### Post by [Grevane] on 2008-12-12
Thank you again mate. Don't worry about being "wrong" or "not quite right"...
 
Sometimes its just as useful discussing something with another person just to stimulate alternative thought processes.
 
i.e. I would've never thought about the fact it was in my server originally if we hadn't been discussing this so you're help/discussion is still very much appreciated.

---

### Post by albinootje on 2008-12-12
Cool! Good luck, and have fun with Ubuntu and/or Debian.

---

### Post by [Grevane] on 2008-12-12
You too mate and if I can ever help or if you just wanna bounce a few idea's off someone, feel free to PM me.

---

### Post by psusi on 2008-12-12
Either you DO have a bios fake raid in your system, or those disks used to be in a system that did ( using an nvidia chipset ) so they still contain the information identifying them as part of a raid.

If you do not want to use them like that any more then you can remove the raid signature by running sudo dmraid -E /dev/sda /dev/sdb.

You might want to read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for a bit more background info.

---

### Post by [Grevane] on 2008-12-13
> **psusi said:**
> Either you DO have a bios fake raid in your system, or those disks used to be in a system that did ( using an nvidia chipset ) so they still contain the information identifying them as part of a raid.
 
If you do not want to use them like that any more then you can remove the raid signature by running sudo dmraid -E /dev/sda /dev/sdb.
 
You might want to read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for a bit more background info.
hello psusi,
 
thanks for the reply mate.
 
funnily enough, i'd been doing some further google'ing this morning and i've literally just fixed it. and you were quite correct.
 
the place i ended up at was the dmraid command.
 
firstly, i ran "dmraid -r" which confirmed the presence of raid metadata (i forget exactly now, but i think it confirmed it specifically on sdb)
 
then as you just suggested i ran "dmraid -r --erase_metadata /dev/sdb" (same basically as what you said) and it removed the raid metadata.
 
however, gparted still (i guess) had the info cached so a quick reboot and everything was sorted.
 
the rogue raid device was gone. solved! yay!
 
thanks for the replys. been very useful.

---

### Post by The other One on 2009-05-07
Thankyou so much for this post and the replies - I've been having this same problem for a long time now, and this has solved it for me too.

:KS:KS:KS:KS:KS

---

