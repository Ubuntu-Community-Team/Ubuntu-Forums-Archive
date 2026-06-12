---
title: "Daru2 earphones/speakers problem in Gutsy"
date: 2007-10-04
forum: System76 Support
---

### Post by sonmez on 2007-10-04
Hello,


I have daru2 with Gutsy on it. I noticed that when I plug in my earphone into the computer  the speakers don't mute.
Is there anyone else experiencing this?

---

### Post by greg_g on 2007-10-04
I am assuming that is this bug:
[https://bugs.launchpad.net/system76/+bug/130669](https://bugs.launchpad.net/system76/+bug/130669)

It is fixed by the System76 driver, however, if you run the current Systm76 driver on Gutsy it won't do anything (because it checks what release you are using, which is good).  The driver will be updated after Gutsy's release.

However, if you manually make the change that Tom mentions in the bug report, I bet it will work.  I haven't tested it though, so be sure to back up the file first.

Hope this helps.

---

