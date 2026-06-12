---
title: "Ubiquity should set up a separate /home for new users."
date: 2011-12-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fabricator4 on 2011-12-24
As experienced users I'm sure many of us set up a separate /home partition for our production machines. New users on the other hand never do, since they don't know how to, or indeed know that it's a good idea to do so.  This makes support for us here in the forums that much harder when things do go wrong, such as when they lose power during an on line upgrade without doing backups, or something equally risky because they don't know any better.  I'm sure you all know the scenarios; I have spent days at a time with users helping them recover their data (a 10 or 15 minute job for us can take a great deal of time with an inexperienced user over the forum or email).

I suspect it may be too late to get this implemented for Precise, but I've started a Brainstorm idea: [Brainstorm idea 29025]("http://brainstorm.ubuntu.com/idea/29025/").  I'm having trouble getting it accepted because it was proposed and rejected three years ago, but I really do feel it's time to have a fresh look at a simple implementation of this. I don't know of any other distro that does this, and think that it would be a small but significantly important feature that would give users a more robust system and make support in worst-case scenarios that much easier.

If you think this would be a good idea I'd appreciate some support for it, so please have a look.

Since it's Christmas morning here in Oz I'll wish you all a Merry Christmas!

Chris

---

### Post by cariboo on 2011-12-24
With the option to do an upgrade from the install CD, I don't think you see'll the added complication of creating a /home partition automagically.

I haven't tried it, but the upgrade/install in place option doesn't touch you home directory, so the main reason for having a separate one is no longer valid.

---

### Post by IWantFroyo on 2011-12-24
I agree with fabricator4. My method of getting myself to clean my /home is by taking only the files I really like/need and blanking the HDD.
That's only my reason, but I'm sure that if I have one, many other people will have one too.

Edit: Merry Christmas!

---

### Post by collisionystm on 2011-12-24
I don't do a separate simply because I see no use in doing so on a single hard drive computer. It just creates problems when you make it to large or to small. If the hard drive physically fails, your screwed. If the hard drive "fails" then you can just recover your files. Your average user does not care about separate home partitions. They like the idea of an automatic backup system like iCloud or Ubuntu One that is simple enough to make sense to someone who knows nothing of partitions or computers. Put in user name and password, files backed up. Computer breaks, Put in username and password, files recovered.

If you have the capability of more than 1 drive, than by all means, 'be a pro' and do a separate partition, but do it on a separate drive.

---

### Post by teh603 on 2011-12-25
Looks like a moot point; the brainstorm mods want you to add new info and petition to have the old one re-opened instead of continuing with the new one, and I doubt they'll go thru with it. When "replace Plymouth with xsplash because xsplash is stable and Plymouth isn't" doesn't count as an idea, I'm not sure what is.

Although I must say, be careful with trying to isolate userspace and rootspace too far. I had enough problems with that on an eePC 701 with UnionFS; the "recovery" partition simply ran a script that wiped the user partition and functionally reset everything back to zero. It was also the only system where you lost drive space when you uninstalled packages, and massively lost it when you tried to run the updater.

---

### Post by fabricator4 on 2011-12-25
> **cariboo907 said:**
> With the option to do an upgrade from the install CD, I don't think you see'll the added complication of creating a /home partition automagically.

I haven't tried it, but the upgrade/install in place option doesn't touch you home directory, so the main reason for having a separate one is no longer valid.

In testing that I've done, re-installing without formatting doesn't always work - you can still have a non-booting machine afterwards. This seems to happen on a broken updgrade - exactly the kind of scenario we are trying to fix.  Conversely it has worked in situations where I've suggested it.

If it hadn't been for the testing scenarios I've seen where it didn't work I'd feel a lot happier recommending it.

There's also the issue that we tell the user (rightly) that they should do a backup before proceeding.  Some of the broken systems I've helped with have the permissions messed up so badly that the user can't copy their data with Nautilus even after booting off the LiveCD.  In these cases the filesystem may be so badly broken that the only safe thing to do is backup the data and start from scratch since their /home is on the root partition.

You finish up coaching people command line, then it turns out that they can't or won't buy a new external drive to save data on.  It can be a nightmare...  If only they had set up with a separate /home...

Chris

---

### Post by fabricator4 on 2011-12-25
> **collisionystm said:**
> I don't do a separate simply because I see no use in doing so on a single hard drive computer. It just creates problems when you make it to large or to small.

If the / partition is 15Gb then I don't think there would be too many users that will install enough programs to fill it - we'd be talking about over 11GB of programs and games.  Even the most avaricious or careless user would have some trouble and take some time installing that much software.  

The smallest hard drive I've come across in the last few years has been 80Gb, which would leave 65GB for user data.  If the user has requirements larger than this you could certainly make a case that their real requirement is for a larger drive, or a newer computer.  There is another advantage to a separate /home in this case though - if they did fill their /home directory then the computer would still be capable of booting and running, and something could be done about the full /home.  A full / partition on the other hand can require a lot more work and support to fix.

