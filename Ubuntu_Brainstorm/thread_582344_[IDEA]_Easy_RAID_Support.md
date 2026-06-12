---
title: "[IDEA] Easy RAID Support"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by Flashstar on 2007-10-19
Once again, I am bringing up an important issue which has prevented me (and surely numerous others) from running Ubuntu for at least a year. The big problem is that software RAID of any type can only be activated through the alternative CD and even then one must go through guides online to figure out how to get it to work. 

I propose a simple entry in the graphical installer which can easily support using two separate disks in a RAID 0 or RAID 1 array. I believe that Fedora has such a feature enabled for much time now. This feature could support purely software RAID, hardware assisted, or a combination of the two. 

Such a feature would be beneficial to numerous people and would be another benefit of running Ubuntu versus Windows XP at least since one would not need to install drivers through the F6 entry. 

I'm not sure why this feature couldn't be included in Feisty, but hopefully Hardy will include it.

---

### Post by bethaviv on 2007-10-19
> **Flashstar said:**
> Once again, I am bringing up an important issue which has prevented me (and surely numerous others) from running Ubuntu for at least a year. The big problem is that software RAID of any type can only be activated through the alternative CD and even then one must go through guides online to figure out how to get it to work. 

I propose a simple entry in the graphical installer which can easily support using two separate disks in a RAID 0 or RAID 1 array. I believe that Fedora has such a feature enabled for much time now. This feature could support purely software RAID, hardware assisted, or a combination of the two. 

Such a feature would be beneficial to numerous people and would be another benefit of running Ubuntu versus Windows XP at least since one would not need to install drivers through the F6 entry. 

I'm not sure why this feature couldn't be included in Feisty, but hopefully Hardy will include it.

I have two raptors in RAID 0 for Vista and I would rather use them for Ubuntu and move Vista over to a different hdd since I find myself using Ubuntu way more often.

---

### Post by dagrump on 2007-10-19
Yes, please raid is a pain @ this point. It would be nice if this could be simplified, I have messed up many times attempting to configure a raid array.

---

### Post by autocrosser on 2007-10-19
I have posted another part of the disk utility needs--  [http://ubuntuforums.org/showthread.php?t=580757](http://ubuntuforums.org/showthread.php?t=580757)

The OSX Disk Utility has the ability to do raid creation & I think that we all should request a utility that can partition, edit fstab, label & create raid(s).

Please add your thoughts to the other post --I've contacted the developer for Disk Manager & will refer him to this post also.....

---

### Post by elvis on 2007-10-20
Just a few points:

1) Linux software RAID (or "MD RAID") can only support RAID1 mirror for the /boot partition.  /boot will never exist on RAID0, RAID5 or any other striping system simply because the Linux kernel (and modules) need to be loaded so that it can "understand" a striped RAID set.  With a RAID1 mirror, the system can boot off one disk, and add the second mirror in after /boot is mounted and read.

2) RAID controllers come in two sorts.  Essentially these can be broken down to "good" controllers (true hardware RAID controllers that appear to the system as SCSI devices and do all RAID calculations on their own custom on-card CPU), and "bad" controllers (usually cheap, nasty sub-$200 controller cards or onboard RAID devices that offload RAID processing to the main CPU via a driver).

The first kind ("good" hardware controllers) are already well supported under Linux.  Most of the big-name controllers from people like Adaptec, 3Ware, LSI and Intel all work perfectly already.

The second kind ("bad" cheap/onboard controllers) generally don't work.  Why?  Simple because the people who make them continue to refuse to open up either specs of the devices, and/or the drivers themselves to the Linux community.

On top of that, these cheap onboard RAID controllers frequently don't offer the realtime support that Linux's own software/MD RAID system does.  WIth MD RAID you can do many, MANY more things in real time (both monitoring and administration/changing of RAID volumes).  You can be quite certain also that Linux's software/MD RAID will give you the same or better performance than a cheap onboard RAID controller, as both use the system CPU anyway, but the Linux software RAID system enables far better customization of how fast the RAID devices rebuild in the event of a failure, and better support for adding in new/different devices in real time (no reboots needed, assuming you are running RAID1/5/10/15 where the system can continue to operate even with a disk blown).

My advice to anyone seeking RAID support under Ubuntu (or Linux in general) is either

1) Use a real RAID controller, and not a cheap and nasty pretend one.  Or

2) Turn off those crap onboard RAID controllers, use the SATA ports as plain old SATA, and use Linux MD RAID instead.  Just ensure that your /boot partition is either a single, standalone disk, or a RAID1 mirror.  All other partitions (including /, /home. /usr, /var or anything else you like) can be any RAID set you wish.  Although I do recommend /etc is also on a RAID1 mirror, based from personal experience with disks blowing up.  It makes data retrieval a whole bunch easier.

