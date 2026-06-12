---
title: "Installing Highpoint 2310 Raid"
date: 2006-11-03
forum: Server Platforms
---

### Post by moulin on 2006-11-03
Hello,

We decided to use the Highpoint 2310 pci-express raid card for our server. Since the kernel has no native support I need to install the linux driver the producer supplies. Becaue I want to boot from the raid disk I need to install a kernel patch. The manual for doing this is quite clear:

```
make patchkernel KERNELDIR=<kernel-source-dir> KERNEL_VER=2.6
```

But I keep having trouble with the installation. I installed all kind of headers and source code. At the moment I use the *2.6.15-27-amd64-server* kernel. Who can give me any advice or who tried to install this raid card?  Any help is welcome. 

Kind regards,

Marco

---

