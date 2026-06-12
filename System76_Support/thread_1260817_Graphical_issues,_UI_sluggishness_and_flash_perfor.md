---
title: "Graphical issues, UI sluggishness and flash performance"
date: 2009-09-08
forum: System76 Support
---

### Post by bmitchell on 2009-09-08
I recently purchased a Bonobo laptop.  When I received it, I installed the system76 drivers, and ran the update manager.  Afterwards I poked around with the various installed programs, and when I got to the little games, I was sort of disappointed because there were issues that I wouldn't expect on a computer with this hardware, with a clean install.

I am new to linux, and plan to look for ways to improve/fix these problems as I have time, but any help or suggestions would be wonderful.

In Robots and Nibbles, while you're in a non-maximized window, the game performs poorly.  Sprites flicker, old screen information is not cleared consistently or at all (so you can't tell if a sprite is currently in a location, or if it just didn't get cleared).  Running maximized seems to fix most issues.

Gnometris is very sluggish to respond to my pressing arrow keys.  The shapes rotate with an odd, somewhat random delay.  Sometimes almost immediately, sometimes not.  If I hold down to drop a piece, sometime it will start falling faster, then stop completely.  If I let go of the down button in these cases, the pieces usually stays frozen in place until I hit down again.

Flash performance is also poor.  UI response within flash is sluggish.  Framerates are not what I would expect  (Games I run smoothly on my 5 year old XP desktop are choppy on this laptop).  Sound is not timed correctly, there is a noticeable delay.


I don't really care about the pre-installed games themselves, but their poor performance seem to be symptoms indicating that I need to address some issue.  Again, I am a linux noob, so any direction in solving these problems would be great.

Thanks

---

### Post by drewbenn on 2009-09-08
> **bmitchell said:**
> Gnometris is very sluggish to respond to my pressing arrow keys.  The shapes rotate with an odd, somewhat random delay.  Sometimes almost immediately, sometimes not.  If I hold down to drop a piece, sometime it will start falling faster, then stop completely.  If I let go of the down button in these cases, the pieces usually stays frozen in place until I hit down again.

I can't comment on anything else, but I was playing Gnometris a fair amount in Ubuntu 8.10; I thought the game's performance decreased significantly when I upgraded to 9.04.  I don't remember if I was seeing exactly the same issues you described, but everything about it felt "sluggish" and non-responsive.  It was bad enough that I just uninstalled it and installed the bsdgames package for my casual gameplay.

You might, if you have the time, try a few of the games on a 9.04 Live CD on your desktop machine and see if they behave similarly there.

---

### Post by thomasaaron on 2009-09-08
Hmmm... Make no mistake about it, the Bonobo is a lightning bolt. So, there's something else going on.

Have you installed any software? If so, what?
Have you made any configuration changes? If so, what?

Out of curiosity, try disabling desktop effects (System > Prefs > Appearance > Visual Effects > None) and see if things speed up.

If they don't open a terminal (Applications > Accessories > Terminal) and run this command...

```
**top**
```

...and then run gnometris and see what processes appear near the top of top's list of processes. I'm curious as to what might be eating CPU time.

---

### Post by bmitchell on 2009-09-08
I didn't install any additional software on the first run through.  I ran the system76 driver installer, and then ran the Update Manager.


I have, since then, installed Blender via the Add/Remove interface, and at some point I installed something so that I could play mp3's but I can't remember where I found the steps I followed to do that.

I don't believe I've made any configuration changes.

I did the Top thing before and after setting visual effects to None (it was on Normal).

Before: Xorg was on top, followed by gnometris.  As I played Xorg's CPU range was something like 7%-51%, and gnometris's CPU range was maybe 3%-25%.

After:  Xorg still on top, again followed by gnometris.  Initially everything feels more responsive, and Top shows Xorg at 3-4% and gnometris at 1%.  After only a few seconds, it's developed some sluggishness, though it still seems better than before.  CPU spikes seem to be in the 30's for Xorg and usually in the teens for gnometris.   (I did just see a spike to 59% for XOrg.  Yikes!)

---

### Post by thomasaaron on 2009-09-08
It's best to run the System76 Driver *after* updating and rebooting. In other words...

Update
Reboot
System76 Driver
Reboot

That way, if a kernel update breaks something, the System76 Driver has a chance to fix it. So, you might want to try running the driver again (Install tab, Install Button). And then reboot.

Try that and let me know if it fixes the problem.

---

### Post by bmitchell on 2009-09-08
Ok.  I didn't do a system restore or anything, but I did the Update->Reboot->Driver Install->Reboot.  Things seem pretty much the same in gnometris.  Visual effects still set to none, initially seems ok, but degrades after a few seconds.

I mentioned in the first post that if I hold the Down arrow, sometimes the piece will stop mid-drop and the game hangs.  Well, during this run I noticed that if I continue to hold Down during these hangs, top shows Xorg hitting 66% and gnometris hitting 31-32%


A friend said "It looks like software rendering".   How do I find out whether it's using software or hardware graphics?  The only place I know to look is the NVIDIA X Server Settings, and nothing seems to obviously indicate one way or the other.

---

### Post by thomasaaron on 2009-09-09
If you go to System > Administration > Hardware Drivers, what version of the driver nVidia driver are you using?

---

### Post by bmitchell on 2009-09-09
I am using version 180

---

### Post by thomasaaron on 2009-09-09
Try disabling that driver. Then log out and back in. Then re-enable the driver. The log out and back in.

If that doesn't fix it, please post the output of...

```
cat /etc/X11/xorg.conf
```

...and...

```
uname -a
```

---

### Post by bmitchell on 2009-09-09
Ok.  The 2 other games are working fine.  No sprite flickering or anything.

Gnometris still has the same sluggish response.  Maybe drewbenn is right, it just doesn't run well.

Flash has been a little odd.  When I first used the computer, it seemed like no flash was installed.  Later, it was there (I guess after I installed drivers and updated).  Then I followed your Update/Install directions, and it appeared to be gone again (or not showing anything at least).   After the video driver disable/re-enable, flash is back.  It's fine for some things, not fine for others.  Youtube videos seem fine.  Games at kongregate do not.

I realize this is probably more than one issue, and the primary one is probably solved now.  I'm just mentioning everything I notice that seems to be wonky.

Output from the 2 commands in the next post.

---

### Post by bmitchell on 2009-09-09
Output from "cat /etc/X11/xorg.conf":
```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```Output from "uname -a":
```

Linux system76-pc 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009
x86_64 GNU/Linux

```

---

### Post by marshmallow1304 on 2009-09-09
For what it's worth, Gnometris is laggy for me as well, and I've also had the disappearing sprites in Nibbles.  More advanced games (both native and via wine) and flash are flawless.

---

