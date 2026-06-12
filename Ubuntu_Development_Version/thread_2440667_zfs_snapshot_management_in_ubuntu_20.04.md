---
title: "zfs snapshot management in ubuntu 20.04"
date: 2020-04-13
forum: Ubuntu Development Version
---

### Post by odror on 2020-04-13
As of 20.04 I switched to zfs and started using lxd instead of lxc. In my lxd setup I am using zfs. I am new to zfs and to lxd. In ubuntu 20.04 there is a zsys package and zfs-auto-snapshot, which is not installed by default.

[LIST]
[*]Is zsys a replacement for zfs-auto-snapshot
[*]how do I set parameters for zsys (i.e. how many or how long snapshots are kept)
[*]If zsys is not managing snapshots for lxd then what is.
[*]Can zfs-auto-snapshot and zsys run simultaneously. Can they manage the same snapshots or each create their own snapshots.
[*]Is there any other way to automatically manage system (rpool) and lxd snapshots
[*]can zfs-auto-snapshot be used to manage only lxd snapshots (if it is not managed by zsys)
[/LIST]

---

