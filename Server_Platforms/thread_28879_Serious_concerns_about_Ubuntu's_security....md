---
title: "Serious concerns about Ubuntu's security..."
date: 2005-04-22
forum: Server Platforms
---

### Post by LobsterSan on 2005-04-22
For the last few days I've been playing around with Ubuntu 5.04 (hoary hedgehog), as I'd like to get a small understanding of what Linux is and how it can absolve me of WinXP dependence.  Installation and setup has not been easy, but I understand that it is a learning process, just as my first computer (an Apple IIe, using BASIC) was a learning process.  Anyhow, I recently installed hoary unto my computer and had it running just fine in dual-boot with winxp for a few days.  Just now, I attempted to boot into winxp.  I went to check on the pasta I was cooking, and returned to my computer to find the windows chkdsk-type screen up and deleting my .dll files left and right.  I sat in disbelief, then pondered whether this was a hack job or virus of some sort.  I hit the manual reset-switch, pulled my ethernet cable, and thought about my next plan of action.

For a litte more background on my situation, I had just recently mounted my NTFS partition containing the winxp files in ubuntu, but I did not write anything to the drive.  I thought that this might have caused the problem, but I don't see why this would cause winxp to automatically delete my .dll files.  Now, I cannot boot into Windows at all, and attempts to run the recovery program from my disc also meets with failure.  This is due to my inability to access my windows system due to my winxp administrator password being rejected.  I am fairly certain that my administrator password is correct, so this only heightens my fears that my system was somehow hacked and my administration password changed.

My winxp system was fairly stable before the install of ubuntu, and as well I have zonealarms firewall and avg anti-virus running on winxp.  I understand that my winxp was not completely invulnerable to attack, but I feel it was much more protected than ubuntu.  So, I am wondering now how secure ubuntu is, and I'm especially scared to continue usage of a system that I have little knowledge of and that others have a vast knowledge of and ability to tap my system.

If anyone can spot an alternative hypothesis as to why this is happening, I would love to hear it because I'd like to regain my trust in Linux and ubuntu.  At the moment, I am considering just wiping my drives and keeping my main system clear of Linux, perhaps when the time comes and if I have a spare computer, trying out linux on a different box with no sensitive or important information on it.

---

### Post by BAshworth on 2005-04-22
In general, any Linux distribution is more secure than Windows XP.  The architectural flaws that make Windows vunerable are just not there in Linux.

Also, unless you installed some application specifically for it, Linux can't write or delete items from a NTFS partition.  

It sounds more like you picked up a virus of some sort, scary one too by the sound of it.  I know you mentioned AVG, which is a fine free antivirus, but it doesn't catch everything.  No antivirus can, despite what they may claim.  Bootsector virus' (sp?) are very hard to protect against.  They aren't very prevalent because they actually require someone to know more than basic VB scripting to create.

---

### Post by guyforget on 2005-04-22
I dont use Windows at all, so I havent really kept up with development but I think that youd have to go pretty far out of your way to be able to mount NTFS filesystems with write abilities.  Chances are that nothing in your linux installation could write to your NTFS partition.  

It is** much more likely** that Windows got infected last time you used it and you never knew until you booted back into it.  

This is a good thing.  You can now mkfs.ext3 that drive and never boot back into Windows again.  Its own insecurity finally ate itself up and left you with an amazingly capable and intuitive Ubuntu Desktop.  

But seriously; its comical to be "seriously" concerned with Ubuntu's security, especially compared to WinXP.  You can put your concerns to rest though, Id bet the farm that nobody haxored your Linux system and then used it to ruin your Windows installtion.  Its a great plan, however...   ;-) 

 :)

---

### Post by LobsterSan on 2005-04-22
Well, the two responses above are both pleasing and distressing in different ways.  Distressing because I though my winxp system was pretty failsafe.  Pleasing because that perhaps, indeed, Linux is more secure.  What I find strange, however, is the particular timing of the incident.  I had been running my current winxp system just fine for about a month now (I recently built a new computer), but just a few days after installing ubuntu this happens.  I suppose it may be just coincidence, but the thought did cross my mind that some avid Linux hacker saw my dual-boot system and decided to teach me how to use ubuntu by brute force.  I actually wouldn't mind this type of tough-love so much if the reason why I was booting into winxp was to backup a couple of files I had forgotten about before.  As well, the whole invasion of privacy aspect of it is fairly humiliating as well.  But hey, if it makes me into a hardcore Linux expert, then the Tyler Durden approach may not be such a bad thing (though i don't particularly like being associated with Raymond K. Hessel).

In any regard, I will be reinstalling winxp with even more safety nets in place.  I'm just going to be better about backing things up and I'll give Linux another go (though I'm considering an even more automated release than ubuntu, as I'm finding it's taking me considerable time to get my system setup the way it should be... usb soundcard, external hd's, and other possibly unsupported devices are really eating up my free time).

---

### Post by nocturn on 2005-04-22
The Ubuntu kernel does not have NTFS write support compiled in.
Therefor, it is impossible that something running under Linux modified your NTFS partition.

