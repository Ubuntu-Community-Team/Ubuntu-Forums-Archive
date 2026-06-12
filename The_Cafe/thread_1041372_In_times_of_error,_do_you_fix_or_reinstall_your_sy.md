---
title: "In times of error, do you fix or reinstall your system?"
date: 2009-01-16
forum: The Cafe
---

### Post by sofasurfer on 2009-01-16
1) When you find yourself facing a failed system, either not functioning at all or not functioning to your standards, are you most likely to reinstall your system or do you usually find out how to fix it?

2) Post the circumstances of your last system failure.

I try to find fixes but I am not very good at that yet. I usually end up reinstalling my system by using a previously saved package list. This takes about and hour and a quarter which isn't really a problem for me.

Most recently I am not able to get my Nvidia driver working. I have tried 3 or 4 differant solutions which were posted in the forums but still no luck. Usually after a failed fix attempt I reinstall just to be sure my system isn't contaminated with bad stuff.

---

### Post by Valok on 2009-01-16
Depends on the state of my system.  If I've been tinkering with a lot of things, and the system feels clunky / messy then I'll back up my files and do a complete re install of Ubuntu.  Otherwise I'll just try and fix the bug.

---

### Post by Sunflower1970 on 2009-01-16
I will usually try to fix the problem first so I can learn a bit more about the system. But, if that doesn't work, or it's taking just too darned long, I'll go ahead and reinstall.

Last circumstance of a reinstall was user error (lol). My old Compaq where I try out different distros, and try other things before I install anything on my main computers. It originally had Xubuntu, PCLinuxOS, Arch & Debian on it..I screwed something up in Xubuntu, have no idea what it was, got frustsrated, wiped the hard drive and did a fresh install with just Debian and Arch. (which was something I was planning on doing anyway, so no big loss)

---

### Post by Barrucadu on 2009-01-16
Always fix. My last system failure was inability to boot after accidentally deleting my /boot folder.

---

### Post by RATM_Owns on 2009-01-16
Fix.

My last mess-up was tweaking /etc/rc.sysinit

---

### Post by kyroha on 2009-01-16
I use Partimage and the System Rescue CD to go back to the last known good image that I keep in an external drive. So I guess that is reinstalling, except I don't have to reinstall all the packages, its all there like magic :)

---

### Post by Kappity on 2009-01-16
Would much rather fix it, and learn something in the process.  I have the luxury of having other computers available, and I regularly back up work in progress, so it's not like I would normally have to put important work on hold.

Most recent problem like this, I screwed up my permissions, and was having to log in as root to do a number of routine things.  A couple of people told me that I might just have to reinstall, before somebody here told me the solution.

---

### Post by saulgoode on 2009-01-16
I have never re-installed a GNU/Linux system in order to fix it. I have re-installed in order to revert to a pristine state in order to build packages for release.

---

### Post by fissionmailed on 2009-01-16
Fix.

---

### Post by drjonze on 2009-01-16
I try to fix because I learn more. At first I would just reinstall, often it would be faster than trying to find a fix because I have a good back up I can easily restore but I wouldn't learn anything and I would often break my system again because I never learned what I did wrong the first time.

My last screw up was that I blew away Grub by installing Windows 7. I just fired up the Live CD and restored Grub.

---

### Post by Thelasko on 2009-01-16
I'm going with reinstall.  I don't reinstall for every problem.  It depends on the severity and how long it's taken for me to troubleshoot.  If the problem is system-wide and takes more than a day to troubleshoot, it's time to reinstall.

Last time I reinstalled, my audio quit on Gusty.  I still have no idea why it happened.  Someone suggested I recompile ALSA and I was done troubleshooting.  Hardy had been out for a while so I just upgraded while I was at it.  Ubuntu is so easy to install, sometimes troubleshooting just isn't worth it.

I'm still on Hardy, by the way.  If it ain't broke don't fix it.

---

### Post by bigbrovar on 2009-01-16
reinstalling just because you have a problem is like sweeping things under the carpet .. they come back to hunt you in the end.. because if u dont fix the problem and reinstall .. the fresh install might come up with same .. what would u do? another reinstall?

---

### Post by sofasurfer on 2009-01-16
This is very interesting. I am surprised to heard that so many people do not see reinstallation as a bad thing. This gives me hope that I am progressing as well as most people...slowwwwww.

---

### Post by RATM_Owns on 2009-01-16
Oh, another time when I messed up is when a ton of files in /etc got rm'd.

Thank god nothing was written to the space, I was able to restore it.

---

### Post by uberdonkey5 on 2009-01-16
Wow, this is such a pertinent question for ubuntu users. I reinstalled ubuntu 3 times due to messing (never lost data though). I think, as a beginner some mistakes I made were just too big to understand how to correct.

However, last night I STUPIDLY changed the permissions on my user folder (read it somewhere that I had to do this to get a file to work). Needless to say, ubuntu would not boot cos user folder has to be read/writable by user but not by anyone else.

Well, fiddled around using live disk to change permissions back, and after 50 mins was back to my lovely system.

We have to face it, with great power comes great responsibility :D

---

