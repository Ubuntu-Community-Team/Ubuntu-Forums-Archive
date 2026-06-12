---
title: "Ubuntu Install disc will not boot."
date: 2011-03-06
forum: Ubuntu Studio
---

### Post by KostamojeN on 2011-03-06
I burned a disc from the Ubuntu Studio 10.10 ISO (which works fine in Virtual Box) and it locks up on a black screen.

I have an Athlon II with 4Gb RAM. Surely that should be enough?

Any tips gratefully received.

---

### Post by KostamojeN on 2011-03-08
Has nobody else seen this? :(

---

### Post by sgx on 2011-03-08
It won't work on everything, but I would shut off all extras in the bios, choose vesa or other alternate video mode, and give that a try, then try various boot options like noacpi, noapic, nolapic.

You can make a timing list of what happens up to the blackout, reboot
and duplicate the steps with the monitor unplugged, then plug it in after the blackout time.

Try installing to a usbstick, and boot from that, in case you can get into a shell at some point, to edit config files.

Debian hardware detection is incomplete, all the rpm based distros
I try boot fine, and none of the current mainstream debian variants do.

There may be some motherboard jumpers that can disable/enable something that is not cooperating. Google your motherboard and chipsets to see if others using your motherboard are having such issues.
Good luck!

---

### Post by leeshaub on 2011-03-10
my uncle kevin uses Virtual Box never had that happen

---

### Post by XsheepX on 2011-03-12
Are you booting it by having your disc drive as the first boot item in the sequence? 
Try pressing F12 (or whatever key it may be, depending on your computer) at the startup and manually choose to boot from your disc drive.

---

