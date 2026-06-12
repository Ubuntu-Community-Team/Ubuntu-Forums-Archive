---
title: "Compaq Proliant Secondary IDE Controller weirdness"
date: 2008-09-08
forum: Server Platforms
---

### Post by djb132 on 2008-09-08
I'm using a Compaq Proliant ML330 G2 w/ a single 1.4 GHz Pentium III & SCSI Server Feature Board.

I set ubuntu up booting off a SCSI drive (the only one in the system), a 500 GB SATA drive and a 40 GB IDE drive (master on the Primary IDE channel w/ the CD ROM as slave).  It worked fine.

Then I got the bright idea of putting in two other IDE drives I had laying around.  I hooked them up to the Secondary IDE channel and have had very strange behavior ever since.  The odd behavior began before I even thought to enable the secondary IDE channel.

The first sign something was amiss was I couldn't "F9" into BIOS setup w/ a USB keyboard that worked fine throughout the initial setup of ubuntu.  I switched over to a PS/2 keyboard and everything goes really slowly (& appears to stop - I end up giving up & powering down).

I've not upgraded/updated the BIOS (I plan on doing this tonight) - any other suggestions?

Thanks,
David

---

