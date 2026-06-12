---
title: "Does anyone actually use swap space anymore?"
date: 2009-05-23
forum: The Cafe
---

### Post by random_hypocrisy on 2009-05-23
I dont. Havent in ages, and have never had any problems.

---

### Post by happysmileman on 2009-05-23
I do,  have 512MB of RAM and frequently go into 3-400MB of swap.

---

### Post by binbash on 2009-05-23
Of course i do, because of hibernate function

---

### Post by Dharmachakra on 2009-05-23
I've set aside a 2GB swap space. It's complete overkill but it keeps my partition set-up nice and clean. 

I rarely use a single KB of that space.

---

### Post by SuperSonic4 on 2009-05-23
Occasionally on the desktop when I've been running CPU intensive tasks like when I ran devede, kopete (+3 convo windows), KWin and composting, full screen video in vlc, k9copy, amarok paused, firefox, konsole and dolphin running at once

On the laptop I frequently use it because I am using it to test KDE 4.3 which isn't the best idea on 512mb ram but it works thanks to a light arch base XD

---

### Post by Kareeser on 2009-05-23
With boot-up on par with hibernate, and suspend-to-memory taking over the middle ground, I'm actively considering formatting Karmic to use zero swap space.

In the long run, it really doesn't matter, but I suppose it's a nice "backup" in case a process goes awry and starts eating memory for breakfast!

---

### Post by 0per4t0r on 2009-05-23
I use swap space because the installer told me to. O holy ubuntu installer, what is thy next command?

---

### Post by Vadi on 2009-05-23
8GB of swap here.

Because when linux runs out of ram + swap, it's all HD trashing and a hard reboot. I definitely don't like losing data.

---

### Post by RiceMonster on 2009-05-23
> **binbash said:**
> Of course i do, because of hibernate function

yep same

2GB swap here, because I have 2GB ram

---

### Post by thegreenblob on 2009-05-23
I have 4GB of RAM and 1GB of swap, and I ALWAYS use swap ...when I play frets of fire, seems to have a major memory leak. lol. But any other time it's never touched.

---

### Post by hanzomon4 on 2009-05-23
Swap-file, better then a partition

---

### Post by s3a on 2009-05-23
> **hanzomon4 said:**
> Swap-file, better then a partition

How so?

---

### Post by ee19921 on 2009-05-23
Yes, for hibernation. But I am using Swap file instead.

[HOWTO: Use swapfile instead of swap partition and have working hibernation]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile")

---

### Post by Regenweald on 2009-05-23
2gigs ddr2 800mhz, no swap, even with VB running. I don't hibernate so a swap would be a waste of space.

---

### Post by FuturePilot on 2009-05-23
> **binbash said:**
> Of course i do, because of hibernate function

Another one here for hibernate. I also use some swap when doing intensive stuff like virtual machines.

---

### Post by kk0sse54 on 2009-05-23
> **random_hypocrisy said:**
> I dont. Havent in ages, and have never had any problems.

I have a 3 GB swap but I've never even expierenced any kind of swap usage at all except when trying to run htop in bsd...

---

### Post by Mr Bean on 2009-05-23
I got rid of my swap partition because I recently installed 8GB of RAM (yeah it's overkill, but they had 4GB matched pairs on special offer, and getting two sets meant I didn't have to pay postage)

DDR2 is dirt cheap now, there's really no excuse to be depending on swap space/page files and the like. 

I didn't realise you need a swap partition to hibernate though, I'll have to look into that.

---

### Post by Magneto on 2009-05-23
I only use swap space when my wife and I find a cute couple.

---

### Post by ghindo on 2009-05-23
I have the same amount of swap space as I do RAM (2 GB), but don't know if it's actually necessary.  I don't use hibernate (only suspend), and I'm not sure how often the swap is used.> **Vadi said:**
> 8GB of swap here.Woah.

---

### Post by HappyFeet on 2009-05-23
> **Vadi said:**
> 8GB of swap here.

Because when linux runs out of ram + swap, it's all HD trashing and a hard reboot. I definitely don't like losing data.

I don't like losing data either. That's why I backup on 3 different drives/partitions. But 8gb of RAM is overkill/paranoia.

I have had 20 apps open and working as a test. I was only using 40mb swap. 8gb swap is a definite waste of space.

---

### Post by HappyFeet on 2009-05-23
> **ghindo said:**
> I have the same amount of swap space as I do RAM (2 GB), but don't know if it's actually necessary.  I don't use hibernate (only suspend), and I'm not sure how often the swap is used.Woah.

That antiquated logic went out the door soon after XP came out. 

If I have 4gb RAM, then I should have 4gb swap? I think not. The more memory you have, the *less* swap is needed.

