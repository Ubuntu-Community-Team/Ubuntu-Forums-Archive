---
title: "AppArmor profile fix for usr.lib.ipsec.stroke"
date: 2018-07-07
forum: Security
---

### Post by adosztal on 2018-07-07
I have strongSwan installed on Bionic, and issuing 'ipsec status' resulted in segfault. I [digged]("https://discuss.linuxcontainers.org/t/solved-ipsec-status-segfaults-in-lxd-container/2201/2") into the problem and in the end I found that AppArmor denies the mmap action for /usr/lib/ipsec/stroke:
```
Jul 7 04:53:32 lxd1 kernel: [ 4526.583617] audit: type=1400 audit(1530939212.389:68): apparmor="DENIED" operation="file_mmap" namespace="root//lxd-vpn1_<var-lib-lxd>" profile="/usr/lib/ipsec/stroke" name="/usr/lib/ipsec/stroke" pid=3372 comm="stroke" requested_mask="m" denied_mask="m" fsuid=100000 ouid=100000
```

After adding '[FONT=courier new]/usr/lib/ipsec/stroke rm[/FONT]' to /etc/apparmor.d/usr.lib.ipsec.stroke, it started working. You can find the whole profile [here]("https://pastebin.com/xam3TKX7").

---

