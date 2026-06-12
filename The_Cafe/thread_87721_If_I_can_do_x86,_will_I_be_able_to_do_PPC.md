---
title: "If I can do x86, will I be able to do PPC?"
date: 2005-11-08
forum: The Cafe
---

### Post by aysiu on 2005-11-08
There are very few people I know who express any interest in having Ubuntu installed on their computers. Someone from work has an old Mac (I think it's a G3 iBook... maybe even earlier) that she's thinking about putting Ubuntu on.

I'm still a newbie of sorts, but I'm proficient enough that I'm confident I can install Ubuntu on just about any x86 computer (with the help of these forums, of course) that's Linux-compatible. However, will that knowledge translate well to PPC installations?

I know there's Yaboot instead of Grub, but how many other things will catch me off guard? It still uses repositories and such, right? sudo? apt-get? All that jazz?

---

### Post by xequence on 2005-11-08
Youve been saying youre a newbie since your 500th post, when I joined these forums. Don't you think youre past newbie status? ;) Anyway, I am pretty sure it will be the same. I have no experience but the only other thing I can think of is you might not have as much of a choice of packages from the repos. Just a wild guess ;)

Anyway, good luck. Take the PPC world by storm, aysiu.

---

### Post by poofyhairguy on 2005-11-08
[QUOTE=aysiu]There are very few people I know who express any interest in having Ubuntu installed on their computers. Someone from work has an old Mac (I think it's a G3 iBook... maybe even earlier) that she's thinking about putting Ubuntu on.

I'm still a newbie of sorts, but I'm proficient enough that I'm confident I can install Ubuntu on just about any x86 computer (with the help of these forums, of course) that's Linux-compatible. However, will that knowledge translate well to PPC installations?

I know there's Yaboot instead of Grub, but how many other things will catch me off guard? It still uses repositories and such, right? sudo? apt-get? All that jazz?[/QUOTE]

I have personal experiance to go on, so I'll try my best to give advice.

1. Make sure they have enough RAM. Often those old G3s and whatever were only shipped with a small amount of RAM. When Gnome even gets around 128mb it starts to lag. If you can talk them into getting more RAM.

2. If not, then XFCE is your friend. In fact, it might be no matter what. I have a G3 Clamshell iBook (the original) that won't run Gnome worth a darn even with 256 mb of RAM. It crashes on me a lot and is very slow. 

I HAVE to use XFCE on mine. KDE likes CPU more than RAM it just runs like a dog on that machine too. My advice if that the case: install full Ubuntu, then xbuntu-desktop, then run nautilus and gnome-volume-manager and tell it to save the session with it open. Most people want those two Gnome features the most. And maybe find a good Aqua theme for XFCE (there are tons) cause the default is ugly- you know that.

3. Some things are really lacking- the closed source things. New Windows Media Codecs. A decent Flashplayer (I never have gotten the OSS to work worth using- get the "flashblock" extension for Firefox so they don't have to see a million puzzle pieces). Adding dvd playing abilites and Java is harder.

I mean, there is no PPC automatix. There is most of the pain right there.

4. If they have an airport extremem and they use it or want to, walk away. Bail. There are no working drivers for that, and there is no ndiswrapper to bail you out. The old airports work great as long as you don't need to scan for networks.

5. Please show them virtual desktops. Especially if its an old iBook that is 800x600. I use virtual desktops as my task switcher on there- otherwise its painful. Please.

6. From my experiance, suspend work better than I could ever dream for my girlfriends toshiba laptop.

7.   [http://ubuntuforums.org/showthread.php?t=29833](http://ubuntuforums.org/showthread.php?t=29833)

---

### Post by TravisNewman on 2005-11-08
as far as installing/configuring/apt-getting, all is the same. You will notice less packages though.

---

### Post by aysiu on 2005-11-08
Thanks for all the info (especially from Poofyhairyguy). I'll keep those things in mind, and I'll read up on that link to the much longer post. Thanks again. I love this forum.

P.S. I am a newbie (I swear)... just not a total one.

---

### Post by benplaut on 2005-11-08
newbie my arse :rolleyes:  (i'm in the same boat as you...)

---

### Post by aysiu on 2005-11-08
Okay, okay. I'm not a newbie. I'm not an oldbie, either, though. Maybe I'm a middlebie.

By the way, panickedthumb and Poofy made mention of fewer packages being available. How would I know what's available and what's not (apart from searching)? My plan, if this actually happens, would be to install Inkscape and GIMP (does GIMP come standard? I forget...)--maybe Thunderbird, too.

---

### Post by xequence on 2005-11-08
[QUOTE=aysiu]Okay, okay. I'm not a newbie. I'm not an oldbie, either, though. Maybe I'm a middlebie.

By the way, panickedthumb and Poofy made mention of fewer packages being available. How would I know what's available and what's not (apart from searching)? My plan, if this actually happens, would be to install Inkscape and GIMP (does GIMP come standard? I forget...)--maybe Thunderbird, too.[/QUOTE]

Gimp comes standard in x86, not sure about PPC.

---

### Post by aysiu on 2005-11-10
Update on "Project Co-worker": So during our lunch break today I showed her the live Ubuntu CD on her work computer (x86), and she was impressed. I had to reassure her of a few things:

1. You don't have to go to the BIOS set-up every time you boot-up. In fact, once I have it installed on her computer, she'll probably never see that. Actually... in OS 9, do you hold down the "C" key as you do in OS X to boot from the CD-ROM drive?

2. Ubuntu's not always that ugly. I know some people dig the "human" brown theme, but she was taken aback. Good thing I had a screenshot of my home desktop to show her.

3. It's slow because it's a live CD, not because Ubuntu's slow. I would probably install Gnome and XFCE. If Gnome appeared too slow, I'd make XFCE the default desktop.

4. OpenOffice does having a drawing toolbar, just as Microsoft Office does.

She was overall impressed, though, and she assured me she has airport but not airport extreme, so that makes me hopeful. She particularly liked that Firefox was on by default, that OpenOffice even existed, and that there were lots of games--I launched up Gnometris, and she started playing right away--even knew all the keys for it (I'm sure they're standard Tetris keys). 

The plan is that we'll try the live CD on her laptop, and I'll probably get a sense of how well it works. If there seem to be more than two major hardware issues, then I'm just going to give up, I think.

Otherwise, I have a few more questions:

1. Does Yaboot work similarly to Grub? Will I be able to figure it out, especially if she wants to dual boot?

2. I know how to mount FAT32 partitions, but will she be able to read/write from her OS 9 installation files, if we do a dual boot?

Well, I'll keep you all posted. If this works, it'll be my first Ubuntu "conversion." She's the only person I know who sees that GIMP stands for GNU Image Manipulation Program and says, "Oh, GNU! I like that. That sounds cool."

She had a hard time at first grasping what an operating system was. "So, Ubuntu's an entirely different... platform?" I guess she didn't realize it would replace OS 9, not run on top of it. But she seems cool with the idea--it just took her a while to understand there was more than Mac and Windows...

---

### Post by ssam on 2005-11-10
about the only things missing from powerpc ubuntu are the w32codecs, flash, the 686/k7 kernels and grub.

there are a few things different, yaboot replaces grup/lilo.

nearly every program in main and universe compiles fine for powerpc and so is included. there are a few [big endian]("http://en.wikipedia.org/wiki/Big_endian") bugs around (eg rotating photos in f-spot corrupts them) but these are very rare these days.

the install is mostly the same.

macs have a slightly odd partitioning system. there are about 9 small apple partitions that are usually hidden in mac os x. if you want to dual boot with mac os, the partition using the mac disk tool (on a mac os install cd), and leave free space for the ubuntu partitioner.

also the mac bios is very different. to boot from a cd, you must hold down the 'c' key.

---

### Post by aysiu on 2005-11-10
Thanks for the tips.

---

### Post by aysiu on 2005-11-23
Project Co-Worker Part II:

Okay. Install day is coming up (next Tuesday). I've asked her a bunch of questions, and I'm keeping my fingers crossed.

First of all, I think I've found Linux equivalents for all her programs, except I don't even know what Entourage is. It's a "journaling" program? What does that mean? Like a blog? Like a word processor?

She loves Firefox, but just in case she uses something User Agent Switcher can't handle, does IE on Wine work on a PPC? If not, why not?

It's kind of a risky situation. I'm going to try out the live CD. If I can get internet working on it with her airport (which she assures me is not extreme), I'm just going to go ahead and install Ubuntu on there. She seems excited (I didn't have to twist her arm about this), and even though she doesn't have a restore disk or installer for OS 9, she says it's gotten so bad she can't even work on it for more than fifteen minutes without it crashing. I'm hoping that's not a hardware issue (because Ubuntu will crash too, then)--but it can't get much worse than it is now!

Any other tips before "the big day"?

---

### Post by poofyhairguy on 2005-11-23
How much RAM does it have?

---

### Post by aysiu on 2005-11-23
[QUOTE=poofyhairguy]How much RAM does it have?[/QUOTE] I don't know, but I figure if it's less than 256 MB, I'll plop her on XFCE. If it's less than 64 MB... I don't know what to do.

---

### Post by Brunellus on 2005-11-23
[QUOTE=aysiu]I don't know, but I figure if it's less than 256 MB, I'll plop her on XFCE. If it's less than 64 MB... I don't know what to do.[/QUOTE]
fluxbox, and give her a real three-button mouse.

of course, she might not dig the "grim industrial" aesthetic.

---

### Post by aysiu on 2005-11-29
First of all, I want to say thank you to everyone who chimed in. I'm glad we have such a supportive community here.

Unfortunately, "project co-worker" was a bust. Turns out she had some kind of hardware failure that even Ubuntu can't fix. Usually, it was pretty bad, but today, when she brought her computer in, it wouldn't even turn on properly.

---

