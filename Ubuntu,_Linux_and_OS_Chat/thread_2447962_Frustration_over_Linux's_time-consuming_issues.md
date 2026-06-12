---
title: "Frustration over Linux's time-consuming issues"
date: 2020-07-29
forum: Ubuntu, Linux and OS Chat
---

### Post by LK_gandalf_ on 2020-07-29
Hi all, I just wanted to share some frustrations and maybe get some motivations to keep trying. I've been a Linux user for over 15 years, never pretended to be an expert but I want to keep using it and support the idea (years ago I even created a blog with a first-time installation and setup guide of Kubuntu/Ubuntu).

As life goes on, one typically has less and less time to spend fixing the many issues that unfortunately still plague Linux.

Most recent example. Approaching photography, I really want to learn Gimp and Darktable instead of bowing to the monopoly of Adobe. Of course I want to use these softwares on Linux, and not on Win10, since these should work perfectly on Linux, right?
I install Darktable and it works ok, but I had to search online and fix some graphical issues.
I install Gimp and it cannot open my raw files and the error message does not help. I search online for a solution, nothing works. Someone recommends to uninstall Gimp from the software center and install it from a PPA. The PPA, I find out, it's no longer mantained, so let's try another one. I install Gimp again from this new PPA. It seems it opens the raw files....but now a different error message. The idea of spending more time to fix this, and have a software depending on some guy's willing to mantain a PPA is not tempting.

I wanted to spend the hour I had available watching a tutorial and learning to edit in Gimp. Instead, I spent almost the whole hour just dealing with the issue. Frustrated, I turned to Win10, quickly installed Gimp with the one unequivocal way to install it (an .exe), and opened my raw files without any problem.

Anyone sharing similar frustrations? What keep you sticking with Linux?

---

### Post by monkeybrain20122 on 2020-07-29
> **LK_gandalf_ said:**
> 
Most recent example. Approaching photography, I really want to learn Gimp and Darktable instead of bowing to the monopoly of Adobe. Of course I want to use these softwares on Linux, and not on Win10, since these should work perfectly on Linux, right?
I install Darktable and it works ok, but I had to search online and fix some graphical issues.
I install Gimp and it cannot open my raw files and the error message does not help. I search online for a solution, nothing works. Someone recommends to uninstall Gimp from the software center and install it from a PPA. The PPA, I find out, it's no longer mantained, so let's try another one. I install Gimp again from this new PPA. It seems it opens the raw files....but now a different error message. The idea of spending more time to fix this, and have a software depending on some guy's willing to mantain a PPA is not tempting.

I wanted to spend the hour I had available watching a tutorial and learning to edit in Gimp. Instead, I spent almost the whole hour just dealing with the issue. Frustrated, I turned to Win10, quickly installed Gimp with the one unequivocal way to install it (an .exe), and opened my raw files without any problem.

Anyone sharing similar frustrations? What keep you sticking with Linux?

If you just install gimp from the repo you won't have any problem. 

This is not a general linux issue but because Ubuntu offers a variety of ways (2, or potentially 3 if you get the flatpak plugin) to install some software (like gimp) in the software store. You have an older version from the repo and a snap version (check the publisher in the description, if it is published by snapcraft than it is a snap) The snap is a kind of experimental way to distribute software more quickly and in an up to date manner but the catch is for some software (like Gimp) the sandboxing prevents it from accessing external plugins. 

But just to confuse you a bit more, GIMP itself publishes a flatpak for Linux on its download page, which has the same sandboxing issues as the snap, but there is also an [appimage]("https://appimage.github.io/GIMP/") for Linux, it is up to date and can access external plugins like Darktable, and it doesn't need installation.

Little things like these can be frustrating because there are many options in Linux, I think the software store needs to provide more information about the snaps and their possible limitations (probably you can find them in the comments in the Software store) but it doesn't take too much effort to learn about them on forums like this. Windows has its own oddities for the uninitiated too (look at Windows forums for frustrated customers and all the weird registry hacks that might blow up your system)

The PPA is maintained by a member of the Ubuntu community, not Canonical or GIMP, so that is kind of an added bonus for Ubuntu users. It seems that he has been preoccupied with other things and haven't updated his repo since 19.10. With the way 2020 is going really can't blame him.

---

### Post by mastablasta on 2020-07-30
from experience point i was battling with old game (from GOG) in POL. i tried different setups. i must have spent a few hours. i got frustrated, so i checked the issue. as it turns out some cnan't even get it to run in windows 10 at all. or they faced same issue. 

i then combined this internet knowledge and setups and i tried this crazy idea. and it worked. it's amazing but game runs flawlesly now in linux. it turns tou you run an exe which crashes, then you run the 64bit exe and it runs the game menu and then the game itself. i was more upset a the lack of information when  the error sows up. getting correct information form the start would help solve this much faster.

