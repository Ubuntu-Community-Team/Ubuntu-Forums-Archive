---
title: "My experiences with Ubuntu"
date: 2007-08-25
forum: Testimonials &amp; Experiences
---

### Post by treis on 2007-08-25
Hello all.  I came over to Ubuntu because Microsoft/Vista pissed me off.  I wanted a new laptop and I found an HP one that I liked.  However, I knew that, despite the Vista Capable tag, the machine was going to be underpowered for Vista.  I called up HP to see if I could get XP on the machine instead and I got a big negatory.  Fine I said.  I'll get it and if I don't like Vista I can always get XP.   I ordered it with 512 mb RAM so I could upgrade it later, because I wasn't paying HP's ridiculous RAM prices.  

When I first tried to play games (BF1942 specifically) it was buggy.  I determined that it was a driver problem, and after DLing a new driver from a 3rd party site I got everything working.  Still, there were problems that were just annoying.  Firefox was very unstable, and I didn't think my computer was as fast as it should be.  What bugged me the most was that even though I had 1.5 gb of RAM Vista was still using a swap file.  I don't know about you guys, but I can't stand the noise of a reading HD.  I was considering buying (or pirating) XP but I thought that was a load of ****.  I already paid Microsoft for an OS, and I wasn't about to do it again.   I decided that I had enough of the crap and dual booted Ubuntu for a while.  

 I don't know if there is something wrong my disk drive or my CDs or what, but I couldn't get the Live CD to burn properly.  Luckily I got the text only CD to burn.  The partitioning in the CD was confusing at best.  I had resized my windows drive to make room for Ubuntu.  However, when I went to install Ubuntu I wasn't quite sure if it was going to install on the proper partition.  I thought it was, and luckily it did.  

First impressions were pretty good.  It had me install my restricted video driver right away.  The desktop was clean, and I really liked the package manager.  However, the first problem was that my wireless card simply didn't work.  Luckily I was able to use the wired connection and I found a thread on here with a real nice program that automatically configured my wireless.  Next problem I discovered was that my mouse didn't work properly, specifically the scroll and back/forward buttons.  

Other than those two problems, everything else worked fine.  I decided that it was time for some eye candy.  I installed Beryl, and that was a huge mistake.  I had the black screen bug, which I understand is endemic to Nvidia cards.  I had no idea on how to fix it, so I decided that a reinstall would be the quickest solution.  

I reinstalled, fixed the wireless and mouse again.  Further reading on the black screen bug led me to believe that it was possible to fix it by modifying xorg.conf.  Did so and I broke my X windows.  Again, with no idea how to fix it I decided a reinstall would again be the quickest solution.  

Upon reading the forums more I got the distinct impression that KDE was considered superior to GNOME.  So I DL Kubuntu, and this successfully burns to a CD on the first try.  I fire it up and see quickly that it's superior to GNOME.  I had been using Ubuntu exclusively for a couple weeks, and decided to stop dual booting and move all my files over to Kubuntu.  

I installed Kubuntu and created 3 partitions (boot, swap, and Media).  First mistake off the bat is naming my file partition Media because there is a /media file already.  More on this later.  I started moving my files onto the system, but I had to shut down for the night.  When I booted up in the morning the system was broke.  The error message flashed too quickly on boot for me to read.  Another re-install.  

This installation I was smarter and made my third partition /home.  This is my current installation.  Somehow I forgot what I did to get my mouse working, but the back/forward buttons aren't working.  I haven't gotten my wireless working either just because I've been monkeying around with my system too much.  Otherwise, it's been going pretty good.  

My thoughts:

**Good**

Package manager.  This blows Windows out of the water.  I have 20000+ programs to search, and each of them are installed by one click.  

Memory management.  My RAM is only at 800 mb, and thats with Firefox taking up 250.  No swap file and no HD access.  Love it.  

