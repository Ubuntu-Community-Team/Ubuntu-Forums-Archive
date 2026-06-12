---
title: "Samba server set up"
date: 2011-08-31
forum: Server Platforms
---

### Post by Ed_Ziffel on 2011-08-31
Never used samba before. Have large raid partitions on Ubuntu server that would be nice to get formated right the first time.  Need to network with win machines and other linux boxes.  What file system should the raid partitions be formated with?

Thanks

---

### Post by JDorfler on 2011-08-31
I use EXT4 on my Samba Shares.  No issues.

---

### Post by PierreRobiquet on 2011-08-31
It doesn't matter to Samba what file system the shares are based on as long as the kernel has support for them. As far as I know anything the kernel supports, Samba will support.

---

### Post by Ed_Ziffel on 2011-08-31
Thanks.  Hate the wait for the reformat thing.  Will use ext4.

---

