---
title: "Ubuntu 8.10 server crash"
date: 2009-12-27
forum: Server Platforms
---

### Post by mewt on 2009-12-27
Hi, 

My server has suddenly stopped responding to web requests. I checked  var/log/messages and these were the only lines that appeared:

Dec 27 14:53:35 mcgvoice kernel: [2168473.423135] apache2[8841]: segfault at 7f3160d8 ip b68e94e0 sp bf98b060 error 6 in libstdc++.so.6.0.10[b6882000+e3000]
Dec 27 14:54:12 mcgvoice kernel: [2168510.353649] apt-get[8845]: segfault at 7f499538 ip b7ed74e0 sp bfa4ca90 error 6 in libstdc++.so.6.0.10[b7e70000+e3000]
Dec 27 14:54:54 mcgvoice kernel: [2168552.278067] apache2[8928]: segfault at 7f041df8 ip b697f4e0 sp bf820ef0 error 6 in libstdc++.so.6.0.10[b6918000+e3000]
Dec 27 14:55:45 mcgvoice kernel: [2168603.444645] python[8935]: segfault at 7f5b64f8 ip b7cb54e0 sp bfadb270 error 6 in libstdc++.so.6.0.10[b7c4e000+e3000]
Dec 27 14:55:51 mcgvoice kernel: [2168609.799583] python[8937]: segfault at 7f8947d8 ip b7c244e0 sp bfc4a3e0 error 6 in libstdc++.so.6.0.10[b7bbd000+e3000]


Any ideas why ? On reboot, everything seems to be back to normal..

---

### Post by mewt on 2009-12-27
bump ?

---

### Post by Vegan on 2009-12-27
Could be any of 1 million things. If the system does not work right reboot, if that fails start checking hardware then software.

---

### Post by mewt on 2009-12-27
rebooted and it seems to be working..id like to avoid it happening again...

---

