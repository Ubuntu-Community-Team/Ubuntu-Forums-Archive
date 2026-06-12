---
title: "fsck problems while booting"
date: 2008-04-17
forum: Server Platforms
---

### Post by awacs on 2008-04-17
After a hardware crash, server won't boot. Fsck fails (fsck not found - WTH?) and drops me into single user. So, I cobble together fsck.ext2 that i found on another system, and bring it over, somehow. Oh yeah, half a dozen other libraries are also missing. Well.

Finally getting fsck.ext2 to run, it breezily tells me that "fsck: Is a directory while reading /. Superblock, etc ....."

but the associated device file, /dev/hda1 (as i see in fstab) works (and fsck runs, fixes some stuff, then runs cleanly). Ok, but booting leaves me high and dry. Each time it tries on boot to run fsck (which i've linked to fsck.ext2) and gives me the "is a directoy" message, and back to single user.

Oh. The other disk now has the same symptoms: fsck /u fails, fsck /dev/hdb1 succeeds. Is my problem that I grabbed the wrong fsck binaries? (fstab tells me that my filesystems are ext2).

So, what's going on with this?

Also, if I do have to re-install, can someone point me to directions to reinstalling from a hard disk ISO? cd-rom is broken ...

thanks!

---

### Post by lavinog on 2008-04-17
I think fsck will always say your file system is ext2 even if it ext3.

what was going on when the server crashed.
do you have a dual boot setup?
can you post your fstab?
and maybe dmesg?

---

### Post by awacs on 2008-05-02
> **lavinog said:**
> I think fsck will always say your file system is ext2 even if it ext3.

what was going on when the server crashed.
do you have a dual boot setup?
can you post your fstab?
and maybe dmesg?

Ok, I fixed it. I found (on another system) and loaded /sbin/fsck
(which, apparently, calls e2fsck, a/k/a fsck.ext2) which ran without complaint and let me boot.

But I still don't know why (even now, after reinstalling)
fsck.ext2 /u (or fsck.ext3 /u) fails with the above message,
while fsck /u succeeds. Can anyone hazard an opinion/guess?

---

