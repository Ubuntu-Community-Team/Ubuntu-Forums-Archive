---
title: "MS easily thwarts linux installs with raid"
date: 2007-08-13
forum: The Cafe
---

### Post by sdowney717 on 2007-08-13
[http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system)

all they need to do is push more raid systems from the hardware makers and people who want to install linux wont dare try it.

I did not think this would be so hard for linux and so easy for MS.

---

### Post by HermanAB on 2007-08-13
You don't need a RAID controller on Linux.  Linux has RAID built into software.  So all you need to do is toss the RAID adaptor away and plug the drives directly into the machine.

'Hope that helps!

Herman

---

### Post by Nekiruhs on 2007-08-13
Would Dell go along? Or soon to be (Crosses fingers) Lenovo and HP? Dell already sells linux, and so will Lenovo, and there have been rumors of HP following. Besides, RAID isn't cheap and I sure don't see a need in my home environment for a Redundant Array of Independent Disks.

---

### Post by cmat on 2007-08-13
I know someone who tried to install Ubuntu but RAID made it impossible to dual boot. openSUSE installed though.

---

### Post by prizrak on 2007-08-13
XP doesn't install on a RAID either...

---

### Post by jimrz on 2007-08-13
> **cmat said:**
> I know someone who tried to install Ubuntu but RAID made it impossible to dual boot. openSUSE installed though.

ran into this but was able to get around it by removing the win drive, installing ubuntu to a 2nd drive , replacing the win drive and setting the boot order to 1 - dvd drive -2- ubuntu -3- xp. since on the fairly rare occasions that I boot to xp only require that I hit f12 and select the xp drive to boot, I never even bothered to go back and add xp to menu.list. this method actually only takes about the same time (and fewer keystrokes) than a normal dual boot via grub + it leaves the mbr on the xp drive untouched.

---

### Post by sdowney717 on 2007-08-13
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

actually it is fake raid and it is not expensive. it lets people combine disks or write an immediate copy in case of hard drive failure. Just look at what you have to go thru to install ubuntu on systems like this and it will scare people away.

Does open suse handle this easily, several people and sites seem to imply this, does anyone have any direct info on this because I think we will be seeing more of this raid hardware in the future.

---

### Post by Nekiruhs on 2007-08-13
> **sdowney717 said:**
> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

actually it is fake raid and it is not expensive. it lets people combine disks or write an immediate copy in case of hard drive failure. Just look at what you have to go thru to install ubuntu on systems like this and it will scare people away.

Does open suse handle this easily, several people and sites seem to imply this, does anyone have any direct info on this because I think we will be seeing more of this raid hardware in the future.
Not really, Most home users would see now point in having 2 or more copies of the same data when that HD space could be used by them. Maybe a RAID for backups, but thats all I see it for.

---

