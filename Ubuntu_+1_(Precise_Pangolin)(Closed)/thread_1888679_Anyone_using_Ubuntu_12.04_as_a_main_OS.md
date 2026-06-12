---
title: "Anyone using Ubuntu 12.04 as a main OS?"
date: 2011-11-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by JF382 on 2011-11-29
I know this is a very early release but I am just curious if anyone is using this as a Main OS. If you are, did you have any problems? I am assuming you would just because it is an early release, but who knows.

---

### Post by cbowman57 on 2011-11-29
It's my primary Ubuntu installation.

So far it's much better than the 11.10 pre-release, haven't encountered anything show stopping.

---

### Post by OrangeCrate on 2011-11-29
I've seen show stoppers all the way into betas. (Lucid had a notoriously bad one.) If you need your computer for everyday work, it really is best to have a backup operating system. I know many of the testers (including myself when I had the time) who did not have machine dedicated to the new release, dual booted the latest stable release with the dev release.

---

### Post by kuvanito on 2011-11-29
it's my main OS....:guitar:

---

### Post by cbowman57 on 2011-11-29
> **OrangeCrate said:**
> I've seen show stoppers all the way into betas. (Lucid had a notoriously bad one.) If you need your computer for everyday work, it really is best to have a backup operating system. I know many of the testers (including myself when I had the time) who did not have machine dedicated to the new release, dual booted the latest stable release with the dev release.

I have a grub.cfg from hell. :)

Yep, multiple installations & clonezilla in case things go bad.

---

### Post by effenberg0x0 on 2011-11-29
Right now there are no problems. As development really starts, things get ugly. Developers have no real goal of making their releases usable, complete or synced when it comes to dependencies. It is completely usual to have your system alternating between 100% unusable and 50% usable 4 times a day. The difference is that, unlike for those that are running Oneiric, there will be no support here or at General Help, and Launchpad bugs will be disregarded, as the software is in alpha phase (theoretically never released to the public).

Experience tells me that people who don't have spare hardware to test Ubuntu+1, or test it in a Virtual Machine, end up frustrated, asking for support for something that no one can give support to (you can't really learn what broke a system and come up with a workaround during development phase. There are too many updates happening at the same time).

Unless someone is really committed to serious testing / reporting bugs, that is, is willing to help improve Ubuntu and, most importantly, has enough skills to quickly get out of pitfalls by itself with no support whatsoever, I don't recommend U+1.

---

### Post by cariboo on 2011-11-29
I use Precise as my main daily usage install, but I still have an Oneiric install just in case things go south.

---

### Post by ranch hand on 2011-11-29
I am not but did run the testing OS for a 3 testing cycles with little trouble.

You should have;
A stable install on the drive in case you need it to access your files and chroot in to update/upgrade, run rescue commands, etc

More than one install of the testing OS that use the same user and computer name so that you can screw one and switch to the other and it will appear the same.  This is important if you run programs like Boinc, installed in user land for portability.   You can just copy it from your broken OS to one that is working and it will never know the difference.

Always update/upgrade one install and reboot before update/upgrading the other so that you do not screw both.

I actually had 3 identical installs (different wallpaper and grub background so I could tell them apart at a glance).  I did, at least once a cycle, end up using number 3.  This was usually the result of some self inflicted wound.

All were rebooted at least daily.  Box ran all the time.  Boinc operated without interruption on the "main" install when I was logged into it (90% of the day).  CPU usage was set to allow Boinc to run at 96% so they were cranked  to 99-100% at all times.

That tests hell out of your dev release.

---

### Post by ranch hand on 2011-11-29
> **cariboo907 said:**
> I use Precise as my main daily usage install, but I still have an Oneiric install just in case things go south.
They probably will.  That is what makes it FUN.

---

### Post by sammiev on 2011-11-29
It's my main at this time but I have a full usb backup to date of 11.10 if all fails. :)

---

### Post by grahammechanical on 2011-11-29
I agree with the advice to run a development release in another partition. I am doing that right now. 12.10 I am finding is stable and I am using it to work with but my documents are stored to my 11.10 home partition.

