---
title: "mount / read only"
date: 2018-11-23
forum: Security
---

### Post by mcyber4 on 2018-11-23
I'm fine with booting a Little slower from a live usb stick but wonder how to store network logins etc so I don't Need to enter them all the time.
Or maybe someone has a script to boot installed Ubuntu read only?
For security reasons, thanks.

---

### Post by TheFu on 2018-11-23
You can boot an Ubuntu ISO and that will be read only.  I use ddrescue to image the flash drive with a .ISO file.
If you care about security, use wired connections, not wifi. No network setup needed that way for 90+% of systems.

For which parts of the Linux file system can be readonly and which parts need to be read-write, the Linux Filesystem Hierarchy standards are fairly clear. Google that term.

---

