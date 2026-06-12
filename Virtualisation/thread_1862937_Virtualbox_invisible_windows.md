---
title: "Virtualbox invisible windows"
date: 2011-10-17
forum: Virtualisation
---

### Post by raabe on 2011-10-17
Hello,

currently, I'm testing Ubuntu 11.10 in Virtualbox 4.1.4. 
With Ubuntu 2D everything works fine, but I've got window problems in Ubuntu default with 3D support.

Login works fine and I see the desktop and menubar. But if I start a program i can't see the program window.
I see the updated menu bar with the menu functions of the running programm but no window visible.

Is there a compiz problem with virtualbox?

Thank's for your help...

Stephan

---

### Post by jackdale on 2011-10-18
I'm having the same problem.  I was having problems with 11.04 and was delighted when 11.10 appeared to work well.  That is until I realised that I was working in Unity 2D.  Going to 3D, everything loads as normal, but I cannot get any windows visible.

This seems to affect all app windows, notification windows (e.g. the "another user is controlling your computer" notification for vnc) and message windows (e.g. the log-out dialogue).

Appropriate mouse changes suggest that the window is being loaded (i.e. the hand icon for buttons and the arrow icons for edges), but the window is not rendered visible.

2D still works perfectly.  Full  3D acceleration is apparent as is guest-additions (e.g. it automatically detects and adjusts for my MacBook Pro's 1400x900 resolution).

Snooping around, I found [this]("https://answers.launchpad.net/ubuntu/+source/compiz/+question/174613") in launchpad:

A kind of workaround is given, but the outcome is a bit messy...and only enables compiz in unity 2D.

MINOR WORKAROUND:
I just discovered that if you click on the workspace switcher, it brings the windows back.  However, returning to the window will cause the window's title bar to remain invisible.  Still, at least I can now work within the Unity 3D environment to see if there is a better workaround.

---

### Post by jackdale on 2011-10-18
OK, after a bit of fiddling, I've got a temporary workaround:

Step 1: Login to Unity
Step 2: type Alt-F2 (or fn-alt-F2 on a Mac)
Step 3: type "killall nautilus" (without the ") and press enter (you will now be able to see windows, but don't open any nautilus windows)
Step 4: install pcmanfm (or other file manager either from terminal: "sudo apt-get install pcmanfm" or from Software Centre)
Step 5: open a window with the new file manager and add it to the unity launcher
Step 6: remove the nautilus home folder from the launcher

When you reboot and log in again, you would have to follow steps 2-3 again, so to prevent that there should be a way to automate the killall nautilus command. However, I tried to just put it in the start-up applications and this killed the gnome session.

The only problem I've had is forgetting that the trash can in the launcher uses nautilus.  If nautilus is accidentally loaded, just do steps 2-3 again.

Also, saving to the desktop will also have problems as it runs on nautilus

NB DO NOT UNINSTALL NAUTILUS as this has some important packages for unity associated with it.

I've submitted it to the bug-report, but if anyone reading this knows how to automate the killall command after login without messing up the gnome session, please submit it to the but report as well.


Even better would be a fix that uses nautilus, as I don't particularly like the other file managers.

[B][COLOR="Red"]
Edit: For a much better, simpler and elegant workaround, please see post by camillo below.[/COLOR][/B]

---

### Post by daeld on 2011-10-18
Well, thanks mate. This works for me. It still leaves it a bit buggy, but at least the fn-alt-f2 works every time. I was about to give up on Ubuntu for my virtualbox.  I'd hate to be without ubuntu, but I don't want to dual-boot the mac.

---

### Post by camillo on 2011-10-31
I had the same problem with macox host. I seem to have found an alternative workaround,
different than that of jackdale, which also works for me. In gnome-tweaks (advanced settings, you should install it, it is not there by default) , under Desktop, choose "have file manager handle the desktop" to "off". This apparently makes the invisible windows bug to disappear. The price (at least, the first one that comes to my mind)  is that you do not have icons on the desktop anymore. But you can use nautilus, there is no need to install an alternative file manager.  And dont have to do go through  the "killall nautilus" routine every time you login. It might be a less annoying  workaround
for someone at least.

---

### Post by jackdale on 2011-11-04
> **camillo said:**
> I had the same problem with macox host. I seem to have found an alternative workaround,
different than that of jackdale, which also works for me. In gnome-tweaks (advanced settings, you should install it, it is not there by default) , under Desktop, choose "have file manager handle the desktop" to "off". This apparently makes the invisible windows bug to disappear. The price (at least, the first one that comes to my mind)  is that you do not have icons on the desktop anymore. But you can use nautilus, there is no need to install an alternative file manager.  And dont have to do go through  the "killall nautilus" routine every time you login. It might be a less annoying  workaround
for someone at least.



Yipee!!!!  Thanks so much!  This works perfectly for me because I don't have icons on my desktop anyway!

:popcorn:

:D

I did give gnome-shell for a few days but now I'm back with unity.  Thanks again.

---

### Post by Aearenda on 2012-02-04
Version 4.1.8 of VirtualBox seems to have fixed this, for me at least!

---