With all of that said, Linux software/MD RAID options are still only available on the alternate CD.  Truth be told, they are not difficult to set up if you know what you are doing.  The biggest mistake I see people make is trying to set up /boot (or having a single / partition with /boot underneath) as a RAID5 volume, and wondering why their system fails.  You need to understand what the RAID subsystem is doing before you try and build one.

Seeing Linux software/MD RAID make it to the LiveCD GUI installer would be a good idea.  My only recommendation is that the Ubuntu team provide some sort of 1-click "set up my system with RAID for me" button where it automatically sets up a separate /boot partition on a RAID1 mirror, and the rest of the system under whatever RAID level the user desires.

But it is important to realize that setting up RAID does require a little bit of user smarts.  Many of the questions/complaints I read about RAID (both in this thread as well as in other threads/forums) can all be attributed to users not fully understanding the various RAID systems out there, and not the fact that Linux RAID itself is non-functional (because it is quite functional, says me using it in large-scale commercial production).

---

### Post by jaygo on 2007-10-20
+1
As an experienced PC tech and a linux noob, it took me about 40 hours of experimenting (with various guides) to get a RAID 0 setup. Well, I never managed to do it with the guides' methods as they were all about RAID 1 or 5 ... so I finally installed fedora. They have a very nice installer that made it very easy. Probably not as easy as OS X, but easy enough for half of us raid-hungry ubunteros.

Shortly afterwards, I found out that kubuntu has an alternate CD and reinstalled with that. It's not that intuitive but only took a bit of playing to figure it out and now it's ridiculously easy to set up raid. 

The problem is, it should be in the GUI installer. I imagine the only reason it's not already is that no one has put the time in. Any place we can vote for features around here?

> **elvis said:**
> 
But it is important to realize that setting up RAID does require a little bit of user smarts. 

While that's true, it doesn't need to stay that way. An easy-as-pie raid 1 install option (with a matching, easy-as-pie raid alert utility) could benefit a lot of novice users.

---

### Post by chrisccoulson on 2007-10-20
> **elvis said:**
> Just a few points:

The second kind ("bad" cheap/onboard controllers) generally don't work.  Why?  Simple because the people who make them continue to refuse to open up either specs of the devices, and/or the drivers themselves to the Linux community.

I've been using one of these 'bad' controllers since Breezy, with zero issues.

> /boot will never exist on RAID0

I have /boot on RAID0 with one of these 'bad' controllers.

> My advice to anyone seeking RAID support under Ubuntu (or Linux in general) is either

1) Use a real RAID controller, and not a cheap and nasty pretend one. 

Why, when I can do it using the stuff onboard my motherboard?

> 2) Turn off those crap onboard RAID controllers, use the SATA ports as plain old SATA, and use Linux MD RAID instead. Just ensure that your /boot partition is either a single, standalone disk, or a RAID1 mirror. All other partitions (including /, /home. /usr, /var or anything else you like) can be any RAID set you wish. Although I do recommend /etc is also on a RAID1 mirror, based from personal experience with disks blowing up. It makes data retrieval a whole bunch easier.

How do you propose I do a dual-boot with Windows using MDRAID? The fact is, these 'bad' controllers, or FakeRAID or whatever we like to call them are available on nearly every motherboard on sale now, so we can't just ignore them.

---

### Post by Vinas on 2007-10-20
> **elvis said:**
> Just a few points:
1) Use a real RAID controller, and not a cheap and nasty pretend one.  Or

Wrong answer. Maybe in the Ubuntu story we could put "2007, the year that elvis refused to load good raid support for cheap onboard raid controllers". Really I understand your frustration and reasoning for not really *wanting* to support these devices. Reality is that we must add support because the main players like nVIDIA, intel, and AMD are going to keep manufacturing these devices into their motherboards and chipsets. It works for most workstations and it's on the cheap! I agree maybe these fakeraid controllers shouldn't be used in server class machines, but again for workstations a person can achieve 120MBs in raid0 fakeraid. That's a valuable performance factor for people who maybe already have a EMC SAN that they back up to. The point is I think you're missing the real reason people actually use these devices. Since they ARE indeed using them I think it's smart for the community to at least keep up with Fedora in support of fakeraid devices. Let alone vista.

---

### Post by chrisccoulson on 2007-10-20
> **Vinas said:**
> Since they ARE indeed using them I think it's smart for the community to at least keep up with Fedora in support of fakeraid devices. Let alone vista.

I agree with this! The reality is, people do use them, and they aren't going to go away. It would be silly to just ignore them on the basis that a few people think they aren't very good.

---

### Post by Zdravko on 2007-10-20
Nice idea, but I don't know whether I will benefit from it...

---

