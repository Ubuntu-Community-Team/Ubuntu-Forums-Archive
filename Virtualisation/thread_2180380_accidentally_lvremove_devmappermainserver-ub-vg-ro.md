---
title: "accidentally lvremove /dev/mapper/mainserver-ub-vg-root!"
date: 2013-10-12
forum: Virtualisation
---

### Post by jeanepaul on 2013-10-12
Greetings,

i've accidentally deleted/lvremove my primary /dev/mapper/mainserver-ub-vg-root partition. i cant boot my ubuntu-server anymore. i have been looking through the forums, internet and everywhere for half a day already but no luck. i've tried 
e2fsck /dev/sdb already and nothing happens...

i think i have tried everything already, and now my current error message is "targeted file system doesnt have /sbin/init"

i was installing a new hard disk to my dev-server. partitioned it, and added a storage pool, then a kernel panic happen after i created a new freebsd guest.. after that, i cant boot anymore and while trying every solution out in the internet, i could not find my mainserver-ub-vg partition anymore..

please help, i have lots of projects and in that volume. i need to recover it soon. 

if there is any other way i could recover those files instead, if its impossible to fix this boot problem, please help!!.

---

### Post by TheFu on 2013-10-14
I'm afraid you are screwed.
Time to restore from the last backup you made.
Sorry. Losing changes since the last backup sucks.

---

