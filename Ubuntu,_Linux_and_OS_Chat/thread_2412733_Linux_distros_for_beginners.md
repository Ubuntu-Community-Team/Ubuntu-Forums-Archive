---
title: "Linux distros for beginners?"
date: 2019-02-16
forum: Ubuntu, Linux and OS Chat
---

### Post by mbeechey on 2019-02-16
I am using Zorin and Ubuntu and Mint on different computers to avoid Msoft, which I can't support, but I notice a difference at the beginner level. Some tasks in different distros seem straightforward, others seem impossible for a beginner, depending on the distro. Sometimes i have to use my Win7 boot just to get something done. Any suggestions?

by tasks i mean mainly installing work arounds/patches..many times i do a sudo command i have copied from a post and terminal says it doesn't exist

thanks in advance!,

---

### Post by wildmanne39 on 2019-02-16
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by freemedia2018 on 2019-02-16
The concept of distros for beginners is great, but it really just comes down to included software and reliability. If you have a good package manager (I like the Debian/Ubuntu family for this) and a good desktop environment and a reliable system, you're good.

Where that falls apart (I've got years of experience but suppose I'm recommending something that is easy to support for someone less experienced) is when they throw together some friendly software, but it changes a lot or is unreliable.

Any distro that is reliable and has good support can help you add a desktop that is easier to use. But not every "beginner-friendly" distro has good support or will prove reliable-- which is just as bad as being unfriendly. 

If Xubuntu (my favourite version of Ubuntu) isn't friendly enough for you, then IMO you might as well use something like Puppy or Refracta-- Refracta is well-supported and reliable, and Puppy is often considered friendly (but you'll learn that you can customise everything.) Puppy has a "everything as Root" philosophy which can make Debian/Ubuntu fans wince, Refracta does not. Xubuntu uses XFCE as the desktop, which to me has proven reliable and easy to use since 2007, Refracta uses XFCE too. 

But if you note the features of whatever "beginner-friendly" distro you find, chances are you can install similar components (very easily) in Ubuntu, Xubuntu or whatever distro proves reliable to you. Depending on who you ask, installing a different desktop may or may not be considered a beginner task, but if it's not then I'm not sure the distro is friendly enough anyway. "sudo apt-get install desktopname should really be all it takes." I wouldn't use a desktop that was more than trivial to install.

---

### Post by poorguy on 2019-02-16
> **mbeechey said:**
> 
by tasks i mean mainly installing work arounds/patches..many times i do a sudo command i have copied from a post and terminal says it doesn't exist

thanks in advance!,

Ubuntu and Linux Mint are good choices for a new user wanting to learn and use Linux as both offer excellent support forums.

I copy and paste commands when using the terminal to avoid mistakes.

Mistakes in the command is generally where the statement pops up saying the command doesn't exist.

---

