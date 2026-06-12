---
title: "new Sable Performance desktop, login hangs up"
date: 2009-03-21
forum: System76 Support
---

### Post by budr on 2009-03-21
Yesterday I took delivery of a new Sable Performance desktop machine.  It arrived well packed and with no apparent damage.  When I powered it up the first time, it asked for my language, timezone, keyboard, new user, etc.  Then when I then tried to log in as the new user, I got a blank beige screen. No menus, no nothing.  I could move the mouse cursor around, but AFAICT the system stopped responding to any mouse clicks or keyboard action.  After a short wait I cycled power.  After reboot I was able to log in with no apparent problems.

I immediately did an update/upgrade and it upgraded a couple of packages. Then I spent a little while exploring the new system.  At some point I made a change to system settings that required a reboot.  After the reboot, the first login hung up again at the blank beige screen.  Again I had to cycle power to regain control.

Overnight I downloaded most of kubuntu desktop and installed it this morning.  Another restart and another hang, this time in the kde startup sequence, at about the same time as the previous hang ups in gnome.  KDE puts up the login splash, adds the unfocused drive icon, and hangs at that point.  The drive icon never comes in focus.  Again, the only way I've found to regain control is to cycle power.  I can't even Ctl-Alt-F1 to get a text mode login.

So far this morning I have logged out and in maybe a dozen times.  Roughly half the time the login hangs at the same point.  While it is hung up, the drive light blinks about every two seconds and AFAICT, nothing else happens until I cycle power.

I have almost no experience with gnome, but I've been messing around with linux and kde like forever.  The hangup seems to be at roughly the same place in the login sequence in both gnome and kde.  Has anyone else seen this behavior?

---

### Post by thomasaaron on 2009-03-21
Sounds like it might have taken a bump during shipping and joggled something loose -- loose enough to cause an intermittent problem. The most likely suspects would be a hard drive cable or the video card (if you got the ATI option). 

Can you remove the side panel and check the SATA cables (they're either red or blue) that go between the hard drive and the motherboard? Just re-seat them on both ends.

If you have the graphics card, you can remove it and re-seat it as well. If you have any difficulties with this, give me a call at support.

---

### Post by budr on 2009-03-22
Thanks for the response, Thomas.  I reseated the sata cable at both ends.  No joy.  I just have the onboard X3100 graphics, so no cables to reseat there.  No change in behavior.  

FWIW, this is a Sable Performance, quad core 2.4 GHz, 4 GB mem, 250 GB sata machine, no other extras.  Also FWIW, this is my first experience with 64-bit linux.

This doesn't feel like a hardware problem to me.  First login after a reboot works fine.  Second login hangs at the same place every time.  I added a second user, just in case there was something wrong with that first user setup.  Second user exhibits the same behavior.  First login after reboot works fine, second hangs.  I can login as either user first time after reboot, second login as the same or the other user hangs.

And always at the same place in the login sequence.  I don't know enough about gnome to tell anything useful there, but I've been running kde for a long time.  I've never seen this kind of hangup before, so I've never paid that much attention to the login sequence.  I'm going to ask around the kubuntu and kde forums.  Maybe the precise place where it hangs is a clue to what's going wrong.

---

### Post by mayerg on 2009-03-22
For grins/giggles, try completely removing the SATA cable and power to the DVD drive. Then boot up. For why, see my post under "[ubuntu] boot up error(s)" in this forum.

Regards,

- Gary

---

### Post by budr on 2009-03-22
Thanks, that didn't help either.

---

### Post by thomasaaron on 2009-03-23
It sounds like software to me. However, I'm not going to be able to help you much on the Kubuntu side. 

If the problem is happening in gnome too (sounds like it is) lets work on that side. We don't support Kubuntu.

That said, there is a slim chance that it may have something to do with your monitor. If your monitor is going to sleep, it could conceivably be causing the xserver to crash on the way back from a re-start.

Can you check your monitor settings and disable any power-saving features or sleep mode it may have?

---

### Post by budr on 2009-03-23
I just checked and I don't have any power saving features enabled.  I doubt that would come into it if I did, as I can log in after a fresh reboot, log out, log right back in and freeze in under 40 seconds.  I did that a bunch last night, tailing log files and such.  And it didn't seem to matter whether I chose kde sessions or gnome sessions, the second login always hangs maybe five or ten seconds in.

OK, I have switched back to gdm as login manager and gnome as default session.  When I logged out and tried to log back in, I get the blank beige screen.  I can move the mouse cursor, but that's about it.  I just noticed this bit, which I hadn't noticed before.  Here's what .xsession errors says:

> 
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[6581]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
gnome-session[6581]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout



I'm not at all familiar with gnome, so I don't know how significant that is.  Locate shows a shell script /usr/bin/gnome-wm and /usr/share/gnome/autostart/gnome-wm.desktop. What else should I look for?

---

### Post by thomasaaron on 2009-03-24
Can you please give me a call at support?

It sounds like it is only finding the gnome window manager sometimes, and other times it is failing. Which might point to a corrupted image.

I'm not sure why the heck it is looking for nVidia modules on that machine though.

Anyway, let's take this one to phone support to expedite it, if you don't mind.

---

### Post by budr on 2009-03-24
OK.  I'm at work right now.  I should be able to call you in about 2 hours.

---

### Post by budr on 2009-03-24
No luck, Thomas.  Same behavior with the other monitor.

And just FYI, I'm going be out of state from tomorrow through the 2nd.  I still have to pack this evening, so we may not get to do a lot more on this until I get back next week.

Let me know what else we can try.

---

