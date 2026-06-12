---
title: "Studio 10.10 dualboot on Mac -- launching any app crashes the whole machine"
date: 2011-03-31
forum: Ubuntu Studio
---

### Post by LeFou on 2011-03-31
I finally got US 10.10 successfully booting on my MacbookPro yesterday, but after logging in and seeing the (beautiful) desktop, attempting to launch any app fails utterly -- the screen goes blank and I have to power the machine off.

Possibly-related observations:

1) When dealing with an earlier installation issue, I added
-rw /bin/bash
to the grub boot line, so that I could get a root console. But when I did this I got
root:>
and was unable to type anything at the prompt. I no longer have this line in grub

2) This MBP has a wonky sensor, and consequently OSX doesn't run the fan properly. I had to install a Fan Control plugin to keep it cool.

3) I have just now successfully got some apps to launch by selecting "User Defined Session" at the gdm login screen... then I logged out and back in with the regular Ubuntu Desktop and .. wow, things working much better.

So maybe I'm okay now.. any ideas as to what was happening? Things for me to check on?

---

