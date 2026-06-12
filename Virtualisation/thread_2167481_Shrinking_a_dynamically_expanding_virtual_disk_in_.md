---
title: "Shrinking a dynamically expanding virtual disk in real time"
date: 2013-08-13
forum: Virtualisation
---

### Post by andicniko on 2013-08-13
I have a dynamically expanding virtual disk which gradually grows in size over time as things get deleted and written etc.

I know I can shrink the virtual disk using zerofree - which I understand zeroes the data on the disk so that it is recognised as empty space by the host machine.

But my question is, can I achieve the same thing in real time by mounting partitions on the virtual disk with a 'discard' option in fstab or something similar?

My thinking is that the 'discard' option is used to perform a trim function on SSDs in real time - which I imagine zeroes data on the disk similar to zerofree (please let me know if any of this is plausable, I am only guessing here). So if the discard option could be used on a dynamically expanding virtual disk partition, then could it shrink as I delete things in real time?

So:
1) Does the discard option for ext4 partitions in fstab perform a function similar to zerofree - does it zero data on the disk?
2) Can the discard option for ext4 partitions in fstab be used for a partition on a virtual disk/HDD, or do SSDs have some extra functionality?

Any help would be appreciated.

---

