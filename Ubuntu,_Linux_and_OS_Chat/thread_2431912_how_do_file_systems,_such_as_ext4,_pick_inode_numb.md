---
title: "how do file systems, such as ext4, pick inode numbers"
date: 2019-11-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-11-23
i was looking at some of the inode numbers some new files got.  a group got some sequential numbers, then there was a big gap, then some more sequential numbers, then a big jump to way lower numbers around 3000, a couple non-sequential near there, then a jump up high again.  i ran a recursive scan of everything and got all numbers.  the first inode of the first gap has not been used anywhere.  obviously inodes that have been used cannot be picked.  but i am curious how it goes about doing that.  a these new files were in the same directory.  in this case it is ext4, but i have seen this kind of things on others, like the old reiserfs and the new btrfs.  i've even seen this happen on freshly formatted file systems, though the sequential runs are longer.  **does anyone know anything about the logic used to pick the numbers?**

---

### Post by TheFu on 2019-11-24
Use the source, Luke.
I'd start in the mkfs.ext4 code and work out to the _open() call.

---

### Post by Skaperen on 2019-11-24
> **TheFu said:**
> Use the source, Luke.
I'd start in the mkfs.ext4 code and work out to the _open() call.

i'm looking more for a general summary, not trying to learn how just one file system is implemented.

---

