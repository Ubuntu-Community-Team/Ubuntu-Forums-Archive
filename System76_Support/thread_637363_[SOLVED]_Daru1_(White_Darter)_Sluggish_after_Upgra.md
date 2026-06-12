---
title: "[SOLVED] Daru1 (White Darter) Sluggish after Upgrade"
date: 2007-12-10
forum: System76 Support
---

### Post by shaft350x on 2007-12-10
I upgraded my wife's darter1 a few days ago, Gutsy installed fine, except I got the hangup on boot.  I did the "remove piix" fix and it booted up fine.

Now however it takes it quite some time to do normal operations.  Clicking and dragging files, maximizing windows, etc.  From when I've tinkered with it, it seems that when the operation is done, then it works fine after that, but it is still sporadically sluggish.

Is there a way to fix this?  I thought at first this might be an indexing thing with the deskbar applet but I don't think that this is actually the case.

---

### Post by imhavoc on 2007-12-10
My Daru2 is also sluggish after upgrading to Kubuntu 7.10. I've got a duo cpu, so I'm always caught off guard by a momentarily stalled system....

got any thoughts on things I may have done wrong, or things I may have overlooked.

---

### Post by shaft350x on 2007-12-11
Anyone?

(I hate bumping my threads, but my wife really needs her computer to not be doing this)

---

### Post by thomasaaron on 2007-12-12
There was previously a freezing bug that was caused by the cd drive in the Darter. It was fixed by flashing the firmware in the cd drive. Did you ever do that?

If not contact me at support(at)system76(dot)com for instructions.

If you did flash the firmware, you might go to a terminal and run:
top

This will show you what is sucking up cpu time and we can probably figure out what to do from there.

---

### Post by shaft350x on 2007-12-12
Just finished with the drive flash.  I think that did the trick!

Thanks a bunch!

---

