---
title: "Which video card to use?"
date: 2009-11-08
forum: Wine
---

### Post by Pikzilla on 2009-11-08
Hey, I've been having speed issues for application-building software I use, and so far, everywhere I've looked has pointed to "get a new video card". Now, the applications it builds are only 2-d, so I don't think this should be much of an upgrade, so what video card should I get? Also, I should point out that an (incomplete) report from appDB rates the application I'm trying to use as "platinum"
Here's links to threads containing more detailed analyses of my problem:
[http://ubuntuforums.org/showthread.php?t=1310389](http://ubuntuforums.org/showthread.php?t=1310389)
[http://forum.winehq.org/viewtopic.php?p=34537#34537](http://forum.winehq.org/viewtopic.php?p=34537#34537)

---

### Post by Bucky Ball on 2009-11-08
You are unlikely to find a 2D card I expect.

---

### Post by Duskao on 2009-11-08
Ok, I took a quick peek through the other branches you have posted here. I'm going to have to agree with FatButtLarry on the winehq branch. But there are a couple questions I have for you as I never saw it mentioned anywhere. What are you actually trying to run? What are your system specs. What version of ubuntu are you using?

I also saw that you are using an integraded intel chip. Unfortunately they are a bit notorious for not running that well at the moment, however there are a couple things you can try, but you will have to get your hands a little dirty so to speak. 

First you are going to want to add the xorg.org ppa. Now this is easily done with ubuntu tweak if you are new to ubuntu. You can get this program form [www.getdeb.net](www.getdeb.net). Just follow the instructions of how to install software from that site (learn how to install software from getdeb.net) and use the first option of downloading the .deb file then install it, then install the program you are looking for. Also there might actually be a decent program listed there for what you want to accomplish with your game developement.
If you do add the ppa through Ubuntu Tweak then you have two choices, one stick with the Ubuntu X (should show some improovement) or go with Ubuntu X (unstable)(might show more improovement, but might give you more trouble with your system)

Then you are going to want to open up 'sudo gedit /etc/X11/xorg.conf'

under the Section "Device" you are going to want to (probably have to add) 

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                    "uxa"
        Option          "EXAOptimizeMigration"           "true"
        Option          "MigrationHeuristic"             "greedy"
        Option          "Tiling"                         "true"
EndSection

It should look like that for the device secion. So then save it. close it and reboot. 

Now there is a bit of work there for ya, it's not too tough, but if you feel that you don't want to do it, then you might have to get a new video card (of course that depends on your system specs, you might need a new computer if it is rather old, but I doubt that)But you can run into alot of the same problems with new video cards as well.

I also feel compelled to mention that most programs do NOT work as well using wine as they do on windows. There are a couple exceptions, but be prepared for less performance. I really hope this helps you out. 

Best of luck.

---

### Post by Duskao on 2009-11-08
In the device section in the aforementioned post, there are supposed to be spaces (tab) before the "Options" and after as well. Not sure why it got rid of them when they were posted.

---

### Post by Pikzilla on 2009-11-11
So, like this?
Section "Device"
Identifier "Configured Video Device"
[INDENT]Option "AccelMethod" "uxa"
[/INDENT][INDENT]Option "EXAOptimizeMigration" "true"
[/INDENT][INDENT]Option "MigrationHeuristic" "greedy"
[/INDENT][INDENT]Option "Tiling" "true"
[/INDENT]EndSection

---

### Post by Pikzilla on 2009-11-12
Sorry 'bout bumping, but...

---

### Post by Pikzilla on 2009-11-14
Hey, I followed the instructions, but nothing really worked. Again, which video card do you think I should get?

---

