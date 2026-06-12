---
title: "Worst changes after upgrading"
date: 2009-06-30
forum: The Cafe
---

### Post by Leed on 2009-06-30
I love my Ubuntu and I'm hell glad it converted me away from that Windows hell. I also must say, that the developers are doing a great job to make things better, there's updates just about everyday, so many that it even gets annoying, but hey things do get better and you don't get such a service anywhere else than with linux. 

Still there were many changes/attempts that weren't positive, let's name them for a better future: 

-Amarok 2.0
-Removal of Ctrl+alt+backspace
-Removal of Update Icon -> new update window system
-Removal of MSN smileys from Pidgin/Gaim (messages should look the same on each pc)


Anything else?

---

### Post by caravel on 2009-06-30
> **Leed said:**
> -Amarok 2.0
-Removal of Ctrl+alt+backspace
-Removal of Update Icon -> new update window system
-Removal of MSN smileys from Pidgin/Gaim (messages should look the same on each pc)

Trivial things?

-Amarok, I don't think I've ever used.  What is the specific issue?  Can you not remove it and installthe version you want?

-CTRL+ALT+BKSP is nothing to do with Ubuntu, I think that was removed from xorg.  Google it - it's pretty simple to re-enable.

-They (Canonical/Ubuntu) had their reasons for the update icon - I must admit that I can't understand the logic in it either.  There is probably a solution to this, though I've never looked into it.

-Nothing to do with Ubuntu either - I'm not too sure about this, but I think those MSN smilies have been gone for a long time now - we're talking several versions past.  Not sure why they're gone, perhaps the pidgin devs wanted to avoid any possible issues that might arise from using something proprietary?

---

### Post by derekeverett on 2009-06-30
I have to be able to make a VPN connection to my work from home. For some reason I can't seem to connect using 9.04...

I hope they work that out..

---

### Post by Leed on 2009-06-30
@Caravel

Agree, many things are not from the Ubuntu team itself, also this should not be understood as a matter of blaming anyone, every open-source effort is good, it's more about sharing the dislikes to see what others think.

Amarok, yes you can uninstall it and put the previous version on, as long as it stays available at least. Many functions were removed in the new version in an attempt to make things more automated, unfortunately it doesn't work as well as it did before and you can't adjust any settings.

---

### Post by Dragonbite on 2009-06-30
Used to be when I had Pidgin opened, I could click on the icon in the status page I could close all of Pidgin, or disconnect from there. Now I only get a one item menu and have to close Pidgin from the buddies list box.

Also, Pidgin's status bar icon is now an envelope?  Kinda confusing when I get email in Evolution.

---

### Post by Slug71 on 2009-06-30
Well Pidgin is being replaced by Empathy in Karmic 9.10.

---

### Post by Bios Element on 2009-06-30
> **Dragonbite said:**
> Used to be when I had Pidgin opened, I could click on the icon in the status page I could close all of Pidgin, or disconnect from there. Now I only get a one item menu and have to close Pidgin from the buddies list box.

Also, Pidgin's status bar icon is now an envelope?  Kinda confusing when I get email in Evolution.

You have too many posts not to know how to research things. Go play with the pidgin preferences, you can remove the notify applet and add an icon for pidgin.

...Granted I think your just making things more difficult by doing so but I admit it took me a few days to get used to it.

---

### Post by Paqman on 2009-06-30
> **caravel said:**
> 
-They (Canonical/Ubuntu) had their reasons for the update icon - I must admit that I can't understand the logic in it either.  There is probably a solution to this, though I've never looked into it.


There's an option you can check in Gconf that restores the previous behaviour.

---

### Post by mcduck on 2009-06-30
**-Amarok 2.0**
What's the problem? If you don't like Amarok 2 just use something else, or complain to Amarok developers.
[B]
-Removal of Ctrl+alt+backspace[/B]
Can be enabled in xorg.conf, although SysRq+k does pretty much the same thing..

**-Removal of Update Icon -> new update window system**
You can switch to old behaviour through gconf-editor. (apps/update-notifier and disable the "auto_launch"-key)

**-Removal of MSN smileys from Pidgin/Gaim (messages should look the same on each pc)**
Why they should look the same? In my opinion messages sholdn't even have smileys in the first place.. (yes, these were most likely removed to avoid copyright issues)

**-Used to be when I had Pidgin opened, I could click on the icon in the status page I could close all of Pidgin, or disconnect from there. Now I only get a one item menu and have to close Pidgin from the buddies list box.**
You can enable Pidgin's notification icon from Pidgin's preferences. (Tools/Preferences/Interface/Show System Tray Icon->Always)

**-Also, Pidgin's status bar icon is now an envelope? Kinda confusing when I get email in Evolution.**
Although not really a Pidgin-related thing, but I agree that using the letter icon for the *Indicator-Applet* is confusing and pretty bad choice.. However even worse is the fact that the applet becomes invisible when nothing's using it, but doesn't have any handle (like Window List and Notification Area have) that would allow moving/controlling the applet when it's not visible. It's rather annoying to have invisible applet somewhere in the middle of your panel, messing with other applets..

---

