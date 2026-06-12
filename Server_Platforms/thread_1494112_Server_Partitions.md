---
title: "Server Partitions"
date: 2010-05-26
forum: Server Platforms
---

### Post by JimmieC on 2010-05-26
I'm attempting to set up a Linux home file server. I have four desktops and two laptops. One Windows system and the rest Ubuntu/Windows dual-boot systems.

I have an older computer I plan to use for the file server. My question is about the partitioning scheme for the file server. I have one 160GB hard drive. What partitions do I need for a home file server and do I need the data partition to be NTFS for compatibility. For my Ubuntu non-server systems I use a \ partition, a home partition, and a swap partition, will this scheme work for a server system?

Also, is the use of Ubuntu 10.4 Server overkill for my needs or can I install it and use only the features I need? 

Thanks for the help.

Jim

---

### Post by Iowan on 2010-05-26
Sounds like an interesting project - I'd do it just for the experience. You should be able to install only the features you need - and add others only when/if you need. A Samba server *should* be able to provide shares for the Windows machines. I have a server admin book that suggests:
/boot 100M (50M)
/ 20GB (5 GB)
/var 5 GB (1 GB)
/tmp 1 GB  (1 GB)
/srv 50GB (1 GB)
/home 50 GB (1 GB)

---

### Post by JimmieC on 2010-05-27
Iowan,

Thanks for the response. The experience, yes, that's the main reason. Seems like there's always more to know, I think it's a disease. I gather from your suggested partitions I don't need a NTFS partition, that Samba will write a Windows file to a Linux server. Is that right?

Jim

---

### Post by volkswagner on 2010-05-27
> **JimmieC said:**
> Iowan,

Thanks for the response. The experience, yes, that's the main reason. Seems like there's always more to know, I think it's a disease. I gather from your suggested partitions I don't need a NTFS partition, that Samba will write a Windows file to a Linux server. Is that right?

Jim

Correct.  Samba does the work, windows machines machines don't "see" the file system on disk.  Most all consumer NAS boxes run a small linux distro and operate the same way with SAMBA and an ext2 partition to share.

---