### Post by Flashstar on 2007-10-20
For me as well as 99% of other prospective Linux RAID users, DMRaid or MDRaid doesn't really matter. What matters is that it works and that it's easy the set up a RAID array with the graphical installer. So, if we must stick to purely software RAID, then by all means do.

---

### Post by elvis on 2007-10-20
> **Vinas said:**
> Wrong answer. Maybe in the Ubuntu story we could put "2007, the year that elvis refused to load good raid support for cheap onboard raid controllers".

This has nothing to do with me.  This has everything to do with hardware manufacturers choosing not to support Linux with free drivers.

"FakeRAID" needs good driver support to work, end of story.  This either means requesting hardware manufacturers release either free drivers or at least specifications so that the free software community can write their own, or reverse-engineering existing systems to make free drivers.

And none of these things belong in the Hardy Heron Ideas thread.  It has very little to do with the Ubuntu team, and quite frankly is way out of their realm.  They have their hands full already.  You would have much better luck either approaching your preferred hardware manufacturer yourself, or chatting with some of the kernel developers on their mailing lists and seeing what you can do to help (and yes, even if you're not a programmer you CAN help).

> **chrisccoulson said:**
> I've been using one of these 'bad' controllers since Breezy, with zero issues.

I have /boot on RAID0 with one of these 'bad' controllers.
You are lucky, and in the minority of users with a supported controller. (And very silly, putting /boot on a RAID0 stripe, as once the kernel is loaded it's never touched again, and you're putting your data integrity at risk for next to no gain).

For the record, what chipset does your controller use?  Perhaps you could add some constructive feedback to this thread and help others by actually telling them what hardware works for you.  These "it works for me" comments don't help anyone if you don't expand on the technical details.

Recommending hardware that works has two benefits:

1) You're helping your fellow Linux users

2) Most hardware manufacturers listen only to sales numbers.  If a bulk amount of Linux users go out and buy a particular motherboard/RAID controller because of it's known support for Linux, hardware manufacturers will gleefully listen to sales figures, and actively choose chipsets that make them the most profit.

> **chrisccoulson said:**
> How do you propose I do a dual-boot with Windows using MDRAID?
I propose you stop using toy operating systems with limiting features and poor security.  I'm personally not interested in supporting Windows nor its users, so I'm afraid that question doesn't garner any sympathy from me.  (For the record, I used to support Windows and Windows users professionally.  Decades of frustration and seeing customers treated like thieves and second-rate citizens made me realize there are much better alternatives out there, hence why I am here posting in a Linux forum).

> **chrisccoulson said:**
>  The fact is, these 'bad' controllers, or FakeRAID or whatever we like to call them are available on nearly every motherboard on sale now, so we can't just ignore them.
I agree - we certainly can't ignore them.  But as mentioned at the top of this post, without free/open driver support, there's nothing the Ubuntu team nor any other distro can do.  Jumping up and down about it in this thread isn't going to gain you any ground in this quest.

And again, the Ubuntu forums and especially the Hardy Heron Ideas Pool is not a place that airing such grievances will help the cause.

You need to be organizing large groups of people - private citizens, corporates and others - to be lobbying hardware manufacturers to release specifications and/or code freely to the free/open-source software community. 

THAT is the only way you'll get real support.

And even then, once support is available, building RAID sets will not be a part of the Ubuntu installer.  They'll be handled by the card BIOS utilities on the RAID cards themselves, and the logical drives exported to the system as SCSI devices.  So the whole issue of install-time RAID setup regarding Hardy Heron's GUI installer is completely void if you're only focus is using third-party RAID controllers, and not using Linux's own kernel software RAID.

If install-time simplified RAID setup is what you want (and indeed, is the TOPIC OF THIS THREAD), then it will need to be Linux Software/MD RAID.

If driver support for "FakeRAID" cards is your desire, hop on the Linux Kernel mailing lists and chat with the developers there to see what you can do to make it happen.

---

### Post by chrisccoulson on 2007-10-20
> And very silly, putting /boot on a RAID0 stripe, as once the kernel is loaded it's never touched again, and you're putting your data integrity at risk for next to no gain

Very true. But not putting /boot on a RAID 0 stripe would require an extra physical disk, which isn't worth it for me.

> For the record, what chipset does your controller use? Perhaps you could add some constructive feedback to this thread and help others by actually telling them what hardware works for you. These "it works for me" comments don't help anyone if you don't expand on the technical details.

My motherboard uses the NVIDIA chipset, which is luckily well supported, as are quite a few others. And, there is quite a good wiki detailing how to set up DMRAID, which I have contributed a small amount to.

