---
title: "tracefs auto mount"
date: 2022-02-07
forum: Server Platforms
---

### Post by lacid2 on 2022-02-07
Does anyone know why is tracefs automatically mounted on 18.04, 20.04 Ubuntu servers?
```
% mount|grep tracefs
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)

```

snmpd doesn't like it, rather than disabling snmpd logs I'd like to know if it hurts unmounting it?
```
snmpd[3393]: Cannot statfs /sys/kernel/debug/tracing: Permission denied
```

---

