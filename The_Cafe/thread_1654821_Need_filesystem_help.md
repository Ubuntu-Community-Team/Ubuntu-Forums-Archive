---
title: "Need filesystem help"
date: 2010-12-28
forum: The Cafe
---

### Post by sandyd on 2010-12-28
Im currently looking for a filesystem to store large files (only storage). Doesn't need to be windows compatiable.

I was looking at btrfs, but im not so sure seeing that its still beta, and doesnt have fsck support (yet), and if the HD crashes, there might be issues with data recovery.

Maybe XFS?

---

### Post by GabrielYYZ on 2010-12-28
define "large" 

i have a HD for storage and i have it with EXT4, but "large" files for me have been, so far, 1-4gb. are your files larger than that?

ps: EXT4 works fine for me too, no problems so far. but, again, the "large files" you're talking about might be larger than mine.

---

### Post by sandyd on 2010-12-28
> **GabrielYYZ said:**
> define "large" 

i have a HD for storage and i have it with EXT4, but "large" files for me have been, so far, 1-4gb. are your files larger than that?

ps: EXT4 works fine for me too, no problems so far. but, again, the "large files" you're talking about might be larger than mine.
32GB files.

---

### Post by GabrielYYZ on 2010-12-29
in that case, XFS seems like the sensible choice, yeah. 

as you yourself noted, btrfs can not be fully trusted yet.

---

### Post by suprman2020 on 2010-12-29
What is ext4's file size limit?

---

### Post by GabrielYYZ on 2010-12-29
> **suprman2020 said:**
> What is ext4's file size limit?

according to Dr. Wik. E. Pedia:

[QUOTE=Wikipedia]Max file size 16 [TiB]("http://en.wikipedia.org/wiki/Tebibyte") (for 4k block filesystem)[/QUOTE]

but i guess he/she doesn't want to take his/her chances with ext4. i say chances 'cause i've read about corruption problems with ext4, even though it has worked great for me, mileage may vary.

---

### Post by mips on 2010-12-29
Xfs

---

### Post by NightwishFan on 2010-12-29
If it helps any, google uses Ext4 for storage. I advise it merely for the fast filesystem check. :)

---

### Post by sandyd on 2010-12-29
hmm. xfs it is.

---

### Post by sandyd on 2010-12-29
hmm.
xfs it is.
btrfs whenever it matures.

---