[/quote] If the hard drive physically fails, your screwed. If the hard drive "fails" then you can just recover your files. Your average user does not care about separate home partitions. They like the idea of an automatic backup system like iCloud or Ubuntu One that is simple enough to make sense to someone who knows nothing of partitions or computers. Put in user name and password, files backed up. Computer breaks, Put in username and password, files recovered.
[/quote]

Hard drives will break, and Murphy's law practically guarantees that it will be the one with your data on it, that's why we tell the users to keep regular backups: I just can't see this as a reason to not have a separate /home on a single drive or a multi drive system.  The only advantage to a multi drive system is where backup data is kept on the other drive from /home. This is not a practice that I recommend as the only backup regimen.

I don't know _any_ new users using off-site or cloud backups. Most either do nothing or use and external hard drive - and the ones who at least do something with an external hard drive do so because they've lost data in the past.

Chris

---

### Post by fabricator4 on 2011-12-25
> **teh603 said:**
> Looks like a moot point; the brainstorm mods want you to add new info and petition to have the old one re-opened instead of continuing with the new one, and I doubt they'll go thru with it. When "replace Plymouth with xsplash because xsplash is stable and Plymouth isn't" doesn't count as an idea, I'm not sure what is.

I'm not going to try to re-open a three year old Brainstorm idea that has been marked "won't implement"  I think that's just a ploy to get the idea to go away. If they're not willing to re-visit an idea with a fresh look after three years in the wilderness then the term "obstructionist" seems appropriate (and I see no reason to bother with brainstorm further.)


> Although I must say, be careful with trying to isolate userspace and rootspace too far. I had enough problems with that on an eePC 701 with UnionFS; the "recovery" partition simply ran a script that wiped the user partition and functionally reset everything back to zero. It was also the only system where you lost drive space when you uninstalled packages, and massively lost it when you tried to run the updater.

I had to look up unionFS as I've not even considered it.  I can't say that I'd recommend it out of hand - it seems like a kludge.  My wife's 701 I set up with 10.04 LTS on the SSD with /home on the separate SD card.  It's quite workable, however with only a 4GB SSD there isn't room for much of a swap partition.  The computer I am on at the moment (We are staying with relatives for Christmas) is my 900SD. It has an 8GB SSD drive for root and a 1GB swap partition and I have an 8GB SD card which is mounted as /home. It's very workable and I'm a fan of the EeePc; with three batteries I can be independent of mains power for days at a time with a bit of care.

Chris

---

### Post by fabricator4 on 2011-12-26
Well, we're underway!  I managed to convince the moderator in question to let it through for consideration and he has agreed, though in a rather limited sense.

Anyone who wants to vote on this, or add their own solutions can now do so.

Any ideas on how we can get more people to look at this quickly (given the limited time frame).  I believe the idea is important enough to give it a good run if possible.

Chris.

---

### Post by zika on 2011-12-26
After install-from-Live-CD-process was organized so that install can be (easily) made without disturbing /home folder, there is a little advantage in having separate /home partition on a single-disk-PC... Major con is waste of space... Not to mention other (serious) contenders in &#8222;con&#8220; list... List of &#8222;pro&#8220; is very small, getting smaller with every improvement in install process...

---

### Post by teh603 on 2011-12-26
> **fabricator4 said:**
> Well, we're underway!  I managed to convince the moderator in question to let it through for consideration and he has agreed, though in a rather limited sense.

Anyone who wants to vote on this, or add their own solutions can now do so.

Any ideas on how we can get more people to look at this quickly (given the limited time frame).  I believe the idea is important enough to give it a good run if possible.

Chris.Got a link so I can +1 it?

> **zika said:**
> After install-from-Live-CD-process was organized so that install can be (easily) made without disturbing /home folder, there is a little advantage in having separate /home partition on a single-disk-PC... Major con is waste of space... Not to mention other (serious) contenders in „con“ list... List of „prod is very small, getting smaller with every improvement in install process...Uh... hunh?

---

### Post by Morbius1 on 2011-12-26
I'm not going to get into a debate about the merits or lack thereof of a separate home partition but please make obvious what the installer is doing so that the truly experienced among us can easily identify and disable this feature.

---

### Post by MacUntu on 2011-12-26
People need to do backups. If they don't understand this on their own, they probably will after data loss.

A separate home partition - what's the point?

---

### Post by teh603 on 2011-12-26
> **MacUntu said:**
> People need to do backups. If they don't understand this on their own, they probably will after data loss.

A separate home partition - what's the point?Well, it also has an advantage in upgrading. Instead of having to run the updater, you can just do a clean install without risking data loss by having /home on another partition.

---

### Post by MacUntu on 2011-12-26
You never risk data loss if you have up-to-date backups. :P

I moved /home to a separate partition a couple of weeks ago and I'll definitely undo that step, because I don't see any advantages - just a more complex setup.

---

### Post by fabricator4 on 2011-12-26
> **zika said:**
> After install-from-Live-CD-process was organized so that install can be (easily) made without disturbing /home folder, there is a little advantage in having separate /home partition on a single-disk-PC... Major con is waste of space... Not to mention other (serious) contenders in „con“ list... List of „prod is very small, getting smaller with every improvement in install process...

