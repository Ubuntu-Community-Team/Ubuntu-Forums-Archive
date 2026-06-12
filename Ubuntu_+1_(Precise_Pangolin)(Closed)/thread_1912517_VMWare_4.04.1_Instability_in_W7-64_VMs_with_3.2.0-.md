---
title: "VMWare 4.0/4.1: Instability in W7-64 VMs with 3.2.0-10"
date: 2012-01-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-20
I have just noticed that W7 64-bit VMs get constant Blue Screen errors (page fault in nonpaged area, etc) when using kernel 3.2.0-10. I have tested with 5 VMs. They work flawlessly with the previous kernel release. I have tried rebuilding the kernel module, but obtained the same results. We probably need some update to VMWare kernel module.

Regards,
Effenberg

---

### Post by fjgaude on 2012-01-20
As you might remember I only use 32-bit WinXP VMs... they still work fine with kernel 3.2.0-10.

---

### Post by effenberg0x0 on 2012-01-20
> **fjgaude said:**
> As you might remember I only use 32-bit WinXP VMs... they still work fine with kernel 3.2.0-10.

I remember. It's weird: I can make a single W7-64 VM go past login screen on 3.2.0-10 and all of them work perfectly in 3.2.0-9. I don't have W7-32 VMs though, I better install and test it.

---

### Post by xyzzyman on 2012-01-22
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-10.17](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-10.17)

The only thing from the changelog that might cause this is 

[Config] Enable CONFIG_IRQ_REMAP

Which enabled this: [http://cateee.net/lkddb/web-lkddb/IRQ_REMAP.html](http://cateee.net/lkddb/web-lkddb/IRQ_REMAP.html)

---

### Post by effenberg0x0 on 2012-01-22
> **xyzzyman said:**
> [https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-10.17](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-10.17)

The only thing from the changelog that might cause this is 

[Config] Enable CONFIG_IRQ_REMAP

Which enabled this: [http://cateee.net/lkddb/web-lkddb/IRQ_REMAP.html](http://cateee.net/lkddb/web-lkddb/IRQ_REMAP.html)

Hey xyzzyman, 

You are absolutely right. And, shamefully, I forgot to update this thread a couple days ago with what I was trying to do with it. With this change you pointed out, it seems like Windows VMs were affected because they refer to hardware that was not presented to them in the same conditions any more. Discussing with other people that use Linux/VMware/W7-64 VMs, it came down to the need to fix the Windows installs, to match the change in the virtual hardware presented to VMs as a results of the change you mentioned.

I was doubting it at first. In my head VMWare would still present the same virtualized hardware environment to the VMs. But after running W7 "Repair" mode, we see change in it's Control Panel/System/Device Manager/Details regarding IRQs and the VMs got stable again, one by one, proving I was wrong.

Regards,
Effenberg

---

