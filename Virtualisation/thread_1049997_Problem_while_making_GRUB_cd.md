---
title: "Problem while making GRUB cd"
date: 2009-01-25
forum: Virtualisation
---

### Post by Fionnzer on 2009-01-25
Im a n00b and  havent a clue how to make this Grub cd thing

>  First, make a top directory for the bootable image, say, `iso':

     $ mkdir iso

Make a directory for GRUB:

     $ mkdir -p iso/boot/grub

Copy the file stage2_eltorito:

     $ cp /usr/lib/grub/i386-pc/stage2_eltorito iso/boot/grub

What does that mean ?
Do I paste the code into terminal ?

---

### Post by photon_man62 on 2009-01-25
> **Fionnzer said:**
> Im a n00b and  havent a clue how to make this Grub cd thing


What does that mean ?
Do I paste the code into terminal ?

Yes, you paste it, but without the $.

---

### Post by Fionnzer on 2009-01-25
> **photon_man62 said:**
> Yes, you paste it, but without the $.

But notin happens when I paste it

---

