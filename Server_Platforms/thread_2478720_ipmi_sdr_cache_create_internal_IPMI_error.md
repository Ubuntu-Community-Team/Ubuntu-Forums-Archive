---
title: "ipmi_sdr_cache_create: internal IPMI error"
date: 2022-09-03
forum: Server Platforms
---

### Post by cosy2 on 2022-09-03
```
sudo ipmi-sensors
Caching SDR repository information: /root/.freeipmi/....
ipmi_sdr_cache_create: internal IPMI error
```

```

sudo dmseg
ipmi-sensors:1178 map pfn expected mapping type uncached-minus for [mem 0x8dc16000-0x8dc17fff], got write-back
```

```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy

```

any suggestions?

---

### Post by ameinild on 2022-09-05
Maybe you should start by telling which hardware you're trying to run this on?

BTW, I'm using impitool and not ipmi-sensors, so I'm not familiar with that exact package. But you could troubleshoot with ipmitool, just for the sake of it.

---

### Post by cosy2 on 2022-09-05
> **ameinild said:**
> Maybe you should start by telling which hardware you're trying to run this on?
qemu VM

---

### Post by ameinild on 2022-09-06
I have zero knowledge about emulating an IPMI interface. I believe this is an extreme edge case...

---

### Post by cosy2 on 2022-09-06
> **ameinild said:**
> I have zero knowledge about emulating an IPMI interface. I believe this is an extreme edge case...

thx for the reply :)

maybe google will index this and later other will join

---

