---
title: "apparmor mount rule help"
date: 2012-12-09
forum: Security
---

### Post by Lfekey on 2012-12-09
I don't want firefox mount some sda partition.
I add "deny mount /dev/sda7" to /etc/apparmor.d/local/user.bin.firefox, but it doesn't work.
sda7 is a fat32 partition.

---

### Post by Laiquendi on 2012-12-09
1. Do you have your firefox profile enabled in apparmor?
2. Read here about editing apparmor profiles
```
http://ubuntuforums.org/showthread.php?t=1008906
```
Maybe you should just try denying the access?
then it would be
```
deny /whatever/the/place/is r,
```

---

### Post by Lfekey on 2012-12-09
Firefox profile is already enforced.
Dening the access is not a good choice, because you can mount a partition at any place.
I think mount rule is needed.

---

