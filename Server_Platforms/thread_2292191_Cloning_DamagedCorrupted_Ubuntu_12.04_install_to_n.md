---
title: "Cloning Damaged/Corrupted Ubuntu 12.04 install to new HD"
date: 2015-08-26
forum: Server Platforms
---

### Post by Marc-NJ on 2015-08-26
I have a damaged/corrupted Ubuntu 12.04 install (most likely due to issues with the hard disk).  Clonezilla doesn't seem to be able to clone it to a new hard drive - I've gotten a variety of different issues/errors when attempting it, but it's not managed to do it so far (even with using fsck when attempting to clone).  Can anyone recommend a way to do this so I can try and clone it to a new hard drive (and hopefully if the portions that are damaged aren't critical, get it up and running again)?

Thanks very much!  Feel free to ask me if more info is needed and I'll happily provide.

---

### Post by TheFu on 2015-08-26
Use **ddrescue** to clone it. It is the best tool to clone bit-for-bit when the disk involved is failing. Clone either the entire disk device (which gets the partition table too) or at the partition level.

Boot off a liveCD/flash drive for this.

---

### Post by Marc-NJ on 2015-08-26
Just tried to boot up the machine using a LiveCD with the bad/damaged drive connected via a USB enclosure and the destination drive in the machine (via SATA) and it detected both.  Then wanted to wipe the destination drive (so I could use ddrecuse to clone to that drive) but wanted to be absolutely certain I didn't accidentally wipe the bad/damaged drive, so I disconnected it.  Wiped the destination drive in the machine, and now I can't get Ubuntu LiveCD to detect the bad/damaged drive any longer.  I've restarted with the LiveCD, and still no go.  In fact, when I hit F12 for boot options, it doesn't even list the bad/damaged drive there any longer (which it used to).  Did I just somehow kill that drive?  Any suggestions on how to fix this so I can try ddrescue?  Thanks!

---

### Post by Marc-NJ on 2015-08-26
I tried swapping the bad/damaged drive back into the machine (so it was connected directly to the motherboard via SATA cable) and booted into BIOS, and BIOS is reporting "Drive details | Drive ID = Unknown" - so does that mean this drive is basically toast, or anything else I can try?

Thanks!

---

