---
title: "Ubuntu 16.10/64 bit Unity 8 issue..."
date: 2016-10-16
forum: Virtualisation
---

### Post by dfrandin on 2016-10-16
I just installed the Ubuntu-16.10-desktop-amd64.iso as a Virtualbox VM on my host system running KUbuntu 14.04. The install of 16.10 went flawlessly and the default Ubuntu login works fine, however, the only reason I installed 16.10 was to see what Unity8 looks like, as I stay on LTS versions only on my VM host system. When I try to login with the "Unity8" login at the greeter, my password is apparently accepted, the screen goes black for a moment, and then returns to the greeter.  Not sure whats going on here....

Dave

---

### Post by deadflowr on 2016-10-16
Seems mir is incompatible in Virtualbox.
see a current bug:
[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1632968]("https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1632968")

---

### Post by howefield on 2016-10-16
Thread moved to the "*Virtualisation*" forum.

---

### Post by dfrandin on 2016-10-16
Hmmm.. Thanks for the tip... Guess I'll have to wait a while till I can check out Unity8..

---

### Post by deadflowr on 2016-10-16
> **dfrandin said:**
> Hmmm.. Thanks for the tip... Guess I'll have to wait a while till I can check out Unity8..

It runs fine in a live session and real hardware.
[https://ubuntuforums.org/showthread.php?t=2339314]("https://ubuntuforums.org/showthread.php?t=2339314")
fur what it's worth

---

### Post by dfrandin on 2016-10-17
I don't currently have any spare hardware to run it on.. I've always tested new releases via Virtualbox.. I wasn't aware that 16.10 had made the switch from Xorg to Mir... 

Thanks
Dave

---