Three _big_ scenarios where a separate home works to a new users advantage:

User fills up / because /home is on the same partition

User upgrades and decides to go back to an older version - Have you tried downgrading without formatting / ?  The installer gets confused about what to keep and what to remove.  Likewise, I've seen a similar problem just upgrading from 10.04 to 11.04 (I think it was) by installing without formatting.

User suffers an interrupted upgrade - power failure or a hang.  The file system gets messed up and they can't even back up their data, let alone re-install.  I've spent literally days talking users through this scenario to get their data back.  If it had been on a separate home partition there's some chance a simple re-install with format of / only would have fixed it.

The pros for a separate /home far outweigh the cons when it comes to considering how to make a more robust system.  Despite the advances made in the installer and release upgrade software this is still true.

Chris

---

### Post by fabricator4 on 2011-12-26
> **teh603 said:**
> Got a link so I can +1 it?


It's up there in the first post in the thread, but here it is again:
[brainstorm idea 29025]("http://brainstorm.ubuntu.com/idea/29025/")


Chris

---

### Post by fabricator4 on 2011-12-26
> **MacUntu said:**
> People need to do backups. If they don't understand this on their own, they probably will after data loss.

But they don't.

Or they have every intention of doing so but forget to do it regularly, or not at all.

Users are the same everywhere.  I just visited my Niece's place and showed her 11.10.  It would have been nice to install it for her but she had hundreds of photos of the kids that were not backed up.  I asked her about this and she said she had an external drive, but hadn't done the backup for about year.  I left her with an install disk and the suggestion that she really needs to do the backups.


> A separate home partition - what's the point?

The same as it's always been; it's makes for a more robust system and there's been a lot written about the subject. For example a careless user can't trash the whole system by filling up /, and re-installs are simple no matter whether it's an upgrade, downgrade, another distro (hopefully not) or simply a fix.

Chris

---

### Post by teh603 on 2011-12-26
Voted on. I actually voted on solution number 3 instead of 1 or 2, because I think we need to keep the "average user" who has precious little experience in computing in mind when we're working on things. This isn't Slackware in which we can assume the end user is an advanced programmer. Ubuntu's target audience is (or needs to be if it isn't) a user who has about the same experience level as the average person who's had Windows 7 forced upon them. Even if it means adding a few extra layers of nooblet protection to things.

Although I don't like /home encryption, because it makes the user that much more vulnerable to social engineering attacks. The more times you enter your user password, the less people start to wonder about why it was asked, and then you get such things as root-privilege viruses and all that.

---

### Post by Ibidem on 2011-12-27
It should only happen if you install in a secondary partition: remember, you only get 4 primary partitions and a standard Win7 setup uses 3, occasionally all 4 (boot, recovery, main, and sometimes something else unjustifiable, just to make Linux difficult).
Some SSDs are 16GB or less.
Also, don't assume full HDD capacity to be available. 3-5 GB is about all you can count on being available when someone is just testing it out...
And yes, filling up a 15GB / is possible- the repositories install at over 90 GB, though most people wouldn't do that.  But install all the CAD programs in the repos, build brlcad, install GRASS and Google Earth, then build Mesa from git... and you will be regretting your partitions, guaranteed.

---

### Post by fabricator4 on 2011-12-27
> **Ibidem said:**
> It should only happen if you install in a secondary partition: remember, you only get 4 primary partitions and a standard Win7 setup uses 3, occasionally all 4 (boot, recovery, main, and sometimes something else unjustifiable, just to make Linux difficult).

Which is probably why Ubiquity likes to set up an extended Gb, at least for the swap file if not for both. I don't think there's any more problem with this than there would be otherwise.

>  Some SSDs are 16GB or less.
Also, don't assume full HDD capacity to be available. 3-5 GB is about all you can count on being available when someone is just testing it out... 

Which is why I specified at least 30 Gb.  It's just not practical.  Small SSDs are a special case.  The one I'm on at the moment is only 8GB - /home is the 8 GB card in the SD slot as it's the only practical solution.  Having everything on the SD card just doesn't work if there's even the slightest chance of filling it up.  It took me a couple of installs to get it right.

> And yes, filling up a 15GB / is possible- the repositories install at over 90 GB, though most people wouldn't do that.  But install all the CAD programs in the repos, build brlcad, install GRASS and Google Earth, then build Mesa from git... and you will be regretting your partitions, guaranteed.

Which is hardly normal usage. You can use that argument no matter how much drive space you have: someone is always going to do something to fill it up.  The idea is to help stop the normal first time users from shooting themselves in the foot and make their Ubuntu experience a good one no matter what happens to /.

Chris

---

### Post by zika on 2011-12-27
> **fabricator4 said:**
> Three _big_ scenarios where a separate home works to a new users advantage:

User fills up / because /home is on the same partition

User upgrades and decides to go back to an older version - Have you tried downgrading without formatting / ?  The installer gets confused about what to keep and what to remove.  Likewise, I've seen a similar problem just upgrading from 10.04 to 11.04 (I think it was) by installing without formatting.