It is good and well possible that you were cracked, but it would be the Windows system that got hit, as it is the only venue to changing the NTFS partition.

Good luck.

---

### Post by ubuntu_demon on 2005-04-22
Your windows is probably hacked. A computer connected to the internet can never be 100% safe but a default installation of Ubuntu that's fully updated comes really close. Only pro hackers have the ability to get in and the chance that such a hacker targets YOUR system is close to 0.0000000000000000000000000000000000000001% or something.

(although you can make it hackers really easy to get in .. like installing telnet or ssh and using a very very stupid password such as your own username)

edit :
see also this thread :
[http://www.ubuntuforums.org/showthread.php?t=28858](http://www.ubuntuforums.org/showthread.php?t=28858)

---

### Post by ghost on 2005-04-22
[QUOTE=demon666_nl]Your windows is probably hacked. A computer connected to the internet can never be 100% safe but a default installation of Ubuntu that's fully updated comes really close. Only pro hackers have the ability to get in and the chance that such a hacker targets YOUR system is close to 0.0000000000000000000000000000000000000001% or something.

(although you can make it hackers really easy to get in .. like installing telnet or ssh and using a very very stupid password such as your own username)[/QUOTE]

The best way is block all incoming port.  :) 

By the way, you meant Cracker not Hacker. Cracker is the bad guy. I am an ethical Hacker, work in a well known Information Security Firm. And I hate people keep on mixing up the 2 terms.

Going back to the original post. Windows is just bad in design, that is why there are so many security holes. But if you truely lockdown your Windows XP box, it can be pretty safe. 

Here following this guide to lockdown your XP [http://www.nsa.gov/snac/downloads_winxp.cfm?MenuID=scg10.3.1.1](http://www.nsa.gov/snac/downloads_winxp.cfm?MenuID=scg10.3.1.1)

---

### Post by ubuntu_demon on 2005-04-22
[QUOTE=ghost]

By the way, you meant Cracker not Hacker. Cracker is the bad guy. I am an ethical Hacker, work in a well known Information Security Firm. And I hate people keep on mixing up the 2 terms.

[/QUOTE]
 yeah you are right but I was afraid he wouldn't know the term cracker

---

### Post by nautilus on 2005-04-22
Hmmm....

Is this system a dual-boot?  Maybe somehow your Windows partition was affected by the partitioning process, or some partition resizing...?

Does the Ubuntu side still work properly?  The reason I ask is, between a cracker getting into an Ubuntu system and going through the pains of modifying a partition s/he likely doesn't even know exists, one would think they would sooner trash the currently-active filesystem.

Another possibility is you were logged into your Ubuntu system as root and accidentally streamed some junk into your Windows partition..?

---

### Post by heimo on 2005-04-22
[QUOTE=nocturn]The Ubuntu kernel does not have NTFS write support compiled in.
Therefor, it is impossible that something running under Linux modified your NTFS partition.
[/QUOTE]
 
I really tried to resist. But it's not impossible. Very, very, very unlikely, yes. But if someone somehow got access to that computer, dropped in (or compiled right there) a new kernel with NTFS read-write support (it has to be compiled into the kernel, not available as module, as far as I know), made the computer to reboot... Mounted NTFS partition and messed it up...
 
Oh. Sorry guys. Sorry... But it's not impossible. (Just too many ifs in there.)
 
I'll just shut up for now. :-#
 
EDIT: I break my promise. Of course you don't need read-write support to mess the partition on lower level. You don't need to use filesystem to do that.

---

### Post by ghost on 2005-04-22
LobsterSan: This is the only way you know the truth. If you remember the date and time when this happened. Go into your logs, and history files. Match the time and date, you will see if Linux is the path which damaged your XP.

---

### Post by nocturn on 2005-04-22
[QUOTE=heimo]I really tried to resist. But it's not impossible. Very, very, very unlikely, yes. But if someone somehow got access to that computer, dropped in (or compiled right there) a new kernel with NTFS read-write support (it has to be compiled into the kernel, not available as module, as far as I know), made the computer to reboot... Mounted NTFS partition and messed it up...
 
Oh. Sorry guys. Sorry... But it's not impossible. (Just too many ifs in there.)
 
I'll just shut up for now. :-#
 
EDIT: I break my promise. Of course you don't need read-write support to mess the partition on lower level. You don't need to use filesystem to do that.[/QUOTE]

Yes you can, hell, you can even vi /dev/hda1 ;-)

But to insert a trojan that deletes dll's at windows boot...  well it is a hell of a lot of work for no aparant reason.

---

### Post by LobsterSan on 2005-04-22
Thank you all for the valuable input.  I took a look at the logs (by just going through the gnome GUI to the log section... is there a more thorough way to do this via the terminal?).  It doesn't appear that any strangeness occured on the Linux side of things, though It seems that root access is made every hour for less than one second.  I'm not sure if that is normal behavior or not.  The lines read as follows:

