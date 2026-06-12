---
title: "If installing your home directory in a separate partition..."
date: 2008-01-11
forum: The Cafe
---

### Post by moeFinley on 2008-01-11
If placing your home directory in a separate partition is the best way to organise  your files why don't all the distros provide the option in the install?  :confused:

---

### Post by fedex1993 on 2008-01-11
PLEASE MOVE TO THE RIGHT PLACe this is a caffe not the newbie talk.

---

### Post by Sef on 2008-01-11
OP is not asking for help, but just asking a general question about why distros don't include home partitions as part of the install.

My guess would be to is that it is more complicated to do that (root, swap, and home) than simply root and swap.

---

### Post by perbiu on 2008-01-11
Last time I used SimplyMepis it has that option, so its easy to upgrade versions without reformatting the /home directory during Distro upgrade.

---

### Post by az on 2008-01-12
> **moeFinley said:**
> If placing your home directory in a separate partition is the best way to organise  your files .

It's not.

All-on-one partition is the best and safest way to go.

---

### Post by shad0w_walker on 2008-01-12
I would imagine it is a matter of the target audience. Beginners will be worried enough at the mention of partitions, let alone getting a swarm of choices about them.

---

### Post by FuturePilot on 2008-01-12
> **az said:**
> It's not.

All-on-one partition is the best and safest way to go.

Really? Why? I'm just curious because I've thought about moving my /home to a separate partition.

---

### Post by zenwhen on 2008-01-12
> **az said:**
> It's not.

All-on-one partition is the best and safest way to go.

How so?

---

### Post by Lostincyberspace on 2008-01-12
It is really opinionated subject, I believe. I think it is really wise to have it separate since you can easily reinstall, and keep your settings available at the same time.

---

### Post by sumguy231 on 2008-01-12
Since I don't think anyone else has offered this answer, I should add that most distros I have used *do* allow you to manually partition and put /home on whatever partition you want.

---

### Post by miggols99 on 2008-01-12
I think it's a lot better because if you need to reinstall, you can just keep your files and settings in your home partition instead of overwriting it.

---

### Post by Vinno on 2008-01-12
I have a parition for /home also but dont settings get overwritten when you install programs again with the default settings after a fresh os re-install.

---

### Post by moeFinley on 2008-01-12
Looks like this is a bit of a hot topic.

> All-on-one partition is the best and safest way to go.
Az why do you think this?

> most distros I have used do allow you to manually partition
sumguy231 I should clarify that I was alluding to having default options in the install just as they have a default option to have a single partition.

> **Vinno said:**
> I have a partition for /home also but dont settings get overwritten when you install programs again with the default settings after a fresh os re-install.
No, pretty much all applications write there settings when you first open the program.  Not during the install.  If the settings already exist then it uses those.

---

### Post by az on 2008-01-12
This topic has been discussed to death for the past few years.

The advantages of a separate home partition are pretty much artificial.  

You do not protect yourself from hardware failure, in fact by not keeping your files properly backed-up, you make yourself vulnerable to data loss.  If your drive dies, you just lost all your data.  If your drive only develops a few bad blocks, you are not going to have any more ease at backing up your data from your home directory regardless of what partition it's on.  

I would not continue to use such a drive after that, anyway.

The same goes for reinstalling.  It's a lot less complicated to just back up your data the conventional way (to a separate hard disk) than to create another partition on a single drive.

Often, the configuration files for some versions of applications don't work well with another version of the same application.  So if you want to share a home directory between different distros, or different versions of the same disto, you will run into trouble.

Creating a separate partition adds complexity to the installation process.  The installation process is the single most significant hurdle to getting new users to use Gnu/Linux.  A specific goal of a simple installation is to keep the number of questions (clicks) to a minimum.  

Splitting a hard drive into smaller pieces creates smaller pieces.  This is obvious.  What is less obvious is that it increases your chances that one of those partitions will fill up and take down your system.  Keeping everything on one shared partition prevents that (since all of the space will be shared, and you are not limited).  Keeping one shared partition also greatly simplifies the install process.

Instead of even having to consider partitioning, the user can be asked one question:  How much space do you want to use?

That being said, if you want to keep a separate home, go ahead.  It's your choice and it's fun to play around with your system.  But, the question was about the default install.  I think the default behaviour is the best/correct one.

