---
title: "mdadm RAID5 woes: spare to active?"
date: 2012-12-20
forum: Server Platforms
---

### Post by codemaster on 2012-12-20
So I recently came home to find that data access to my RAID5 4-disk array was a bit spotty and checked my mdstat. Holy shnikes, two drives dropped! So I rebooted into a live CD, force assembled the RAID which left me with 3 out of 4 disks. Phew.

I tried to re-add the 4th disk, but was unable to. I did a bunch of googling, trying to see what the best way was to re-add this disk. I eventually found some instructions that said to fail it, remove it, zero-superblock it, and add it to the array again.

This worked!...however, I now have my RAID rebuilding with 3 active syncs and one "spare rebuilding".

Is there any way I can convert this spare to an active drive? I'd rather not have a degraded array, of course, although my mail goal is to have access to my data again (hopefully :()

---

### Post by darkod on 2012-12-20
Is the spare the "new" one? After you zero superblocked it, it is considered as new because it will not be detected that it was ever part of the array.
When you add a new disk to a degraded array, it should start the sync process and until it finishes it will be in dagraded state. Is the sync process finished and the disk still shows as spare?

---

### Post by codemaster on 2012-12-21
I managed to luck out and it seems after fully rebuilding, it swapped from a spare to active! Awesome :)

Thanks for your good luck!

---

