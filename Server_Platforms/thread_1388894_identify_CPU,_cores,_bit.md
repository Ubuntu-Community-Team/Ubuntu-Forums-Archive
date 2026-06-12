---
title: "identify CPU, cores, bit"
date: 2010-01-23
forum: Server Platforms
---

### Post by boondocks on 2010-01-23
I need to upgrade a system remotely.
I only have ssh (remote) access to this Ubuntu system.

How do you identify the following via CLI:
[LIST]
[*]Which CPU it has?
[*]How many cores?
[*]Is it a 32-bit or 64-bit?
[/LIST]

I know that dmesg will provide various details.
I would like to issue a command or two to obtain this information in a consistent manner on any Ubuntu system.

---

### Post by Queue29 on 2010-01-23
```
cat /proc/cpuinfo
```

will get you all the info about the cpu

---

### Post by boondocks on 2010-01-23
Thank you.

---

### Post by tgalati4 on 2010-01-24
cat /etc/issue
uname -a
lsb_release -a
sudo apt-get install hwinfo
hwinfo

---

