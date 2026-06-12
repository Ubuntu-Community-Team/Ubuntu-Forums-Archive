---
title: "ureadahead always segfaults at boot"
date: 2013-02-05
forum: Server Platforms
---

### Post by mc0001 on 2013-02-05
Hi,
We have a server running 12.10 and ureadahead always segfaults at boot time, e.g. output from dmesg:

[   56.218951] ureadahead[462]: segfault at 7fe07e909350 ip 00007fe07e746bf9 sp 00007ffffa889b00 error 6 in ureadahead[7fe07e741000+a000]
[   62.169315] init: ureadahead main process (462) killed by SEGV signal

Can anyone shed any light on the cause of this, and its seriousness? The machine proceeds to boot up, but its h/w RAID6 write performance is very flakey, and we're wondering if this could at all be related.

---

