---
title: "Ubuntu 12.04 Beta 2 freezes before installing?"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by BanannaSplitzer on 2012-04-01
Okay, so I'm trying to do a fresh install of 12.04 on my dell latitude d610 by using a usb. However, it hangs at the splash screen (the one with the orange dots.) I turned off the splash screen to see where it freezes at, and it gets stuck on 
 *starting crash report submission daemon
What should I do?

---

### Post by Paddy Landau on 2012-04-02
I thought this problem had been solved. I suggest you report a bug.

[s](BTW, as 12.04 is still in Beta, this thread should be in the [Ubuntu+1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412") forum.)[/s]

---

### Post by pmwellman on 2012-04-07
I've had this same problem, and I'm pretty sure that it's due to bad Broadcom wireless card drivers failing as the installer is trying to connect to the internet.  You may have to remove or disable the card in the BIOS, then re-enable/reinstall after the process is over.

---

