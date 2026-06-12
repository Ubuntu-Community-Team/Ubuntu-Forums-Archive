---
title: "Single-click sends double-click in Gnome"
date: 2010-04-01
forum: System76 Support
---

### Post by samalex on 2010-04-01
Hi Everyone,

This is about to drive me nuts...  On my PanP5, which is still running 9.04 that came preloaded, most of the time when I single-click the mouse it actually sends a double-click. It's like pushing down the mouse button is interpreted as a click then letting off is another click.  In testing I opened up the Mouse Preferences and where you double-click the lightbulb which lights-up with a double-click to test the gap between clicks, clicking once lights-up the light most of the time.

Months ago I installed the Accessibility features of Gnome to toy with setting-up an on-screen keyboard and that's when it started, but after uninstalling it seemed to fix the problem.  It happened only occasionally but now it seems 95% of the time it's happening but I can't find any rhyme or reason why.

It gets really annoying when trying to navigate menus because I have to hold down the mouse button to keep the menu open and let off on the option I want... which reminds me of the old Mac Classic :)

Anyway, any suggestions on how to gut the accessibility settings or any clue what's causing this?  I even created a new profile and it happens there too, so it's gotta be something in Gnome or the Accessibility layer of Gnome.

Thanks for any advice ..

Sam

---

### Post by samalex on 2010-04-01
I've been testing this more, and I copied my .gconf to .gconfbak and rebooted to get a new desktop.  I figured what the heck, and it didn't help... but moving .gconfbak back to .gconf didn't bring my old desktop back :-(  I guess I just lost all my settings.

But after some testing I did find that the doubleclick problem only happens with the mouse and not the trackpad.  I've tried a second mouse with the same results, so I know it's not hardware problems.

Any suggestions?  Thanks --

Sam

---

### Post by thomasaaron on 2010-04-02
Samalex, I don't know if this is related, but it's worth checking out. 

I happen to *like* opening files and such with a single click. You can set that up in Nautilus by going to Edit > Prefs > Behavior.

But that would make it happen 100% of the time and work with both the mouse and the touchpad.

Also, if you go to System > Prefs > Assistive Technologies in your main menu system, and then click on Mouse Accessibility, there is time delay that slider that allows you to trigger a second mouse click by holding down the mouse button after the first click.

---

### Post by samalex on 2010-04-02
Hi Thomas,

Thanks for the reply... I have played with the Mouse Accessibility and Nautilus Settings, but they are all set pretty much standard from what I can see.

I tried two different Microsoft mice (same model) and it happened on both, but at work I connected Dell mouse and it appears to be working great thus far.  Yesterday I had renamed .gconf to .gconfbak to see if resetting the Gnome settings would work, but it didn't.  Blah though is moving .gconfbak back to .gconf kept the stock profile and didn't bring back my old stuff.  Maybe that had something else to do with it, not sure, but even after doing this with the Microsoft mouse it still had the problem.

Yeah, I know ... that's what i get for using a MS branded mouse :)  I've had it for years and it's always worked.  And now that I'm at work it's not doing the same thing on a second computer, though that system is running Windows.  Just thought maybe it was a hardware problem with the mouse, but doesn't appear to be.

Anyway, I'll keep using the mouse I have now and see if it happens again.  Thus far I've reset-up my desktop with my preferences using the new mouse and it hasn't wigged out thus far.  I'm keeping my fingers crossed :)

Sam

---

### Post by thomasaaron on 2010-04-02
Sounds good. The intermittent-ness of it certainly sounds like hardware.

Maybe the branding on the mouse is causing it to go bad. ;)

---

### Post by fishexe on 2010-05-24
I do not think this is a hardware issue.  I am having the same problem in Gnome (on Debian Lenny) and have tested two different Logitech mice, both of which work normally on my other machines.

This issue is also discussed in these two other threads:
[http://ubuntuforums.org/showthread.php?t=1429091&highlight=gnome+double+click](http://ubuntuforums.org/showthread.php?t=1429091&highlight=gnome+double+click)

[http://ubuntuforums.org/showthread.php?t=1371815&highlight=gnome+double+click](http://ubuntuforums.org/showthread.php?t=1371815&highlight=gnome+double+click)

If anybody finds a solution please cross-post so the people in all the threads can find out about it.

---

### Post by samalex on 2010-05-25
For me it started after I installed the Accessibility tools for Gnome, and even though I verified the setting to send two clicks with a single click was disabled along with uninstalling the Accessibility tools, the problem lingered.

I'm still not sure exactly what the 'fix' was, but as a last ditch effort I replaced the mice, recreated my profile, and even did some digging in the gnome config file, so one or a combination of all this fixed it and I haven't had the problem since.  

I think my mouse was flaky to some degree, but the problem happened even after switching mice so who knows. 

At any rate I never was able to put my finger on exactly what caused it, but it was VERY annoying and almost prompted a reload.

Sam

---

