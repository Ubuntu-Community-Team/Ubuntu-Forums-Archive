---
title: "ERROR: ddf1: seeking device"
date: 2015-05-24
forum: Server Platforms
---

### Post by Iacpav on 2015-05-24
Hello, 

After checking the raid status on one of my servers today I found:

```
# dmraid -r
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
/dev/sdb: isw, "isw_bbiiddhjde", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sda: isw, "isw_bbiiddhjde", GROUP, ok, 1953525166 sectors, data@ 0
```

The server works fine, is this something to worry about ? if yes how to fix it?

Best Regards,
Pavel Iacovlev

---