### Post by TheFu on 2019-02-16
Similar questions in other threads here:
[https://ubuntuforums.org/showthread.php?t=2409967](https://ubuntuforums.org/showthread.php?t=2409967) 
[https://ubuntuforums.org/showthread.php?t=2412525](https://ubuntuforums.org/showthread.php?t=2412525) 
[https://ubuntuforums.org/showthread.php?t=2412511](https://ubuntuforums.org/showthread.php?t=2412511)
Might be helpful.  IDK.

Some good, free, no-hassle, beginner CLI/Shell guides:  
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
[https://wiki.lpi.org/wiki/Free_Training_Materials](https://wiki.lpi.org/wiki/Free_Training_Materials)

And there are free online courses taught by world-class professors at [https://www.edx.org/](https://www.edx.org/) and different affiliates. 

But none of this is point-n-click. For that, we are stuck using GUI-specific resources which are constantly changing: [https://help.ubuntu.com/](https://help.ubuntu.com/) has those for the normal Ubuntu desktop.

Anyways, I hope this is helpful in some way.

---

### Post by oldos2er on 2019-02-17
> **mbeechey said:**
> I am using Zorin and Ubuntu and Mint on different computers to avoid Msoft, which I can't support, but I notice a difference at the beginner level. Some tasks in different distros seem straightforward, others seem impossible for a beginner, depending on the distro. Sometimes i have to use my Win7 boot just to get something done. Any suggestions?

by tasks i mean mainly installing work arounds/patches..many times i do a sudo command i have copied from a post and terminal says it doesn't exist

thanks in advance!,

Copy/paste the commands and their output so that people may do more than just guess at the problem.

---

### Post by Frogs Hair on 2019-02-17
I have collected commands via copy/paste in text document  since  beginning to use Ubuntu and categorizing them by function. Most will work in any Debian based disto which Ubuntu, Mint and Zorin are.

---

### Post by mbeechey on 2019-02-18
if Zorin isUbuntu based, why does the functionality differ? The interface is different of course, but some tasks don't work the same, add ons seem to be different, a wifi printer will install on one and not even be seen on another. Lots of examples I have come across, will have to log them from now on. Just a general question at this pt.

---

### Post by mastablasta on 2019-02-19
> **mbeechey said:**
> if Zorin isUbuntu based, why does the functionality differ? The interface is different of course, but some tasks don't work the same, add ons seem to be different, a wifi printer will install on one and not even be seen on another. Lots of examples I have come across, will have to log them from now on. Just a general question at this pt.

you can install ubuntu mini.iso / barebones / netinstall... whatever they call it now. and then you can add only things you want. if you go this way, you get an OS in the end that is Ubuntu based, but will have things missing from it because you didn't choose to install them for example. 

then another difference is the kernel they use. f they use an older kernel they might be using different driver. or if they chose not to add all patches, again something will be missing.

i once installed from the mini iso to virtualbox. i added only minimalistic. it had plenty of stuff missing bu tit was ok as i didn't need it. end result was a faster and lighter os specifically designed to test certain things.


you have bitnami stack for example with turnkey images that have minimal Ubuntu OS+specific web service (e.g. wordpress). very good for testing stuff. but many things on it won't work eventhough they work in Ubuntu. still since it is Ubuntu based they can be installed and setup.

for example: Ubuntu has firewall disabled, Mint has it enabled. Ubuntu doesn't have restricted extras preinstalled, mint has it. neither mint nor ubuntu have ssh or fail2ban, preinstalled. and they also do not have unatended upgrades enabled. these are all things i immediatelly add to Ubuntu server. and some Ubuntu based server distros would have them preset or at least enabled and you would have to set them up.


For me Kubuntu (or rather KDE) offers the easiest switch in GUI from windows to linux. 

as to your issues needing a windows 7 boot - the only reason you need to boot in windows 7 to resolve a problem is if you are trying to (need to) run a windows application. they are not made to run in linux and they do not usually run in linux. though some do via wine, crossover, proton or lutris. most will run in a virtual environment such as virtualbox (as long as they are not too graphically intensive).

---

### Post by CatKiller on 2019-02-20
> **mbeechey said:**
> many times i do a sudo command i have copied from a post and terminal says it doesn't exist

Don't do that. Don't ever do that.

Blindly pasting instructions that you don't understand, from random places on the Internet, particularly if they require elevated privileges, is exactly how you end up with a broken system that you don't know how to fix.

How "friendly" a distribution seems to a new user is almost entirely down to the desktop environment, and particularly how discoverable everything is. I would say that KDE works well for that, and Gnome, with their drive to remove all options from everything, works very badly. Cinnamon I would put somewhere in between. The other part of it - having things work out-of-the-box - is broadly equivalent in any modern release, whichever distribution it is.

---

### Post by TheFu on 2019-02-20
> **mbeechey said:**
> if Zorin isUbuntu based, why does the functionality differ? The interface is different of course, but some tasks don't work the same, add ons seem to be different, a wifi printer will install on one and not even be seen on another. Lots of examples I have come across, will have to log them from now on. Just a general question at this pt.

Never used Zorin. Don't know anything about it, but to answer that question, perhaps asking the Zorin team would be more effective?

What goes into a distro is a compromise.  Nobody wants to download 10GB of a distro when only 400MB is needed. Perhaps the 400MB distro cannot include every driver and setup for new/unpopular printers.

---