User suffers an interrupted upgrade - power failure or a hang.  The file system gets messed up and they can't even back up their data, let alone re-install.  I've spent literally days talking users through this scenario to get their data back.  If it had been on a separate home partition there's some chance a simple re-install with format of / only would have fixed it.

The pros for a separate /home far outweigh the cons when it comes to considering how to make a more robust system.  Despite the advances made in the installer and release upgrade software this is still true.

ChrisYou've got some points. I must admit that I did not get into situations like those mentioned. And, I do have a good backup... You did not convince me, but I can not give counterargument for situations You've mentioned...

---

### Post by kansasnoob on 2011-12-27
Ripping into 'ubiquity' scares the heck out of me, remember the dreaded data loss bug in Maverick:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

We're just now finally getting the last of the serious bugs fixed from that debacle:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

And I question how exactly that would work with someone reinstalling where a dual/multi-boot exists :confused:

It's not at all hard to use the manual partitioner and create a separate /home if desired, and to reuse that /home w/o formatting if desired in the future, so I really hate to see the devs add an additional level of complexity to the "automated" part of the installer.

If you do manage to convince them to do this I'll expect to see you join the rest of us iso-testers when they open that can of worms. I may hide under the bed for a few months :D

---

### Post by kansasnoob on 2011-12-27
I actually prefer using a dual/multi-boot to retrieve data and/or settings from an existing OS (whether it's broken or not). I walked someone through such a thing here:

[http://ubuntuforums.org/showthread.php?t=1687962](http://ubuntuforums.org/showthread.php?t=1687962)

It's a bit strung out :(

I'd planned at the time to try collaborating with someone like Hedgehog1 to compress the important parts of that into a how-to like he produced here:

[http://ubuntuhedgehog.weebly.com/dual-boot-install.html](http://ubuntuhedgehog.weebly.com/dual-boot-install.html)

---

### Post by effenberg0x0 on 2011-12-27
I'm not entering the discussion about a separate partition for /home (I have used it for many years, but I'm not completely sure how much it would help in the hands of a newbie). 

But if anyone here is going to officially propose changes to the installer, I'd like to make a (sort of related) suggestion too:

One of the things that have saved the day a couple times for me, that is absolutely ridiculously easy to implement and that I have *never* seen a newbie do, is to create a secondary admin account in the PC. 

The logic, although obvious, is that one can easily screw the dotfiles, ownership and perms of it's own $HOME. But being able to simply restart the DM and login with another sudoer allows the inexperienced user to:

a) Immediately adopt this backup account as his default and continue to use the PC without any major intervention.  

b) Use this as a rescue account, through which he will login and cut/paste whatever we tell him to. We frequently have to walk users through rebooting, holding shift, avoiding plymouth, selecting the recovery grub option, mounting root as rw, getting a valid IP via console, etc just to fix some basic stuff - It takes too much time and users never manage to get it right quickly.

Even a more experienced user may be in a rush and need to simply login/finish a doc or  something else important ASAP, and don't have the time to play with some setup  problem.

Regards,
Effenberg

---

### Post by kansasnoob on 2011-12-27
> **effenberg0x0 said:**
> I'm not entering the discussion about a separate partition for /home (I have used it for many years, but I'm not completely sure how much it would help in the hands of a newbie). 

But if anyone here is going to officially propose changes to the installer, I'd like to make a (sort of related) suggestion too:

One of the things that have saved the day a couple times for me, that is absolutely ridiculous to implement and that I have *never* seen a newbie do, is to create a secondary admin account in the PC. 

The logic, although obvious, is that one can easily screw the dotfiles, ownership and perms of it's own $HOME. But being able to simply restart the DM and login with another sudoer allows the inexperienced user to:

a) Immediately adopt this backup account as his default and continue to use the PC without any major intervention.  

b) Use this as a rescue account, through which he will login and cut/paste whatever we tell him to. We frequently have to walk users through rebooting, holding shift, avoiding plymouth, selecting the recovery grub option, mounting root as rw, getting a valid IP via console, etc just to fix some basic stuff - It takes too much time and users never manage to get it right quickly.

Even a more experienced user may be in a rush and need to simply login/finish a doc or  something else important ASAP, and don't have the time to play with some setup  problem.

Regards,
Effenberg

Yes! Good idea :D

Something I've always found odd, but also helpful, is that Puppy assumes everyone is "admin". That of course means that anyone with a Puppy flash-drive can access anything on your puter and save it anywhere they want :D

---

### Post by JRV on 2011-12-27
> **fabricator4 said:**
> Well, we're underway!  I managed to convince the moderator in question to let it through for consideration and he has agreed, though in a rather limited sense.

Anyone who wants to vote on this, or add their own solutions can now do so.

Any ideas on how we can get more people to look at this quickly (given the limited time frame).  I believe the idea is important enough to give it a good run if possible.

Chris.

Submit it to Ubuntu Brainstorm at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by jbicha on 2011-12-27
The Ubuntu installer & upgrader doesn't hurt the /home part of the / partition unless it's told to format the partition by someone using the advanced partitioner or choosing the replace all. If it does, that's a critical bug. Ubuntu users do not needed to use a separate /home partition but can use the advanced partitioner if they like. This has been the case for years now.

