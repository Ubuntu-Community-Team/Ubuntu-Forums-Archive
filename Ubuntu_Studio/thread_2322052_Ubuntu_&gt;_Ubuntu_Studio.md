---
title: "Ubuntu &gt; Ubuntu Studio"
date: 2016-04-26
forum: Ubuntu Studio
---

### Post by anon24 on 2016-04-26
So, I just got the new 16.04 and have pretty much everything up and running other than my damned Nvida graphics card. :/

Anyway, my question is:

Is it difficult to switch over to Ubuntu Studio or does it transfer all of your settings and everything from vanilla?

---

### Post by jejeman on 2016-04-27
Ubuntu uses Unity, US uses XFCE.
So, I don't know on which settings do you refer?

---

### Post by anon24 on 2016-05-07
My plan has since changed. 

Don't worry about the settings, I want to keep Ubuntu Vanilla now.

My goal is to have this triple boot setup:

I have three internal SSD's and one internal SATA Drive.

sda (SSD): Ubuntu 
sdb (SSD): Ubuntu Studio
sdc (SATA): Storage
sdd (SSD): Windows

So, is installing this on one of my other internal drives fairly easy?

---

### Post by ubu_dynamite on 2016-05-08
Any reason you want to have 2 separate ubuntu installations?
You could just install the ubuntustudio meta packages without ubuntustudio-desktop or just the programs you really need.
Ubuntustudio is just xubuntu with lowlatency kernel and allot of audio, video and graphics programs installed.

I would go for 
sda (SSD): Windows <-- Install windows first or you wil have to fix grub afterwards windows bootloader will not show your linux install
sdb,sdd software raid0 (SSD): Ubuntu with your preferred desktop any other programs can be installed afterwards, raid0 will give you extra read/writing speed and disk space for your video, audio work but if one drive fails you lose the content of both drives.
sdc (SATA): Storage

---