Where I get opinionated is when I read new users being told that a separate partition is best.  A new user should not have to worry about that;  the hurdles to linux adoption are high enough already.  And the benefits are questionable.

---

### Post by moeFinley on 2008-01-12
Az, I agree there is little advantage to a separate partition and there is the issue of limiting the space you have.  But as you also point out a lot of people seem to prefer that way of working.  With this in mind doesn't it make sense to have the option (not replace the default) in the install process?

---

### Post by uberdonkey5 on 2008-07-30
Thanks Az - just reinstalling due to buggering up one of my partitions (think its the boot) and you have changed my mind. I think the important thing is KEEP A WORKING COPY OF UBUNTU ON DISK AT ALL TIMES*. Your reply makes sense and it IS a hassle having seperate partitions esp. with dual boot. I know some people now work off a removable hard drive, leaving the whole computer drive for the operating system. But still, there is no replacement for regular back-ups (its just as easy to get this stolen or broken when moving it around).

One thing for newbies though: Ubuntu operating system is small, but I found I was using it all the time to copy large files (like video files) due to the speed (I can boot ubuntu and copy about a dozen video files in the time it takes me to boot vista and copy one - this is one thing that sold ubuntu to a friend). THUS if you are using dual boot I recommend allowing quite alot of space for the ubuntu (single) partition, even though windows can't access it (I'm going 50/50 on a 260GB Hard Drive).

*[I managed to back up my files using this disk (I know I should have done this first). I downloaded SIX copies from internet, and TWO USB copies and none worked. Eventually just found a friend that had a copy.]

---

### Post by Dharmachakra on 2008-07-30
Forgive me if I'm out of it, but isn't that option in the install? Granted, if memory serves me correctly, that option is "hidden" by way of the user having to choose it specifically. I would take the stance that if a user doesn't know how to create a seperate home partition at install time, they probably don't need it.

---

### Post by original_jamingrit on 2008-07-30
az is right.  It's handy if you're installing across multiple hard drives, but it's not worth partitioning a single hard drive.  Partitioning was meant to help save space and prevent fragmentation, and separate file systems that could seperatley become corrupted.  But none of those things are a big issue with modern hard drives.  And partitioning definitely does not give you an excuse to not back up.

---

### Post by ezsit on 2008-07-30
I used to use a separate partition for /home but have come to the conclusion that having a separate partition for /myfiles. When I experiment or reinstall all my files are still where they belong and a merely chown the entire partition at once as necessary. I always keep backups on two different external hard drives, so no matter what happens, all my stuff is safe. 

However, I've been partitioning and formatting hard drives since 1993 when my DOS / Win3.11 / OS/2 all shared the same 500MB hard drive, so multiple partitions do not scare me in the least.

---

### Post by cardinals_fan on 2008-07-30
I keep a separate partition labeled "data" that takes up almost all of my hard drive.  I keep all my files in there :)

---

### Post by Kvark on 2008-07-30
The easiest option should be the default. The fewer questions the better as long as those who know they want something else can change things after installation. Storing user files on a separate partition does not replace the need for backups or provide any other advantage relevant enough to ask about it during installation.

However, if you want to use your personal files on several different distros then it's good to have the files on a separate partition that all distros mount. It's not good to mount this partition on the home directory because then the different distros will get their config files mixed up; instead I mount my personal files on each distro's default documents directory (/home/username/Dokument in Ubuntu) but this only works for a single user. Is to possible to have each distro store all their settings on their own partition but all users' files on a separate partition they all share?

---

### Post by cdtech on 2008-07-30
Some feel that greater security is achieved by moving their user directories under a separate "/home" partition. You can format one partition and keep the data on a separate partition. You could also reinstall your operating system and not loose any of your personal data within your "/home" partition. Also if you had a hard drive failure the chances of recovering your personal data are increased (security).

I feel that keeping the directories that fill up separate from the directories that are needed by the system to function properly protects the system against a crash.

For a beginner I suggest using a root "/" and a "swap" only, until you know for sure how much space you will acually use in the long run. After which you can always make a partition for your separate "/home" "/tmp" "/" directories. I've found a common ground on my setup using "/", "/home" and "/tmp" partitions. With my setup I feel safe that I wont loose my personal data during an upgrade or even a reinstall of my OS.

---

