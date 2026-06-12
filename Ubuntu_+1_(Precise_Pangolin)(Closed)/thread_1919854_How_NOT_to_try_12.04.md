---
title: "How NOT to try 12.04"
date: 2012-02-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by anewguy on 2012-02-03
I thought "hey, let's try this 12.04 out.  Surely by now the bugs are worked out - I mean April release is only about 2 months away."  So, I downloaded the ISO and burned a DVD - 64 bit version.  I boot up and try the install - against everything I've ever "preached" or practiced, I decide to be lazy and "just" do an upgrade, thus preserving my /home partition - and hey, who needs to back up right this instant?

Well, the upgrade went partway in, then hung.  We're talking 20 minutes doing nothing.  So I went to a terminal window and requested a reboot.  The reboot started, but grub wouldn't work - apparently somehow my root partition got hosed in this supposed upgrade only.  So I try the install again - it aborts with some stupid error that's been on launchpad for quite a while, and apparently not fixed.  It keeps telling me my disk is hosed.  So it boots up the "try ubuntu" instead and tells me to run disk utility to clean up my partitions.  I run disk utility and blow away only the root partition considering it shouldn't have touched my /home partition yet.

Reboot trying the install again - fails again but with a different error.  This one also has been on launchpad for quite a while and apparently not fixed either.  Mind you, both of these deal with just trying to INSTALL 12.04.  I have no way of knowing what happens if you get lucky enough for 12.04 to install.

The end result is that I lost *ALL* of the partitions off my disk and had to reinstall everything.  Everything from /home gone (and hey, who needs to back up right this instance ;) ).

So, I grab the only other CD I could find handy - 11.10 64-bit, and install it.

End result - wanted to try 12.04 but couldn't even install it.  Instead I lost everything on my PC.  Not a happy camper.

So, I do have a question:

- besides the obvious backup thing, why is 12.04 aborting in the installation phase this late in the game?  Since this means a lack of testing, it means people like myself need to do something to be sure it doesn't happen again.  So, I assume there is a lack of testers.  What is the official policy for:

- becoming a tester
- deciding a release has really been through enough testing

I ask this because I've felt in the last couple of releases that not enough was done to test some very basic things - people were reporting problems on using 11.04 and 11.10 - not kernel or driver problems for the most part (at least that is getting better), but instead common usage things like flashplayer, etc..  I know these aren't Ubuntu products, however with their widespread daily use it would seem to me that before the release is released it should at least be able to run those things as well.  I won't say sloppy - instead my experience in the field tells me "rushed", like in rushed to meet the release date.

I doubt I'm the only one who would gladly wait on a release if it means a more clean delivered product.

So, what can I do, and how, to help this for the next release?  I don't do much at all, REALLY simple things.  But, if that can help in the testing, or if specific tasks are handed out in the testing I would be glad to help, as I suspect others might if we understood the process better and if we knew that the average user could help.

Anything to avoid possible tangles with my stupidity ;)

Dave ;)

---

### Post by wolfen69 on 2012-02-03
> **anewguy said:**
> 
End result - wanted to try 12.04 but couldn't even install it.  Instead I lost everything on my PC.  Not a happy camper.



You don't believe in backups I can see. ;)

Secondly, this thread should probably be in the Ubuntu +1 (precise) section, and is not fit for the absolute beginners section. 

Thirdly, I always do fresh installs after BACKING UP! But I can't get the daily image live cd of 12.04 to install. But I realize there is a ways to go before 12.04 will be usable for most people. You probably should have just used a spare hard drive, or vbox for testing.

---

### Post by Hedgehog1 on 2012-02-03
kansasnoob has been doing a most of the heavy lifting testing ISOs.