### Post by anon24 on 2016-05-08
Well, I want Ubuntu Vanilla as my boot for web browsing.
Windows for gaming, which I will never connect to the web with it unless downloading games from Steam (I don't do online multiplayer). 
Even if I do get a virus from Steam, which is unlikely, but entirely possible, I will at least know the source and can narrow down what to do to fix the issue.

The idea is that if I ever do get a virus from browsing or downloading anything, god forbid, then US and Windows will be at least half way isolated from that system and I will still be able to record music/play games until I get UV back up and running.
Also, this allows me to try short term updates for Ubuntu Vanilla, if I so choose, while leaving my Ubuntu Studio at 16.04 until I know that the next version is stable.
Maybe my idea is a bit misguided and idealistic, but it seems to make sense in my head. 

I've been doing multimedia work for a long time. 
I've had issues in the past with updating every time there is an update. 
Sometimes, the programs change for the worse, change too much, in turn negatively effecting my work flow, leaving me unable to open old sessions, or even completely inoperable. 
Hell, there have been situations where the company that made the program disbanded and the program was no longer supported or even compatible at all with new versions of the OS.
Which, is not an option at this point because I need to be able to work. 
I find it better to pick one version of the OS and of my multimedia programs and stick with them **offline**.

I thought that someone had previously said that having Windows installed first is the way to go.
Thanks for that, that's the main thing that I was really wondering about! :)
So, basically, I need to back everything up and do a clean Windows install?

I'd really prefer to not use RAID, I just got rid of it.
It basically left me with no working OS.
I had to take all of my drives out of RAID, which finally enabled me to get Ubuntu installed again.

---

### Post by vasa1 on 2016-05-09
> **ubu_dynamite said:**
> Any reason you want to have 2 separate ubuntu installations? ...
Having them separate would be cleaner. Of course, OP would then need to reboot to change rather than log out from one and log in to the other.

---

### Post by anon24 on 2016-05-09
Yes, having to reboot is a slight inconvenience in the long run! :D

---

### Post by ubu_dynamite on 2016-05-09
> **anon24 said:**
> Well, I want Ubuntu Vanilla as my boot for web browsing.
Windows for gaming, which I will never connect to the web with it unless downloading games from Steam (I don't do online multiplayer). 
Even if I do get a virus from Steam, which is unlikely, but entirely possible, I will at least know the source and can narrow down what to do to fix the issue.

The idea is that if I ever do get a virus from browsing or downloading anything, god forbid, then US and Windows will be at least half way isolated from that system and I will still be able to record music/play games until I get UV back up and running.
Also, this allows me to try short term updates for Ubuntu Vanilla, if I so choose, while leaving my Ubuntu Studio at 16.04 until I know that the next version is stable.
Maybe my idea is a bit misguided and idealistic, but it seems to make sense in my head. 

I've been doing multimedia work for a long time. 
I've had issues in the past with updating every time there is an update. 
Sometimes, the programs change for the worse, change too much, in turn negatively effecting my work flow, leaving me unable to open old sessions, or even completely inoperable. 
Hell, there have been situations where the company that made the program disbanded and the program was no longer supported or even compatible at all with new versions of the OS.
Which, is not an option at this point because I need to be able to work. 
I find it better to pick one version of the OS and of my multimedia programs and stick with them **offline**.

Linux viruses are almost nonexistent so wouldn't worry that much about it.
If you want to test your updates so you don't break your working environment i would recommend two exactly the same Linux/Ubuntu installs.
To make things more complicated you could also use btrfs snapshots to roleback your updates [https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)
Also have a look at [http://kxstudio.linuxaudio.org](http://kxstudio.linuxaudio.org) for your music recording.


> **anon24 said:**
> 
I thought that someone had previously said that having Windows installed first is the way to go.
Thanks for that, that's the main thing that I was really wondering about! :)
So, basically, I need to back everything up and do a clean Windows install?

Installing windows first is the best yes because windows will break grub and just show its own OS.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

> **anon24 said:**
> 
I'd really prefer to not use RAID, I just got rid of it.
It basically left me with no working OS.
I had to take all of my drives out of RAID, which finally enabled me to get Ubuntu installed again.

Softwareraid is a different thing then your fakeraid and so far worked fine for me.

---

### Post by ubu_dynamite on 2016-05-09
> **vasa1 said:**
> Having them separate would be cleaner. Of course, OP would then need to reboot to change rather than log out from one and log in to the other.

There is no log out from one and log in to the other if there is just one dektop environment  with just the programs you will need.

---

### Post by anon24 on 2016-05-11
I really like Ubuntu Vanilla, it reminds me a lot of Mac OSX, especially the Unity Launcher. I "tried" Ubuntu Studio and it just doesn't flow as well for me. I've gotten spoiled and don't really want to switch from UV as my main OS. 

I've looked up KXstudio and read various things saying how buggy it is. Also, again, I really want to stick with UV as my main OS and I'm not sure how dual booting would work with KXstudio.

I tried to install US on SDB and was unable to dual boot. When I would boot up, it just launched UV. I tried to see if US appeared in grub2 to no avail.

---

### Post by ubu_dynamite on 2016-05-12
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by anon24 on 2016-05-12
Oooooo, thank you! :)

In the step where I'm supposed to install Ardour. Is it possible to install v4 instead of v3?

---

### Post by ubu_dynamite on 2016-05-12
> **anon24 said:**
> Oooooo, thank you! :)

In the step where I'm supposed to install Ardour. Is it possible to install v4 instead of v3?

If you added the kxstudio repositories you can not sure if ardour4 is in 16.04 repos still have 14.04 here.

---

### Post by jejeman on 2016-05-14
You don't need to install Ubuntu to see which packages at which versions it has.
You can serch it here
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Example
[http://packages.ubuntu.com/search?keywords=ardour&searchon=names&suite=xenial&section=all](http://packages.ubuntu.com/search?keywords=ardour&searchon=names&suite=xenial&section=all)

---

