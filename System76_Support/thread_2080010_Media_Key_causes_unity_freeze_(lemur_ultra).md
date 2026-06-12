---
title: "Media Key causes unity freeze (lemur ultra)"
date: 2012-11-02
forum: System76 Support
---

### Post by screaminj3sus on 2012-11-02
I have a pretty new system76 lemur ultra running ubuntu 12.10. I've noticed a VERY annoying bug with the lemur ultra's play/pause key and unity. At first I thought this was a rhythmbox bug but it happens with every single media player:

About 50% of the time when I use the play/pause key on the keyboard (fn + `), it causes unity to semi-freeze, I can't click on any indicators and the dash won't open, but I can mouse over stuff on the launcher and tooltips show. The freeze lasts until I hit the media key again, also when the bug triggers the media key doesn't have any effect on play/pause until it un-triggers (I can make it go away by hitting the key a few times). This is infuriating! It doesn't happen on any of my other laptops running ubuntu, seems to be an issue specific to the system76's media key...

I've made a video of what it looks like when the bug is triggered: [http://www.youtube.com/watch?v=52TaFzCDDkA&feature=youtu.be](http://www.youtube.com/watch?v=52TaFzCDDkA&feature=youtu.be)

EDIT: I've now been able to reproduce it a few times with all media players closed (rebooted, logged in, used the play/pause key a few times and the bug triggered as in the above video),  so its definitely just something to do with that key. The only time this bug ever appears is when using that specific key on the keyboard (fn + `)

EDIT2: I can also reproduce it on an ubuntu 12.10 liveusb, so its not just limited to my install. Downloaded 12.10, put it on a usb, booted it. Used the media key. Bam, freeze.

EDIT3: Also reproducible with gnome-shell (stops activities from opening), so not unity specific.

**EDIT4: Talked with system76 support. Doesn't seem to be an ubuntu issue, rather a firmware issue that occurs when fn + ~ is hit too quickly, the firmware gets confused and causes a lockup.** I've just changed the keybinding in the gnome settings to avoid the issue.

---

