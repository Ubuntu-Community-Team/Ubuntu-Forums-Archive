---
title: "Server install on mbt partition"
date: 2023-02-21
forum: Server Platforms
---

### Post by hungarycraft on 2023-02-21
Hi, would it be possible to instal ubuntu server on an older computer that can only read mbt partitions? I ask this as when I tried to do this yesterday, I noticed that in the server installer the only option to customize partitions could only configure gpt partitions and not mbt. Thus I could not use this older machine in order to run my jellyfin server.
thanks,
Kristóf

---

### Post by darkod on 2023-02-21
Yes, you should be able to install on msdos/mbr disks. Haven't used the latest installer so I don't know how that step looks. Is this 22.04 you are trying to use?

Also I always prepare partitions in advance. Yse the Desktop live usb/cd and boot into live mode. Then in terminal use parted to create partition table type that you want, and the partition sizes.

Then during the server install you will just tell it to use existing partitions. At least with the installers of few years back that was easy to do.

---

### Post by hungarycraft on 2023-02-22
Ok, tysm. I will try this as soon as possible.

---

