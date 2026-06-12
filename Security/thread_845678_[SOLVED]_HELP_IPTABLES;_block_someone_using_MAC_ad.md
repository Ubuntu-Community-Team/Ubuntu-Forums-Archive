---
title: "[SOLVED] HELP: IPTABLES; block someone using MAC address"
date: 2008-06-30
forum: Security
---

### Post by cjtjamandra on 2008-06-30
How can i block someone using his computer name? or is it possible to block using MAC address? i want to do this because if i use IP only or computer name only, he can change his ip address or computer name so he will not be blocked. and by the way is there any way to know someone's MAC address?

---

### Post by cjtjamandra on 2008-06-30
I have managed to solve it... :)

```
iptables -A INPUT -m mac --mac-source 00:0F:EA:91:04:08 -j DROP
```

---

