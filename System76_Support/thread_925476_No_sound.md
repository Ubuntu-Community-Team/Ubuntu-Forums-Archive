---
title: "No sound?"
date: 2008-09-20
forum: System76 Support
---

### Post by melonbug on 2008-09-20
I just got my System76 Pangolin, and I cannot hear a single thing from it, and it seems as though the mic isn't working either but that's a bit hard to determine, with no sound.

I have tried ending the PulseAudio process, I have turned everything up in the speaker icon switches, I have the volume all the way up through the keyboard control, everything is set to ASLA...

Can someone help me out here?

---

### Post by thomasaaron on 2008-09-21
Run your system76 driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot.

If your sound is gone after resuming from suspend, that is a known bug. If it doesn't work after running the driver, do the following...

double-click the speaker icon.
in the resulting window, go to edit > preferences
select all checkboxes
then make sure nothing is muted or turned down too low

---

### Post by earrame on 2008-09-28
> **thomasaaron said:**
> If your sound is gone after resuming from suspend, that is a known bug.

That must be the issue I am seeing. Is there a fix that doesn't involve a reboot? (I've been rebooting.)

---

### Post by melonbug on 2008-09-29
^ I'd like to know that too.

Also, my mic still doesn't work, as noted earlier. =/

---

### Post by thomasaaron on 2008-09-29
melonbug, 

Your mic will work (I'm assuming you have a new pangolin since you posted in this thread).

Run your system76 driver and reboot. Then double-click the speaker icon and, in the resulting window, go to edit > preferences and make sure all check boxes are selected.

This will activate all available sliders and you will just need to configure it to record from the internal mic.

Let me know if you need more help.

---

