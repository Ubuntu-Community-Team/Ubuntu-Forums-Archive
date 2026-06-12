---
title: "filesystem errors while mounted, none when unmounted"
date: 2011-03-17
forum: Server Platforms
---

### Post by southerngeek on 2011-03-17
Ok, so here's my problem. I've spent most of the day on this one, and I'm scratching my head. I'm running 10.10 server x64, with six sata drives in a software raid 5 array. I have a seventh 160gb drive with all the system files on it, with lvm partitions for /, /swap, and /home, all ext4. I logged in this morning to a screenful of I/O errors on /dev/dm-0 and /dev/dm-2, which are / and /home respectively. The system had finally had set those two lvm partitions to read only, so I couldn't do much with it. I rebooted, and that seemed to fix the problem. Except now, only on dm-0 (root), I have e2fsck reporting errors. 

The real issue I have now though is that when I boot into recovery mode from the install disk, or one of several live cd's I've tried, and run e2fsck on my activated but now unmounted root partition, it comes out clean, even with e2fsck -f. Boot back into Ubuntu, and it shows errors again whenever it's mounted. Wassup with that?? Can anybody help me please, I'm at a bit of a loss... ](*,) thanks in advance.

---

### Post by dtfinch on 2011-03-18
It almost always returns errors if you try it while the filesystem is mounted read/write. If it gets part way, and something changes mid-scan, it's going to look like an error. And if it actually tries to fix those mistaken errors, while mounted, it could end up corrupting your filesystem.

To run fsck on the root I think you'd normally do "touch /forcefsck" then reboot.

---

### Post by southerngeek on 2011-03-18
I'm running e2fsck -nv, so there's no danger of corrupting anything. Would it still report errors though? I tried it on another mounted volume (/home, or /dev/dm-2), and it came out clean on there.

I also tried running it at boot, came out clean, but then once I've booted I'm still getting the same errors. This is strange...

---

### Post by southerngeek on 2011-03-23
ok.... for anyone else who is ever confused about this, here is what my problem was. Exactly what dtfinch said (thanks for your help). e2fsck was simply spitting out errors because the drive was mounted, which will almost always happen with your root. To run e2fsck you are using files stored in / so that gives it a kind of false positive for errors. So don't freak out if this ever happens to you.... Ah. there is something new to learn about *nix every day. ;):roll:

---

