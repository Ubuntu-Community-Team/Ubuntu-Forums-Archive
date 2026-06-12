---
title: "x64 Last usable image?"
date: 2013-02-20
forum: Ubuntu Development Version
---

### Post by Budovi on 2013-02-20
Hi all,

Who knows which image should be ok? I have decided to reinstall my system because of "only-me" errors, and after long "self-persuasion" it may help I downloaded last daily build. Then another, another, another, tried about 6 times (and not sure which, maybe two multiple times or all 5 existing right now at cdimage.ubuntu.com/daily-live/ :D ).

I used Startup Disk Creator and Universal USB installer. But no, they cannot boot ("missing vmlinuz image" or "cannot find <some> partition" errors)

I'm really... confused and feel abused :D I also checked md5 sums! Now I go take some shower and calm down. :D I really should sleep at night, at least once! :D And this happens... Ubuntu is ruining my day cycle (and also school project) I cannot remember if I have slept at night this week :D

Thank you (:

PS: advices how to learn (force) sleep at night are also welcome :D in PM of course

Edit: checked my download history and it seems like I tried every possible version :( (20130219, 20130220, 20130220.1, 20130220.2 and also current, which is just copy of 2013.02.20.2). Is there any other sources or I should wait for today's build and hope it will be ok? Is there any place where to report this type of malfunctions? Thanks again.[URL="http://cdimage.ubuntu.com/daily-live/20130220/"]
[/URL]

---

### Post by sgage on 2013-02-20
> **Budovi said:**
> Hi all,

Who knows which image should be ok? I have decided to reinstall my system because of "only-me" errors, and after long "self-persuasion" it may help I downloaded last daily build. Then another, another, another, tried about 6 times (and not sure which, maybe two multiple times or all 5 existing right now at cdimage.ubuntu.com/daily-live/ :D ).

I used Startup Disk Creator and Universal USB installer. But no, they cannot boot ("missing vmlinuz image" or "cannot find <some> partition" errors)

I'm really... confused and feel abused :D I also checked md5 sums! Now I go take some shower and calm down. :D I really should sleep at night, at least once! :D And this happens... Ubuntu is ruining my day cycle (and also school project) I cannot remember if I have slept at night this week :D

Thank you (:

PS: advices how to learn (force) sleep at night are also welcome :D in PM of course

Edit: checked my download history and it seems like I tried every possible version :( (20130219, 20130220, 20130220.1, 20130220.2 and also current, which is just copy of 2013.02.20.2). Is there any other sources or I should wait for today's build and hope it will be ok? Is there any place where to report this type of malfunctions? Thanks again.[URL="http://cdimage.ubuntu.com/daily-live/20130220/"]
[/URL]

For a start, don't use "Startup Disk Creator" if you have a USB device. Use unetbootin, available in the standard repos.

I made a fresh install today, from USB, no problem.

But I do get the impression that something has changed in the booting arrangement such that there can be issues...

---

### Post by ventrical on 2013-02-20
Todays daily is completely  inoperable . Only get Busy Box.

---

### Post by Budovi on 2013-02-21
At 1:30 today I tried boot from new USB with yesterday's image and, sgage's advice, unetbootin (and "current" version). Stuck on black screen while loading live version, I was able to chceck the image (with self-check) before and it was ok.

@ventrical: Hmm I can see only yesterday's image for now, not today's build (20130221)

---

### Post by ventrical on 2013-02-21
My apologies... that was i386 build.

---

### Post by Cheltspy on 2013-02-21
x64 3.8.0-6-generic+ appears to have boot problem it has completely corrupted nvidia-304.

I was on 3.8.0-2-generic for a long time.

---

### Post by Cheltspy on 2013-02-21
No.. that image doesn't boot either. 64bit is totally screwed. The regression appears to have happened over several reboots.

i386 seems to be okay... for now.

---

### Post by Budovi on 2013-02-21
I just tried 20120221 x64 from USB (unetbootin). "Default" load causes "corrupted kernel" message to appear, "Install ubuntu" freezes and "Try ubuntu" is working fine, except when I try to install it. Installer freezes after making choice "how to make an install" (reinstal, delete, "something else")...

I'm just... :D I just want to reinstall... why this have to happen right now :D

---

### Post by grahammechanical on 2013-02-21
Have you tried any of the F6 options? I have not tested a daily build for a few weeks. But those 5 or 6 I did test always put me into a Busybox prompt. I just could not get to a live session or install. I tried all the F options and in various mixtures. 

The only thing that worked was to add acpi=off and to change this

> initrd.lz quiet splashto

> initrd.lz irqpoll quiet splashI have never needed to do any thing like this before for any previous version of Ubuntu. But then again the Ubiquity installer has had a lot of development lately.

Edit: I have just run today's daily build (20130221). Now even acpi=off and irqpoll doesn't stop me getting a Busybox promt. But putting a check mark against all the F6 options has got me to a live session. I am using it now.

Regards.

---

### Post by Cheltspy on 2013-02-21
Just updated to 3.8.0-7-generic_3.8.0-7.15_amd64.deb all of the drivers are up and running again and get logon screen.

However, still cannot get unity desktop.

Incidentally, this is the first time I haven't had to manually update the kernel headers on 64.

---

### Post by Cheltspy on 2013-02-22
Updated a second machine this morning to 64 3.8.0-7-generic and the update when fine, everything working on Intel chipset.

There were boot corruptions started again on my main machine on boot up.

The second machine has 2gb of RAM and the main 4gb of RAM.

Downgraded the main machine to 2gb everything is fine:confused:

Put in an extra 1gb to 3gb everything is still fine.

There seems the be a memory problem above 3gb with 64 bit.

---

### Post by Budovi on 2013-02-22
Ehm, I think, you should check your RAM modules for malfunction and "ability of cooperation". Use memtest or similar software and chceck your modules by one, then, if not errors foud, you can check them both in a system (lot of guides available on the internet for this).

This really seems like hardware fault, not software one. Correct me please if I'm wrong...

And you are also offtopic, this topic is about installation image and troubles with the latest builds.

---

### Post by Cheltspy on 2013-02-22
Yes, I am talking about the installation images as well.

The latest image does not boot on my main machine either as DVD image or USB with 4G memory.

The memory has tested fine and has been working for over 6 months, no problems.

The x64 iso images of 26-01-13 and 10-11-12 boot fine.

I think this is the bug we are experiencing.

[https://bugs.launchpad.net/utah/+bug/1092924](https://bugs.launchpad.net/utah/+bug/1092924)

---

### Post by sudo san on 2013-02-23
I would reinstall 12.10 and change all mentions of 'quantal' in '/etc/apt/sources.list' to 'raring'.

Then do 'sudo apt-get update' and 'sudo apt-get dist-upgrade'.

Then you would have upgraded your system to raring.

---

### Post by zika on 2013-02-23
> **sudo san said:**
> I would reinstall 12.10 and change all mentions of 'quantal' in '/etc/apt/sources.list' to 'raring'.

Then do 'sudo apt-get update' and 'sudo apt-get dist-upgrade'.

Then you would have upgraded your system to raring.You first give a resolute advice (above) and then ask (about the same thing) if that were the correct way... [http://ubuntuforums.org/showpost.php?p=12525754&postcount=1](http://ubuntuforums.org/showpost.php?p=12525754&postcount=1) ... Nice...

---

### Post by cariboo on 2013-02-23
> **sudo san said:**
> I would reinstall 12.10 and change all mentions of 'quantal' in '/etc/apt/sources.list' to 'raring'.

Then do 'sudo apt-get update' and 'sudo apt-get dist-upgrade'.

Then you would have upgraded your system to raring.

The one problem  with this strategy, is that you end up downloading several hundred (thousand) packages, to get to the point that most of us are at right now. If you have bandwidth limits, this could cut your usage this month because of the tremendous number of packages that need to be installed.

---

### Post by Budovi on 2013-02-23
Yeah, I installed Ubuntu with today's snapshot (20130222.1) succesfully :)

I just had to disable download updates during installation and installing third party software, which causes ubiquity not to try connect to internet. Maybe it has something in common with my ethernet bug, which occured in live session too. Hmm.... At least I have clean OS and will see...

---

### Post by zika on 2013-02-23
> **cariboo907 said:**
> The one problem  with this strategy, is that you end up downloading several hundred (thousand) packages, to get to the point that most of us are at right now. If you have bandwidth limits, this could cut your usage this month because of the tremendous number of packages that need to be installed.It kind of comes to the same amount of traffic: sum of some parts is not ever bigger then whole...
There were some troubles with installer in RR so...
As we hear, lately, troubles might be over...

---