[http://ubuntuforums.org/showthread.php?t=1918537]("http://ubuntuforums.org/showthread.php?t=1918537")

You will find the folks testing it in the Ubuntu +1 (Precise Pangolin) area:

[http://ubuntuforums.org/forumdisplay.php?f=412]("http://ubuntuforums.org/forumdisplay.php?f=412")

However, what you did was rather risky/foolish (as you have already made reference too).

The upgrade process is one of the hardest things to get right.  At an alpha level it has not matured yet.

Not backing up the data, well,  "No soup for you for 2 weeks!" :KS

Jump in at the Ubuntu +1 forum and see what you have been missing.


***The Hedge***

:KS

---

### Post by lisati on 2012-02-03
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by Hedgehog1 on 2012-02-03
> **wolfen69 said:**
> You don't believe in backups I can see. ;)


Events like this make us believe in backups.

:KS

---

### Post by Penguinnerd on 2012-02-03
1) Always back up data. I usually do a backup every 1-2 weeks, as well as when I do anything with partitions or OS installations.

2) It's in Alpha. That's not "late in the game". When you consider that one of these releases happens every 6 months, it's hardly surprising. They don't call it "Alpha" or "Beta" for nothing.

It's a hard lesson to learn. Installing or upgrading to Alpha-quality software is like playing with fire. Always expect the worst, and you usually won't be disappointed.

I'm waiting for Beta to "try it out".

---

### Post by nm_geo on 2012-02-03
> **Hedgehog1 said:**
> Events like this make us believe in backups.
 
:KS
 
Hey hedge.. You be correct that is why I make a Clonezilla clone of my harddrive on about a weekly basis and always before I try a fresh install.  My take has been that Ubquity has caused me lots of problems on installs and the alternate iso works better for me.  However when we are testing it is best to test installs that the newer users will be using.

---

### Post by wolfen69 on 2012-02-03
> **Penguinnerd said:**
> 
I'm waiting for Beta to "try it out".

I'm just waiting for a daily image that will install on my laptop. But usually late alphas, or early betas are good enough to install and use. I no longer have my desktop and can't just switch out drives easily, so I guess I'll have to try and use an external drive for now. When it will install that is.

---

### Post by anewguy on 2012-02-03
Yeah, I really am smarter than the no-backups thing, even though this makes 2 times in a row I've done something so stupid. ;)

As far as alpha goes, I come from the mainframe down to micros technical background, dealing with the OS.  In the mainframe land, by 2 months prior to release everything would be pretty much bug-free, with just the final tweaking going on.  This is why I mentioned that I would rather wait longer for a more polished release than ones that are rushed to meet an every 6 months deadline.

I'm also serious about wanting to help, not just complain!  We all know about all of this being voluntary, so the more testers the better.  It provides for a more diverse hardware base to test as well as usage base to test.  I'm just not anywhere near being an expert, and I thought perhaps there was a list of things to test, conditions to test them in, QC tests brought forward from previous releases to be sure nothing broke, etc., and I guess I just always thought this was more for the gurus.  In the mainframe world I was one of those, but in Linux I'm just your average (perhaps even below average!) putz.

So, I know I made some serious mistakes -as I mentioned in my post.  But.....there were most definitely some bugs, and some apparent big ones at that since I couldn't even install and lost everything.

I also don't want to be one to just bitch - so whoever needs help in some phase of the testing, that can give me some guidance on what to test and how, please contact me!

thanks guys - I know you take my know-better-than screwups as they are meant -> amusement.  I really do know better and just sort of shot in the dark this time. ;)

Dave ;)

---

### Post by ronacc on 2012-02-03
The installer crashes are unusual for an A2 but they obviously can happen so as noted by others backups are necessary . There are several ways you can minimize the damage , One is if you already have a working grub in the mbr tell the installer ( ubiquity) to put grub in the partition you are installing to rather than the mbr and then either boot off of the partition if yoyr bios allows that or just boot into the install that wrote the mbr and run ```
 sudo update-grub 
``` and it will add your new install to its grub . Another way is to install to a separate drive altogether ( if you have one ) and have the installer put grub on the mbr of that drive and just change your bios to boot that drive . Either of those methods should protect you against all but the worst disasters .

---

### Post by QIII on 2012-02-03
Sheesh!

I bet NONE of us has EVER done something stupid like THAT!

Loser!  

;)

---

### Post by kurt18947 on 2012-02-03
Precise's installer does have ..... 'issues'. I tried to install a daily about a week ago via DVD and it would abort even after trying different drives and disks.  I installed an earlier daily then updated it.  Precise really seems pretty mature once it's running.

