---
title: "Help: server crushed...."
date: 2009-05-06
forum: Server Platforms
---

### Post by amai on 2009-05-06
Sever on Ubuntu 8.04 crushed here is the error I am getting how do i fix this... Tried googling but no luck so far....

[B][I]fsck.ext3: No such file or directory while trying to open /dev/sbd7/dev/sdb7
The superblock could not be read or does not describe a correct ext2 filesystem, if device is valid an it really contains an ext2 filesytem(and not swap or ufs or something else), then the suoerblock is corrupt, and you might try e2fsck with an alternate superblock
    e2fsck -b 8193 <device>
fsck died with exit status 8
  .... fail ![/I][/B]

---