### Post by cardinals_fan on 2009-01-16
It depends on whether I blame myself or the system.  I've screwed up my Fedora system by removing packages I don't need, which then removed dependencies that I **do** need.  In that case, I blamed Fedora/YUM for automatically removing all the "unneeded" deps and wiped it.  However, I screwed up my GRUB config badly the other day, rendering my Slackware partition useless.  That was my fault, so I fixed the GRUB and continued using Slackware.

---

### Post by uberdonkey5 on 2009-01-16
> **cardinals_fan said:**
> It depends on whether I blame myself or the system.  I've screwed up my Fedora system by removing packages I don't need, which then removed dependencies that I **do** need.  In that case, I blamed Fedora/YUM for automatically removing all the "unneeded" deps and wiped it.  However, I screwed up my GRUB config badly the other day, rendering my Slackware partition useless.  That was my fault, so I fixed the GRUB and continued using Slackware.

he he, like it... its like bad software needs to come back through reincarnation, whereas good software is allowed to live :D

---

### Post by cammin on 2009-01-16
If it's quicker/easier to reinstall than to fix the problem, I'll reinstall.

---

### Post by logic++ on 2009-01-16
Older days I would reinstall. Now, with all that information out there fixing works for me.
I only reinstall on each new release.

Last mess up: my cat slept on the keyboard. A million of screenshot windows appeared and the system freezed... I had to hard-shutdown it. While rebooting i realized that before shutdown I was formating a fat partition to ntfs... The next day I bought her a cat basket.

---

### Post by cardinals_fan on 2009-01-16
> **uberdonkey5 said:**
> he he, like it... its like bad software needs to come back through reincarnation, whereas good software is allowed to live :D
Methinks I misread the thread title.  Good software is allowed to live whenever possible.  Otherwise, it is humanely put down and reincarnated.

Bad software gets permanently wiped off my hard drive.

---

### Post by jimi_hendrix on 2009-01-16
i have never had a system "fail"...if it doesnt work...chances are its cause my stuff isnt supported so i just delete the install

---

### Post by crimesaucer on 2009-01-16
I have to at least try fixing it first. 


The reason is that all of my packages are compiled from source..... and if I start over with a quick FTP install then I have to build 500 packages from source and then add all of my custom patches and configurations to make it the same..... and that takes for ever.

---

### Post by steveneddy on 2009-01-16
I reinstalled a lot when I first started using Linux. Since I discovered that an upgrade in Ubuntu is a sure way to whack your system, I reinstall once when I update the versions and it doesn't whig out on me like an upgraded Ubuntu install does.

It only takes 20 minutes to reinstall and maybe another 15 to reconfigure.

So yes - [COLOR=Blue]**reinstall**[/COLOR].....

---

### Post by |eafhound on 2009-01-16
Fix it man

---

### Post by frrobert on 2009-01-17
On my own systems which are all Linux based OSes I fix.  Occasionally I get stuck helping a friend with a messed up Windows machine.  Most of the time their machine does not have an error but usually is infested with malware.  The standard solution there is backup any data, wipe, and reinstall.


I did contract work at an insurance company years ago and they had a fairly standard system of solution.


So when they  had a problem if you could fix it in 30 minutes or less you fixed otherwise you did a reload. 


Every user's had a profile based on their job which was tied a unique number and all their data was stored on the network.

A reload was a simple process with the machine connected to the network you booted the machine from a boot disk, typed in the unique number, and in about an hour you had a fresh install with all the correct software for the user

---

### Post by namegame on 2009-01-17
I tend to reinstall. I have a seperate /home partition so all my important data/documents are there.

I can have Arch reinstalled and ready to go in about 10-15 minutes.

---

### Post by avaralom on 2009-01-17
I'm guilty of reinstalling my operating system more than a few times. 

Few years ago, when I ran XP on this laptop I would have random problems that I wouldn't even know where to begin to fix. I figured that clearing out everything and starting over would work better than taking the time to fix the problem. 

With ubuntu, I will generally try to fix any of my problems. Primarily because getting everything up and running takes a bit more time than with Windows.

---

### Post by lakersforce on 2009-01-17
Depends. If a rough estimate tells me that it will take more than a couple of hours to fix, I'll re-install.

Time is money :)

---

### Post by richg on 2009-01-17
I do not break the OS. Works for me.

Rich

---

### Post by DeadSuperHero on 2009-01-17
It really depends on how badly I mess things up. In my earlier days of Linux when I wasn't so sure about CLI stuff, I used to reinstall all the time when I screwed up driver installation stuff.

But now, not so much. I keep elinks, nano, and cplay along with screen to do any X-crashing fixing work. I like to think of computing as a learning process now, it's more fun to try and fix something because you ultimately learn more about what you've just messed up.

---

### Post by jomiolto on 2009-01-18
1) Usually I try to fix things, but I end up borking them even worse and then I have to reinstall... :D

2) Accidentally ran the unthinkable command in /. (A result of a typo and too fast fingers/too slow brain). When I realized what I had done, I had already lost the whole /bin directory, and lots of unimportant data (or so I thought).