---

### Post by vasa1 on 2011-12-27
> **effenberg0x0 said:**
> ...
One of the things that have saved the day a couple times for me, that is absolutely ridiculous to implement and that I have *never* seen a newbie do, is to create a secondary admin account in the PC. 
...
Hi, don't you mean "ridiculous**ly easy**"?

I like the idea and if you do start a new thread it would be great!

---

### Post by vasa1 on 2011-12-27
> **JRV said:**
> Submit it to Ubuntu Brainstorm at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

It's in the first post.

---

### Post by bcschmerker on 2011-12-27
I would definitely recommend separate hard drives, at least for /home, and preferrably for /usr, /opt, /var and /tmp (the swap has to be a separate partition by default, as it uses a unique variant of the ext filesystem group).  I had /home on its own drive since my hybrid Everex® system had the now-orphaned gOS® 1.0.1; it both provides insurance for system recovery in the event of primary hard drive failure and mitigates the backup issues of a major Dist-Upgrade between LTS releases.

As part of the preparation for a Dist-Upgrade from my present Lucid Lynx™ (10.04.4-LTS with backported Kernel 3.0.0.14-generic-pae from Oneiric Ocelot™) to Precise Pangolin™ (probably 12.03b2 or 12.04rc, if financial issues don't slow me to the point that Precise is officially released as 12.04-LTS or 12.05-LTS by the time I'm ready for said Dist-Upgrade), I plan to purchase a set of five SATA hard drives (what the Everex'® current Gigabyte® MA78GM-S2HP can handle), creating at most two partitions per drive (see also my Thread "[[color=green]all variants[/color]] [Partition sizes for typical max-out install?](http://ubuntuforums.org/showthread.php?t=1634084)").  I already plan on a PATA optical drive for sound-card compatibility (whether my current Creative Laboratories® SB0350 PCI 2.0 audio card/SB0110 I/O drive, or the upgrade-candidate Auzentech® X-Meridian™ 7.1 2G PCI 2.2 audio card/X-Tension™ DIN™ daughtercard) and intend to search for a PATA digital-audio-tape transport for backup/restore purposes.

---

### Post by jbicha on 2011-12-28
> **bcschmerker said:**
> I would definitely recommend separate hard drives, at least for /home, and preferrably for /usr, /opt, /var and /tmp (the swap has to be a separate partition by default, as it uses a unique variant of the ext filesystem group).  I had /home on its own drive since my hybrid Everex® system had the now-orphaned gOS® 1.0.1; it both provides insurance for system recovery in the event of primary hard drive failure and mitigates the backup issues of a major Dist-Upgrade between LTS releases.

Why in the world would you suggest a separate hard drive for /opt or /tmp? Further, I'm skeptical of any benefit at all to a separate /usr in 2012; I think it's likely to cause more problems than it solves. And unless you're managing a server, /var shouldn't be worth splitting out.

Putting /home on a separate partition or even a separate hard drive is not a backup; putting a copy of /home on a separate hard drive is.

---

### Post by Morbius1 on 2011-12-28
> **jbicha said:**
> Why in the world would you suggest a separate hard drive for /opt or /tmp? Further, I'm skeptical of any benefit at all to a separate /usr in 2012; I think it's likely to cause more problems than it solves. And unless you're managing a server, /var shouldn't be worth splitting out.

Putting /home on a separate partition or even a separate hard drive is not a backup; putting a copy of /home on a separate hard drive is.
Ah, the voice of reason. Er ... um .... what I meant to say is:

+1

---

### Post by kansasnoob on 2011-12-28
> **jbicha said:**
> Why in the world would you suggest a separate hard drive for /opt or /tmp? Further, I'm skeptical of any benefit at all to a separate /usr in 2012; I think it's likely to cause more problems than it solves. And unless you're managing a server, /var shouldn't be worth splitting out.

Putting /home on a separate partition or even a separate hard drive is not a backup; putting a copy of /home on a separate hard drive is.

I think someone is still confused by Windows drive A, drive C, Drive D, etc :(

This was a mis-education on the part of Windows since day #1 that I suspect has been responsible for more data loss than any flaw in any Linux installer. 

Partitions and discs/drives are two different things :P

---

### Post by effenberg0x0 on 2011-12-28
I have recently posted somewhere here at U+1 my concerns about backing up $HOME dotfiles, $HOME in general and even doing systemwide backups. Basically, what I said back then was that:

1) Inexperienced users think about backup as a way to restore their systems back to the exact state it was when the backup was made.
a) That would only happen if 100% system-wide backups, with very frequent (hourly, daily, weekly) snapshots were done and kept elsewhere, in another safe media. 
b) How is that doable in the average PC without impacting system speed, never failing, never being cancelled (i.e. system reboot/crash during snapshot) and if the average user will not have access to a very fast, large and reliable external storage?

2) We frequently see inexperienced users believe that by backing up $HOME they would be backing up programs. Many also believe that saving dotfiles would be enough to keep configs, unaware of /etc, for an example.