> I propose you stop using toy operating systems with limiting features and poor security. I'm personally not interested in supporting Windows nor its users, so I'm afraid that question doesn't garner any sympathy from me. (For the record, I used to support Windows and Windows users professionally. Decades of frustration and seeing customers treated like thieves and second-rate citizens made me realize there are much better alternatives out there, hence why I am here posting in a Linux forum).

I play games, so I don't have much of an option. For the record, thats all I use Windows for, and thats all I have used Windows for since Breezy. And I don't think that having to dual-boot puts me in a minority either.

> I agree - we certainly can't ignore them. But as mentioned at the top of this post, without free/open driver support, there's nothing the Ubuntu team nor any other distro can do. Jumping up and down about it in this thread isn't going to gain you any ground in this quest.

I think you might be missing the point of the original suggestion. There is already quite good support for these FakeRAID controllers. But the Ubuntu installer doesn't support them out of the box, and you have to jump through hoops to install Ubuntu on to an array.

> And even then, once support is available, building RAID sets will not be a part of the Ubuntu installer. They'll be handled by the card BIOS utilities on the RAID cards themselves, and the logical drives exported to the system as SCSI devices. So the whole issue of install-time RAID setup regarding Hardy Heron's GUI installer is completely void if you're only focus is using third-party RAID controllers, and not using Linux's own kernel software RAID.

Correct, but the installer should be able to partition the FakeRAID array, install to it, and set up GRUB on it, without having to jump through hoops.

> If driver support for "FakeRAID" cards is your desire, hop on the Linux Kernel mailing lists and chat with the developers there to see what you can do to make it happen.

If I thought it would help, I would. But, unfortunately, I'm not all that knowledgeable with software and probably wouldn't be able to offer that much.

I've just found a spec for this as well (originally proposed for Feisty I think)
[https://wiki.ubuntu.com/FakeRaidSpec]("https://wiki.ubuntu.com/FakeRaidSpec")

---

### Post by elvis on 2007-10-20
> **chrisccoulson said:**
> Very true. But not putting /boot on a RAID 0 stripe would require an extra physical disk, which isn't worth it for me.
Your controller doesn't support multiple RAID levels on a single disk?

Linux's software RAID allows you to RAID at a partition level as well as at a device level.  You can buy 2 physical disks, have /boot as RAID1, and the rest of your system at RAID0 if you like - different RAID levels on the same physical disks.

For most of the locations I admin, I use a combination of /boot on RAID1 mirrored across all active drives (even if that's 8+ drives - /boot only needs to be 100MB or so, not even that if you only ever use the default boot images provided by Ubuntu), and the rest of the system on RAID5 or 6.  Again, I find Linux's own software RAID more often than not provides you with more options than many cheap hardware RAID systems.  To find the same functionality in hardware devices, you often need to spend thousands of dollars on very high-end controllers (which, of note, generally also work "out of the box" with Ubuntu).

Likewise, I can get realtime per-disk reporting from /proc/mdstat with Linux's software RAID, which is infinitely better than most of the reporting tools provided by most RAID card manufacturers (I can get reporting from tools like Nagios as well, thanks to that - which means I can have systems alert me by IM/Jabber/email/SMS if they have RAID device failure).

And finally, if my motherboard blows up, I can take a Linux software RAID disk and slap it in any other system, bring the RAID set up and recover my data.  Conversely if I'm using a proprietary RAID card or motherboard, if the RAID devices blow I often need to find exactly the same card with exactly the same firmware to resurrect my data.  Similarly some won't even allow you to do that much!

> **chrisccoulson said:**
> I think you might be missing the point of the original suggestion. There is already quite good support for these FakeRAID controllers. But the Ubuntu installer doesn't support them out of the box, and you have to jump through hoops to install Ubuntu on to an array.
There's a very good reason for that - many of the drivers supplied are non-free/proprietary/closed-source.  

As I keep saying, if driver manufacturers will not open the source/specs of their devices up, or release them under licenses incompatible with the Linux kernel, what you will find is "support" for these devices under Linux (especially at boot time) will be lacking.

The single best way to have RAID (or any driver controller) devices supported is to get that source code merged into the Linux kernel tree, and if necessary into the GRUB source tree as well.  For this to happen, non-free/closed/proprietary drivers cannot be the answer.  Once again, you need to approach the driver manufacturers for your devices and demand that their drivers be freed.  Anything less will ensure you will never get the boot-time support you desire.

For the record, the Ubuntu team already do their fair share of lobbying hardware developers to open up their drivers and specifications.  So do a lot of other distro authors such as Debian and RedHat, as well as BSD folk like the FreeBSD and OpenBSD teams.  All of these teams would be willing to take any help you can provide, even if it's just another voice pressuring hardware manufacturers for the same things.

---

### Post by Zdravko on 2007-10-21
Can someone tell here the amount of Ubuntu users (in percentage) who have RAID system.

---

