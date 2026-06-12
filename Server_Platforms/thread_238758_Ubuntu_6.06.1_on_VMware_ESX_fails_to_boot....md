---
title: "Ubuntu 6.06.1 on VMware ESX fails to boot..."
date: 2006-08-18
forum: Server Platforms
---

### Post by McCall on 2006-08-18
Hi Folks,

I have just finished an install of Ubuntu 6.06.1 Server under VMware ESX Server 2.5.2 and it fails to boot.  I used the complete virtual disk and default options for everything (other than networking) and upon reboot I am given the error:

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 18
```

I have done a quick Google on the problem, but can't find anyone else having this issue.  I tried a second install and got the same result.

Can anyon help out getting this corrected please?

Thanks,

Andrew McCall

---

### Post by FictionPimp on 2006-08-18
I can tell you that we have no issues here running on an ESX 3 server.

---

### Post by CasPat on 2006-08-23
Try making a boot partition, dont use default partitionning...

---

