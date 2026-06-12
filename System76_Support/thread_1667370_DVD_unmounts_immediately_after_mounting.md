---
title: "DVD unmounts immediately after mounting"
date: 2011-01-14
forum: System76 Support
---

### Post by mosestruong on 2011-01-14
I've noticed that on the starling with 10.04LTS, I find that my DVD drive unmounts immediately after mounting. 

dmesg has a lot of the following error:
```
[ 6090.026255] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6090.026281] sr 2:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 6090.026309] Info fld=0x0
[ 6090.026321] sr 2:0:0:0: [sr0] Add. Sense: Logical block address out of range
[ 6090.026348] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[ 6090.026402] end_request: I/O error, dev sr0, sector 0

```

Does anyone know how to fix this? Thanks

---