Recovering from the problem was interesting. I couldn't run any of the /bin commands ("ls: command not found") and all of the programs in GUI also failed to start. I couldn't install packages with apt, because I had lost it along with dpkg, so I couldn't recover the coreutils. I couldn't even mount partitions, because I didn't have mount!

For a moment I thought that my only option was to reinstall the whole system, but then I realized that I had another root partition mounted (I think it had another installation of Ubuntu on it). So I did a "cd /mnt/sda2" and an "echo *". It listed the stuff you'd expect to find at / and I decided to try running a command from that partition; "/mnt/sda2/bin/ls" I said and behold! An ls file listing! It worked!

From there on it was quite easy to return the important stuff; I just created a /bin directory and copied everything from /mnt/sda2/bin there (using "mkdir" and "cp" from /mnt/sda2/bin of course), and after that I could use the system quite normally to return the other folders that had been destroyed.

The only things I actually lost in the accident were some files I didn't have a backup off; basically some stuff I had downloaded from the Internet, which I thought I would always be able to download again if I lost it. To my grief I found out that, for example, some of the Internet artists I had music from, had pretty much disappeared from the face of the Internet and I couldn't find their music anywhere anymore :(

EDIT: apt and dpkg don't actually live in /bin but in /usr/bin, but still I was unable to run them for some reason...

---

### Post by Trail on 2009-01-19
> **sofasurfer said:**
> 1) When you find yourself facing a failed system, either not functioning at all or not functioning to your standards, are you most likely to reinstall your system or do you usually find out how to fix it?

Fix it. I used to reinstall it the past, but I guess I've grown better. In any case, I do quite a bit of customisation for productivity on my working environment and I wouldn't want to have to do it from scratch. Besides, fixing a failed system is quite fun. Usually.


If I do have to reinstall (probably due to distro upgrate, I'd guess) I tend to backup my home and copy-paste individual settings I am interested in (amarok, firefox, kmail, kdevelop, etc).

> **sofasurfer said:**
> 
2) Post the circumstances of your last system failure.

Latest failure has been the stupid nvidia drivers, where while working properly, have a damn issue where they would freeze the system. Currently reverted to opensource drivers because nvidia pissed me off.

Latest *system* failure was because I was updating to OpenSUSE 11.1 and I cut the  installation midway because I had to leave. And the installer would install packages as they were downloaded install of installing all at the end, which left half my system updated and half intact.

Couldn't start X amongst other things, had a bunch of recursive dependency problems (which was annoying to deal with through the console TBH), but I fixed it eventually after a bit. I knew I'd have a problem aborting the upgrade, but didn't expect that much :D

---

### Post by DeadRobot on 2009-01-19
Today, I decided to reinstall my system when my wireless wasn't working.  I just reinstalled it and it worked fine!

---

### Post by wheezer on 2009-01-19
For my mother, and mainstream consumers, a Windows style "Restore Point" system would be so rational and useful. Even for many power users, rolling back to yesterday, can often be a lot less work than diagnosing and fixing things that fail or just get confused. I know  it's been requested before, and I am sure there are technical arguments to be heard, but in general, why hasn't such a restore system been implemented  thus far?

---

### Post by spupy on 2009-01-19
When I was a noob I used to reinstall a lot, since that is what I knew from the windows days.

My current gentoo installation is holding for more than an year already. It survived two ubuntu installations, one of them borked, and a borked bsd install.

Actually, the mere thought of reinstalling gentoo (takes a couple of days + all the customization) is crushing my will...

---

### Post by cdekter on 2009-01-20
Usually I will fix it, although I did have to reinstall once when apt disappeared up its own fundamental (a bug that there was no workaround for and prevented any further use of the package system!).

---

### Post by cerpin on 2009-01-20
Funny to see a thread about this.

I actually just reinstalled hardy about 30 minutes ago due to a Nvidia graphics driver issue.

I had install Kubuntu 8.10 to see if i liked the KDE interface compared to Gnome, safe to say I liked gnome more. anyway, i tried to upgrade the driver for the graphics card and it messed it all up. when i would try to log in it would just give me strange symbols and colors on the screen. being a somewhat fresh install i figured i'd just go back to gnome.

no problems so far.
i did get one good thing out of it though, Windows is no longer on my laptop.

full ubuntu!!

---

### Post by jrusso2 on 2009-01-20
I can usually fix it unless its screwed up really bad.  But after so many years of using Linux I don't mess it up so bad anymore.

---

### Post by dmizer on 2009-01-20
> **sofasurfer said:**
> 1) When you find yourself facing a failed system, either not functioning at all or not functioning to your standards, are you most likely to reinstall your system or do you usually find out how to fix it?
That largely depends on the nature of the "failure". Generally failures are caused by actions that I take, so it's usually a simple matter of reviewing what I did to make things work again. Can't recall the last time I had to reinstall as a result of any kind of problem.

> **sofasurfer said:**
> 2) Post the circumstances of your last system failure.
I had a broken kernel on one of my laptops because of some kind of quirk with resume/hibernate.

Pulled my hair out (which is difficult because I'm bald) for a couple days trying to fix the problem. I wound up simply booting into an earlier kernel until a new kernel was released (a couple weeks).

---

