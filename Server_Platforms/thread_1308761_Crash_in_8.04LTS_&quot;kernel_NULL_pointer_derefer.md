---
title: "Crash in 8.04LTS &quot;kernel NULL pointer dereference&quot;"
date: 2009-10-31
forum: Server Platforms
---

### Post by smagister on 2009-10-31
Hi,

I'm running 8.04 LTS 2.6.24-16-server kernel on a Dell Core 2 Duo tower with 3GB of RAM.

I was running rsync and the machine froze. After restarting I found this in /var/log/kern.log


Oct 31 02:38:33 hostname kernel: [617414.584615] Unable to handle kernel NULL pointer dereference at 0000000000000070 RIP:


I'm running a software RAID 5 cluster across 3 disks using mdadm and the os is on a separate 4th disk.

Is there any other possibility that this is not a hardware/memory issue?

Thanks,

Sam

---

