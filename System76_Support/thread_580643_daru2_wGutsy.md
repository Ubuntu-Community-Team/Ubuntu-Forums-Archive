---
title: "daru2 w/Gutsy"
date: 2007-10-18
forum: System76 Support
---

### Post by palintheus on 2007-10-18
my screen has randomly started blanking, its not dimming or the back light going out, its like I have closed my laptop lid. Anyone else getting this with a daru2 on Gutsy?

---

### Post by sonmez on 2007-10-19
That happened to me couple times yesterday. 
By the way does Daru2 have backlight? if so how do you turn it on off?

Best,

---

### Post by thomasaaron on 2007-10-19
Can you turn the brightness back up with Fn-F5?
Or does jiggling the lcd do anything?

---

### Post by palintheus on 2007-10-19
its not a brightness issue, its like the computer thinks the lid has been closed, I can push any button or tap the touchpad and it comes on.

---

### Post by thomasaaron on 2007-10-19
Have you checked your screensaver settings? Sys > Prefs > Screensaver. That sounds like it is activating the "Blank Screen" screensaver option at some interval.

---

### Post by palintheus on 2007-10-19
It happens at random intervals, sometimes if as soon as I stop typing it goes off, sometimes it stays on for 30min while I let it sit.

I have my screen saver set to something other than blank screen. I thought this may be related to the power management issues that have been plaguing the daru2, but I set the power management to never turn the display off, it still occurs. Other than the screen saver and power management is there another area where screen blanking is controlled?

---

### Post by palintheus on 2007-10-19
Whats strange is that this does not happen when I am playing Tremulous. I can play for an hour or more and the display stays on.

Also should there be any reason that I can't enable visual effects?

---

### Post by greg_g on 2007-10-20
[EDIT: This may be old information, read next post!]
About the visual effects: yes, there is a reason you can't enable it.  The graphics card in daru2 is blacklisted because if you try to play a video or even the visualizations in totem when playing music, totem crashes.  It is a known bug and being worked on. linky: [http://www.realistanew.com/2007/09/23/compiz-in-ubuntu-update/](http://www.realistanew.com/2007/09/23/compiz-in-ubuntu-update/)

You can comment out the line of the compiz check file and be able to run desktop effects that way, but you can't watch videos or play music in Totem (I'm not actually sure about using vlc or something else).

---

### Post by greg_g on 2007-10-20
I may have given you old information in that post.  According to this bug report, the fix is released.  I'm not sure what exactly that means (the last update to compiz was before Gutsy's release, and the card is obviously still blacklisted).

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257)

---

### Post by palintheus on 2007-10-20
hmm, the comments on the bug indicate its still an issue. Thats really a minor issue to me since I do not use them, I have just been trying different things. The screen blanking really annoys me.

---

