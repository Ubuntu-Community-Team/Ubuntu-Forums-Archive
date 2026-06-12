---
title: "Cannot Play CS1.6 on Ubuntu 9.04 with wine"
date: 2009-10-15
forum: Wine
---

### Post by rudie_techie on 2009-10-15
I **Cannot Play CS1.6 on Ubuntu 9.04 with wine**, I have this computer with Gigabyte G31 motherboard and no graphics card [Onboard Intel graphics]but CS1.6 works on the same machine with Windows XP. I have 3GB Ram. Any other thing i need to mention? Please help... :( The thing is after installing CS, when i start it, it freezes, i installed ms fonts and everything required, but still it wont work...

---

### Post by hikaricore on 2009-10-15
Your "video hardware" probably doesn't support OpenGL very well.
OpenGL is a REQUIREMENT for gaming and such on Linux.
My suggestion is to get a real one such as Nvidia.
ATI cards are coming along well from what I hear as well.

You should also try other 3d applications (native if possible) to see if they run.
As well as ensuring your video drivers are properly installed in the first place.
You can do a basic check with the following in a terminal.

> glxinfo | grep rendering

This should return: Yes.

---

### Post by MaindotC on 2009-10-15
I can't play CS1.6 either on a Gigabyte GA-MA785GM-US2H.  I tried 9.04, and it kept freezing on startup, and some reviews on Newegg said my board worked great in Karmic.  I tried that as well but the same issue - Steam works fine but CS freezes and crashes after 30 secs or so and returns to the desktop with output I posted in another thread.  I really want to play CS on something other than the crappy machine listed in my sig :(

---

### Post by gh4ever on 2009-10-15
I responded to you on my thread.
[http://ubuntuforums.org/showthread.php?p=8105487#post8105487](http://ubuntuforums.org/showthread.php?p=8105487#post8105487)

---

### Post by rudie_techie on 2009-10-15
I don't think its the onboard graphics that is at fault, else i would have problems with it in Windows also. I have tried everything but cannot get this stuff to work. I will try and see if OpenGL is supported for my card on linux. Any other advice/suggestion?

---

### Post by beastrace91 on 2009-10-15
> **rudie_techie said:**
> I don't think its the onboard graphics that is at fault, else i would have problems with it in Windows also.

This is not true. The drivers on Windows work differently (as they are different drivers) than the ones on Ubuntu.

Also it is important to note that on Windows CS uses directX and on Ubuntu Wine uses OpenGL (which odds are is not support by your intel card) to emulate said directX

Regards,
~Jeff

---

### Post by rudie_techie on 2009-10-15
I play CS on windows using OpenGL. I know the drivers work differently as the whole architecture is different, but any way to make it run? Come on guys, there should be a way, i just want to play CS 1.6 not source. Also when i had nvidia graphics card 8400GS it did the same thing. I installed the restricted drivers for nvidia but still i used to get the same problem, CS1.6 screen appears when i select a map and start the game it would freeze at first the screen where map info is shown and we have to click OK....:confused:

---

### Post by beastrace91 on 2009-10-15
What Wine version and what driver version for the nVidia card where you having it crash on? You can get it working on the nVidia card.

As for the intel card - it is simple, if the card does support OpenGL with the current drivers then no there is not a way to get it working on said card.

And just as a heads up the architecture of your system (32/64bit) is the same on Windows and Linux - but just because Windows drivers do something does not mean the Linux drivers for the same hardware will as well (This is the hardware maker's fault).

Sorry,
~Jeff

---

### Post by rudie_techie on 2009-10-16
Well, in that case, mods can close this thread... Isn't going to work... I had tried it around 2 months ago nad i don't know which version of nvidia i had but i had tried both, the one which ubuntu has and the other i downloaded from nvidia... :(

---

### Post by asdfoo on 2009-10-16
> **rudie_techie said:**
> Well, in that case, mods can close this thread... Isn't going to work... I had tried it around 2 months ago nad i don't know which version of nvidia i had but i had tried both, the one which ubuntu has and the other i downloaded from nvidia... :(

Threads aren't closed unless someone does something bad.

I don't know what you mean here, first you had an intel card and intel drivers (which are not of the same quality as windows, hence a lot of things don't work or work in strange ways), then you installed nvidia drivers?  You need to buy a nvidia card to use nvidia drivers.

CS 1.6 worked a few Wine versions ago, 1.1.29 maybe.  Latest version is broken due to some regressions in the part that displays html which causes it to crash on map load.

Yes ATI is coming along compared to nvidia, except they dropped support for many old cards in their newer drivers.  One hopes the free ati drivers should start working well with Wine.

---

### Post by rudie_techie on 2009-10-16
:mad: I had a nvidia graphics card 8400GS and CS wouldn't work, So i used Windows for CS. And now i dont have the nvidia card as it burnt, my idiot brother did something stupid... [I had no cabinet, just the motherboard and other components on my study table. So now i don't have nvidia card but still CS works great with XP and i use OpenGL 32 bit video resolution of 1280x1024. But only on Windows. Ubuntu runs CS in any resolution and from lowest to highest but cannot play the game... I hope you got what my point was... :confused:

---

### Post by asdfoo on 2009-10-16
yeah, so in conclusion, it's a limition of intel drivers on linux, they simply didn't put in the same amount of work as they did with the windows drivers.

---

### Post by MaindotC on 2009-10-16
Can we continue this with the ATI drivers on Karmic being the subject or do I have to start a new thread?

---

### Post by MaindotC on 2009-10-16
Update - check my post on [this thread](http://ubuntuforums.org/showpost.php?p=8116666&postcount=14)

---

