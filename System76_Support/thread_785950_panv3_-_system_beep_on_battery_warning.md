---
title: "panv3 - system beep on battery warning"
date: 2008-05-07
forum: System76 Support
---

### Post by agentjon on 2008-05-07
Hello:

I've got a panv3 that i got last year (before they started including nvidia graphics/webcam, if that makes any difference) with a clean hardy install from the live cd

My issue is that whenever my battery starts to run down to the point that the battery level systray icon shows its first warning(at 10 or 15 percent I think), I get a really loud system bell beep.

I've already disabled the system beep via System>Preferences>Sound, and "xset b off" doesnt help either. I've also unchecked "Use sound to notify in event of an error" in System>Preferences>Power Management.

Anyone got any ideas?

EDIT: i filed a bug report on launchpad:
[https://bugs.launchpad.net/system76/+bug/227995](https://bugs.launchpad.net/system76/+bug/227995)

---

### Post by thomasaaron on 2008-05-08
You might open gconf-editor, and then navigate to apps > gnome-power-management > lowpower and de-select the on_battery checkbox. If that doesn't do it, it might be a bug in gnome-power-manager.

---

### Post by agentjon on 2008-05-08
Awesome.
I changed the gconf value and ran the battery all the way down to zero without incident (the notification messages from the power manager are still there, which is all I need).  

Thanks!

---

### Post by thomasaaron on 2008-05-09
Lucky guess! I just didn't want to spend four hours running my battery down to test it. So I winged it.

---

### Post by agentjon on 2008-05-10
Uh oh.

The beep is back (or maybe it was never gone in the first place). Looks like it only comes on when my Master volume is on (not muted)

---

### Post by thomasaaron on 2008-05-12
Try...

System > Preferences > Power Managerment > General > Uncheck "Use sound to notify in event of an error"

The use of the word "error" makes me question whether or not it has anything to do with the battery level. But it *is* a power-management function...

It looks like this beep was only recently added into gnome. I'm not seeing a *lot* on it. Most people are REQUESTING it, not trying to get rid of it!

Let me know if that works. I'll keep looking.

---

### Post by agentjon on 2008-05-13
It's already unchecked :\

Since my last post I've also tried removing / blacklisting the pcspkr kernel module. That didn't seem to work either.

I've seen the other threads about power management (not neccessarily related to this at all) that suggest booting with acpi=noirq - do you think that would be worth trying?

But yeah, I'm seeing the same type of stuff out there - looks like people are trying to turn a software sound alert on, not so much trying to turn a hardware sound off...if that makes any sense.

Oh well, I'm going to double check all the settings again and see what happens tonight.

---

### Post by Zxaos on 2008-05-14
As a side note, it seems to do the same thing in gdm if you hit backspace when there's nothing in the edit box. I'm wondering if there isn't some system-wide setting hidden somewhere.

---

### Post by thomasaaron on 2008-05-14
...when there is nothing in what edit box?

If I can reproduce it, it will help me troubleshoot it...

---

### Post by thomasaaron on 2008-05-14
I just got rid of the beep that you get when you are in a terminal and hit the backspace button.

System > Preferences > Sound > System Beep > Uncheck "Enable System Beep"

---

### Post by Gonzell on 2008-05-15
I have the same problem for when my battery runs low. It's by far the most annoying feature ever. And the beep is SO horrifically LOUD too. It's simply embarrassing when it happens in public. None of the solutions above worked for me. The beep only happens when the battery runs low, not when I press backspace in an empty terminal (I already had that disabled and it uses a visual system beep).

---

### Post by thomasaaron on 2008-05-15
Just checked, and there is nothing in the BIOS for it.

---

### Post by thomasaaron on 2008-05-15
In gconf-editor, try going to apps > gnome-power-manager > notify and unchecking "low power."

I'm guessing it won't give you a pop-up. But does it disable the beep?

---

### Post by agentjon on 2008-05-15
> **thomasaaron said:**
> In gconf-editor, try going to apps > gnome-power-manager > notify and unchecking "low power."

I'm guessing it won't give you a pop-up. But does it disable the beep?

I just tried this to no effect.

I'm going to try purging/reinstalling gnome-power-manager and see what happens

---

### Post by agentjon on 2008-05-18
a couple of things i've tried that didnt work, but who knows maybe they'll work for other people:

removed/purged and reinstalled gnome-power-manager (if you try this, do it in the same session, the system won't boot if you restart between removal and reinstallation)

did the aforementioned gconf tweaks on the new install 

and most interestingly:

I removed Power Manager from the list of startup programs (System>Preferences>Session) to make sure gnome-power-manager doesn't run.

So at this point, is it safe to assume this is some kind of kernel issue as opposed to a bug in gnome power manager?

---

### Post by thomasaaron on 2008-05-19
I think you're right about it being a kernel issue. I've seen threads indicating that this feature was added. It's odd, though, that nobody can find a way to control it.

---

### Post by agentjon on 2008-05-22
Odd indeed. Oh well, because it only happens when my front speakers are on, it's not too big a deal for me to just leave the thing muted most of the time.

If you have them handy, could you do me a favor and post a link to those kernel-related thread(s) just so I can keep up with what, if anything happens next?

Thanks!

---

### Post by phyzome on 2008-09-22
> **thomasaaron said:**
> I think you're right about it being a kernel issue. I've seen threads indicating that this feature was added. It's odd, though, that nobody can find a way to control it.

It could be a BIOS feature.  I think I recall seeing something like that in the BIOS settings.

---

### Post by agentjon on 2008-10-15
Just to close out this thread, I guess it's worth mentioning that this seems to have resolved itself in the new Intrepid beta.  

Yay! :)

---

