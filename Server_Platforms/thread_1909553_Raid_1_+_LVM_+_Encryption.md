---
title: "Raid 1 + LVM + Encryption"
date: 2012-01-15
forum: Server Platforms
---

### Post by harveyd on 2012-01-15
Hi All,

I have my OS installed on a single drive that is unencrypted.

I then have 2 Drives that has been set up as Raid 1. I have then placed an LVM partition on the Raided drives and placed a filesystem. All mounts just fine.

From this I want to encrypt the entire file system on the raid.

I expect that when restarted the OS will boot just fine and I will have to ssh in to the server to manually mount the encrypted raid drives before I can access data on it. That is fine

Does anyone have any suggestions on the best way to achieve this.

Harv

---

