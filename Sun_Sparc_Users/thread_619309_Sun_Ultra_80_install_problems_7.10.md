---
title: "Sun Ultra 80 install problems 7.10"
date: 2007-11-21
forum: Sun Sparc Users
---

### Post by Tancor on 2007-11-21
Hi all,
I wanted to try 7.10 on my Ultra 80, but I'm having some trouble.

It is locking up when it gets to booting linux.  

At first I thought it might be because I had 2 video cards in the machine, so I took one out and still have the same problem.

I have:
Ultra 80, 2gig ram, 4x450 CPU, 2x36gig SCSI HD, 2 (currently 1) Elite3D Lite video cards.

I'm not quite sure why it is locking up.  I have OBP 3.32 (at least that's what I think it is off hand, it's either 3.32 or 3.31).  I get the initial boot prompt where I can go rescue or install, and after install it's after the inital load - it identifies one of the PCI items, then shows (either loading or booting) linux and hangs.

Any tips would be appreciated!

-T

---

### Post by jcastill on 2007-11-21
Well I got some Ultra 60 with cdual elite3d cards with OBP 3.31 and they work fine. Do you know if the Ultra 80 has UltraSparc III or II CPU? Maybe the problem is over there... Ultra60 has UltraSparc II @ 360MHz.

---

### Post by Tancor on 2007-11-26
Hi,
No, it uses Ultrasparc II cpu's.  I'm thinking of trying installing 6.06 lts first and see if I can then do an upgrade.

Does the 60 use SCSI for the disks, or IDE?

-T

---

### Post by jcastill on 2007-11-26
SCSI 80 pin. I curently have 2x9GB HDD installed. Are you using CDROM boot or netboot? I use netboot.

---

