---
title: "ZFS enhancements documentation (16.04 to 18.04)?"
date: 2019-06-06
forum: Server Platforms
---

### Post by kpatz on 2019-06-06
Having recently upgraded my ZFS based file server from 16.04 to 18.04, I was wondering if the changes and enhancements to ZFS between these two releases are documented somewhere.

I could google, read and compare man pages, get versions and find BSD documentation, and spend hours trying to figure this out, or maybe there's a summary posted somewhere.

Just yesterday, I discovered, quite by accident, that 18.04 no longer requires root/sudo to run non-destructive zfs commands (like **zfs list** or **zfs get**).  It seems that **zfs allow **works to allow granting permissions to non-root users to manipulate datasets and snapshots without requiring root as well, within limitations (such as the Linux limitation where only root can mount/unmount).

I've also run into some changes in **zfs send** that breaks my backup scripts... I'm working on ways around this, but recursive sends don't work in some cases where they used to.  I may post another thread on this down the road.

---