Regards.

---

### Post by effenberg0x0 on 2011-11-29
Regular backups in external media, running the test version on a secondary PC, an external or separate HDD or, if not possible, in a separate partition, etc, are all good advice. 

During OO cycle I found my self in not-easily-fixable situations a couple times: deps so broken no matter what you try you can't find a way out, could only load X to vesa for about 2 or three days because there's was no way to make vga work with X until fix was released, libgtk broken (no gtk app would run for more than 30 seconds without crashing, etc. In order to have fun with this, you gotta be absolutely confident that your personal/work stuff is safe elsewhere.

---

### Post by JF382 on 2011-11-29
> **kuvanito said:**
> it's my main OS....:guitar:
Thanks for your answer. Is there anything different in the OS from Ubuntu 11.10 yet? Thanks.

---

### Post by JF382 on 2011-11-29
> **grahammechanical said:**
> I agree with the advice to run a development release in another partition. I am doing that right now. 12.10 I am finding is stable and I am using it to work with but my documents are stored to my 11.10 home partition.

Regards.

Did you mean 12.04 because you said 12.10? Would like to know if that one is out yet.

---

### Post by cariboo on 2011-11-29
> **JF382 said:**
> Did you mean 12.04 because you said 12.10? Would like to know if that one is out yet.

In Ubuntu, the version number is the release date, 12.04 will be released in April of 2012, testing on 12.10 (release date October 2012) won't start until after 12.04 is released.

---

### Post by zika on 2011-11-30
+1 for main system... I have backup machine...

---

### Post by Quackers on 2011-11-30
I too have a 12-04 installation as my daily user. This one was a new OO install which was immediately upgraded to 12-04.
I also have an 11-04 and an 11-10 installation (and a "spare" 12-04 one too, for those dodgy moments :-) )

---

