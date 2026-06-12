---
title: "Another World of Warcraft in Wine whine"
date: 2011-02-19
forum: Wine
---

### Post by Geebsie on 2011-02-19
Right, so I copied my WoW folder from a Windows installation, I'm running it in opengl, using the proprietary ATI drivers (the open-source one gave me glitches in graphics). I have done the recommended tweaks to the registry (the opengl thang) and to the config.wtf file. I can start WoW just fine, I can even play for about 15 minutes, but then it sort of crashes. What happens is that I'll be doing whatever, but my mouse and everything seems to be on the desktop. I'm literally unable to click anything, but the game seems to continue going (mobs and players move around etc), I just can't do anything with it. I even get the little icon when hovering over certain parts of my screen indicating that I can write (the little I icon), and if I type something/hit enter I get a loading icon. It's really odd.

This has happened the two last times I've tried and I've been forced to do a sudo reboot (I'm relatively new to Linux btw!). Also, I'm unable to tab in and out of WoW. I've tried googling this, but most people seem to have an audio issue or a cursor issue when they tab in and out. I simply can't tab anywhere. If I tab once it will kind of have the same symptoms as when it "freezes" (the problem named above), except I can just tab another time and it'll be fine again.

If anyone can help me out with any of this, I'd be very grateful!
Thanks.

EDIT: Ubuntu 10.10, using ATI Radeon Mobility HD 3400 series (on Acer Aspire 5920G). It can handle WoW just fine in Windows btw!
Also running in maximized windowed mode.

EDIT #2: Just ran it in full screen, can't tab.. Goes all screwy when I tab out, but after a while I can at least close the terminal without the entire thing breaking. Will try and run it in full screen and see how it goes after a little while.

---

### Post by ajackson on 2011-02-19
So you want people to help you but you can't be bothered to follow the guidance in the stickies at the top of this forum?

Good luck with that.

---

### Post by Geebsie on 2011-02-19
Uh, exactly what haven't I done?

[LIST=1]
[*]***Use the proprietary drivers for your video card***  - Check
[*]***Check AppDB*** - Check
[*]***Never run Wine with sudo*** - Check
[*]***Do not try and install DirectX*** - Check
[*]***Reinstalling Wine won't help*** - Check
[*]***Update Wine*** - Check
[*]***Search the forums*** - As I stated in my posts, I've looked through a lot of stuff on both crashes and the alt tab thing. So I guess, check·
[*]***Try different Windows versions*** - I might be mistaken here, but I wouldn't think this was the problem. WoW is set to use global settings and it seems to work fine except when it crashes in windowed mode.
[*]***Check the terminal output*** - I've looked and can't find anything that says DLL files missing. My knowledge level isn't really that high which is why I'm asking these "noobish" questions.
[/LIST]

---

### Post by Geebsie on 2011-02-19
Right, so running it in maximized seems to be working. However, I can't alt+tab. If I do I end up with a smaller version of the WoW window centred and all scrambled with colours. And yes, I have googled, I have read the stickies, I have done all this stuff. As I mentioned, the only thing that people seem to have an issue with is sound or cursors.

Are there any settings that I might want to change in Ubuntu for it to allow me alt+tabing in and out?

---

### Post by gerowen on 2011-02-19
Try snagging copies of actual MS .dll files, specifically the Direct3D 9 dll file.  I think it's named d3d_39.dll or something like that.  I had to do this when I played WoW cause' I had issues with the ones from Wine.

---

### Post by ajackson on 2011-02-20
> **Geebsie said:**
> Uh, exactly what haven't I done?
Let's see...

**Wine and Ubuntu version** - Ubuntu version yes, Wine version (probably more important than Ubuntu version) no.
**Terminal output** - You state yourself that your knowledge levels are low so why not include what output you have?
**Wine configuration** - You mention that you've done the recommended registry tweaks but don't say what they are. It is always possible you made a mistake or made changes that weren't needed.

WoW is very playable under Wine but problems require information to solve. I can't express how important the Wine version is.

---

### Post by Geebsie on 2011-02-20
Wine version: 1.2.2
By tweaks to the registry I mean the HKEY_CURRENT_USER -> Software -> Wine -> OpenGL -> Disabled Extensions (data: GL_ARB_vertex_buffer_object) (everyone's kind of saying that this is necessary).

I'll throw in some terminal output later if you think it's necessary, but my main concern is alt-tabbing which I'm sure has to do with settings in Ubuntu or so?

---

### Post by ajackson on 2011-02-20
> **Geebsie said:**
> Wine version: 1.2.2
You could try the development version of wine 1.3.14 (see stickies for how to)

> **Geebsie said:**
> By tweaks to the registry I mean the HKEY_CURRENT_USER -> Software -> Wine -> OpenGL -> Disabled Extensions (data: GL_ARB_vertex_buffer_object) (everyone's kind of saying that this is necessary).
Didn't see any mention of that in the brief glance I made of the WoW AppDB page so I'm not sure where you got that from.

> **Geebsie said:**
> I'll throw in some terminal output later if you think it's necessary, but my main concern is alt-tabbing which I'm sure has to do with settings in Ubuntu or so?
You obviously know better so I doubt I can help you, I hate having to slowly draw information out of people (unless I'm getting paid by the hour of course :)).

---

### Post by Tweak42 on 2011-02-20
> **Geebsie said:**
> Wine version: 1.2.2
By tweaks to the registry I mean the HKEY_CURRENT_USER -> Software -> Wine -> OpenGL -> Disabled Extensions (data: GL_ARB_vertex_buffer_object) (everyone's kind of saying that this is necessary).

It's from Ubuntu community documentation.
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I didn't see it mentioned anywhere but switching the window manager from Compiz to Metacity might help.  I use the Compiz Fusion Icon utility to do this.

Definitely give wine 1.3.14 from the ubuntu ppa a try (see the stickies)

---

### Post by ajackson on 2011-02-20
Hmm that says.

> This is a simple registry edit for Wine that either will either fix crash issues and increase frame rate in game, or it will decrease the performance and even make the game crash. You should give it a try to see what is does for you, as you may always easily remove it again, if it acts negatively for you.
And the OP is complaining about crashing yet includes a tweak that *might* cause crashing - anyone spot the obvious?

---

### Post by Zenmij on 2011-02-22
Just wanted to add my 2 cents.

I cannot alt+tab either, it just doesn't want to play ball. Simple solution to that, I don't alt+tab.

In addition; a small modification to the config.wtf I found useful:
```

SET ffxDeath "0"
SET ffxGlow "0"
```

---

### Post by zurien on 2011-02-22
When I did this for wow this thread here was spot on:
[http://ubuntuforums.org/showthread.php?t=579378&highlight=world+warcraft](http://ubuntuforums.org/showthread.php?t=579378&highlight=world+warcraft)

Since you already have copied the game from windows, just start at step #6.

This command here helped performance in wow aswell for me:
nice -15 wine /PathToWowFolder/Wow.exe

Good luck

---

### Post by damonVT on 2011-03-05
> **ajackson said:**
> anyone spot the obvious?

Yeah, ajackson is a jerk. Kudos for helping and asking specific questions, but drop the attitude.

---

### Post by drs305 on 2011-03-06
As the OP hasn't responded in two weeks and we have multiple mods monitoring this thread due to the tone, the thread is closed. If the OP needs further assistance please ask in the Resolution Center to have the thread reopened.

---

