---
title: "Logcheck for dummies..."
date: 2008-07-17
forum: Security
---

### Post by dalio on 2008-07-17
Hi folks,

I'm getting used to CLI Ubuntu as I'm running with it as a webserver.

I recently found out that I should be running Logcheck to make sure that my server wasn't under any attacks.

I've installed it and it's working and sending me emails, but I have a quick question:

Does anyone know of a good 'for dummies' guide to logcheck? I've read a few tutorials, which start off ok, but then seem to expect the user to have years of experience of Unix.

Also (and I should really split this into another question - mods please tell me if that's right?), I'm regularly getting lines in the logcheck emails that say:

```
Jul 17 16:18:46 mywebserver kernel: iptables denied: IN=eth0 OUT= MAC=*MAC address here* SRC=*IP address here* DST=*My server IP address here* LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=39861 DF PROTO=TCP SPT=56151 DPT=139 WINDOW=16384 RES=0x00 SYN URGP=0
```

Can anyone give me an insight into this?  I get this about 4 or 5 times an hour from different IP addresses.

Thanks in advance!

L

---

