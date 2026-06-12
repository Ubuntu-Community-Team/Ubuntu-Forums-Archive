---
title: "How to see rcX summary?"
date: 2013-04-17
forum: Server Platforms
---

### Post by pneumatic on 2013-04-17
I have an amazing dual-primary DRBD iSCSI SAN configured with aacraid, drbd and targetcli (iSCSI) to sit under VMware.  Everything works great except for the order in which the services start.


[LIST=1]
[*]DISCLAIMER: Adaptec 6805E cards in RAID1 were faster than mdadm RAID1.  Please don't punish me for this.
[*]DRBD needs to start first (assuming that aacraid.ko is loaded).
[*]"target" needs to start after drbd.
[/LIST]

This sequence does not happen properly because I need to restart target after each reboot.  I could inspect all of the rcX files to figure out what is where but there has to be an easier way to do this, no?

How do I easily list the runlevel defaults?

---

