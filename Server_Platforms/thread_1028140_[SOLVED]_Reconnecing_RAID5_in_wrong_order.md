---
title: "[SOLVED] Reconnecing RAID5 in wrong order"
date: 2009-01-02
forum: Server Platforms
---

### Post by MilkeySUFC on 2009-01-02
Hi,

I have a small Ubuntu 8.10 box with 3x 500Gb SATA disks in software RAID5 (uses 3 on-board SATA ports). Also has 160Gb IDE system drive.

Issue I have is, after a mobo failure, I made the fatal mistake of pulling the cables out to replace mobo WITHOUT labelling which was SATA0,1,2!!

Now the maching is back up with system drive in, will I have a problem with plugging the 3 RAID5 drives back in if I get them in the wrong order because - as fate would have it - my back-up drive burnt out when I was rebuilding!

TIA,
Milkey

---

### Post by Cracauer on 2009-01-02
You use Linux 'md' drivers, right, not some onboard SATA raid junk?

'md' will just say "whatever" and assemble your drives correctly no matter what order you state. It has extensive on-disk labels that contain the required information.

Just don't use any --force options before checking back with us.

---

### Post by MilkeySUFC on 2009-01-02
> **Cracauer said:**
> You use Linux 'md' drivers, right, not some onboard SATA raid junk?

'md' will just say "whatever" and assemble your drives correctly no matter what order you state. It has extensive on-disk labels that contain the required information.

Just don't use any --force options before checking back with us.

Yes, it uses mdadm.

I went for it and voila! Working, no errors, no warnings, just working. Either I'm a lucky s-o-b and put them all back the right order or mdadm done the business for me. Phew!

Thank you.
Milkey

---

