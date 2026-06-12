---
title: "Netbook Remix: Lock Screen on Suspend?"
date: 2009-10-30
forum: System76 Support
---

### Post by Teasdale on 2009-10-30
I got my Starling a week ago, but I was gone when it arrived so I'm just now playing with it. The Starling works great, but Netbook Remix is different than Ubuntu in some ways I didn't anticipate - that will take some getting used to.

I've been using an EEEPC with eeebuntu installed. To save power, I would put it on 'suspend' instead of shutting it on and off all day. When I turned it on it would come out of 'suspend' and prompt me for my password.

I can't figure out how to do that on the Starling. When I put it on 'suspend,' it comes out without asking for a password. I can't find a setting to require a password to come out of 'suspend.'

---

### Post by thomasaaron on 2009-10-30
Go to a terminal and run...

gconf-editor

In the resulting window, go to apps > gnome power manager > lock and select the suspend checkbox.

Did that work?

---

### Post by Teasdale on 2009-10-30
> **thomasaaron said:**
> Go to a terminal and run...

gconf-editor

In the resulting window, go to apps > gnome power manager > lock and select the suspend checkbox.

Did that work?

It was already checked. So it doesn't appear to be working.

---

### Post by Teasdale on 2009-10-30
I tried it again. It by-passed the login box, went to a black screen, then a minute later, the login box came back up. So it did work this last time. But is it normal for it to take so long on a black screen while coming out of suspend?

---

### Post by thomasaaron on 2009-10-31
Well, it should take a good several seconds. I'd say 10 or 15?? But I don't have one at home to test with this weekend.

---

### Post by Teasdale on 2009-10-31
It seems to be working as it should now - maybe it took it a couple of times to save whatever information it needed at first?

---

### Post by Phyrexicaid on 2009-11-07
If I choose suspend, the screen locks, but if I use the keyboard shortcut (Fn+F4) then when it comes out of sleep the screen is not locked.

Probably what's happened to you as well.

---

### Post by AgenT on 2009-11-12
I get this issue as well. Very strange. What is most annoying, is that lock is disabled in gnome-power-manager (via gconf-editor): apps -> gnome-power-manager -> lock: hibernate, suspend and use_screensave_settings are all disabled (no checkmark). I still get the lock screen when using the menu and no lock screen when using the keyboard shortcut.

Anyone find a solution? I searched gconf-editor and nothing else seems to enable and disable the lock screen mechanism... :-k

Using Ubuntu 9.10, GNOME Version: 2.28.1. Upgraded from Jaunty, where this problem did not occur.

---

