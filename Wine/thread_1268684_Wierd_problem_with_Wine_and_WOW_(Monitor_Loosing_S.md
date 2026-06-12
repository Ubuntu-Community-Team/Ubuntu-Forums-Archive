---
title: "Wierd problem with Wine and WOW (Monitor Loosing Signal and locking up)"
date: 2009-09-17
forum: Wine
---

### Post by LeoLeal on 2009-09-17
Hi Friends, 

This is not just another WOW Thread. I'll tell you my story and then If you ever see It please share your knowledge... if U never see It, please share your Ideas, cause I ran out of them.

I'm having a serious problem with playing WOW. When i play WoW throught Wine - It can take seconds or It can take several minutes of gameplay - my Monitor just looses signal and the computer locks up completely! Only a Hard reset can take me back to the Desktop. Nothing seems to fix this. What i Already Tried:

- Reinstall Wine;
- Reinstall WOW;
- Setting the Power Manager to "Always On" on everthing;
- Turning Off Power management in the BIOS;
- Change Display Drivers;
- Change Graphics card;
- Change PSU;
- Format the computer and reinstall everything;
- Formatting the Computer and changed from Ubuntu 64 to 32 and Vice versa(Formatted 3 Times);

Heck! I tried migrating all my hardware pieces to another computer mobo+CPU one by one and testing... with no sucess... I Even just put my HDD with Ubuntu Installed in another computer with a "weaker" graphics card and complete different hardware to eliminate the possbility of Hardware and Power Issues. Still no success.

As absurd as It may seem, My Biggest suspect is actually the Display Monitor! I Use a LCD Samsung T220 Monitor, and It's the Last piece I couldn't test... I don't have another Monitor and It's the Only piece I used in Both Machines I Tested and Both if them gave me the Random LCD Signal Loss and Lockup.

I mean completely different machines with only the LCD and HDD as a common piece gave me the exact same behaviour, while my firends play wow with Wine nicely.

Before this LCD Monitor I used to play WOW throught Wine just nicely on a 19" CRT Monitor.

Ain't that Strange?

I Already tried switching the Input source of the LCD Monitor from DVI to D-SUB but using the D-SUB connector gave me the same problem still.

Any ideas? Anybody knows about any issues with wine running 3D Games with Samsung T220 LCD? Or Maybe any Issues with XORG and this particular or any other LCD related Problems?

---

### Post by LeoLeal on 2009-09-17
By The way I also tried turning off compiz on both machines... no success yet.

Just for the people that may find It useful, here are the 2 computers used  that gave me the problem:

Computer #1 (My Computer)
- Intel Core 2 Quad Q6600
- 4GB DDR2 Memory
- Geforce 8800GT
- PSU ThermalTake XASER III - 480W (Real)
- MOBO Asus P5K SE

Computer #2 (My Friend's Computer)
- Intel Pentium D 2Ghz;
- 3GB DDR Memory;
- ATI Radeon 9800Pro (Software OpenGL Acceleration, since Ubuntu 9.04 doesnt Support ATI Drivers for this board);
- Generic PSU 480W;
- MOBO Asus DX-Something (rsrsrs)

Computer Pieces in common
- Serial ATA Western Digital HDD 250GB
- Samsung LCD Display Model T220
- Mouse and Keyboard

All Pieces of Hardware were exchanged one by one, even the PSUs, with no successful results.

---

### Post by sena_akada on 2009-09-17
it sounds like a monitor issue definitely. have you tried lowering the hz in your nvidia-settings?

---

### Post by LeoLeal on 2009-09-17
> **sena_akada said:**
> it sounds like a monitor issue definitely. have you tried lowering the hz in your nvidia-settings?

That was one of my guesses too... I tried adjusting It manually but no success... It really looks like Wine (or even ubuntu itself in response to a Wine call)changes the frequency sent to the monitor, cause the Screen flickers once, turns off and the Monitor keep changing from Digital to Analog, like It is searching for a Signal Source.

I'd like to know more about the EDID! There's a Button on NVSettings that says: "Acquire EDID"... and When i Click It is Asks for a Binary File. I WOuld like to know What It does... cause It really looks like IT's something realted to telling the Video Board the Capabilities of the Monitor Itself.

By Default the Monitor is Detected, but Ubuntu doesnt seem to fully understand the Monitor's Capabilities, cause on the Resolution ListBox, all the Resolutions are 4:3 Aspect Ratio, save the Native 1680x1050. That is something that intrigues me. Why isnt there any other 16:9 Resolution listed on the Graphics setting for my Widescreen Monitor?

I Would Like to test this Acquire EDID Feature, but I Can't find a file to use on It.

---

### Post by sena_akada on 2009-09-17
do you still have the old crt monitor? :P

---

### Post by LeoLeal on 2009-09-17
> **sena_akada said:**
> do you still have the old crt monitor? :P
Not anymore :(

But I Got a friend to bring me his Pre-Historic CRT Monitor so I can play WOW for a couple of hours(Hopefully) and be 100% sure that the Monitor (the only piece in common) is the one piece that is causing my headaches... but I really really really really want to workaround this issue with my LCD Display beign used. 

I'm still Looking for an EDID file for T220... If I find some, I'll test It or maybe I'll Acquire the defective EDID from Ubuntu and Edit It using the Monitor's Specifications from the User Manual, if the Resolutions and Frequencies are specified there.

---

### Post by sena_akada on 2009-09-17
> **LeoLeal said:**
> Not anymore :(

But I Got a friend to bring me his Pre-Historic CRT Monitor so I can play WOW for a couple of hours(Hopefully) and be 100% sure that the Monitor (the only piece in common) is the one piece that is causing my headaches... but I really really really really want to workaround this issue with my LCD Display beign used. 

I'm still Looking for an EDID file for T220... If I find some, I'll test It or maybe I'll Acquire the defective EDID from Ubuntu and Edit It using the Monitor's Specifications from the User Manual, if the Resolutions and Frequencies are specified there.

that sucks lol. i use an old crt. i would buy a new monitor, but none of them have as good a dot patch :(

---

### Post by LeoLeal on 2009-09-17
I Just tested It... Played WoW for a full hour and half on my friend's CRT Monitor and No Lucks... Do U believe It really is the LCD Display that is causing My Computer Locks??? rsrsrs..

Now I Need an EDID file to use on Custom EDID... :P

---

### Post by sena_akada on 2009-09-17
> **LeoLeal said:**
> I Just tested It... Played WoW for a full hour and half on my friend's CRT Monitor and No Lucks... Do U believe It really is the LCD Display that is causing My Computer Locks??? rsrsrs..

Now I Need an EDID file to use on Custom EDID... :P

it is really weird :confused:

---

### Post by LeoLeal on 2009-09-18
> **sena_akada said:**
> it is really weird :confused:
Yeah It is really weird, but It's the reality... I still didnt find an EDID File for Samsung T220 nor any clue on how to solve It in another way, but I Can't stay with my Friend's CRT Monitor forever...

---

### Post by sena_akada on 2009-09-18
does your card have tv-out?

---

### Post by sena_akada on 2009-09-18
try [this](http://ubuntuforums.org/showthread.php?t=316985)

---

### Post by LeoLeal on 2009-09-18
That will probably extract the Defective EDID from my Monitor. I Need a good one to replace my monitor's.

Ideally a perso that has a Samsung T220 and plays WOW under wine with no problems! :P

---

### Post by sena_akada on 2009-09-18
> **leoleal said:**
> that will probably extract the defective edid from my monitor. I need a good one to replace my monitor's.

Ideally a perso that has a samsung t220 and plays wow under wine with no problems! :p#-o

---