### Post by thisllub on 2008-07-31
> **az said:**
> It's not.

All-on-one partition is the best and safest way to go.

Wrong on both counts.

Seriously wrong.

I have been using the same home partition for years.
It has been through at least 10 distros in that time.
It isn't even on the same disk as my root.

When a major distro update is released I install it on its own relatively small partition and test it. If I like it I point the home directory at my home partition. My computer seamlessly takes the new changes on board.
If my distro gets hosed a partition restore has me up and running in less than 15 minutes with no loss of data. If I had to restore hundreds of GB it would be far more painful.
If my data drive takes a dump I still have a working computer.

Likewise backups are simpler. 
I get my system right then backup the root partition to a file on a USB drive. I rarely need to change this - even on Arch I only go to the trouble of updating this backup ever 3 months.
My home and data partitions get backed up( with rsync) every day.

---

### Post by Jimmey on 2008-07-31
> **az said:**
> It's not.

All-on-one partition is the best and safest way to go.

Personally, I think that was an unhelpful comment.

You just contradicted what the other person said without saying anything helpful to back up your claim. As if you know better.

---

### Post by aaaantoine on 2008-07-31
> **Jimmey said:**
> Personally, I think that was an unhelpful comment.

You just contradicted what the other person said without saying anything helpful to back up your claim. As if you know better.

And in his next post, he explained his response.

---

### Post by gletob on 2008-07-31
I like separate home, root, and boot

---

### Post by TravisNewman on 2008-07-31
Separate /home isn't necessary, but it makes life far, far easier. I don't understand why people seem to think otherwise. I have had 4 linux distributions installed on one hard drive, all sharing one swap, one /boot and all sharing one /home. Beyond that, like has been said before, it makes backup and restore far easier. Disaster recovery is less of a concern (though still a major concern) because unless it's a physical hard drive problem or a partition table going out, it's most likely one partition dying. If /home goes out, you can restore it while using the PC, and if / goes out you can restore it in 30 minutes or less, and not have to worry about restoring your system and all the other 1-1000 gigs of /home. 

So to summarize... It's safer, easier, and more efficient to use a separate /home, and if you know what you're doing or you're brave enough to try, I recommend it to everyone.

---

### Post by Depressed Man on 2008-07-31
If your Home is the equiviliant of say all of Microsoft's individual folders (My Documents, Music, Video) then I say use a seperate partition. I don't, mainly because I use my home partition as an area to put Linux stuff (Scripts, etc..) stuff that I generally may throw away with a reinstall of Ubuntu (whenever a new one comes) since all my files are on a NTFS partition (so my dual boot computer can read them both).

---

### Post by Redrazor39 on 2008-07-31
openSUSE does it by default

---

### Post by pterosky on 2008-09-08
I can't recommend using the "/home" folder the same way some people use Microsoft's My Documents. Settings and newly installed programs liberally fill the "/home" folder up with cryptically named folders and files, making it harder and harder to find the folder you are actually looking for.

My next installation will be near all-in-one; No separate /home partition, only a separate partition labeled "storage" for all my files and a swap partition, though I am not sure I need it with 2 gigs of ram.

When switching to Linux, one thing I had a hard time understanding was the concept of the swap partition: How big should it be, how do you partition it to be a swap file, where should it be located, etc...

So my suggestion would be for the Ubuntu installation process to check whether there is below, say 512 Mb of ram and if yes, create a swap partition. Or even better, would it be possible to integrate the swap process as a part of the system itself? 

The Linux aficionados will surely want to save hard disk space by sharing a swap file between multiple Linux distros, the rest of us might not need that option and with hard disk space being cheap and plentiful these days not even needed...

I really think it would ease peoples' entry into the world of Linux a great deal :)

---

### Post by LaRoza on 2008-09-08
> **pterosky said:**
> I can't recommend using the "/home" folder the same way some people use Microsoft's My Documents. Settings and newly installed programs liberally fill the "/home" folder up with cryptically named folders and files, making it harder and harder to find the folder you are actually looking for.

What are you talking about? Most program settings files/directories are hidden.

> 
When switching to Linux, one thing I had a hard time understanding was the concept of the swap partition: How big should it be, how do you partition it to be a swap file, where should it be located, etc...

Most installers do it by default.

