---
title: "fresh install - browser videos don't play"
date: 2016-08-29
forum: Virtualisation
---

### Post by celador1unforsaken on 2016-08-29
fresh install of ubuntu and xubuntu (tried both) in virtualbox, youtube and vimeo straight up do not work whatsoever. the first frame of the video loads (and the grey bar goes all the way to the right), and the ticks of the ads load, but the video never plays. no audio, nothing. moving the slider around makes the video go to the frame, but it just never plays. tried both firefox and chromium.

the 'are you experiencing issues' blue box sometimes pops up underneath the video but youtube works fine on my host machine..

---

### Post by howefield on 2016-08-29
Thread moved to the "*Virtualisation*" forum.

---

### Post by &amp;KyT$0P# on 2016-08-29
What version of Ubuntu/Xubuntu?  What version of VirtualBox?
What's the setting for 3D, is it enabled or disabled?
Do you have Guest Additions installed?

What browser (& version) are you using, and did you install it through the package manager?

---

### Post by celador1unforsaken on 2016-08-29
16.04.1 is the version, 5.1.4 vb.
3d was not enabled, will try that again now. 
yeah tried with/without guest additions.

doesn't work on firefox (came with os) or chromium i got through package manager.

---

### Post by &amp;KyT$0P# on 2016-08-29
If you instead use [latest VirtualBox 5.0.x]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0") does it work?

---

### Post by celador1unforsaken on 2016-08-29
well that fixed it. thanks! what was i running? i just downloaded it a few days ago..

---

### Post by &amp;KyT$0P# on 2016-08-29
You're welcome!  :KS

> what was i running?
According to your previous post you were running latest **5.1.x** VirtualBox which although considered stable has been reported to have various weird issues especially including graphics issues.

---

