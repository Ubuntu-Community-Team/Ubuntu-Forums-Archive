---
title: "Gnome shell freezes sometimes?"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-03-16
Hello All

Installed and updated i386 Precise today on a recycled HP xw6200 PC with quad xeon and nvidia GT520 graphics, restricted drivers as installed from Jockey.

New gnome-shell (3.3.90-0ubuntu1) avoids earlier search bug, but has frozen a couple of times, last one when scrolling in a small LibreOffice document. Unity not freezing. When frozen, no response to mouse or keyboard, can't move windows &c. Can use ctrl-alt-1 to get a tty and sudo reboot from that.

Any pointers as to logs I could load from the tty or on rebooting that would have any useful information as to what is happening?

PS: new gs is very nice

---

### Post by sgage on 2012-04-03
> **keithpeter said:**
> Hello All

Installed and updated i386 Precise today on a recycled HP xw6200 PC with quad xeon and nvidia GT520 graphics, restricted drivers as installed from Jockey.

New gnome-shell (3.3.90-0ubuntu1) avoids earlier search bug, but has frozen a couple of times, last one when scrolling in a small LibreOffice document. Unity not freezing. When frozen, no response to mouse or keyboard, can't move windows &c. Can use ctrl-alt-1 to get a tty and sudo reboot from that.

Any pointers as to logs I could load from the tty or on rebooting that would have any useful information as to what is happening?

PS: new gs is very nice

I am seeing occasional freezes with GS 3.4 now. Sometimes after a few seconds, the shell resets itself and all is well. Sometimes after a few seconds the panel goes away, and that's that. Ctl-alt-sysrq-k will get to the login screen.

---

