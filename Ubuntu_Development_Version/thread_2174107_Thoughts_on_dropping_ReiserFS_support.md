---
title: "Thoughts on dropping ReiserFS support"
date: 2013-09-12
forum: Ubuntu Development Version
---

### Post by cariboo on 2013-09-12
Colin Watson posted this to the ubuntu-devel mailing list:

> Debian has removed reiserfs support from its kernel packages and its
installer ([http://bugs.debian.org/717517](http://bugs.debian.org/717517)).  I don't really want to keep
maintaining it without Debian; for instance it would mean adding support
for [http://bugs.debian.org/696123](http://bugs.debian.org/696123) as an Ubuntu-specific patch once we
have the underpinnings done.  Does anyone feel desperately that we have
to keep this or shall I just go ahead and drop it?

Thanks,

-- Colin Watson 

Any thoughts on this?

---

### Post by VMC on 2013-09-12
I've never used it. I studied the various fs's for comparisons, but in the end I stuck with ext4.

---

### Post by davetv on 2013-09-12
ReiserFS was conceived as a replacement for ext2. It was faster in some circumstances but had issues with corruption.

Time has moved on. It was good in its time but now irrelevant.

---

### Post by kostkon on 2013-09-12
It was a good FS (OK, it is) but it doesn't have a future, company has folded, its creator is in prison for life, so better drop it and forget about it; it's about time :|

---

### Post by lonniehenry-gmail on 2013-09-13
Gave it a try on a test machine, but had problems with it.  Have no reason to keep using it.  My opinion is to drop it as there is no support for it.

---

### Post by tgalati4 on 2013-09-13
I used it for a while and it did fold up on itself once.  It was faster than ext2.  Not sure if it is faster than ext4.  Data recovery tools have a harder time with it.  The files are still there, but it is more difficult to rebuild the tree.  Without a maintainer or improvements, it's a dead-end file system.

I have no problem with dropping it.  

If you are running a production server with ReiserFS, then now is the time to migrate.

---

### Post by ZoiaGuyver on 2013-09-13
With the advent of BTRFS and it improving all the time, the speed at which even EXT4 is still running, ZFS, XFS plus the myriad of others, personally I don't see the point in "beating a dead donkey" as it were. If reiserFS was still in development maybe there could be an argument for it. 

I'm all for removing it as an option as to be fair we have very capable and more impressive filesystems to choose from. Plus if debian no longer is maintaining, it that for me settles it.

---

### Post by QDR06VV9 on 2013-09-13
> **davetv said:**
> ReiserFS was conceived as a replacement for ext2. It was faster in some circumstances but had issues with corruption.

Time has moved on. It was good in its time but now irrelevant.
i Agree also, EXT4 & BTRFS are ok. (just my 2 cents)

---

### Post by ibjsb4 on 2013-09-13
I have never deviated from the EXT* FS, but if I did,  BTRFS would be my choice and ReiserFS would of never been considered. RIP

---

### Post by Yellow Pasque on 2013-09-14
It doesn't seem any different than dropping OSS audio or support for non-PAE CPU's. Ubuntu used to be a distro more accommodating to older machines and backwards compatibility. For better or worse, it's no longer that distro...

---

### Post by kostkon on 2013-09-14
> **Temüjin said:**
> It doesn't seem any different than dropping OSS audio or support for non-PAE CPU's. Ubuntu used to be a distro more accommodating to older machines and backwards compatibility. For better or worse, it's no longer that distro...
OSS is not about older hardware, but old deprecated unmaintained audio software; and PAE about a small percentage of a small percentage of Pentium M CPUs (even Pentium 2 is PAE capable for example).

ReiserFS is unmaintained (as a software, not only as a debian package) and and that isn't going to change, only maybe if Reiser is acquitted of his murder charges...

---

### Post by Yellow Pasque on 2013-09-15
^I didn't mean to imply that those were "bad" decisions. I'm just saying that there are better distros out there for folks who need stuff like non-PAE support or still have some disks with reiserfs partition.

---

