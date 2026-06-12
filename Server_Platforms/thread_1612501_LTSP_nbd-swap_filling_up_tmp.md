---
title: "LTSP: nbd-swap filling up /tmp"
date: 2010-11-03
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-11-03
I noticed this morning on my LTSP server that there are 13 GB in /tmp.  The bulk of the space is eaten up by files that are 128MB in size and called things like "tmp.Zv0lxkfj2".  They're all owned by 'nobody'

Based on size and ownership, I'm thinking these are swap files for nbd swap.  Problem is, I have 13 clients are there are 822 of these swap files.  Clearly, the unused ones aren't getting cleaned up.

I could, I suppose, just start deleting them, but I have no way of knowing which ones are in use.   Is there no mechanism in LTSP for cleaning these files up?

---

### Post by lykwydchykyn on 2010-11-04
bump

---

### Post by lykwydchykyn on 2010-11-04
Wow... Let me rephrase this question:

 - Does anyone out there actually actively use LTSP on Ubuntu Lucid in a production environment?

 - If you do, do you use network swap files?

 - If you do, is /tmp full of several hundred files, each the size of a single swap partition?

---

### Post by lykwydchykyn on 2010-11-19
Bump...

Need some help on this if anyone has seen this issue.  Today it took down the server because / filled up with swap files.

---

### Post by FanOfTuxs on 2010-11-29
Having the same problem (with Maverick 10.10). Apparently it's because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/281501](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/281501)

which is nowadays documented in here:

[https://help.ubuntu.com/community/UbuntuLTSP/EnableNBDSWAP](https://help.ubuntu.com/community/UbuntuLTSP/EnableNBDSWAP)

---

