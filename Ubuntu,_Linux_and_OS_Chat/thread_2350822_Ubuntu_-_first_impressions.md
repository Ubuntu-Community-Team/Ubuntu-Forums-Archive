---
title: "Ubuntu - first impressions"
date: 2017-01-28
forum: Ubuntu, Linux and OS Chat
---

### Post by oceanknr on 2017-01-28
I installed Ubuntu on my two desktops few days back. Here is a list of the problems I faced.

- There was no dual boot option on my desktop having UEFI enabled BIOS. Had to run boot-repair to fix it.

- Ubuntu didn't boot at all in that desktop running windows 8.1. I tried reinstalling many times with no success.

- I noticed Ubuntu took longer than my windows 8.1 to boot up.

- Software installation is a hassle. Even after downloading packages and dependencies I couldn't get third party applications to work.

- Ubuntu software center is too slow. It completely stopped working. I had to purge and reinstall it then there were two software centers and the problem still persisted so I had to reinstall Ubuntu itself. This happened three times. 

- I was unable to install applications using apt because dpkg got locked.

- Too much updates to download. Not suitable for users with a slow internet and limited bandwidth.

- After installing many applications the OS got bloated with unnecessary packages. I was hesitant to use autoremove command so used an application called bleachbit which broke my OS. Had to reinstall again.

I think so far I had to reinstall the OS around 8 times. I still don't know why I haven't switched back to windows. Maybe I am a masochist.

---

### Post by QIII on 2017-01-28
None of what you list here is "normal".  Millions install Ubuntu without anything like this number of issues.  Looking at several of them, it is clear that you are not doing things correctly.  Third party software is always a risk.  The apt/dpkg lock is simply a matter of trying to use tools incorrectly.

If this is not worth it, by all means use Windows.  There's nothing wrong with that.

But if you would like help, start a single thread for each issue and people will be happy to help.

A "laundry list" like you have here is impossible to help with without massive confusion.

---

### Post by ian-weisser on 2017-01-28
I'm not sure who your list of complaints is intended for, but we'll try to help you as best we can.

Please keep in mind that we are not your vendor and you are not our customer. We are volunteer community members who contribute our time to help users lost in the woods.
Ubuntu is not Windows, and your Windows power-user skills are holding you back. 

You are not the first Windows power-user here (most of us were and are).

---

### Post by oceanknr on 2017-01-28
> **QIII said:**
> None of what you list here is "normal".  Millions install Ubuntu without anything like this number of issues.  Looking at several of them, it is clear that you are not doing things correctly.  Third party software is always a risk.  The apt/dpkg lock is simply a matter of trying to use tools incorrectly.

If this is not worth it, by all means use Windows.  There's nothing wrong with that.

But if you would like help, start a single thread for each issue and people will be happy to help.

A "laundry list" like you have here is impossible to help with without massive confusion.

OK. I will post in the appropriate section if I face another issue. I have fixed all the problems except one.

---

### Post by Geoffrey_Arndt on 2017-01-30
Perhaps by you providing the details such as "dpkg lock" because you forgot to close another open package manager? . . . will help other ex Window Power Users trying to Morph into Linux Enthusiasts . . . (just sayin) . . .  When I was running Suse, I once saw an informative post entitled something like . . . . "for Newbies . . . Never do these things" with a bullet list of a dozen or so items.

---

### Post by mastablasta on 2017-01-31
> **oceanknr said:**
> 
- I noticed Ubuntu took longer than my windows 8.1 to boot up.

not true, Windows 8 actually hybernates. if you trully turn it off and then do cold boot Ubuntu will boot faster. in any case, if it's a desktop i leave it on.

> 
- Too much updates to download. Not suitable for users with a slow internet and limited bandwidth.


wrong perception. updates in Ubutnu by default include various program updates. if you turn on security updates only the size is substantially reduced. if oyu do security updates only on server the size of updates is even lower. especially after some time when things get really stable security updates are tiny. 14.04 is initial release, 14.04.1 is like SP1. so if one would install 14.04.5 most big updates would alredy be applied. with security updates only you would just receive small patches. 

a week ago i got win 10 update on my enpteprise Windows (which means it stays on first version, so no features - only security updates). the updates were close to 150 MB. not small. but then again comparing it with android updates quite small. in Linux a monthly security patch would probably be a few MB.

> 
- After installing many applications the OS got bloated with unnecessary packages. I was hesitant to use autoremove command so used an application called bleachbit which broke my OS. Had to reinstall again.


rather than "official" package manager command you used and trusted a 3rd party app. and that's what happens when you do that. nothing wrong with using bleachbit, but you need some expertise to use it and need to really know what you are doing. 

the choice if you want to stick with linux or move to windows is yours. i had win 8.1 at work before and i have to say that aside from strange start menu i had no issues with it. to me it seemed a good, fast and reliable OS.
now with win 10 i just wish they would let me upgrade to aniversary edition so i can ge tthe dark theme. there is none on this long term support version and my eyes and eyes of my colleagues) are suffering. i made all office stuff dark grey. well at least something, still wish i had the option of dark theme.

---

### Post by lammert-nijhof on 2017-02-04
If you want a fast "boot up" don't 'shut down' Ubuntu, but 'suspend' it. It will be back in 1 second or 2 seconds if you count the re-initiation of the network.

---

