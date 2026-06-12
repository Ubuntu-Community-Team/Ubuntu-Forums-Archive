---
title: "Ubuntu ZFS and non-ECC RAM"
date: 2019-09-15
forum: Ubuntu, Linux and OS Chat
---

### Post by david509 on 2019-09-15
I see that ZFS is being offered as a (possible?) root file system in future Ubuntu releases.

I know that ZFS is able to prevent data corruption that (most) other file systems miss. But desktop and laptop PC's don't have ECC RAM, which could undermine the reliability of ZFS error correction? Would it be possible for the future desktop Ubuntu releases to configure ZFS to check for RAM errors by default: ZFS_DEBUG_MODIFY flag (zfs_flags=0x10)?

---

### Post by lammert-nijhof on 2019-09-17
There is nothing wrong with the ZFS file corruption prevention without ECC RAM. It still works and it will prevent any file corruption due to bit rot on disk, power fails or system crashes unlike ext4 and ntfs. In the place where I live, we have 10 power-fails/week and many music files got corrupted over the years and that stopped after using ZFS.

ECC RAM only adds to the system the possibility to correct and detect errors in the memory itself by the memory itself, but it has no relation with ZFS. 

Of course non-ECC RAM errors might cause your system or zfs to crash or to behave strangely and then you have to run a memory test program and replace the faulty memory stick. You could run those programs periodically as a kind of prevention and early detection.

---

### Post by david509 on 2019-11-03
[COLOR=#000000][FONT=&amp]Non-ECC memory can be problematic, even if it passes memtest86+ (or years of 100% reliable operation).

Quote from this link: [https://louwrentius.com/please-use-zfs-with-ecc-memory.html](https://louwrentius.com/please-use-zfs-with-ecc-memory.html)

"**Q:** When I bought my non-ECC memory, I ran memtest86+ and no errors were found, even after a burn-in tests. So I think I'm safe.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] **A:** No. A memory test with memtest86+ is just a snapshot in time. At that time, when you ran the test, you had the assurance that memory was fine. It could have gone bad right now while you are reading these words. And could be corrupting your data as we speak. So running memtest86+ frequently doesn't really buy you much."[/FONT][/COLOR]

---

### Post by TheFu on 2019-11-03
ECC is preferred, regardless of the file system.
But ZFS has extra validations that other file systems do not, so, on balance, ZFS would be better from a data corruption standpoint than any of the other options.   Yes?

---

### Post by david509 on 2019-11-04
> **TheFu said:**
> ECC is preferred, regardless of the file system.
But ZFS has extra validations that other file systems do not, so, on balance, ZFS would be better from a data corruption standpoint than any of the other options.   Yes?

Definitely. 
I believe the **desktop** versions of Ubuntu should validate the ZFS data in RAM, given that the vast majority of desktop computers/laptops don't have ECC RAM. This would prevent the occasional or rare bit-flip in RAM from ever corrupting ZFS.

---