3) If we promote the separation of $HOME to a new partition, that will be understood by newbies as a security measure to keep data in case of system failure that leads to reinstall. How much of that would be true? When restoring these dotfiles over a new install of Ubuntu there would be no guarantee that:
a) The dotfiles would be 100% compatible to the new versions of the installed applications
b) No guarantee that badly configured / messed up dotfiles were not the initial cause of problems that led to the reinstall of Ubuntu, in the first place.
c) Many of the .dotfiles kept in this new partition would refer to programs that are not even installed anymore. Backing it up repeatedly is just a waste of space and CPU cycles.

So, what I meant to say, is that a separate partition for $HOME:
- Makes no sense as a true backup media if its a partition in the same disk as the system is installed. Considering the amount of 1-HDD systems out there (specially laptops), people with the means to create a true separate $HOME will be a minority.
- Even so, there's really no guarantee that user settings will be kept, sane, if not actually made worse in a new install.
- Could create a false sense of safety in inexperienced users, which would not be true.

And on the other hand, providing a backup tool, such as dejadup, backintime, or any other, with no pre-set profile and clear instructions, is just a waste of time, cpu cycles and space most users don't even have to spare. I'm yet to see ordinary users managing to do smart/selective backup profiles, keep snapshots safe and restore them correctly.

So, I'm still in the same page I was when I first posted this: Average non-technical users are not safe with any of the provided backup methods, separate $HOME, etc. And I have no idea on what could be done to really improve this.

The only thing that makes sense to me is for users to:
- Keep a list of installed packages, so they can batch-install it back quickly.
- Have a pre-set backup profile that only stores user-created content (docs). This can fit common "backup" media, such as USB HDD, home-NAS, etc.

Do you agree? Please point out where I'm failing to understand the logic of this. 

Thanks,
Effenberg

---

### Post by kansasnoob on 2011-12-28
> **effenberg0x0 said:**
> I have recently posted somewhere here at U+1 my concerns about backing up $HOME dotfiles, $HOME in general and even doing systemwide backups. Basically, what I said back then was that:

1) Inexperienced users think about backup as a way to restore their systems back to the exact state it was when the backup was made.
a) That would only happen if 100% system-wide backups, with very frequent (hourly, daily, weekly) snapshots were done and kept elsewhere, in another safe media. 
b) How is that doable in the average PC without impacting system speed, never failing, never being cancelled (i.e. system reboot/crash during snapshot) and if the average user will not have access to a very fast, large and reliable external storage?

2) We frequently see inexperienced users believe that by backing up $HOME they would be backing up programs. Many also believe that saving dotfiles would be enough to keep configs, unaware of /etc, for an example.

3) If we promote the separation of $HOME to a new partition, that will be understood by newbies as a security measure to keep data in case of system failure that leads to reinstall. How much of that would be true? When restoring these dotfiles over a new install of Ubuntu there would be no guarantee that:
a) The dotfiles would be 100% compatible to the new versions of the installed applications
b) No guarantee that badly configured / messed up dotfiles were not the initial cause of problems that led to the reinstall of Ubuntu, in the first place.
c) Many of the .dotfiles kept in this new partition would refer to programs that are not even installed anymore. Backing it up repeatedly is just a waste of space and CPU cycles.

So, what I meant to say, is that a separate partition for $HOME:
- Makes no sense as a true backup media if its a partition in the same disk as the system is installed. Considering the amount of 1-HDD systems out there (specially laptops), people with the means to create a true separate $HOME will be a minority.
- Even so, there's really no guarantee that user settings will be kept, sane, if not actually made worse in a new install.
- Could create a false sense of safety in inexperienced users, which would not be true.

And on the other hand, providing a backup tool, such as dejadup, backintime, or any other, with no pre-set profile and clear instructions, is just a waste of time, cpu cycles and space most users don't even have to spare. I'm yet to see ordinary users managing to do smart/selective backup profiles, keep snapshots safe and restore them correctly.

So, I'm still in the same page I was when I first posted this: Average non-technical users are not safe with any of the provided backup methods, separate $HOME, etc. And I have no idea on what could be done to really improve this.

The only thing that makes sense to me is for users to:
- Keep a list of installed packages, so they can batch-install it back quickly.
- Have a pre-set backup profile that only stores user-created content (docs). This can fit common "backup" media, such as USB HDD, home-NAS, etc.

Do you agree? Please point out where I'm failing to understand the logic of this. 

Thanks,
Effenberg

I agree with everything you said there. There comes a point when we try to make the live-installer truly fool proof, but in doing so we make it almost impossibly "foolish" :)

Complexities do already exist, such as:

[https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507](https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

None of those are easy to solve or they'd be fixed!

Why add more complexity :confused:

---

### Post by teh603 on 2011-12-28
> **effenberg0x0 said:**
> I have recently posted somewhere here at U+1 my concerns about backing up $HOME dotfiles, $HOME in general and even doing systemwide backups. Basically, what I said back then was that:

1) Inexperienced users think about backup as a way to restore their systems back to the exact state it was when the backup was made.
a) That would only happen if 100% system-wide backups, with very frequent (hourly, daily, weekly) snapshots were done and kept elsewhere, in another safe media. 
b) How is that doable in the average PC without impacting system speed, never failing, never being cancelled (i.e. system reboot/crash during snapshot) and if the average user will not have access to a very fast, large and reliable external storage?Size and reliability are more important than speed; we could make a piece of software on par with Apple's Time Capsule, where you plug in a large enough USB device (20 gigs?) and it backs up /home/Desktop, and all the other *visible* folders in there. I'm not so sure we want to back up invisible folders, because that's where a userspace f-up can get carried from one system to another.

