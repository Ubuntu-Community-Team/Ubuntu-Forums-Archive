---
title: "another one is retired"
date: 2013-03-17
forum: Server Platforms
---

### Post by Vegan on 2013-03-17
I have finally retired an old hard disk after over 30,000 power on hours, the ST3200822AS is from the 7200.7 series and while it ran hot and it did eventually start showing some bad sectors, the disk never died outright. All failed sectors were recovered and no files were ever lost, disk was used for backups so it's expendable.

The WD3200BEVT has taken its place. I bought a bunch of plastic notebook disk adapters.

What is the maximum file system for ext4?

---

### Post by Cheesemill on 2013-03-18
Maximum theoretical filesystem size for ext4 is 1EB, however, the e2fsprogs package which contains the mkfs.ext4 program has only recently lifted it's 16TB limit on partition creation size.

So your ext4 limit is 16TB on pre 12.04 systems, 1EB on anything later.

---

