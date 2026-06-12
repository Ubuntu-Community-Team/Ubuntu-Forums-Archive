---
title: "PanV3 no wireless after suspend"
date: 2008-04-29
forum: System76 Support
---

### Post by Zxaos on 2008-04-29
Hi system76 folks!

My installation of Hardy on my panv3 has gone very well so far, however like at the last release of a version, if you suspend or hibernate the machine then you are unable to connect to a wireless network on resume. The system resumes normally, but does not list any available wireless networks.  In addition, the front LED for wireless status doesn't work (at all, not just after resume).

Any suggestions?

---

### Post by thomasaaron on 2008-04-29
Please file a bug report here...
[https://launchpad.net/system76](https://launchpad.net/system76)

In that report, include the output of lsmod before and after suspend.

...and we will have a look at it. It is most likely that the wireless module is not reloading.

---

### Post by Zxaos on 2008-04-29
Ok, now it's working. If I'm ever able to replicate it again, I'll open a bug.

---

### Post by thomasaaron on 2008-04-29
If you can't replicate it, don't worry about reporting the bug.
I've not heard any other customers mention this one.

---

