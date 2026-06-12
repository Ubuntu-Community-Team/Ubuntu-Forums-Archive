---
title: "After update manager, mouse doesn't work"
date: 2010-11-24
forum: System76 Support
---

### Post by tc101 on 2010-11-24
I ran update manager on my new starling.  At on point it asked me something about configuring GRUB and gave me the option to go on without configuring GRUB, which I did, since I didn't know what GRUB is.  

Now I can move the mouse pointer around the screen, but I can't click on anything.  I am entering this message from another computer.  I don't even know how to reboot the computer without using the mouse.  What should I do?

---

### Post by tc101 on 2010-11-24
The situation has now corrected itself and the mouse is working fine without me doing anything.  I didn't  imagine this.  What do you think happened?

---

### Post by matt_symes on 2010-11-24
Hi

> What do you think happened?

No idea. Maybe check the logs?

Kind regards

---

### Post by tc101 on 2010-11-25
It happened a second time, then corrected itself after a few minutes.  It happened both times when I was using firefox, so maybe that is a clue.  You suggested checking the logs.  How do I do that?

---

### Post by matt_symes on 2010-11-25
Hi  

System->Administration->Log File Viewer will display the log file viewer.

The logs i would look at are syslog and dmesg. Also messages, kern.log and xorg0.log might give some clues.

Kind regards.

---

### Post by tc101 on 2010-11-25
Thanks Matt.  I will wait until it happens again and write down the time.  There is so much  info in the log files that think the only way I will be able to track it down is if I know exactly when it happens.

---

