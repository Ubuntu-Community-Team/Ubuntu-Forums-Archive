---
title: "Darter 1, brightness and suspend"
date: 2007-10-20
forum: System76 Support
---

### Post by perce on 2007-10-20
There is already a bug report from Digitalbenji, but I'l repost hre to give the problem more visibility.

After resume from suspend the white Darter is unable to change the brightness of the screen. Fn-F6 and Fn-F5 don't work, power management from the system menu doesn't work either, and even worse brightness is not changed if you go on battery. This problem makes suspend essentially useless if you wont good battery performance on battery.

---

### Post by perce on 2007-10-21
I was experimenting a bit: Ctrl-Alt-F1 followed by Ctrl-Alt F7 fixes the problem. However the text-mode login windows are gone: Ctr-Alt F1 only produces a blank screen; it feels like still in graphic mode, but it dosn't display anything. This smells like a bug related to the Intel driver to me.

---

### Post by thomasaaron on 2007-10-22
Yes, it does. It sounds like it is defaulting to vesa or something instead of sticking with the intel driver...

Will work on this one from Launchpad once I get through the initial "transition to Gutsy" issues on forums and email.

---