> 
So my suggestion would be for the Ubuntu installation process to check whether there is below, say 512 Mb of ram and if yes, create a swap partition. Or even better, would it be possible to integrate the swap process as a part of the system itself? 

Well, it could be done like Windows (page file) in C: which not only fragments the drive horribly but also leads to poor performance and data corruption. But that is the Windows way. (When I used it, I had it setup to use a different partition, on a different drive)

> 
I really think it would ease peoples' entry into the world of Linux a great deal :)
Yes, because we get so many people put off by Linux because of swap right? The goal of Linux is to work, not pander to the lowest level of skill.

---

### Post by ubuntu-freak on 2008-09-08
> **az said:**
> Often, the configuration files for some versions of applications don't work well with another version of the same application.  So if you want to share a home directory between different distros, or different versions of the same disto, you will run into trouble.

 
That's exactly why I don't have a seperate home directory, and the fact it's not a safe and true way to backup your files.

---

### Post by Skorzen on 2008-09-08
I don't know why, but I have a separated home partition and I like it.
Maybe the user have the freedom to choose whether have it or not separated?

---

### Post by LaRoza on 2008-09-08
> **ubuntu-freak said:**
> That's exactly why I don't have a seperate home directory, and the fact it's not a safe and true way to backup your files.

For dualbooting (Linux's), I am not a fan of a separate home and prefer a storage partition, but for a single boot, or a dual boot with a non *nix, it is advisable.

---

### Post by Scruffynerf on 2008-09-08
Data point:

2 hard drives, /root and /swap on drive 1, /home on drive 2.

Found it as a nice way when distro upgrades destroy/corrupt the current installation, or I do it by tweaking something I don't fully understand. It helps that drive#2 is a lot larger.

FWIW, I dualboot XP SP3 as well, and it's arranged the same way - OS on drive 1, data on drive 2.

GParted made it quite simple to set up.

---

### Post by ubuntu-freak on 2008-09-08
> **LaRoza said:**
> but for a single boot, or a dual boot with a non *nix, it is advisable.

 
Why? I've never had a seperate home and I feel fine.

---

### Post by LaRoza on 2008-09-08
> **ubuntu-freak said:**
> Why? I've never had a seperate home and I feel fine.

Of course you feel fine! It isn't like anything breaks if you don't...

I used to not think it was worth it, mainly because I had already installed everything and didn't feel like fiddling.

---

### Post by ubuntu-freak on 2008-09-08
> **LaRoza said:**
> Of course you feel fine! It isn't like anything breaks if you don't...

 
I was being moronic.

---

### Post by uberdonkey5 on 2008-09-08
La Roza, didn't you make a convincing argument previously of why its best not to seperate the home directory?? i.e. if a system goes down it tends to screw up everything and really regular back ups are the only solution (this is definately what happened with me). If your data is NOT corrupted, you can remove it using boot disk anyway!

I was definately convinced anyway and I DO NOT partition my disk. One thing I like about the Asus Eee PC though, is the ability to restore factory settings (including operating system) at press of a button. ALSO I keep my data on the removal SD card. This is more or simple backup.. I just slip it into my big laptop every so often and backup that way.

It would be great if future computer designers catch on to preinstall ubuntu, and have a 'restore factory setttings' option, as well as making the data HD seperate and physically removable (maybe with a couple of screws). What you think?

---

### Post by LaRoza on 2008-09-08
> **uberdonkey5 said:**
> La Roza, didn't you make a convincing argument previously of why its best not to seperate the home directory?? i.e. if a system goes down it tends to screw up everything and really regular back ups are the only solution (this is definately what happened with me). If your data is NOT corrupted, you can remove it using boot disk anyway!

I don't know. I have slightly changed my use of the home directory as well. I used to never keep personal files in it, and use it only for configuration files of the various applications and used a separate partition for all of my files (which were shared with my other OS).

I have since regulated that OS to specialty use only, and no longer have data sharing enabled (by using EXT3, instead of NTFS) and use my home more for some files (usually things I am working on at the moment)

> 
It would be great if future computer designers catch on to preinstall ubuntu, and have a 'restore factory setttings' option, as well as making the data HD seperate and physically removable (maybe with a couple of screws). What you think?
It is called a reinstall disk. For a netbook, that isn't a big deal, but for a system for more local use, such an option would be just the same as reinstalling and isn't always the easiest thing to do.

---

