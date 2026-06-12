---
title: "Help with wine and fps's"
date: 2009-11-11
forum: Wine
---

### Post by Roll FizzleBeef on 2009-11-11
Preface: I am a complete nub to Linux in general.  


I have installed two games, "Thief gold edition" and "System Shock 2," using wine.  Installation went fine.  When I run the games normally, my resolution goes crazy and I can only see the top-left corner of ANY of my workspaces.  

If I run the games from a virtual desktop, they actually run perfectly.  That is, the menus work.  The intro videos work.  The loading screen works.  Once the game is finished loading, NOTHING!  A black screen, my computer freezes up, and I have to cold boot.  

This occurs for BOTH games, at the same time; just as gameplay *should* start.  

Maybe a graphic's thing?  

Using a Dell Inspirion 1150 with 512 megs of RAM, intel 2.4 GHz.  

Any help would be appreciated.  

P.S. I'm loving this community and this OS, even though I just started.  Help me sever the umbilical cord from microsoft...

---

### Post by beastrace91 on 2009-11-11
Wine version, graphics card, and driver version?

~Jeff

---

### Post by Roll FizzleBeef on 2009-11-11
Wine 1.1.32

I do not know nor know how to check what my graphics card and driver versions are.  The computer I am using is a hand-me-down I got recently.  Decided to make it my ubuntu playground.  How would I go about figuring these things out?  

Thanks.

---

### Post by beastrace91 on 2009-11-11
Run the following in terminal - ```
sudo apt-get install sysinfo
```

Then go to *Applications->System Tools->System Info* it will detail everything there.

Regards,
~Jeff

---

### Post by Roll FizzleBeef on 2009-11-11
Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
Subsystem: Dell Device 017f

Driver Version?

---

### Post by beastrace91 on 2009-11-11
Ahh this is what I feared - with an intel gfx card you are limited with what you can do. I fear under Ubuntu it does not have enough steam to run 3D apps under Wine :(

~Jeff

---

### Post by Roll FizzleBeef on 2009-11-11
Alas!  Well, thanks for the help.  

Could it run a linux-native 3d game?  It doesn't have to be all that new.  A horror-style game or fps to while away the time would be great.  

If not I'll just stick to ROMS and my PS3(which one day I may put linux on as well).

---

### Post by beastrace91 on 2009-11-11
Give it a try - the default intel drivers are alright for native applications.

~Jeff

---

### Post by Roll FizzleBeef on 2009-11-11
Any recommendations?  Sorry if I'm being annoying.

---

### Post by beastrace91 on 2009-11-12
Check the repos - Alien Arena, Nexiuz, or Tux Racer are all solid ones.

~Jeff

---

### Post by Roll FizzleBeef on 2009-11-12
Thanks.  I think I'm gonna like this community.

---

### Post by beastrace91 on 2009-11-12
:) It is a nice place to be.

~Jeff

---

### Post by David_UK on 2009-11-21
Roll FizzleBeef
I'm a bit fan of fps games too, and although it's rather different, I also love BZFlag, which you can download with Add/Remove.  Quite difficult to even stay alive, but a similar kick to fps games.  It'll run on virtually any hardware!

PS welcome to Ubuntu

---

