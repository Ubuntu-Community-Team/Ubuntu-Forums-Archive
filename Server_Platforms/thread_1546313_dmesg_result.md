---
title: "dmesg result"
date: 2010-08-05
forum: Server Platforms
---

### Post by pravindra.kumar on 2010-08-05
Dear All,
I am facing some messages in LTSP server, I ran dmesg command and found some logs like following :-

[377478.978287] type=1503 audit(1281003237.960:173): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/gencache.tdb" pid=8520 profile="/usr/sbin/cupsd"
[377489.080994] type=1503 audit(1281003248.061:174): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=8520 profile="/usr/sbin/cupsd"
[377489.171302] type=1503 audit(1281003248.153:175): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=8520 profile="/usr/sbin/cupsd"
[377489.263133] type=1503 audit(1281003248.245:176): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/unexpected.tdb" pid=8520 profile="/usr/sbin/cupsd"
[377489.263340] type=1503 audit(1281003248.245:177): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/var/run/samba/gencache.tdb" pid=8520 profile="/usr/sbin/cupsd"

Can anyone help to understand and resolve the same.

Thanks

---

### Post by FuturePilot on 2010-08-05
Those messages are from Apparmor. Are you experiencing any particular problem that you think is related to those messages? We can't help you resolve anything if we don't know the problem.

---

