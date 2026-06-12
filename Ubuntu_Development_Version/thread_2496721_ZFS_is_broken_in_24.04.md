---
title: "ZFS is broken in 24.04"
date: 2024-04-09
forum: Ubuntu Development Version
---

### Post by ant-starikov on 2024-04-09
anything which involved copy_file_range syscall (which is a LOT of things) will fail if it is on ZFS.
[https://github.com/openzfs/zfs/issues/15930](https://github.com/openzfs/zfs/issues/15930)
[https://github.com/zabbly/zfs/commit/a4b9a58ef2f75c3597930da1b2ccbd0012920af4](https://github.com/zabbly/zfs/commit/a4b9a58ef2f75c3597930da1b2ccbd0012920af4)

particularly it will kill things like PHP. ruby and most of other scripting stuff.

example from strace of php:

```
copy_file_range(5, NULL, 6, NULL, 9223372036854775807, 0) = -1 EOPNOTSUPP (Operation not supported)
```

at least, this is what I see on 6.8.0-22-generic.

---

### Post by ant-starikov on 2024-04-09
Sorry, somehow duplicated threads and can't find how to  remove one.

---

### Post by deadflowr on 2024-04-09
I've removed your other duplicate thread.
Please use the report post button in the future if it happens again.
Or to simply report any other issues you come across.

---

### Post by ant-starikov on 2024-04-10
Anyway, I backported fix and pushed branch with proposed change. Rest is on maintainers of zfs-linux package.

---

### Post by ant-starikov on 2024-04-10
[COLOR=#000000][FONT=&quot]Anybody who wants fix right now can do
git clone -b linux_6.8_compat_splice_copy_file_range_fallback [https://git.launchpad.net/~antst/ubuntu/+source/zfs-linux](https://git.launchpad.net/~antst/ubuntu/+source/zfs-linux)
cd zfs-linux
dpkg-buildpackage -rfakeroot --no-sign -b[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]it will build all related packages, then install locally built zfs-dkms package as
apt install ./zfs-dkms_2.2.2-0ubuntu8_all.deb[/FONT][/COLOR]

---

### Post by MAFoElffen on 2024-04-10
But the fix was released in Ubuntu 5 days ago, right? 4/5/2024: [https://bugs.launchpad.net/ubuntu/+source/linux-apfs-rw/+bug/2054682](https://bugs.launchpad.net/ubuntu/+source/linux-apfs-rw/+bug/2054682)

---

### Post by Phoenixxl on 2024-04-22
Installed 24.04 ubuntu-server-minimal with ZFS boot & root using minimally adapted 22.04 instructions from OpenZFS.
This process failed before -31 but now works.

[https://github.com/openzfs/zfs/discussions/16120](https://github.com/openzfs/zfs/discussions/16120)

---

