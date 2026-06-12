---
title: "TrueCrypt can't mount a 2nd partition under Xubuntu v12.04 LTS"
date: 2013-05-28
forum: Security
---

### Post by scruffyeagle on 2013-05-28
I've relied on TrueCrypt for a long time, and it's performed flawlessly under Ubuntu v10.04 LTS. But, since the forced switch to Xubuntu v12.04 LTS, I've run into a problem, I'm sure the difficulty is being caused by v12.04 OS, because I've used TrueCrypt on Xubuntu v10.04 w/o problems. Anyway, I can get TrueCrypt to mount a single encrypted partition from an external HD w/o any problem. The OS can perform all standard functions on that mounted partition w/o problem - but I can't get TrueCrypt to mount a 2nd partition at the same time. OR, to mount any partition at all if I dismount & close TrueCrypt, then restart it & try to mount something.

I avoid storing any data whatsoever in unencrypted storage, and I sort my data into partitions by category. For example, photos go into one partition, and vids go into a different one. I also mirror my external HD into a backup HD (identically partitioned & encrypted). So, I simply can't function without having several TrueCrypt partitions mounted simultaneously.

I'm actually receiving 2 different error outputs in the pop-up boxes (but not at the same time).

The 1st attempt at mounting any given partition usually (but not always) results in the more lengthy error message, which is:
Failed to write lock '/dev/mapper/truecrypt6': Resource temporarily unavailable
Error opening '/dev/mapper/truecrypt6': Resource temporarily unavailable
Failed to mount '/dev/mapper/truecrypt6': Resource temporarily unavailable

A 2nd attempt at mounting any given partition results in the more simple error message:
device-mapper: create ioctl failed: Device or resource busy
Command failed

Now the capper: If I dismount the one partition I've managed to mount, When I restart TrueCrypt, it's incapable of re-mounting it or any other encrypted partition. The error messages are the same as above.


Anybody know how this issue can be resolved?
Thanks in advance.

---

### Post by scruffyeagle on 2013-06-04
Just an update: I've discovered that my copy of TrueCrypt works properly under the KDE desktop (Kubuntu v12.04). By this, I deduce that the difficulty I've encountered when using Xubuntu v12.04 is NOT because of the kernel - it's the Xubuntu DE obstructing proper functioning of TrueCrypt.

Actually, I should be more specific: The KDE DE I've tested it under was installed as an Xubuntu v12.04 DE. Right after installation, I decided it would be useful to test the v12 KDE, so I immediately installed the KDE, and it's been in use exclusively ever since.

I was browsing some of the other categories, and since I've now pegged that the problem is only happening under the Xubuntu v12.04 DE, I think this thread might be better placed under the "General Help/ Desktop Environments" category. I'd move the thread, but I'm not sure I can do that as a regular member... It might require a higher level of permissions. So, if one of the forum staff is reading this, please go ahead & move it. Thanks in advance.

---