anyway i ran another GOG game in windows XP about 2 years ago. no matter what i tried and guide i followed the game has substantial lag. i reduced resolution manually fiddle with config files, reinstalled it a couple of times, set all on low, added some commands manually, yet the game ran badly (low FPS on many places). but it ran somewhat and i really wanted to play it, so i played it. not the best experience, since it was a FPS game. many cutscenes were off or had lag. then (after installing linux on the same PC) i saw it has platinum rating on linux. so just for fun i though i would give it a go, see how it behaves. i expected major lag, but i wanted to see what areas would show the difference if any. well as it turns out - same game, same install file with no fiddling arrund, the game runs well on medium/high settings. it very rarely has frame drop/stutering. amazing.

in short i don't think it is the OS, but more the apps themselves and miantenance. yes linux is still quite rough, but it is usable. with Win10 getting updates shoved down the users throat and at the same time having major issues with them (no printing. network access lost, deleting user files...) and rising not only in size but also (again?!) ram usage, i think Linux offer some good alternatives. it is often not ideal, but neither it's on win10. i was very surprised reading how people have issues with windows games. not just playing them (ie.e. bugs during gameplay), but their problems often already start when they install them and run them. and they are made for windows and the seller "guarantees" compatibility with win10, yet they don't even run?!

---

### Post by zebra2 on 2020-07-30
My entire Ubuntu experience with three laptops is absolutely wonderful, with Ubuntu 20.04 on one system, Ubuntu 20.10 on another and 20.10 and Windows 10 dual booting on the third. All use Wayland and they are perfect with everything we do. 

I think a lot of the confusion which in part has been already explained is that the Linux community is spoiled rotten by having a very secure system and we don't fret much a hackers and virus's and the like.  But the community is still tightening up their game with all of the sandboxing and other solutions in the dependencies. I didn't know I needed all of this but am getting it anyway. There is a learning curve involved just when I thought I "knew it all". 

Windows 10 runs on Windows 10 systems with drivers provided by the device producers.  Linux is expected to work on every thing that show up at the big store plus all of the IOT and other gadgets and most people don't even know it is there. All I can say about all of this is "Thank God for Linux".  And Microsoft is the biggest supporter. 

Sorry about your problems and your need to go back to the figure it all out mill. I agree with everyone else that has posted on this and other threads like it. My systems have built in Windows licenses and I only use my Windows partition for taxes and Garmin updates. After I get through installing all of the Windows updates just for turning it on. 

Ironically my Garmin has a linux kernel but only updates in Windows and Garmin just had all of their Windows servers hacked and locked down with ransomware. I think they rebuilt from backups but it had the exercise world spinning for a couple of days.  FYI Gee what a rant! I feel better already!

---

### Post by LK_gandalf_ on 2020-07-30
Thanks, good perspectives :) I agree, I've always thought that Linux is superior in many ways, and it's not Linux itself which causes the problems, but many other reasons in particular the simple fact that most producers, developers, etc do not provide software and support. The community-based approach helps working magic in spite of this (as you mention, Linux works on so many machines in spite of not having drivers etc), but it also create confusing ways of doing things sometimes.

However, the focus of my post is not on the reasons, but on the end result. In my long-term experience with Linux and Windows I must unfortunately observe that I have spent much more time fixing things on Linux than on windows. Much more time. While this can be funny and stimulating sometimes, it's also frustrating when you have limited time and you just want to get things done. 

I think that you need some value-based motivations to use Linux over other better supported systems. I believe in the strong need of having softwares that are not grabbing all possible data about your behaviour and using the data to predict what you want and sell your commercial preferences to companies (btw, many here are surely interested in the topic, I recommend the brilliant book "Surveillance Capitalism" by Harvard professor Sjoshana Zuboff). I believe in stuff developed and supported by the people and not only by private unaccountable companies. But it's hard, and values get tested continously :)

---

### Post by SeijiSensei on 2020-07-30
I only install software from the repositories. I avoid things like snaps and flatpaks like the plague.

---

### Post by CatKiller on 2020-07-30
> **LK_gandalf_ said:**
> I think that you need some value-based motivations to use Linux over other better supported systems.

I didn't. 

I didn't mind Windows. I'd used it for a while. I was reasonably comfortable with making it do stuff. I tried Ubuntu out of curiosity and immediately saw that Ubuntu was superior. I stopped using Windows, since it wasn't as good. That was 15 years ago. 

Free software is an entirely pragmatic approach. Sure, there are people that think that it's also *fairer*, or *nicer*, or *more ethical*, but just the pragmatism is sufficient.

---

### Post by sdsurfer on 2020-07-30
There are plenty of people here who can help you. When you say *raw files,* what format does this mean? I know if I shoot from my Nikon in RAW format, they have to be converted to a format the program understands, even in Photoshop. You may just need to install a plugin and *import* the files, not open them (which was exactly what I had to do with Photoshop under Windows.)

---

### Post by TheFu on 2020-07-30
> **LK_gandalf_ said:**
>  
Anyone sharing similar frustrations? What keep you sticking with Linux?

