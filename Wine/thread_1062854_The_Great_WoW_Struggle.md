---
title: "The Great WoW Struggle"
date: 2009-02-07
forum: Wine
---

### Post by windowlickin on 2009-02-07
After spending the last two days of my existence struggling with installing WoW, then, subsequently, getting it to work, I happily launched WoW.  Now, I was thrilled that i had gotten it to work, but it's almost unplayable:

The graphics constantly glitch
Text disappears whether in the chatbox or otherwise
The cursor will either turn into a box or just disappear

I have no clue how to fix this, and I'm not sure if I'm even posting this in the right forum, and I'd really hate to have to go and dual boot with windows just so i can play this game, please help!

Wine Ver. 1.1.14

---

### Post by xonpathos on 2009-02-07
Are you using compiz?  Supposedly it doesn't make a difference, but I found that WoW (and other games) did some really strange things until I switched back to metacity.

---

### Post by windowlickin on 2009-02-07
> **xonpathos said:**
> Are you using compiz?  Supposedly it doesn't make a difference, but I found that WoW (and other games) did some really strange things until I switched back to metacity.

I probably should have mentioned that I'm a complete linux noob, and i have no clue what those 2 things are

---

### Post by xonpathos on 2009-02-07
Then you've most likely got compiz.

In a terminal, type: metacity --replace

Then try running WoW.

If the metacity --replace made your desktop look less pretty, you can just reboot to get it back the way it was.  However, if it makes WoW run better and you want to keep it that way, go to System -> Preferences -> Appearance.  On the Visual Effects tab, select "None".

---

### Post by windowlickin on 2009-02-07
> **xonpathos said:**
> Then you've most likely got compiz.

In a terminal, type: metacity --replace

Then try running WoW.

If the metacity --replace made your desktop look less pretty, you can just reboot to get it back the way it was.  However, if it makes WoW run better and you want to keep it that way, go to System -> Preferences -> Appearance.  On the Visual Effects tab, select "None".

Still glitches out in the same ways whether visual effects are off or on high.

---

### Post by xonpathos on 2009-02-08
Well I've been running WoW under Wine for about 5 days now, and mine just started having very similar problems today.  I haven't changed anything, but suddenly it has become somewhat instable.  It crashes every couple of hours, and the graphics have gone screwy.  I have found that it seems like some textures are being drawn in the wrong level, if that makes sense, and tend to cover up things that shouldn't be covered up (like the mouse pointer).  If it happens, you can point the "camera" in a different direction and usually get it back, but as soon as you point it back at the offending texture it'll disappear again.

Not sure exactly what's going on, but if you find a resolution before I do, please let me know.  :)

---

### Post by Starmoonhorizon on 2009-02-08
I've been able to get Guild Wars to run successfully since the latest Wine update but not WoW. I can get it to work if I put it in 1st person view but then it will crash soon after.

---

### Post by xonpathos on 2009-02-08
Well, I replaced **all** the DLLs in the system32 folder (except kernel32, gdi32, user32, and ntdll, of course) with the ones from my Windows install and then set up Wine to use those instead of the builtins.  I haven't had a chance to test the performance yet, but it certainly seems to have stopped the random crashes.

---

