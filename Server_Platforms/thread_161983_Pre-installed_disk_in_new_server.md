---
title: "Pre-installed disk in new server"
date: 2006-04-18
forum: Server Platforms
---

### Post by sickdude on 2006-04-18
Hi all,

How was your easter weekend? mine wasfine, thnks for asking :)

anyways, i did a install on a new disk last week and now i wanted to stick the disk in my server (yes other hardware) and i hoped it would go on and boot wiith maybe some hardware issues.

but now it dies on me while booting. it tells me

ALERT! /dev/hda3 does not exist. Dropping to a shell.

i really dont have a clue what i should or can do. so if anybody has a tip i would be very greatfull (as always :D)

---

### Post by localzuk on 2006-04-18
Is the disk plugged in as hda? If not, at the grub boot menu press escape and press e to alter the commands that are used to boot. Change the partition numbering etc... to the true values.

To find them out, you may need to boot off a live cd.

---

