---
title: "VB fails to start XP after update"
date: 2007-12-29
forum: Virtualisation
---

### Post by fdimmling on 2007-12-29
After updating VB to 1.5.4 from update manager VB fails to start the saved XP image. System is a x86 Gutsy on a Travelmate 4650 notebook with 1GB RAM.

Error Code 0x80004005

VBox status code -1819 (VERR_SSM_LOADER_TOO_MUCH)

Everything worked fine before. :confused:

Friedrich

---

### Post by loupy on 2007-12-29
I had the exact same issue - the only way I was able to get it back up and running was to revert to a previous snapshot.

It seems that if you update virtual box and have VMs in a saved state as opposed to powered off this issue will occur.

I didn't try re-installing the older version of VirtualBox.  You may want to try that if you don't have any snapshots.

---

### Post by fdimmling on 2007-12-29
I was afraid I might have to go back to a previous snapshot (I have one). However it is a bit boring because I have to redo a lot of updates and loose some data.

Anyway thanks for your answering

Friedrich

[Update] Only changes made after the last regular shutdown of XP are lost

---

