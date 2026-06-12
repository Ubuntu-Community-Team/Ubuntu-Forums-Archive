---
title: "Generic mechanical keyboards -- suspend/resume problem &amp; fix"
date: 2017-10-22
forum: Ubuntu, Linux and OS Chat
---

### Post by kurt18947 on 2017-10-22
I just received an EagleTek KG-010 keyboard. This is one brand, there are others with the same USB I.D., 04d9:a0cd.  I do like the keyboard, much prefer mechanical keys to membrane types even if they're a little noisy and the blue backlighted keys are pretty:). The keyboard worked great on initial boot but after suspending and resuming, no keystrokes were recognized. I plugged its predecessor into another USB port and that one worked fine. I tried a few fixes I found via searching and they didn't work. Here's the one that did:

[https://askubuntu.com/questions/948982/mechanical-keyboard-aukey-km-g9-doesnt-work-after-suspend-ubuntu-gnome-17-04](https://askubuntu.com/questions/948982/mechanical-keyboard-aukey-km-g9-doesnt-work-after-suspend-ubuntu-gnome-17-04)

There is also a kernel patch that is supposed to fix this. I tried 17.10 and it did not exhibit the non-responsive problem, suspend and resume worked as expected.

---