09:17:01 PM localhost CRON[13456] (pam_unix) session opened for user root by (uid=0)
09:17:01 PM localhost CRON[13456] (pam_unix) session closed for user root

I will be going back and redoubling my efforts to keep my winxp system a bit safer this time around.

Also, how does one actually log in as a root user?  And if I can do it from here, what's to stop someone gaining access to my root account?

---

### Post by BAshworth on 2005-04-22
You shouldn't need to log in as root for Ubuntu.  Just use 'sudo' during your terminal sessions.

There are scripts you can put into Nautilus to open up a file brower with root access, or to be able to open a single file with root access.

As far as WinXP goes, I use PC-Cillin Internet Security 2005, and absolutely love it.  It costs $50 initially, but some places offer full rebates for it, so it ends up costing nothing.  It's a firewall, antivirus, anti-spyware scanner, and spam filter.  Unlike Norton's Internet Security suite though, it doesn't bring your system to it's knees performance wise.  The antivirus engine scores higher than most of the others too.

Just my two cents on that.

---

### Post by nautilus on 2005-04-22
Cron is a periodic tasks daemon.  It opens a session, does things, and closes a session.  It does things such as logfile rotation.  Since some logfiles are sensitive, it does so as root.  If you don't like it, edit /etc/crontab and remove the lines, but... I suggest highly you leave it as is ;)

---

### Post by ubuntu27 on 2005-04-26
By the way, here our ubuntu brothers discussed about Antivirus in Linux: [http://www.ubuntuforums.org/showthread.php?t=27828&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=27828&page=1&pp=10)

---

### Post by davahmet on 2005-04-27
Hello LobsterSan,
First off, let me offer a sincere condolences for the annoyance of what happened.  I know it does look very coincidental and I think there is a possibility that your new Ubuntu installtion may have been a contributing factor.  I'll explain that shortly.

As many others have said, Ubuntu by default does not have write access to the NTFS in Win XP.  It can be done, but not without considerable difficulty and especially not remotely without quite a lot of very unlikely conditions being met on your Linux system.

However, you indicate that you have had Windows XP for quite a while beforehand, so I can offer a possible theory that does bring your Ubuntu installation into the picture.  Consider if your Windows XP partition had been carrying a silent infection.  Most Windows boxes do have silent malware if they have been connected online for any length of time.  Anyhow, this infection sits there, active but mostly harmless, un-noticed by the user, AV software and scanners.  Stealthing is old technology, and well-developed in the cracker community.  If something environmental changes in such a way that the hidden malware reacts badly, it is entirely feasible that either the malware, the anti-virus software, or the Windows OS itself may be triggered into removing files, with shared library files (such as DLLs) being particularly vulnerable because of their system-wide exposure.  Considering the horrible architecture of Windows, the behavioral characteristics of most malware types, and the way that Ubuntu accesses filesystems, I think it far more likely that the new installation triggered such a hidden bomb than actually erasing anything.

As far as comparitive security, a Linux distribution is only as secure as its default settings and the user that changes them.  That is, some are very good by default while others are not much better than Windows.  Ubuntu still is quite good and much, much better than Windows XP when it comes to default security.

Zonealarm and AVG are definitely positive steps for securing Windows but cannot do it all because of problems in Windows design.  Both Zonealarm and AVG are software systems that run on the application layer of Windows.  They block much of the bad stuff, but have little ability to block malware riding in code at lower levels, which Windows unfortunately accepts into the OS kernel because fo the shoddy way that Windows handles the kernel/user space boundary.  So, while they are a good idea for security, they will not catch everything.

I seemed to have rambled rather longer than I wanted to, LobsterSan.  Hopefully you will find the answers here enlightening and helpful.  And welcome to Ubuntu, where users can again own the computers.

---

### Post by p.i.m.p on 2006-08-17
hey wats up ppl.. just switched to ubuntu from fedora and everything works flawlessly.. well almost everything and the stuff that doesnt work out of the work can usually be fixed by searching on this forum.. ubuntu seems to have one of the best communities hell its the best community...

now sorry to bring up this thread again it seems to be pretty old but came across it on google.. i faced the same problem while dual booting with windows TWICE and came to the conclusion that it happens wen u dont unmount the windows partition properly in linux.. like if u dont shutdown properly while having the windows partition mounted :rolleyes:

---

### Post by aysiu on 2006-08-17
I have another hypothesis (maybe someone can tell me if it's bunk, but I'll just throw it out there):

Maybe you didn't defragment Windows fully before you resized your partition and installed Hoary? If not, maybe the resizing process damaged some .dll files?

---

### Post by peabody on 2006-08-24
I hate to ressurect this thread too, but I'll bet $20 that it wasn't due to a virus, spyware, or Ubuntu, but rather the repartitioning.  If there was anything wrong with the ntfs filesystem before the resizing, it's likely this would scrag the ntfs partition.  One should always seriosly backup before attempting to move around partitions.  It is a very dangerous operation.

---

