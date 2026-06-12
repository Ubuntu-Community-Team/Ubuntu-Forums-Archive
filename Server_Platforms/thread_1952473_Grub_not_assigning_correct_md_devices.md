---
title: "Grub not assigning correct md devices"
date: 2012-04-04
forum: Server Platforms
---

### Post by zachlac on 2012-04-04
I'm working through a few problems with a Ubuntu server right now (thanks to rubylaser for some other help), and currently I think I'm having a problem with RAID device numbering.

Sometimes, when I boot the computer, it drops to a "grub rescue>" prompt immediately, giving me a "no such device" error.  If I reboot off of a disk and do an "update-grub", then reboot, the problem seems to go away for only that reboot.

What I've noticed is that my RAID1 devices (which /boot is) seem to be numbered strangely in my grub.cfg; for example, I see md125 as boot, but under /dev after I've booted it's md0.

Where does grub get these device names?  How can I verify that these are correct?

---

