---
title: "Tips on locking down ubuntu server and workstations locally?"
date: 2011-06-03
forum: Security
---

### Post by bababooey on 2011-06-03
I have a ibm rack running ubuntu server, and 2 ubuntu workstation at work and looking for ideas on how to lock down these boxes. At the moment, I just use screensaver+password to lock down any running xwin session since everything is hooked up to a monitor. There is a lot of traffic here and would like to implement more security locally here, is there more options available to secure my servers and workstations?

---

### Post by Lars Noodén on 2011-06-04
Set the BIOS so that booting is only from the hard drive, not the CD, a floppy or an USB stick.

Set a password on the BIOS so that the BIOS can't be changed

Set a password on Grub to prevent booting into rescue mode.

Be sure not to lose / forget the passwords...

---