---

### Post by Mr Bean on 2009-05-23
> **HappyFeet said:**
> I don't like losing data either. That's why I backup on 3 different drives/partitions. But 8gb of RAM is overkill/paranoia.

I have had 20 apps open and working as a test. I was only using 40mb swap. 8gb swap is a definite waste of space.

I'd say backing up to 3 drives is paranoia ;)

But then I've yet to properly back up my files to 1 drive, so I can't really talk. 

I do store most of the stuff I care about on a RAID1 array, I know that doesn't count as a backup but it's better than nothing.

---

### Post by HappyFeet on 2009-05-23
> **Mr Bean said:**
> I'd say backing up to 3 drives is paranoia ;)


It's not paranoia, it's making sure my girlfriend's stuff has NO chance of getting lost. She would beat me severely about the head and neck area. ;)

---

### Post by Mr Bean on 2009-05-23
Avoiding a beating is as good a reason as any to backup regularly, I spose. :p

---

### Post by FuturePilot on 2009-05-23
> **HappyFeet said:**
> That antiquated logic went out the door soon after XP came out. 

If I have 4gb RAM, then I should have 4gb swap? I think not. The more memory you have, the *less* swap is needed.

If you want to hibernate you need swap at least equal to your RAM.

---

### Post by Xbehave on 2009-05-23
I still have the partition (~900MB) but i barley use it other than to hibernate. I do however intend to keep it as i just moved my /tmp into tmpfs and if im messing around with large files (e.g burning a disc etc) want there to be somewhere to put them on disk but this way i get better battery life/performance and dont need to worry about wasting space on /tmp elsewhere on my disk.
> **FuturePilot said:**
> If you want to hibernate you need swap at least equal to your RAM.
Not true, you need your swap to be the same size as your **used** ram**+swap** (using swap as the suspend device is a horrible hack), and most hibernate solutions run your ram through a compression before writing it to disk (as it speeds up resume), on my loads it would cut of ~20% iirc. I currently suspend 1473m ram to 951m swap and im sure i could getaway with only 512m if i wanted to.


Swap files are good, they should become the default in future ubuntu versions (IMO) if they can get all the setup scripts to work with a file then new users dont need to worry about it. However where the swap file(s) go needs to be sorted out (/var/swaps/[0-n] ?) and hibernation should not use a swap file but its own (created on demand) hibernate file.

> **hanzomon4 said:**
> Swap-file, better then a partition
Swap partitions are much more powerful than swap files you can raid-0 them, put them at the right part of the disk, share them, don't fragment drives, etc

---

### Post by kc3 on 2009-05-23
I *considered* using a Solid State Drive or even a GC-RAMDISK (but thought it was overpriced) for a swap partition buuut I kind of decided against it, maybe later on. I have 4gigs of ram anyways and never go into it realy at all so seems like a bit of a waste.

---

### Post by FuturePilot on 2009-05-23
> **Xbehave said:**
> 

Not true, you need your swap to be the same size as your **used** ram**+swap** (using swap as the suspend device is a horrible hack), and most hibernate solutions run your ram through a compression before writing it to disk (as it speeds up resume), on my loads it would cut of ~20% iirc. I currently suspend 1473m ram to 951m swap and im sure i could getaway with only 512m if i wanted to.


That makes sense. I learned something new :)

---

### Post by Eviltechie on 2009-05-23
I only use swap on a bad day.

---

### Post by x33a on 2009-05-23
i have got 2 GB ram, and set 2 GB for swap, but it never gets used. 

even, my ram isn't fully used. i rarely hibernate, so all in all, the swap is almost never used in my case.

---

### Post by ghindo on 2009-05-24
> **Xbehave said:**
> Swap partitions are much more powerful than swap files you can raid-0 them, put them at the right part of the disk, share them, don't fragment drives, etcWhat does it matter if they're on the right part of the disk?

---

### Post by aysiu on 2009-05-24
I have a 16 GB SSD and 2 GB of RAM.

I also either shut down or suspend-to-RAM. So I have absolutely no need for swap.

---

### Post by Mr-Biscuit on 2009-05-24
Yes.
When ever I am using blender or some other 3d rendering program.

---

### Post by HavocXphere on 2009-05-24
I don't the 2gb swap on my box were ever used...but I've learned from my Windows days that no swap is a very bad idea, even if it *can* run without swap. BAD things happen and its almost impossible to trace it back to a lack of swap.

---

### Post by Barrucadu on 2009-05-24
I've got 3GB RAM, and a 5GB swap partition (so I could suspend if I ever felt the need to, I picked 5GB because I can have 4GB of RAM). However I very *very* rarely use over 1GB of RAM. My normal usage generally hovers at aroung 500MB.

