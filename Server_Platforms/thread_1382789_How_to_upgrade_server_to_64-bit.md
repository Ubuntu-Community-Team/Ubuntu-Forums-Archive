---
title: "How to upgrade server to 64-bit"
date: 2010-01-16
forum: Server Platforms
---

### Post by R.Bucky on 2010-01-16
I have a production mdadm RAID1 v.8.04 Ubuntu Server and would like to upgrade to a PAE enabled kernel of 8.04 Server. I have 4GB RAM and would like to extend to 6GB RAM in the near future. I remember reading about a simple method of upgrading the kernel, but cannot find much info on the net. Has anyone upgraded and what performance gains were found with the PAE enabled system? Also, can anyone recommend a blog post or page with more information?

---

### Post by HighCommander540 on 2010-01-16
> **R.Bucky said:**
> I have a production mdadm RAID1 v.8.04 Ubuntu Server and would like to upgrade to a PAE enabled kernel of 8.04 Server. I have 4GB RAM and would like to extend to 6GB RAM in the near future. I remember reading about a simple method of upgrading the kernel, but cannot find much info on the net. Has anyone upgraded and what performance gains were found with the PAE enabled system? Also, can anyone recommend a blog post or page with more information?

There isn't a simple way to upgrade the kernel. You have to just install with the 64-bit ISO. What you can do is just install over the previous partition, but you need to back-up critical data first. There isn't a simple or easy way to do it while the system is running.

---

### Post by Cheesemill on 2010-01-16
You can't upgrade 32-bit to 64-bit, you have to do a clean install.

Are you talking about installing the 32-bit PAE kernel to use more than 4GB of RAM? If so then you already have it. The server kernel is already PAE enabled.

---

### Post by BkkBonanza on 2010-01-17
You can compile a 64-bit kernel on your system but the compile tools have to be rebuilt first for 64 bit outputs. Then you would have to mod your boot config to boot on the 64 bit kernel.

While all this is doable I think posts above have the better answer. Just re-installing will be a lot less hair pulling and give you a more robust result.

---

