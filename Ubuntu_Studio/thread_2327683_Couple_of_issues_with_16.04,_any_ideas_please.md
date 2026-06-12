---
title: "Couple of issues with 16.04, any ideas please?"
date: 2016-06-13
forum: Ubuntu Studio
---

### Post by andrew-q2 on 2016-06-13
hi,  I recently installed Ubuntu Studio 16.04 on a Dell laptop, and it seems to be working ok, roughly speaking.
However I have 2 issues,
1) the USB mouse pointer disappears when the system is resumed from having been suspended.  Obviously this makes it unusable!  Ubuntu is seeing the mouse move, because when you manage to get over a control, it lightens.  So you can eventually find the power button icon, click, and shut down.  But the pointer is invisible.  It's fine again when you re-boot.
2) I can't see how to install my screen profile which I had working on a previous 12.04 standard Ubuntu partition.  The various screen-related apps don't seem to have a way of installing it.  Was there a "Colour" app in 12.04 that provided for profiles? - if so, I can't see it among the 16.04 apps.
Any thoughts would be  much appreciated,
thanks.

---

### Post by Fire_Chief on 2016-06-15
Hi Andrew,

Curious about the mouse pointer. What happens if you restart only the GUI after resume using the ctrl-alt-backspace key combination?

Cheers!

---

### Post by andrew-q2 on 2016-06-17
hi,   ctrl-alt-backspace has no effect!  Nothing on the screen changes, nor does the disk light respond.  The pointer is still invisible and behaves as above.  But thanks for replying.

---

### Post by Fire_Chief on 2016-06-17
Ah...my info for Ubuntu is a bit outdated it seems. The ctrl-alt-backspace combination was disabled a while back but can be re-enabled.
See how to enable it here. [http://askubuntu.com/questions/367983/how-do-i-enable-ctrl-alt-backspace-to-kill-the-x-server]("http://askubuntu.com/questions/367983/how-do-i-enable-ctrl-alt-backspace-to-kill-the-x-server")

Cheers!

---

### Post by speartip on 2016-06-17
Your 1st issue is a known bug
Until it's resolved ctrl +alt+f1 then ctrl +alt+f7 should bring the pointer back.

---

### Post by andrew-q2 on 2016-06-17
Thanks @speartip, the above works...

---

### Post by ignitionn on 2016-06-25
Sorry for replying to a week-old thread, but I solved this problem by installing a different screen lock. i3lock works, but it's rather ugly so I prefer i3lock-color (a fork) + i3lock-fancy (a bash script that wraps around that fork to give you a snazzy blur effect). To install it as your default lock, replace /usr/bin/slock with a symbolic link to the executable.

---

### Post by yoshii on 2016-06-27
Always check the release notes for any Linux distro and it makes these things easier to cope with before they happen.

---

