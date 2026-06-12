---
title: "Ubuntu 20.04 mnanage /  delete old zfs snapshots"
date: 2020-03-19
forum: Ubuntu Development Version
---

### Post by dbergst on 2020-03-19
In Ubuntu 20.04 is there a mechanism (e.g., via zsys) to manage old snapshots that are no longer needed?  I have observed that auto snapshots are taken whenever apt updates the system but have not seen what happens when there are too many stored snapshots, e.g,, low disk space.

---

### Post by dad+sithlord on 2020-12-29
zsys performs garbage collection after a period of time.  see [https://discourse.ubuntu.com/t/zfs-focus-on-ubuntu-20-04-lts-blog-posts/16355](https://discourse.ubuntu.com/t/zfs-focus-on-ubuntu-20-04-lts-blog-posts/16355) for discussion on zsys, plus links to a set of blogs that describe how it works.

---

### Post by coffeecat on 2020-12-29
Ancient thread and not the current development release. Please do not necromance dead threads.

Thread closed.

---