---

### Post by grahammechanical on 2012-02-03
I see this:

> I decide to be lazy and "just" do an upgrade,

Could it be that the iso image is not yet ready to be used to upgrade an existing install?

My advice to anyone whether they want to test Ubuntu+1 or move up to the next release is to create a spare partition and install into that to make sure that everything can be set up the way you want before upgrading or fresh installing over the Ubuntu you already have.

I am not speaking from a having a bad experience but based on hearing about the changes that were being made between 10.10 & 11.04 and onwards.

The other week I did something stupid on my 12.04 system and I had to re-install. Importantly, I did not mess up my 11.10 install or my data which I have on a /home partition. I will not upgrade my 11.10 to 12.04 until the middle to end of the month of May. I let the rush die down.

I have been using 12.04 since before alpha 1 and I find it so stable that I now use it for doing my daily work. but, remember, my data is not on the 12.04 partition.

I am glad that you want to help test. let us see if we can find some information.

Have a read of this:

[https://wiki.ubuntu.com/MeetingLogs/devweek1201/RunningTheDevRelease]("https://wiki.ubuntu.com/MeetingLogs/devweek1201/RunningTheDevRelease")

It is the log of an irc session from just the other day.

And these links:

[https://wiki.ubuntu.com/Testing]("https://wiki.ubuntu.com/Testing")

[https://wiki.ubuntu.com/Testing/Activities]("https://wiki.ubuntu.com/Testing/Activities")

[http://testcases.qa.ubuntu.com/]("http://testcases.qa.ubuntu.com/")

Or simply start off by installing 12.04 on a spare partition and start using it. There is one thing that you should be ready for. When 12.04 is released a lot of people will upgrade to it. Many of them will be migrating from 10.04 or 10.10, (There are changes even between 11.10 and 12.04) and the look of the desktop will be unfamiliar to them. So, get to know 12.04 and when people start asking for help on this forum, jump right in and offer advice.

Regards.

---

### Post by cariboo on 2012-02-03
I tried doing an install with the alpha 2 iso after the release yesterday, it crashed while detecting the disk in my system twice. I ended up using the alternate install iso instead.

---

### Post by fjgaude on 2012-02-03
> **cariboo907 said:**
> I tried doing an install with the alpha 2 iso after the release yesterday, it crashed while detecting the disk in my system twice. I ended up using the alternate install iso instead.

Same for me, but today the Daily Build worked like a charm. There is lots still wrong with the installer and drives and partitions. It seems to work only for the defaults, still it is a complex piece of work, and a thank you to the guy who is perfecting it.

---

### Post by effenberg0x0 on 2012-02-03
> **grahammechanical said:**
> I see this:
Have a read of this:
[https://wiki.ubuntu.com/MeetingLogs/devweek1201/RunningTheDevRelease](https://wiki.ubuntu.com/MeetingLogs/devweek1201/RunningTheDevRelease)


A complete/properly formatted ODT version is here: [http://ubuntuforums.org/showpost.php?p=11659374&postcount=12](http://ubuntuforums.org/showpost.php?p=11659374&postcount=12)

> **cariboo907 said:**
> I tried doing an install with the alpha 2 iso after the release yesterday, it crashed while detecting the disk in my system twice. I ended up using the alternate install iso instead.

I wonder whats going on... I made 3 fresh installs in real machines and also 2 VM installs succesfully. 
Also, if QA ISO-Testing had seen such errors, they wouldn't have released it. 

It's got to be something really specific and particular to some hardware, system config, previous partitioning (wouldn't be new to us), etc.

> **anewguy said:**
> 
Well, the upgrade went partway in, then hung. We're talking 20 minutes doing nothing. 

This is not new and as far as I can remember was related to previous partitioning.

> **anewguy said:**
> 
The end result is that I lost *ALL* of the partitions off my disk and had to reinstall everything. Everything from /home gone (and hey, who needs to back up right this instance ).

This shouldn't happen. If possible, it would be nice to know which errors and launchpad reports were mentioned in this whole post. 

> **anewguy said:**
> 
So, I do have a question:

- besides the obvious backup thing, why is 12.04 aborting in the installation phase this late in the game? Since this means a lack of testing, it means people like myself need to do something to be sure it doesn't happen again. So, I assume there is a lack of testers. What is the official policy for:

- becoming a tester
- deciding a release has really been through enough testing

I ask this because I've felt in the last couple of releases that not enough was done to test some very basic things - people were reporting problems on using 11.04 and 11.10 - not kernel or driver problems for the most part (at least that is getting better), but instead common usage things like flashplayer, etc.. I know these aren't Ubuntu products, however with their widespread daily use it would seem to me that before the release is released it should at least be able to run those things as well. I won't say sloppy - instead my experience in the field tells me "rushed", like in rushed to meet the release date.

I doubt I'm the only one who would gladly wait on a release if it means a more clean delivered product.

So, what can I do, and how, to help this for the next release? I don't do much at all, REALLY simple things. But, if that can help in the testing, or if specific tasks are handed out in the testing I would be glad to help, as I suspect others might if we understood the process better and if we knew that the average user could help.


There are links to QA and ISO-Testing in my post #3 here: [http://ubuntuforums.org/showthread.php?t=1918537](http://ubuntuforums.org/showthread.php?t=1918537)

QA sure can use the help, I'm volunteering too. But, IMHO, most of these bugs are reported. My question is: Why some of these bugs are there since Oneiric pre-alpha? Do we need better triaging, to find relevant bugs and classify them with the proper importance? Or do we need more people to talk upstream? My personal opinion is that current triaging, bug tagging, etc is simply irresponsible. Efforts to provide training and testing/"certification" of current bug management people seem vital. And we also need to find new users interested in QA and educate them to create proper reports and do useful triaging. 

Regards,
Effenberg

[B]EDIT:
[/B]Remember this? (From [https://wiki.ubuntu.com/PlusOneMaintenanceTeam/Specs/Priorities](https://wiki.ubuntu.com/PlusOneMaintenanceTeam/Specs/Priorities))
> ...with the goal of keeping the development release buildable, installable,  and upgradeable at all times in order to allow other developers to work  with fewer interruptions.
So... It's a priority.

---

### Post by anewguy on 2012-02-03
Glad to at least see that others have had problems with the installer.

My posts may seem contrary, but I really do know better than to do what I did.  I just got lazy and said the heck with it.  I was going to go the additional partitions route so I'd have room for testing afterwards as well, was going to do backups (while inconvenient, still not a disaster at home as it would have been at work), etc., etc., etc. - I literally decided at the last minute just to go for it, and to try the upgrade once.  I have long been an advocate of fresh installs and not upgrades, and I almost wish it was the standard and that the upgrade path was removed.  Again, this time I just said the heck with it and gave it a try.

So, while I appreciate any/all advice, please be aware I normally do things differently, was aware of the "dangers" going in, and just did something different for me for once ;)

Now the testing of a new release - now that I know about this forum, I'll try to get involved in some way.

I realize that the Beginners Forum is for beginners, but some of us just sort of hang out there.  When a release has been released, such as in April, it might be a good idea none the less to add a sticky for a couple of weeks about getting involved in the testing for the next release, with a link to this forum (or whatever the 12.10 forum will be/is called).  Since there is always someone to filter out who is qualified or not to help on testing, it may provide a larger pool of testers.

Anyway, just wanted to say thanks, I know I was doing something stupid going in and went for it anyway, and none the less for the suggestions.

Just trying to make fun of myself I guess!

Dave ;)

---

### Post by kevpan815 on 2012-02-03
> **cariboo907 said:**
> I tried doing an install with the alpha 2 iso after the release yesterday, it crashed while detecting the disk in my system twice. I ended up using the alternate install iso instead.

cariboo907: I always use the Debian AMD64 Alternate CD Image and I never use the Ubuntu AMD64 Desktop Installer for the following reason: the Ubuntu Desktop Installer has been modified way too much over the last couple of years and I no longer consider it trustworthy.

---

### Post by cariboo on 2012-02-03
> **kevpan815 said:**
> cariboo907: I always use the Debian AMD64 Alternate CD Image and I never use the Ubuntu AMD64 Desktop Installer for the following reason: the Ubuntu Desktop Installer has been modified way too much over the last couple of years and I no longer consider it trustworthy.

I've used the Live CD to install Ubuntu dozens of times, this is the first time in 2 or 3 years that I've had an outright failure. The last time was because the installer wouldn't detect the drives on a system that only had SATA drives connected to it. The system I'm using now has a mix of SATA & PATA drives, that may be the reason for the failure.

I was a little bit busy this time around for iso testing, but I will participate when it comes time to test the beta iso's.

---

### Post by arpanaut on 2012-02-03
> Just trying to make fun of myself I guess!

Dave :wink:Sometimes you gotta laugh at yourself,
to keep from crying.

Just a couple of weeks ago my trusty old testing rig blew a power supply and I was in a panic
until I was able to pull the hard drives and check to make sure the HDD's didn't get scorched too.
Luckily all data was intact and amazingly the motherboard came back to life with a new power supply.
It was a tense couple of days until I had time to get on with data recovery.

Needless to say NOW my data drive is backed up on three different rigs and on a usb external.
I just hate that feeling in the pit of the stomach... Oh no it's gone!

Lesson learned, I hope for you too.
Sorry about your loss.

EDIT: Yup the daily live installer has been very hit or miss this cycle,
but just a little more so than previous testing.
But once installed, it has been pretty stellar for stability. <famouslastwords> :biggrin:

---

### Post by elliotn on 2012-02-04
I downloaded mine in the 1st and created a 25gb partition and install it, got messy and reinstalled 2 more times and now it works perfect, I got few system errors popups but not harmful, am yet to update

---

### Post by kansasnoob on 2012-02-04
In post #16 effenberg0x0 said;

> Also, if QA ISO-Testing had seen such errors, they wouldn't have released it.


As an **independent** iso-tester I tried to delay the release of Precise Alpha 2. I decided to try and pull the plug when I figured out that the Lubuntu live image was offering a "unity-like" DE which would have been a total misrepresentation of the direction Lubuntu is taking.

But even prior to that I was very concerned. I was using two different PC's for iso-testing, which didn't begin until Tuesday allowing 48 hours at best for testing. Considering that I test Ubuntu i386 live, Lubuntu i386 live, and the Lubuntu i386 alternate image that's not much time :(

There were also a number of rebuilds and things were so buggy, and in some cases just confusing, that this round of testing just totally kicked my butt! This was partly my own fault, as much as I'd tried to be prepared a number of things simply caught me off guard.

Regardless I was partly successful as no Lubuntu live images were released, but I'd actually wanted the whole release just delayed for at least 24 hours. I did my best, but I was really off my game this time :redface:

---

### Post by kansasnoob on 2012-02-04
> **anewguy said:**
> I thought "hey, let's try this 12.04 out.  Surely by now the bugs are worked out - I mean April release is only about 2 months away."  So, I downloaded the ISO and burned a DVD - 64 bit version.  I boot up and try the install - against everything I've ever "preached" or practiced, I decide to be lazy and "just" do an upgrade, thus preserving my /home partition - and hey, who needs to back up right this instant?

Well, the upgrade went partway in, then hung.  We're talking 20 minutes doing nothing.  So I went to a terminal window and requested a reboot.  The reboot started, but grub wouldn't work - apparently somehow my root partition got hosed in this supposed upgrade only.  So I try the install again - it aborts with some stupid error that's been on launchpad for quite a while, and apparently not fixed.  It keeps telling me my disk is hosed.  So it boots up the "try ubuntu" instead and tells me to run disk utility to clean up my partitions.  I run disk utility and blow away only the root partition considering it shouldn't have touched my /home partition yet.

Reboot trying the install again - fails again but with a different error.  This one also has been on launchpad for quite a while and apparently not fixed either.  Mind you, both of these deal with just trying to INSTALL 12.04.  I have no way of knowing what happens if you get lucky enough for 12.04 to install.

The end result is that I lost *ALL* of the partitions off my disk and had to reinstall everything.  Everything from /home gone (and hey, who needs to back up right this instance ;) ).

So, I grab the only other CD I could find handy - 11.10 64-bit, and install it.

End result - wanted to try 12.04 but couldn't even install it.  Instead I lost everything on my PC.  Not a happy camper.

So, I do have a question:

- besides the obvious backup thing, why is 12.04 aborting in the installation phase this late in the game?  Since this means a lack of testing, it means people like myself need to do something to be sure it doesn't happen again.  So, I assume there is a lack of testers.  What is the official policy for:

- becoming a tester
- deciding a release has really been through enough testing

I ask this because I've felt in the last couple of releases that not enough was done to test some very basic things - people were reporting problems on using 11.04 and 11.10 - not kernel or driver problems for the most part (at least that is getting better), but instead common usage things like flashplayer, etc..  I know these aren't Ubuntu products, however with their widespread daily use it would seem to me that before the release is released it should at least be able to run those things as well.  I won't say sloppy - instead my experience in the field tells me "rushed", like in rushed to meet the release date.

I doubt I'm the only one who would gladly wait on a release if it means a more clean delivered product.

So, what can I do, and how, to help this for the next release?  I don't do much at all, REALLY simple things.  But, if that can help in the testing, or if specific tasks are handed out in the testing I would be glad to help, as I suspect others might if we understood the process better and if we knew that the average user could help.

Anything to avoid possible tangles with my stupidity ;)

Dave ;)

I have some suggestions but I'm busy ATM. In the meanwhile it would help to know a couple of things:

(1) Do you have a spare computer?

(2) Do you have a spare hard drive and the knowledge to swap hard drives in your computer? (I might add, are you aware of anti-static safeguards?)

You already know that the one time you're not prepared for data loss is the time you'll wish you had been so I'm not going to rub salt in the wound :)

I've hosed things I wish I hadn't more than once :(

---

### Post by jerrylamos on 2012-02-04
Retired here, testing just for fun, on a tower, a netbook, a notebook, and two USB hard drives.  A couple days ago "sudo update-grub" "sudo grub-install" hosed boot capability on the notebook Acer Aspire 5253 Windoze 7, the netbook Acer Aspire1 Windoze 7, and both USB hard drives.  You'd think I'd learn..  

Recovered the 5253 with Boot-Repair.  It's the most serious, sudo grub-install destroys boot record from about Narwhal on.  All I get is a purple screen with 4 columns of faint black lines at the top.  Yes I wrote a launchpad bug.  My guess, the grub-installed code does not recognize the screen and does not resort to safe mode.

I have swapped hard drives on the 5253 but sometimes my wife uses the 5253 for some web site work with Microsoft specific proprietary code so I leave Windoze 7 triple booted on it.  Previous development testing clobbered everything and I did a 4 DVD restore of the Windoze 7.  Don't like to do that.

Cleanest boot record recovery is to do an install of 10.04.3 or 11.10 onto a spare 10 GB partition.  Sometimes Boot-Repair CD works, not much use on the netbook which doesn't have a CD.

Always seems to me the buggiest code on a new release is ubiquity install and grub2.  I've had trouble with both on precise pangolin which is intended to be a stable release.

Let the breakage resume...reported one launchpad bug with HUD so far, generally can't make it function since I update frequently.

Jerry

---

### Post by anewguy on 2012-02-04
Currently the only spare I would have is an older (Pentium M 1.7ghz) Dell laptop that I bought to use for controlling my telescope.

No spare hard drive, but plenty of knowledge there on the hardware side.

I was trying to avoid setting up a new partition on my desktop or my good laptop (both quad core, 8gb) as I didn't want to take a chance on hosing the rest of the information on the drive.

I was also trying to avoid setting up a VM for testing as I didn't know what kind of "accidents" one might encounter in alpha or beta testing of Ubuntu. 

I suppose it would be possible for me to add another drive dedicated just to testing as long as I can stop my other drives from being mounted and therefore vunerable.  Would give me a good reason to make that trip to MicroCenter and buy a couple of drives - I need more space anyway and want to add a shadow.  That's probably the cheapest way.  On the other hand, if I can find room to squeeze another box in I could set up multiple things on it and not care - so I could even screw around with learning a server (tried this before on one of my "live" systems and messed things up fairly badly ;) ).

> **kansasnoob said:**
> I have some suggestions but I'm busy ATM. In the meanwhile it would help to know a couple of things:

(1) Do you have a spare computer?

(2) Do you have a spare hard drive and the knowledge to swap hard drives in your computer? (I might add, are you aware of anti-static safeguards?)

You already know that the one time you're not prepared for data loss is the time you'll wish you had been so I'm not going to rub salt in the wound :)

I've hosed things I wish I hadn't more than once :(

---

### Post by kansasnoob on 2012-02-04
> I was trying to avoid setting up a new partition on my desktop or my good laptop (both quad core, 8gb) as I didn't want to take a chance on hosing the rest of the information on the drive.

How did that work out :p

I multi-boot to perform most of my testing:

[ATTACH]211990[/ATTACH]

But that's major overkill for most folks ;)

I symlink most of my data on separate partitions and before I begin testing I always copy the important partitions to a USB drive.

I started testing in 2008 and I'd just remove my main drive and replace it with a testing drive. Since then I keep buying more and more hardware, particularly hard drives, so I can test faster and hopefully better.

I now have one desktop totally dedicated to testing and it has a legal Win XP on one drive which I swap out from time to time.

My other testing boxes main drive is the one pictured in that screenshot but I swap drives a lot in that box too.

Right now I need at least one more SATA drive (2.0/3GB) or at least another IDE drive but mechanical hard drive prices are insane ATM :(

The bottom line is that there's no absolute certainty of keeping data safe during testing.

---

### Post by kevpan815 on 2012-02-04
> **cariboo907 said:**
> I've used the Live CD to install Ubuntu dozens of times, this is the first time in 2 or 3 years that I've had an outright failure. The last time was because the installer wouldn't detect the drives on a system that only had SATA drives connected to it. The system I'm using now has a mix of SATA & PATA drives, that may be the reason for the failure.

I was a little bit busy this time around for iso testing, but I will participate when it comes time to test the beta iso's.

Yeah well the main reason that I use the Alternate CD instead of the Desktop CD is that it works better when doing an Off Line Installation.

---

### Post by candtalan on 2012-02-04
> **nm_geo said:**
> Hey hedge.. You be correct that is why I make a Clonezilla clone of my harddrive on about a weekly basis and always before I try a fresh install.  My take has been that Ubquity has caused me lots of problems on installs and the alternate iso works better for me.  However when we are testing it is best to test installs that the newer users will be using.

Meh. The *Released* version of Ubuntu desktop 10.10 (incorrectly) wiped three Partitions on a drive of mine when a certain specific install option was selected! The problem was belatedly added to the release notes.
Software, don't you just LOVE it?

---

### Post by nm_geo on 2012-02-04
Ubiquity refused to install during testing OO A2 I believe. The crazy migration assistant thing mounted all my partitions 4 or 5 at the time even though I said no to the question it asked.  I just could not get a clean install on the new partition so I cleaned it and installed Maverick on it as a test.. Maverick grabbed it np.

I later installed on that partition with the OO Alternate iso.  Which I still have for answering user problems on occasion.  

I think the new Ubiquity causes multi-boot users some problems because we have to many partitions with grubs installed in all of them even when we keep one primary boot grub. My main grub boot is on my LL install along with Grub-Customizer which make my life easier when I change kernels and my other partitions.

By the way kansas I did change my PP 12.04 kernel to the non-pae today, and I am using it right now.

---

### Post by cariboo on 2012-02-04
> **kevpan815 said:**
> Yeah well the main reason that I use the Alternate CD instead of the Desktop CD is that it works better when doing an Off Line Installation.

One of the benefits of doing an offline install using the Live CD, is that the language packs don't get installed. 

One benefit for me at least when doing an online install using the Live CD, is that I can still access the forum while the install process is running by using the Try Ubuntu option first, then starting the install process.

---