> 2) We frequently see inexperienced users believe that by backing up $HOME they would be backing up programs. Many also believe that saving dotfiles would be enough to keep configs, unaware of /etc, for an example.Then we need to educate the users better, although there are some users who make a point of not caring. We'd do better leaving those users to their moosely fate at the hands of Win7 than trying to educate them.

> 3) If we promote the separation of $HOME to a new partition, that will be understood by newbies as a security measure to keep data in case of system failure that leads to reinstall. How much of that would be true? When restoring these dotfiles over a new install of Ubuntu there would be no guarantee that:
a) The dotfiles would be 100% compatible to the new versions of the installed applications
b) No guarantee that badly configured / messed up dotfiles were not the initial cause of problems that led to the reinstall of Ubuntu, in the first place.
c) Many of the .dotfiles kept in this new partition would refer to programs that are not even installed anymore. Backing it up repeatedly is just a waste of space and CPU cycles.Simple, the reinstall (provided its the only OS present) purges all folders from /home EXCEPT Desktop, Documents, Downloads, Music, Pictures, Public, Templates, and Vidos.

> So, what I meant to say, is that a separate partition for $HOME:
- Makes no sense as a true backup media if its a partition in the same disk as the system is installed. Considering the amount of 1-HDD systems out there (specially laptops), people with the means to create a true separate $HOME will be a minority.Specifically on laptops, I've been wondering about creating a "roaming /home" on ones that have a card reader. /home lives on an SD card, and can be moved from laptop to laptop. Not sure how good an idea it is, but its something to think about.
> - Even so, there's really no guarantee that user settings will be kept, sane, if not actually made worse in a new install.
- Could create a false sense of safety in inexperienced users, which would not be true.

And on the other hand, providing a backup tool, such as dejadup, backintime, or any other, with no pre-set profile and clear instructions, is just a waste of time, cpu cycles and space most users don't even have to spare. I'm yet to see ordinary users managing to do smart/selective backup profiles, keep snapshots safe and restore them correctly.

So, I'm still in the same page I was when I first posted this: Average non-technical users are not safe with any of the provided backup methods, separate $HOME, etc. And I have no idea on what could be done to really improve this.See, once again this is a problem of user education. You don't have to go into the nitty-gritty to teach someone how to back their computer up. Its because a certain company, starts with M, has made a habit of teaching people just enough to do their job and not enough to properly use the computer.

> The only thing that makes sense to me is for users to:
- Keep a list of installed packages, so they can batch-install it back quickly.
- Have a pre-set backup profile that only stores user-created content (docs). This can fit common "backup" media, such as USB HDD, home-NAS, etc.Ubuntu One was supposed to have some kind of option for this. Now, Ubuntu One being only available for systems running Unity or Windows 7, I'm not exactly sure how useful it'd be for those of us running KDE, xfce, and lxde.

---

### Post by effenberg0x0 on 2011-12-28
I sort of admire the implementation of a "restore point", that exists on MS OS. Of course, we don't know exactly how they do it without a source code to look at. On MS, this procedure doesn't look like a standard systemwide backup. At least it seems to be faster and occupy less space than a standard backup. I have tested it a couple times, it works. 

If somehow we had such a feature in Ubuntu, I think it would make more sense for the average user than complex backup proceedings. 

If that was the case, then I would support the idea of Ubiquity offering to create a restore point, right after the install procedure finishes.

EDIT: Some info [here]("http://en.wikipedia.org/wiki/System_Restore"). So it works as a service, which is why it doesn't feel like a backup... Changes are captured as they happen.

---

### Post by teh603 on 2011-12-28
> **effenberg0x0 said:**
> I sort of admire the implementation of a "restore point", that exists on MS OS. Of course, we don't know exactly how they do it without a source code to look at. On MS, this procedure doesn't look like a standard systemwide backup. At least it seems to be faster and occupy less space than a standard backup. I have tested it a couple times, it works. The one on XP definitely isn't. From what I can tell, it only makes a snapshot of system settings and the registry. I found that out the hard way when I tried using a copy of something that I'd installed post- snapshot, and discovered its registry keys were all missing.

A better version for Ubuntu would probably just be a copy of major system settings (network manager settings, user interface settings, user accounts, stuff like that) and a list of packages installed. That way the system (barring the visible folders in /home) could be wiped and reinstalled based on the stored settings and package list.

---

### Post by effenberg0x0 on 2011-12-28
> **teh603 said:**
> The one on XP definitely isn't. From what I can tell, it only makes a snapshot of system settings and the registry. I found that out the hard way when I tried using a copy of something that I'd installed post- snapshot, and discovered its registry keys were all missing.

