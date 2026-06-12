---
title: "ext3 format hangs"
date: 2007-04-25
forum: Server Platforms
---

### Post by 5hundy on 2007-04-25
I'm installing Feisty 64-bit server on a few new boxes and i found that whenever I try to create an ext3 partition, the progress bar immediately jumps to 33% and then just hangs. I let it run for like 30 min a few times but it never made any progress. I should note these are two 250g sata drives on raid1 via an LSI card.

Anyway, I got around this by creating the partition as ext2 and then later converting it to ext3 with:

```
tune2fs -j /dev/sda1
```

of course I also set the /etc/fstab to use ext3. So far everything seems fine. Anyone seen anything similar?

---