### Post by Harry33 on 2011-11-30
Yes I use 12.04 dev (+ some testing PPA's) on main desktop + on my two other setups.
I have done this now for 4-5 cycles.

But, I also have a live-USB around for chrooting.

---

### Post by tekstr1der on 2011-11-30
> **effenberg0x0 said:**
> Developers have no real goal of making their releases usable, complete or synced when it comes to dependencies.

Actually, that really is a goal and part of an important new initiative.

> Colin Watson, long-time Debian and Ubuntu developer, started the discussion around a team dedicated to development release maintenance. What does this mean? This time the development release should be more likely to be buildable, installable, upgradeable and generally sane during the Alpha and Beta stages. This will make it much easier to run it for development or testing. 

Blueprint here:
[Priorities of the +1 maintenance team and discussed infrastructure changes.]("https://blueprints.launchpad.net/ubuntu/+spec/other-p-plusonemaint-priorities")

Wiki here:
[https://wiki.ubuntu.com/PlusOneMaintenanceTeam/Specs/Priorities](https://wiki.ubuntu.com/PlusOneMaintenanceTeam/Specs/Priorities)

---

### Post by effenberg0x0 on 2011-11-30
> **tekstr1der said:**
> Actually, that really is a goal and part of an important new initiative.



Blueprint here:
[Priorities of the +1 maintenance team and discussed infrastructure changes.]("https://blueprints.launchpad.net/ubuntu/+spec/other-p-plusonemaint-priorities")

Wiki here:
[https://wiki.ubuntu.com/PlusOneMaintenanceTeam/Specs/Priorities](https://wiki.ubuntu.com/PlusOneMaintenanceTeam/Specs/Priorities)

Thanks, this is new to me. I strongly disagree with it thou... 

IMO it is pure nonsense to require that from developers of alpha software: Instead of giving each developer freedom to improve his code up to his goals and according to his schedule, he'll have to only add code that is currently supported by related work from others. If one guy stalls cause he caught a cold, everyone else will also stall, with the only purpose of making alpha daily builds usable. The demands in terms of versioning control and communication between developers increase exponentially. Developers start to get pissed at each other, etc. Not good...

It is a huge mistake to even consider the existence of such thing as "Development version **users". **There's no such thing. Testers should make life easier for developers, not the other way around. The minute such users are accepted to exist and become a priority to developers, things change in development. Speed, adherence to testing bold new stuff, etc. The focus is making something usable for an audience that shouldn't even be considered to exist. 

This is the sort of thing we usually see in the private initiative when they hire a development director that had an amazing previous career as a sales vice-president for a pharmaceutical company or something like that: First thing a guy like that does is drop agile for some ford-like sequential dev model. I wouldn't expect to see such thing in open source. Such things usually kill speed, creativity, the existing and natural dynamic between developers, etc in short-term. I *really* hope to be wrong about that.

---

### Post by jbicha on 2011-11-30
Yes, I run the in-development release of Ubuntu as my primary OS but I know how to fix my machine when things break (and have broken my machine a bunch of times over the years learning). There are definitely things broken now in Precise: I have a few bugs that I haven't sat down to do the work to properly file the bug reports (most bug reports are filed later in the release cycle). Specifically I have a multiarch issue where update-manager wants me to install gnome-shell:i386 on amd64, but more seriously, I have another bug where my computer basically locks up on me (perhaps after resuming from sleep) and requires a reboot.

effenberg, this release cycle is of course different since it's an LTS. Developers shouldn't be haphazardly breaking things and expect to fix everything in the final month. Unity was broken quite a  bit the last two cycles and it would be nice if it would be usable throughout the development cycle. Also, it's nice to have daily builds that are actually installable. I expect there to be a session at the next Ubuntu Developer Summit in May to discuss whether the additional focus on keeping things working during the development cycle is a help or a burden during non-LTS cycles.

This development cycle is less alpha than the last few cycles. In general, we're syncing from Debian testing and Unity & GNOME packages shouldn't be as disruptive.

---

### Post by effenberg0x0 on 2011-11-30
> **jbicha said:**
> Yes, I run the in-development release of Ubuntu as my primary OS but I know how to fix my machine when things break (and have broken my machine a bunch of times over the years learning). There are definitely things broken now in Precise: I have a few bugs that I haven't sat down to do the work to properly file the bug reports (most bug reports are filed later in the release cycle). Specifically I have a multiarch issue where update-manager wants me to install gnome-shell:i386 on amd64, but more seriously, I have another bug where my computer basically locks up on me (perhaps after resuming from sleep) and requires a reboot.

effenberg, this release cycle is of course different since it's an LTS. Developers shouldn't be haphazardly breaking things and expect to fix everything in the final month. Unity was broken quite a  bit the last two cycles and it would be nice if it would be usable throughout the development cycle. Also, it's nice to have daily builds that are actually installable. I expect there to be a session at the next Ubuntu Developer Summit in May to discuss whether the additional focus on keeping things working during the development cycle is a help or a burden during non-LTS cycles.

This development cycle is less alpha than the last few cycles. In general, we're syncing from Debian testing and Unity & GNOME packages shouldn't be as disruptive.

Hi JBicha :) I see... it's a more "conservative" approach because it's LTS. Well, it makes sense from this point of view. I just hope that, after the LTS (PP+1) Ubuntu still have that "edge". In your opinion, do you believe PP+1 tends to be more aggressive in terms of new features, customizations, etc?

---

### Post by Starks on 2011-12-01
My main machines have been Ubuntu+1 since the Feisty alphas.

It gets bumpy at times but Precise has been smooth so far since it's a boring LTS.

Since Quaint Quetzal can't come soon enough, I might just go Arch in 2012.

---

### Post by sgage on 2011-12-01
Count me as another Ubuntu+1 user. I stay very well backed-up, and re-installing is no big deal for me. After all, I've had plenty of practice :KS

So far, PP has been a purring pussycat for the most part. Maybe it's the LTS thing. That said, it could all go to pieces tomorrow...

---

### Post by PaulW2U on 2011-12-01
I'm using both Ubuntu and Kubuntu 12.04 here with /home backed up daily to all of my four *buntu installations.

Ubuntu 12.04 is quite buggy here with a number of problems relating to loss of themes, Gnome 3 and compiz. Kubuntu 12.04 is performing better than Kubuntu 11.10 as I never get a crash notification when logging out of 12.04. Kubuntu 12.04 also gives me better screen fonts but I've yet to discover why as 12.04 was installed using a copy of 11.10's settings.

---

### Post by Redblade20XX on 2011-12-01
> **PaulW2U said:**
> I'm using both Ubuntu and Kubuntu 12.04 here with /home backed up daily to all of my four *buntu installations.

Ubuntu 12.04 is quite buggy here with a number of problems relating to loss of themes, Gnome 3 and compiz. Kubuntu 12.04 is performing better than Kubuntu 11.10 as I never get a crash notification when logging out of 12.04. Kubuntu 12.04 also gives me better screen fonts but I've yet to discover why as 12.04 was installed using a copy of 11.10's settings.

Since your using a shared /home directory, your settings from 11.10, which I presumed you installed first, is located in a file which is inherited by the 12.04 version. Usually on  a fresh install, this file is empty and the os sets it up with the default themes, fonts, etc. I also didn't know why this happened until recently exploring around the os. :)

 -Red

---

### Post by PaulW2U on 2011-12-01
> **Redblade20XX said:**
> Since your using a shared /home directory, your settings from 11.10, which I presumed you installed first, is located in a file which is inherited by the 12.04 version. Usually on  a fresh install, this file is empty and the os sets it up with the default themes, fonts, etc. I also didn't know why this happened until recently exploring around the os. :)

 -Red
Sorry, I'm not clear on what you are trying to say. :confused:

I'm not using a shared /home, I'm just backing up my personal files and documents not settings, across four separate /home partitions.

it seems strange to me that settings that originated in 11.10 and updated in 12.04 give better on-screen results than those of my original 11.10 installation. I'm not complaining but I sometimes wonder if I ever needed to create a new 12.04 installation without using existing settings would I ever get anything so good as what I have at present. KDE 4.7.3 is installed on both 11.10 and 12.04.

Kubuntu users should know what I am referring to when it comes to on-screen fonts. :)

---

### Post by ranch hand on 2011-12-01
> **Redblade20XX said:**
> Since your using a shared /home directory, your settings from 11.10, which I presumed you installed first, is located in a file which is inherited by the 12.04 version. Usually on  a fresh install, this file is empty and the os sets it up with the default themes, fonts, etc. I also didn't know why this happened until recently exploring around the os. :)

 -Red
You can easily use the same /home partition with several installs without this being a problem.  This is Linux, by its very nature it is a multi user system.

All user config files are in /home/<user name>/.whatever.  You can have as many users as you want in any OS and they will all have a separate /home/<user name> and therefore a separate ~/.whatever directory.

When sharing a /home you simple take advantage of this flexibility in Linux.  Each install must have a unique <user name>.  This is very simple and works great.  

To save space and trouble it is good to set user permissions so that all users can access one (usually the /home/<first install user>) directory and use it so that the other directories are not duplicated (Desktop, downloads, music, and so forth}.  That way the only thing needed in the rest of the /home/<user name> directories is the ~/.whatever files.

Haven't tried this, yet, with a BSD install but mixing things like RH and Debian branch Linux installs on one /home is no trouble at all.

---

### Post by JRV on 2011-12-01
My main system is 10.04, everything else is 11.10, except one system used entirely for testing running 12.04.

12.04 will gradually take over the other machines, but will not be used on my main system until after final release.

---

### Post by philinux on 2011-12-01
> **JF382 said:**
> I know this is a very early release but I am just curious if anyone is using this as a Main OS. If you are, did you have any problems? I am assuming you would just because it is an early release, but who knows.

2 internal hard drives dual booting. Ubuntu and ubuntu +1. Chroot essential.  Nuff said .

:evil:

---

