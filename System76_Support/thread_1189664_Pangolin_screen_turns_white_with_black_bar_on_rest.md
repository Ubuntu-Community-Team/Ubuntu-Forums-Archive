---
title: "Pangolin: screen turns white with black bar on restarts"
date: 2009-06-17
forum: System76 Support
---

### Post by solotwit on 2009-06-17
is this normal? The screen glows bright white with a vertical black bar with some color in it about two inches from the right hand side of the screen. Just before the system76 screen comes up. thanks.

---

### Post by thomasaaron on 2009-06-17
That's kind of strange. I know there's a bug in the nVidia driver that causes some discoloration during shutdown. But I've never seen it prior to the System76 splash page. The nVidia driver isn't being used at that point.

Does it happen on *restarts* or also on fresh boot-ups?
How long have you had the machine, and when did the problem start occuring?
Can you reproduce it at will, or is it intermittent?

---

### Post by solotwit on 2009-06-17
it happens about 9 out of ten times when I restart. It doesn't usually happen on a fresh startup, maybe once I remember it did. I've had this for about a month and it started after about a week I'd guess. I've tried to attach a pic.

---

### Post by thomasaaron on 2009-06-17
OK. That really doesn't look great.

Please start using complete shutdowns and starts for a while. Let me know if it keeps happening. Sometimes a restart isn't the equivalent of a complete shutdown.

If it doesn't happen on fresh starts, I'm not so worried about it. If it does, it should be something we have fixed before your warranty expires.

---

### Post by Scotty Bones on 2009-06-17
I have the same thing, except it happens on shutdown. I see the Ubuntu splash screen, the bar gets to the end, it disappears and I get this distortion.  It stays for a few seconds (maybe 4). Its more like a grid though. white with thin black bars. It steadily gets brighter then the system turns off.


EDIT:

System: Pan 5
Has happened since I received the system. with both the preloaded system (as I received it) and after re-installation.
It happens on every shutdown, but not on restarts

---

### Post by thomasaaron on 2009-06-17
> I have the same thing, except it happens on shutdown. 

I don't think it's the same thing. Yours is an nVidia driver bug. His is happening long before the nVidia driver is ever enabled.

---

### Post by solotwit on 2009-06-17
thanks for the help. I just got back from work and it didn't do it on a "fresh" startup. If it does I will let you know. If it continues to do this on restarts, is it doing any damage to the screen?

---

### Post by thomasaaron on 2009-06-18
No.

---

### Post by solotwit on 2009-06-20
This screen has occured twice during shut down.
:sad:

---

### Post by thomasaaron on 2009-06-20
Not to nitpick your words, but strictly for clarification.

There is an nVidia bug that causes coloration problems *during* shutdown. That is not a problem. My question is: Does it occur on *start-up* after a complete *shutdown*? (Not after a restart.)

---

### Post by solotwit on 2009-06-20
No, not during startup from a complete shutdown. Just during the shutdown, right after the ubuntu progress bar screen. Must just be the nVidia driver then. Thanks again!

---

### Post by bdoe on 2009-08-24
> **Scotty Bones said:**
> I have the same thing, except it happens on shutdown. I see the Ubuntu splash screen, the bar gets to the end, it disappears and I get this distortion.  It stays for a few seconds (maybe 4). Its more like a grid though. white with thin black bars. It steadily gets brighter then the system turns off.
I have pretty much exactly the same issue. I had it for a while when I was running Hardy, but the problem disappeared when I got rid of a script for automounting network shares for an unrelated reason (it was stalling shutdown because it would sometimes create up to a hundred or so mounts to the same share, which each had to be unmounted). Unfortunately, the problem came back immediately upon installing Jaunty, and I have found no fix for it.

---

### Post by samalex on 2009-08-25
Hey Guys,

My PanP5 does the same thing on shutdown as well with the crazy white screen on shutdown.  I could post an image identical to solotwit's.  

I used to run Red Hat Linux on an older Dell Inspiron 3800 about 7-8 years ago and when I had X (I think it was Xfree86 back then) set-up incorrectly this exact same screen would appear but stay up, and you could feel the screen getting VERY warm after a few seconds.  The white screen with the PanP5 doesn't stay long enough to really heat-up, but putting my hand on it you can feel more heat then when it's not white.

Would this damage the screen over time?  

Also something to note, mine has done this since the first day I got it, so I figured it was normal.

Sam

---

### Post by thomasaaron on 2009-08-25
Normal, no.
Fixable at the moment, no.

It's a bug with the nVidia driver. We've had no issues with damage because of it. It's just slightly annoying.

---

### Post by marshmallow1304 on 2009-08-25
White screen at shutdown has happened for me since the beginning.  I haven't noticed any adverse effects.

---

### Post by gila_monster on 2009-08-25
Not sure if this helps, but under Sabayon (with nVidia driver 185.18 installed), I do NOT see the white screen on shutdown. Tried a few other flavors, and this seems specific to boxen with nVidia running any Ubuntu-based distribution.

Haven't actually tried plain Debian yet. Would be an interesting experiment.

---

### Post by samalex on 2009-08-25
[QUOTE="thomasaaron"]Normal, no.
Fixable at the moment, no.

It's a bug with the nVidia driver. We've had no issues with damage because of it. It's just slightly annoying. [/QUOTE]

It doesn't bother me at all honestly... I just wait for it to go away before closing the laptop lid.

Thanks --

Sam

---

### Post by bdoe on 2010-01-21
I just wanted to post an update with my experience with this issue.

I made my problem go away by uninstalling network-manager, installing wicd, and making use of wicd's ability to execute scripts on connection/disconnection, telling it to specifically umount my cifs network shares.

The problem is apparently with cifs and init.d. Even though there are scripts in /etc/rc0.d and /etc/rc6.d for shutting down network shares, they are either not executing at all, or are not being allowed to execute to completion before the wireless network connection is killed. I even tried the old hacks to change the shutdown priority for the umountnfs script with no change at all (though executing the script manually worked perfectly).

I tested this out by observing that, with network-manager, when I shut down the laptop, the shutdown splash screen showed, then a short time later, the screen would go black, and then light up with the brilliant white and colored/black vertical bars, eventually fading to black. A few seconds later, the laptop would finally shut down. However, if I manually umounted my cifs shares before selecting shutdown, the whole laptop would shut down within 10 seconds and the white screen problem never happens.

---

### Post by samalex on 2010-01-22
> **bdoe said:**
> I just wanted to post an update with my experience with this issue.

I made my problem go away by uninstalling network-manager, installing wicd, and making use of wicd's ability to execute scripts on connection/disconnection, telling it to specifically umount my cifs network shares.

The problem is apparently with cifs and init.d. Even though there are scripts in /etc/rc0.d and /etc/rc6.d for shutting down network shares, they are either not executing at all, or are not being allowed to execute to completion before the wireless network connection is killed. I even tried the old hacks to change the shutdown priority for the umountnfs script with no change at all (though executing the script manually worked perfectly).

I tested this out by observing that, with network-manager, when I shut down the laptop, the shutdown splash screen showed, then a short time later, the screen would go black, and then light up with the brilliant white and colored/black vertical bars, eventually fading to black. A few seconds later, the laptop would finally shut down. However, if I manually umounted my cifs shares before selecting shutdown, the whole laptop would shut down within 10 seconds and the white screen problem never happens.

Interesting... Not that the white screen on shutdown bothers me, but I may try this out to see if I get the same results.

Sam

---

