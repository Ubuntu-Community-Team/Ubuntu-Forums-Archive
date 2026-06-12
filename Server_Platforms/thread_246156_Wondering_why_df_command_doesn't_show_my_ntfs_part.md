---
title: "Wondering why df command doesn't show my ntfs partition."
date: 2006-08-28
forum: Server Platforms
---

### Post by otherd on 2006-08-28
I've got a NTFS partition mounted on my HP/Compaq 523 RAID card as /dev/cciss/c0d1.

Appears to be mounted fine, can see it as as samba share and can do a ls of what's on it's mount point. 

But when I run a df command, I don't see that volume. I can see the  ext3 partition on the same controller as well as the rest of the mounts on the server. Was just getting curious as to my free space on it and that's when I ran across this. I can do a du and get results, but nothing with df. 

I could live with that if there's another way to check the free space on the drive. :)

---

