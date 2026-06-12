---
title: "Ubuntu i want to love you, but you dont let me"
date: 2016-04-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Filipe_ribeiro on 2016-04-01
So again, i am trying to switch from windows to linux, in 2 years i have a couple of attempts, atm i only have one pc that is running ubuntu just for web and stuff like that, i had a windows machine with multiple harddrives running plex media server and virtual machines, one of them ubuntu.

So i though, wth, let transform that machine into linux.

So there is the issues that i found;

1-Localnetwork sharing, i needed something called samba so i can see my windows local network...OK it was not that difficult to use once you know about it, but when you google you fund a bunch of tutorials with a codes and stuff.

2-Amazon, why is that there in the first place? After googling i find something called gnome and how to deactivate the Amazon, fine, i installed gnome, BUT for the love of god, accidentally i deleted one top bar out of it, it was the end, spent 1 hour how to get it back, when i did, the icons where missing i had to place them again, wth, why such hassle for something that should be simple....i did a fresh install again.

3-And now comes my number 1 nightmare, i have 4 hdd, 1 where i installed ubuntu, the others for my data, the other 3 appear to be always as external drives...ok who cares, as long i can use them, then i installed plex, nice, now lets configure plex, wtf, where are my folders?? seems there is permissions issues, so i need to give plex permission to see what the hell is inside my hard drives, again googled, with many tutorials that i dont understand, boring crap for something that should be simple to use, i just need plex to get to my media folders that are not on the OS drive, dear lord.
I am ok with some times use the terminal, but i dont like to fell like i am hacking nasa, just to give permission for some program to access my drive...Sadly i have giveup.

Linux, we regular users, dont want to deal with stuff like that, we dont want to spend hours to fix simple stuff, we just want to use the OS, i am sry, i realy want to use it, but i cant deal with stuff like this, there is always something missing, always something to code or to install

---

### Post by howefield on 2016-04-01
Thread moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by ian-weisser on 2016-04-01
Seems like a recurring discussion.

Ubuntu is not a Windows clone. It's not trying to be.

1) Windows' fault. You paid Microsoft money for the valuable feature of not recognizing other networking methods. Complain to them.

2) Done. You'll be happy to know that Amazon recommendations are gone from 16.04.

3) Your fault. Your system is not psychic, and has no idea what you want Plex to be able to access. Simply assign ownership in the way it understands. Not difficult after you make the minor effort to learn how.

You are not an Ubuntu customer. And we are not a complaint department.

You are very welcome to be a part of the Ubuntu Project - your feedback has the potential to become valuable. But only if you are involved.

---

### Post by buzzingrobot on 2016-04-01
> **Filipe_ribeiro said:**
> Linux, we regular users, dont want to deal with stuff...

You're first error seems to be Googling randomly for advice. A considerable amount of Ubuntu-specific help is available online in sites maintained by Canonical and otherwise. Until you acquire the skills and experience needed to distinguish good advice from bad, you really ought to avoid blindly doing whatever a site you found in Google tells you to do,.

This applies equally to new Windows or new OS X users looking for help.  Nothing really to do with Linux or Ubuntu.

The "Amazon" feature can be disabled via a click in System Settings. It is not hidden.  You certainly did not need to install Gnome, which is a large, complex and entirely different desktop environment, to accomplish that.

Windows, Linux and OS X are different operating systems.  Habits formed in one usually do not transfer smoothly to another. It's not realistic to expect otherwise.

---

### Post by Filipe_ribeiro on 2016-04-01
Now i have one permanent ubuntu pc, and then one running in virtualbox (so i can try and error stuff), i hope to get there slowly, but this is me, many users will freakout as i did and simply quit, i know there is many linux distro, but seems they work prety much the same.

Plex forum is full of ppl that dont know how to give permissions, please, tell me where is a good place to lear the ubuntu basics, i am not mr robot :p
Linux is not easy to use when you try to do stuff like i do apart from the regular web browsing.

All i need from my windows box is, plex, virtual machine, remote desktop, backup files (local network, mixed* windows and linux pc), i am only missing the plex, i am close, but so far

---

### Post by oldos2er on 2016-04-01
I found [this]("https://support.plex.tv/hc/en-us/articles/200288606-Mounting-NTFS-Drives-on-Linux"), but maybe you've already seen it. You haven't told us which file systems are in use on your other hard drives, so I'm assuming NTFS.

Tutorials frequently use "codes" i.e. commands to be entered into a terminal because it is far simpler to do that than to provide instructions to accomplish the same task for every desktop environment and/or window manager that might be in use.

---

### Post by Filipe_ribeiro on 2016-04-01
i Have tried both NTFS and ext4

---

### Post by mastablasta on 2016-04-04
> **Filipe_ribeiro said:**
> 
1-Localnetwork sharing, i needed something called samba so i can see my windows local network...OK it was not that difficult to use once you know about it, but when you google you fund a bunch of tutorials with a codes and stuff.

right click, share folder. whew that was difficult....

> 
2-Amazon, why is that there in the first place? After googling i find something called gnome and how to deactivate the Amazon, fine, i installed gnome, BUT for the love of god, accidentally i deleted one top bar out of it, it was the end, spent 1 hour how to get it back, when i did, the icons where missing i had to place them again, wth, why such hassle for something that should be simple....i did a fresh install again.

turn it off. type Privacy -> flip the show advertisements switch to off. yet another hard task accomplished.

> 
3-And now comes my number 1 nightmare, i have 4 hdd, 1 where i installed ubuntu, the others for my data, the other 3 appear to be always as external drives...ok who cares, as long i can use them, then i installed plex, nice, now lets configure plex, wtf, where are my folders?? seems there is permissions issues, so i need to give plex permission to see what the hell is inside my hard drives, again googled, with many tutorials that i dont understand, boring crap for something that should be simple to use, i just need plex to get to my media folders that are not on the OS drive, dear lord.
I am ok with some times use the terminal, but i dont like to fell like i am hacking nasa, just to give permission for some program to access my drive...Sadly i have giveup.


no we do not want all programs to have permission to access all OS areas. this was avaialble in DOS and later in first windows version and i don't know if you were arround at that time when PC's could very easily be infected. access is limited for a security reason.

giving access is not that difficult. it involves right clicking in file manager and giving access to folders/disks. this is the same in windows except in windows you still get full access to new disk. even if it has malware that will take over your computer windows will hapilly mount it and autorun stuff.

---

