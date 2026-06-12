---
title: "tracefs remounted every night at 2am?"
date: 2016-10-18
forum: Server Platforms
---

### Post by smurphy2 on 2016-10-18
Hi all,

trying to figure out why tracefs is being remounted every night.
Reason I disable debugfs is that this is a firewall, and I don't need it there. Only the snmpd always tries to access it, and this fill my syslog with:

```

[FONT=monospace][COLOR=#000000]Oct 18 08:17:20 sol-gate snmpd[1211]: Cannot statfs /sys/kernel/debug/tracing: Permission denied[/COLOR]
Oct 18 08:18:21 sol-gate snmpd[1211]: Cannot statfs /sys/kernel/debug/tracing: Permission denied
Oct 18 08:19:21 sol-gate snmpd[1211]: Cannot statfs /sys/kernel/debug/tracing: Permission denied
Oct 18 08:20:21 sol-gate snmpd[1211]: Cannot statfs /sys/kernel/debug/tracing: Permission denied
[/FONT]
```

Note - the firewall runs ubuntu Server 16.04.1 LTS, uses efi-signed kernels to boot.
Why is it mounted? or more spefically, what is mounting it?

When manually unmounting the tracefs directory, it stops:  [FONT=monospace][COLOR=#000000]umount tracefs[/COLOR]
[/FONT][FONT=monospace]
Any hints?
Thx.[/FONT]

---

