---
title: "xfs block size"
date: 2006-07-31
forum: Server Platforms
---

### Post by vb7prog on 2006-07-31
how would i go about checking the block size on my xfs partition?

also i mainly am manipulating files around 600 MB what is the ideal block size for such files?

Thanks in advance.

---

### Post by Akita on 2006-07-31
xfs_growfs -n /dev/your_drive

The "n" option tells it to do nothing other than show geometry.

Ubuntu/Debian default is 4096 IIRC and that should be a very good compromise. Unless you're working with bunch of tiny files, this will be faster and less prone to fragmentation. Anything bigger and you risk slowing down nfs/smb unless you tweak their sizes... again IIRC. Anyone who's read up on this stuff recently or does file systems for a living may feel free to correct the error of my ways :-)

---