Because the other OS options are much more frustrating.  

If you are only a point-n-click user, then you are missing 80% of the power that Linux provides, especially for automation.  If you shy away from creating a 5 line script to batch process hundreds of files, then Unix-like systems probably aren't for you.

I don't use the Canonical GUI stuff much. This is the first way I avoid frustrations. No confusion about which type of package will be installed when I type **sudo apt install {package}**.  I'm using the same window manager that I've used for 10+ yrs or for 25 yrs, so the GUI doesn't change with each new release.  25 yrs ago, we had pretty great window managers - and they were lite, worked fast on 8 MB systems of that time.  Now with 8, 16, 32GB of RAM, I'm amazed that a DE can still make a computer feel slow.

Sure, there are little projects that I go off and do, to make my network more convenient or more secure.  I've done hundreds of those.  Some that I estimate for 2 hrs of effort turn into much more spent over weeks, but those are self-inflicted almost always.

If you find that Linux isn't working in the way you need, that's too bad, but you should choose which OS provides the tools, security, and user happiness that you want.

And as much as I use Linux (which is a bunch, daily), I still have Windows for financial stuff and a different Windows machine for video editing.  

The Linux tools aren't as good for my needs in those 2 situations.  Earlier this year, I replaced scheduled OTA TV recording on Windows with some scripts I created. The massive Linux solutions were so much more than I needed. 3 scripts handle it all now, including finding where commercials are in each recording in a file format supported by my Windows video editor, but not supported by **any** Linux-based video editors. So very sad and slightly frustrating.  For a few hours, I looked into creating my own Linux video editor that would replace the Windows tool used. I already do some CLI-based editing today, so the editing part is already solved, it is just the GUI and cut-segment confirmation parts that I'd need to solve. Anyways, it quickly became a much harder problem than I was willing to tackle.

Even with all those issues - I won't allow a Windows system to access the internet. I don't feel there is any way to secure them sufficiently to allow that - except to a few, specific, web-app sites.  Ever gotten a virus on Windows? I haven't, but relatives have. They'd call and ask for help cleaning.  On Linux, I can wipe the system, do a fresh install so I 100% know there isn't any virus, restore my data, settings, apps, all in 30-45 minutes. A few weeks ago I did that after a grub problem happened. After wasting about 15 minutes trying to fix it - I'd had enough - fresh install, used my backups to restore. Less than 45 minutes later, I was back, with "my" system, my files, my settings and all programs loaded.  On Windows, I'd probably have to spend a week or two getting everything back.

But what works for me doesn't work for everyone. People should use the system that makes them the most productive and happiest.

---

### Post by mastablasta on 2020-07-31
> **LK_gandalf_ said:**
> 
However, the focus of my post is not on the reasons, but on the end result. In my long-term experience with Linux and Windows I must unfortunately observe that I have spent much more time fixing things on Linux than on windows. Much more time. While this can be funny and stimulating sometimes, it's also frustrating when you have limited time and you just want to get things done. 
 

yes, we can safely say that it does need more tinkering that windows, as soon as you need something outside of the repositories. 

on the other hand, to install malware and make it work, is also much easier on windows :). well maybe not so much these days (ms store, various antivirus and firewalls built in...), but these days (or after firing the "army of testers") they would create problems themselves.

---

### Post by VMC on 2020-07-31
> **SeijiSensei said:**
> I only install software from the repositories. I avoid things like snaps and flatpaks like the plague.

Amen to that! snap & flatpaks are the first to go on all my systems.

Xubuntu has Gimp installed, and I have yet to have any issues. Then again, each user has their own agenda. Many of Gimps abilities I don't use.

---

### Post by ajgreeny on 2020-07-31
Interestingly, during my time using Windows, which started with 3.1 and finished with XP, I suspect I spent as much time tweaking and tinkering with things if not more than I do now in Linux, in my case Xubuntu.

I thoroughly disliked the way the file manager looked and acted so always spent quite a lot of time messing around with that to get it to show everything that I wanted; why on earth did they hide by default all file-name suffixes, eg, .doc, .jpg etc etc for known file-types?  That makes no sense at all to me, particularly in an OS where the suffix is more important than it is in Linux.
There were many other things I used to tweak but 15 years without using Windows means I have forgotten most of what I did and why I did it.  All I do know is that the defaults for all Windows version setups that I used were not to my taste and I changed them all.

On the odd occasion that I have to now use Windows I find everything a lot more time-consuming that my Xubuntu system which after an initial setup to my liking just works for me, generally totally trouble-free.

---

### Post by monkeybrain20122 on 2020-07-31
> **VMC said:**
> Amen to that! snap & flatpaks are the first to go on all my systems.

Xubuntu has Gimp installed, and I have yet to have any issues. Then again, each user has their own agenda. Many of Gimps abilities I don't use.

As long as you know the limitations there is no harm (if any, since not all apps got crippled because of sandboxing like Gimp). I have a few flatpaks and they work great.

---

