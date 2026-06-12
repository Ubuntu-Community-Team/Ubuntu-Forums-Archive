---
title: "Did I brick my pangolin?"
date: 2013-08-21
forum: System76 Support
---

### Post by grizdog on 2013-08-21
I was upgrading my laptop from 12.04 to 12.10, using the update manager.  After it had done the downloads and was applying the changes, a dialog box came up asking if I wanted to kill KDE.  It seemed like a good idea, so I said yes, and the screen went to character mode with a login prompt.  I logged in and did a ps, and didn't see anything that looked like an upgrade going, so I did shutdown -h.  When I turned the machine back on, all I get is the screen with the word "ubuntu" with the little ubuntu log above the last u, and 5 dots under the word.  The dots aren't blinking.  There doesn't appear to be any way to get past it.

How do I get my computer  back?  I don't have a rescue disc.

Thanks

---

### Post by grizdog on 2013-08-22
OK, no I did not.  ctrl-alt-F1 got me a character-based login, presumably I can save it from here.

Thanks to anyone who thought about this.

---

### Post by tgalati4 on 2013-08-22
What was your desktop environment?  If it was KDE and you wiped it out, then that might explain the symptoms.  You can reinstall just your desktop environment from the rescue shell (root terminal).  What desktop environment do you want to use?

---

### Post by grizdog on 2013-08-23
Yes, it was KDE, and after getting a boot disk in there, I could see that KDE had been wiped out, so a restore fixed everything.  I am having another problem getting deja-dup/ubuntu1 to restore my home directory, but I'll open a new thread for that.

Thanks very much.

---