### Post by sdowney717 on 2007-08-13
[http://en.opensuse.org/How_to_install_SUSE_Linux_on_software_RAID](http://en.opensuse.org/How_to_install_SUSE_Linux_on_software_RAID)
so easy

when will ubuntu get this?

---

### Post by marsmissionaries on 2007-08-13
Don't feed the troll everybody.

---

### Post by vexorian on 2007-08-13
so, what's specifically hard about the  link in the first post?

Edit: The opensuse way does not seem any simpler, besides of flooding the page with a bunch of images...

---

### Post by sdowney717 on 2007-08-14
so criticism of an install problem is met with scorn and I am a troll.
Well too bad.

 the fake raid does not just allow for instant backups, his is configured as a single drive. So in windows that would be c: and no d:

There is no flush of images from the sus install guide, the suse installer can simply do the job.  I assume someday ubuntu will handle this. And if more systems with multiple drives start running intel matrix software, this will become a major issue for getting linux accepted.

---

### Post by sdowney717 on 2007-08-14
vexorian, did you read all 3 pages of commands from the terminal, and explicit warnings that if you make a mistake your system is toast?
sounds kind of scary and is going to discourage people from trying.
who wants to be responsible for wrecking some one elses computer, say an install of vista just to introduce someone to linuix. If it can happen it will happen. even me with a fair amount of linux experience, i wont risk i nstalling on my brothers PC.

I suppose some of the people 'complaining' at this site about the difficulties n raid are also trolls
[http://kerneltrap.org/node/7378](http://kerneltrap.org/node/7378)

---

### Post by karellen on 2007-08-14
yes, everybody who dares to say anything that "linux is perfect" is a troll and very malevolent in the eyes of people like vexorian ;)

---

### Post by vexorian on 2007-08-14
> sounds kind of scary and is going to discourage people from trying.Which is a good idea imho after I read the 2 first sections of the howto. 

Something is telling me it would be better to use wubi to install things in this case until fakeRAIDs die or become more frequent (which would mean better support in the installers) it would be nice to have a link to wubi in that howto...

---

### Post by Hex_Mandos on 2007-08-14
I know home users who think doubling their RAM will give them more storage space. For them, "raid" would mean the police breaking into their homes searching for stuff.

---

### Post by toupeiro on 2007-08-14
I can only think of four letters...

RTFM

---

### Post by original_jamingrit on 2007-08-14
> **toupeiro said:**
> I can only think of four letters...

RTFM

^ win

to sdowney:
It is indeed possible to install on raid, it just takes more work.  And if you want to complain about people not doing such work for you, then yes you are a troll.  If you think it's seriously an issue that needs dealing with, then you deal with it yourself, and maybe even make the fix available for others if you want.  That's part of the point of open source.

Maybe you do legitimately care, and you're not trying to be a troll.  But simply pointing it doesn't mean that people are going to get a raid system jut for the sake of making a fix for you.  Maybe somebody at Canonical will, but most ubuntu users on this forum simply will not be able to.

---

### Post by sdowney717 on 2007-08-14
I was surprised to find the fake raid on my brothers dell. 

I scream outloud because I can not easily and safely install ubuntu, and if some people get offended, I really dont care. 

My points are already made.

---

### Post by Anthem on 2007-08-14
> **prizrak said:**
> XP doesn't install on a RAID either...
It's 2001 technology.  Ubuntu is current.

---

### Post by WishingWell on 2007-08-14
> **sdowney717 said:**
> [http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system)

all they need to do is push more raid systems from the hardware makers and people who want to install linux wont dare try it.

I did not think this would be so hard for linux and so easy for MS.

Hardware raid is an outdated technology, unless you use your system 100% at all times linux software raid will be faster than hardware raid.

And that is the end of the discussion for my part.

---

### Post by hangfire on 2008-02-06
> **WishingWell said:**
> Hardware raid is an outdated technology, unless you use your system 100% at all times linux software raid will be faster than hardware raid.

And that is the end of the discussion for my part.

OK, but I wish you would please cite some evidence for this claim.

If you are speaking of "soft" hardware RAID, such as Promise on a gaming motherboard, it is both slower and less reliable than any other kind of RAID, and deserves to be ignored. I would agree in that respect.

The servers at work are not being used 100% of the time, but the performance improvement of a good h/w RAID on them has benefits throughout the workday. These are expensive external units, though.

A good 3ware controller can give you that kind of performance and reliability boost internally for less than $500 (not including the extra disks). Not worth it for most folks, but if you run a small business on your home computer, worth considering.

---

### Post by sr20ve on 2008-02-06
> **sdowney717 said:**
> [http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system)

all they need to do is push more raid systems from the hardware makers and people who want to install linux wont dare try it.

I did not think this would be so hard for linux and so easy for MS.

RAID is never going to be a commonplace for household users.

---

### Post by kevdog on 2008-02-06
I disagree. If you are going to go RAID - my opinion is that you have to go through Hardware, and not software.  Promise used to make junky software controller boards, but I think they now offer boards with Hardware RAID controllers.  Ive been using a combination of various 3ware RAID controllers since 2002 on WindowsXP.  However states you cant install WindowsXP to a RAID set -- that is total nonsense.  

As far as home users adopting RAID, older 3ware RAID cards -- ones they no longer manufacture but are still available are quite reasonable.  Many can still be found on Ebay for less than $200.  RAID is for everyone -- if any home user ever had a hard-drive failure then you will probably be motivated next time to prevent the problem.  I personally run a RAID5 which provides me over 1 TB for videos, music, various video edits.  Back in 2003, I had a 800GB RAID5 -- I thought I would never run out of space -- well never came within about 1.5 years.  An 8 or 16 controller RAID card coupled with 400-500 GB harddrives offers almost 3-4 Tb of space.  

If anyone is seriously considering security for their data - RAID is the way to go.  Hardware RAID is much faster than software RAID, and if you by the right product (such as 3ware of others), they come with linux drivers.

---

### Post by rickyjones on 2008-02-06
> **prizrak said:**
> XP doesn't install on a RAID either...

Nice troll there. 

XP installs on a RAID array with only one additional step - loading additional drivers provided by the RAID manufacturer - and I know this from personal experience and from reading installation manuals for Microsoft software.

If you are going to make a statement at least make sure you are somewhat correct.

Thanks,

-Richard

---

### Post by aaaantoine on 2008-02-06
Indeed, I installed Ubuntu dual-boot on my laptop in August, and went to a single OS shortly after Gutsy came out.

But my desktop PC uses FAKERAID, and even loading the Ubuntu live CD scares the crap out of me because of all the hard disk "errors" that show up at boot.  I would want to dual-boot XP and Ubuntu on there, and I'm not entirely sure that's possible without creating a /boot partition somewhere.

---

### Post by sr20ve on 2008-02-06
> **kevdog said:**
> I disagree. If you are going to go RAID - my opinion is that you have to go through Hardware, and not software.  Promise used to make junky software controller boards, but I think they now offer boards with Hardware RAID controllers.  Ive been using a combination of various 3ware RAID controllers since 2002 on WindowsXP.  However states you cant install WindowsXP to a RAID set -- that is total nonsense.  

As far as home users adopting RAID, older 3ware RAID cards -- ones they no longer manufacture but are still available are quite reasonable.  Many can still be found on Ebay for less than $200.  RAID is for everyone -- if any home user ever had a hard-drive failure then you will probably be motivated next time to prevent the problem.  I personally run a RAID5 which provides me over 1 TB for videos, music, various video edits.  Back in 2003, I had a 800GB RAID5 -- I thought I would never run out of space -- well never came within about 1.5 years.  An 8 or 16 controller RAID card coupled with 400-500 GB harddrives offers almost 3-4 Tb of space.  

If anyone is seriously considering security for their data - RAID is the way to go.  Hardware RAID is much faster than software RAID, and if you by the right product (such as 3ware of others), they come with linux drivers.

I agree, hardware raid is the best way to go, I'm all for it, but you're still never going to see the average home user running raid unintentionally, ie because that's how the computer was factory configured. So the statement in the first post of this thread is bunk.

---

### Post by igknighted on 2008-02-06
How is RAID the way for MS to kill linux?  Think about it, RAID, while beginning to enter the home market, has been developed for years for servers.  And linux has been predominantly a server OS for a long time.  I would think RAID would be easier on Linux than windows, which was developed more as a desktop OS.

---

### Post by lespaul_rentals on 2008-02-06
> **cmat said:**
> I know someone who tried to install Ubuntu but RAID made it impossible to dual boot. openSUSE installed though.

Exact same situation here.  Too bad openSUSE didn't work out for my friend though, only OS that does is Windows Vista.  :(

---

### Post by lespaul_rentals on 2008-02-06
> **igknighted said:**
> How is RAID the way for MS to kill linux?  Think about it, RAID, while beginning to enter the home market, has been developed for years for servers.  And linux has been predominantly a server OS for a long time.  I would think RAID would be easier on Linux than windows, which was developed more as a desktop OS.

Not these new RAIDs, it's hell to get Linux working on age <= 3 months RAID setups.

---

### Post by FuturePilot on 2008-02-06
> **kevdog said:**
> I disagree. If you are going to go RAID - my opinion is that you have to go through Hardware, and not software.  Promise used to make junky software controller boards, but I think they now offer boards with Hardware RAID controllers.  Ive been using a combination of various 3ware RAID controllers since 2002 on WindowsXP.  However states you cant install WindowsXP to a RAID set -- that is total nonsense.  

As far as home users adopting RAID, older 3ware RAID cards -- ones they no longer manufacture but are still available are quite reasonable.  Many can still be found on Ebay for less than $200.  RAID is for everyone -- if any home user ever had a hard-drive failure then you will probably be motivated next time to prevent the problem.  I personally run a RAID5 which provides me over 1 TB for videos, music, various video edits.  Back in 2003, I had a 800GB RAID5 -- I thought I would never run out of space -- well never came within about 1.5 years.  An 8 or 16 controller RAID card coupled with 400-500 GB harddrives offers almost 3-4 Tb of space.  

If anyone is seriously considering security for their data - RAID is the way to go.  Hardware RAID is much faster than software RAID, and if you by the right product (such as 3ware of others), they come with linux drivers.

Agreed, hardware RAID is much better than software RAID

---

### Post by koenn on 2008-02-06
> **lespaul_rentals said:**
> Not these new RAIDs, it's hell to get Linux working on age <= 3 months RAID setups.
Isn't that just the same old story : if the manufacturers don't provide linux drivers for their hardware, it takes a while for the OS community to develop them themselves ? 

And if you have a complete environment build around Linux infrastructure, I doubt you're going to buy hardware that Linux can't handle (yet) - You're going to get a compatible raid controller rather than migrating your whole infrastructure to Windows or having to deal with a mixed Windows - Linux environment.

---

### Post by lespaul_rentals on 2008-02-06
> **koenn said:**
> Isn't that just the same old story : if the manufacturers don't provide linux drivers for their hardware, it takes a while for the OS community to develop them themselves ? 

And if you have a complete environment build around Linux infrastructure, I doubt you're going to buy hardware that Linux can't handle (yet) - You're going to get a compatible raid controller rather than migrating your whole infrastructure to Windows or having to deal with a mixed Windows - Linux environment.

Yes, I agree.  I wish hardware manufacturers were better about that.

---