A better version for Ubuntu would probably just be a copy of major system settings (network manager settings, user interface settings, user accounts, stuff like that) and a list of packages installed. That way the system (barring the visible folders in /home) could be wiped and reinstalled based on the stored settings and package list.

It falls back to the idea of a very selective preset backup profile running as a service, right? It can easily be done. The Windows service seems to intercept write syscalls and create a binary repository of changes..much more complex... and probably creates some impact in performance (when intercepting every write syscall).

So, basically, we are talking about creating a cron-based backup service with a smart profile, having Ubuntu accept to add this service as a default, in a way that it is installed by Ubiquity and immediately activated after install and at at every boot. The service greps the list of installed apps/versions to a file, select some but not all config files and tgz the thing to /var/backup/$date.tgz according to cron schedule. sudo service restorepoint restore woud (not surprisingly) restore this stuff.

Very doable... and quick. 

What would be the expected default procedure to have this accepted into Ubuntu? Code first, beg second? Beg first, code second?

---

### Post by teh603 on 2011-12-28
> **effenberg0x0 said:**
> What would be the expected default procedure to have this accepted into Ubuntu? Code first, beg second? Beg first, code second?Hell if I know. The last computer I was able to program successfully was an Apple IIc. When I tried moving from Applesoft to Visual Basic, I discovered the hard way that Basic changed sometime in the mid '80s and nothing I knew worked anymore.

---

### Post by effenberg0x0 on 2011-12-28
Basic :) I remember liking it in school, can't remember the syntax though. Back then teachers made us use horrible stuff like clipper and cobol. Now that was hell.

If you want to come back to programming in a Linux environment one day, and you still have programming logic inside of you (which I'm sure you do), my advice would be to just do some shell scripting first, it will be familiar to you. No matter if you'll use it for fun or profit, you'll have a good time with it and it is useful for daily system tasks. More importantly, it is easy and you'll be writing code as fast as you think in a couple days. It has no classes or object orientation, you won't find it weird coming from basic. [http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial) 

As you warm up with it, you wouldn't find it very hard to jump to python, ruby, or whatever else you choose later.

---

### Post by seeker5528 on 2011-12-28
> **effenberg0x0 said:**
> 
3) If we promote the separation of $HOME to a new partition, that will be understood by newbies as a security measure to keep data in case of system failure that leads to reinstall. How much of that would be true? When restoring these dotfiles over a new install of Ubuntu there would be no guarantee that:
a) The dotfiles would be 100% compatible to the new versions of the installed applications

Same or newer isn't often an issue, using newer configuration files with old applications is the problem area.

> b) No guarantee that badly configured / messed up dotfiles were not the initial cause of problems that led to the reinstall of Ubuntu, in the first place.

A backup is only as good as the data going into it so you have the same issue whether you are backing up the entire home directory or not, or keeping a seperate home partition that you always use.

> c) Many of the .dotfiles kept in this new partition would refer to programs that are not even installed anymore. Backing it up repeatedly is just a waste of space and CPU cycles.

The space and CPU cycles probably won't be enough that most people would care.

Later, Seeker

---

### Post by teh603 on 2011-12-28
> **effenberg0x0 said:**
> Basic :) I remember liking it in school, can't remember the syntax though. Back then teachers made us use horrible stuff like clipper and cobol. Now that was hell.Never tried those; mom wouldn't let me stay after school to join the computer club.

> If you want to come back to programming in a Linux environment one day, and you still have programming logic inside of you (which I'm sure you do), my advice would be to just do some shell scripting first, it will be familiar to you. No matter if you'll use it for fun or profit, you'll have a good time with it and it is useful for daily system tasks. More importantly, it is easy and you'll be writing code as fast as you think in a couple days. It has no classes or object orientation, you won't find it weird coming from basic. [http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial)

As you warm up with it, you wouldn't find it very hard to jump to python, ruby, or whatever else you choose later.Dunno, you entirely sure about that? Most of the architecture I learned was based around the program's "main loop" and lots of nested GOTO and GOSUB sub-loops. GOTO was not evil in those days; he was a necessity.

---

### Post by effenberg0x0 on 2011-12-28
> **teh603 said:**
> Never tried those; mom wouldn't let me stay after school to join the computer club.
No PC club here too lol... it was a mandatory discipline and I flunked it repeatedly... Cobol phase was probably when I learned how to skip school and go drink beer with bad company.
> **teh603 said:**
> Never tried those; mom wouldn't let me stay after school to join the computer club.

Dunno, you entirely sure about that? Most of the architecture I learned was based around the program's "main loop" and lots of nested GOTO and GOSUB sub-loops. GOTO was not evil in those days; he was a necessity.
Ah, now I remember :)
But honestly, have a look at the syntax of some scripts. As your brain gets used to the syntax, you'll see that it's the same thing over and over, unless you move to something in OOP (object oriented). You had if, then, else, while, etc on Basic, these still exist and do the same thing. Loops are the same, but with a small change in syntax, variables are the same thing they always were. Replace subroutines with functions, delimited by brackets and that's it :)

---