---

### Post by Xbehave on 2009-05-24
> **ghindo said:**
> What does it matter if they're on the right part of the disk?

With laptops and small drives it doesn't matter much tbh, but if you put the swap on the outside (i think) of the disks the writespeed for sequential writes (when you start swaping stuff out this is what happens) is faster.

---

### Post by Bölvaður on 2009-05-24
On my laptop I got 502MiB swap partition.
On normal usage it is on about 30MiB and is big enough to hold all the ram + the stuff that was already in the swapspace.

---

### Post by Polygon on 2009-05-24
if you dont mind the kernel killing applications when you run out of memory, sure its fine to not use swap.

---

### Post by aysiu on 2009-05-24
> **Polygon said:**
> if you dont mind the kernel killing applications when you run out of memory, sure its fine to not use swap.
With 2 GB of RAM, I doubt I'll ever run out of memory. I'm a netbook. What kinds of applications do you think I'm running?

---

### Post by dragos240 on 2009-05-24
I don't think so. Oh wait, 5.42 gb of swap, but when I hibernate, it doesn't seem to help, I will never hibernate again after what happened a few days ago. It kept kernel panicing :( on bootup.

---

### Post by tom66 on 2009-05-24
Thankfully Ubuntu rarely uses any more than 1 GB of RAM, so I rarely use swap (I have 3 GB of RAM and 2 GB of swap). When I opened a 12 MB JPEG (773.3 MB uncompressed :o) it hit 2.53 GB, and then it started to use swap...

---

### Post by Mr. Picklesworth on 2009-05-30
Edit:
Oops. Not sure *where* I got the "Windows doesn't do this" from.
Sorry! I guess I'll leave this...


It's worth noting that Windows *does* create huge amounts of reserved swap space, but it is not very clear about it. For example there are 2GB or so reserved on my system for this purpose, as a locked file in the same partition as everything else Windows does. This is basically one of the reasons why Windows Vista has such erratic fluctuations in available hard drive space and one of those infamous 'hidden files'; you can neither see it nor remove it nor resize directly, instead needing to hunt down the tool to configure swap space.

Oh, and aside from being able to resize swap space quickly / dynamically, it's not healthy. Most Linux distros (including Ubuntu) apply a much better approach here by default. They use a separate partition to avoid fragmentation, to keep those space counts separate, to enable hotplugging swap partitions, to have the swap on something like an SSD, and to share the same swap space between operating systems. Seems much more sensible to me :)

---

### Post by The Real Dave on 2009-05-30
Yup I do, 1.4Gb of RAM, and a GB of swap. Dont often use much of it, but better to have it and be safe then be hard rebooting and losing data :S Also helped me in my n00b days, when I got hit by a fork bomb :(:(Gave me enough time to kill the processes :) (~40secs, not bad for a PIV ;))

Also, when I'm really pushing my system (Usually encoding DVD's), to speed up my swap, I turn off the swap space on my HDD, and use an old 2Gb Flashdrive instead. I realise that this can burn the drive to bits (believe me, it gets damn hot :-k) but its a spare and expendable :) 

Im currently working on modifing this set up though. Using a small alluminum case to store the flash drive and act as a heatsink, a basic circuit, and a small old CPU fan (powered by the battery attached to the circuit, charged via USB) to act as a swap farm :D 1Gbx2 of extremely fast swap space, without the worry of burning a hole through my old flashdrives =]

---

### Post by Hobgoblin on 2009-05-30
> **Polygon said:**
> if you dont mind the kernel killing applications when you run out of memory, sure its fine to not use swap.

And when you run out of RAM and swap?

If you find yourself running out of memory then the solution is to buy more memory, unless you have some hardware limitation preventing that.

I've never found hibernate (with Ubuntu) to be any faster than a regular cold boot and hibernating is much slower than shutting down.  So given enough memory I don't bother with swap.

---

### Post by WatchingThePain on 2009-05-30
Never, because I don't use hibernation.

---

### Post by burvowski on 2009-05-30
I'm a recent switcher to Linux and I just had Ubuntu do an auto-install for me onto my new netbook. I just looked at my file system and it devoted 5.74 gigs to the swap partition! :o holy cow, that seems like overkill!

---

### Post by heroidi on 2009-05-30
80 GB swap actually a half-dead hard drive not formatable in any other  filesystem than swap and it works very well as swap

---

### Post by Einsamkeit on 2009-05-30
1g RAM for 1.4g swap, and swap gets used often.
I don't really know why tho, I only do quite simply tasks, some word processing, the occasional movie.. 
But yeah, it's being used.

---