Desktop Environment/Start Menu.  I like them much better in KDE than in Windows or Ubuntu.  Much more customizable and much deeper. 

Free baby!

**Bad**

File System.  I don't need to see /tmp, /var, /dev, or most of the dozen folders in /.  Microsoft is worse in that regard, but I was always able to seperate my data files into D:.  

Hardware support.  I can understand the wireless card, but there is no reason a mouse should not work out of the box.  

Lack of GUI for xorg.conf and other config files.  It's a bit scary thought that I could kill my system with one typo.

---

### Post by jfinkels on 2007-08-25
> **treis said:**
> 

**Good**

Package manager.  This blows Windows out of the water.  I have 20000+ programs to search, and each of them are installed by one click.  

Memory management.  My RAM is only at 800 mb, and thats with Firefox taking up 250.  No swap file and no HD access.  Love it.  

Desktop Environment/Start Menu.  I like them much better in KDE than in Windows or Ubuntu.  Much more customizable and much deeper. 

Free baby!
Yes, yes, yes, and yes.> 
**Bad**

File System.  I don't need to see /tmp, /var, /dev, or most of the dozen folders in /.  Microsoft is worse in that regard, but I was always able to seperate my data files into D:.  

A non-trivial group of people would agree that the structure of the filesystem needs to be changed. I personally disagree. I want nothing hidden from me on my own computer. btw, when you start learning more about your system, /var holds a lot of important files!
> 
Hardware support.  I can understand the wireless card, but there is no reason a mouse should not work out of the box.  

Contact the manufacturer and let the company know that releasing hardware specifications or open source drivers (or at least proprietary Linux drivers) would be a good idea. In the world of Linux, hardware manufacturers don't seem to want to cooperate, which makes our work a little bit harder. It's a big problem that needs to change before we can move forward.
> 
Lack of GUI for xorg.conf and other config files.  It's a bit scary thought that I could kill my system with one typo.
You did kill your system with one typo haha.

Well, this is a holdover from the older Unix based systems. Most configuration files you will find will be in plaintext format and completely user-editable because frankly a GUI is unnecessary for most things.

I think the reason we don't have a built-in GUI for Xorg is because if you want to install xserver on a non-graphical system, you need to have access to the configuration. But many people agree with you that GUI tools should at least EXIST for every administrative task.

Let us know if you need any more help, and welcome!

---

### Post by treis on 2007-08-25
> **jfinkels said:**
> 
A non-trivial group of people would agree that the structure of the filesystem needs to be changed. I personally disagree. I want nothing hidden from me on my own computer. btw, when you start learning more about your system, /var holds a lot of important files! 

There's no reason that those folders have to go away.  Just collect them all under a /System folder or something.  I have a longer post about this in the Gutsy forum, but the jist of it is that I want less folders under "/".  

> **jfinkels said:**
> 
Contact the manufacturer and let the company know that releasing hardware specifications or open source drivers (or at least proprietary Linux drivers) would be a good idea. In the world of Linux, hardware manufacturers don't seem to want to cooperate, which makes our work a little bit harder. It's a big problem that needs to change before we can move forward. 

I understand the problem, and spotted Ubuntu the wireless card, but the mouse isn't a manufacturer problem.  All the mouse buttons work it's just that they don't do the right thing.  It should just work.  At minimum there should be a simple GUI program or something to map the buttons.  Like the old joy-stick configurations.  Have it prompt for a button and map it when the user clicks.

---

### Post by shafin on 2007-08-25
Your last wish is fulfilled in Gutsy

[http://ubuntuforums.org/showthread.php?p=3249307#post3249307](http://ubuntuforums.org/showthread.php?p=3249307#post3249307)

I support your /system idea.BTW,what I do is I just forget about the root folder and do all my works in my home folder.I take the home folder as equivalent to "My computer".

---

### Post by treis on 2007-08-28
Killed another installation today trying to edit my xorg.conf =(.

---

