---
title: "Steam; Wine and Windows 7 Conflict"
date: 2010-11-17
forum: Wine
---

### Post by samham on 2010-11-17
Hi all,

I recently added a second RAID 0 array to my main rig to install Ubuntu 10.10 on. After install and setting up as normal I decided to install steam through wine which worked fine. But when I booted back into Windows 7 I got an error when I tried to run steam:

"Steam.exe (main exception): The registry is in use by another process, timeout expired"

[https://support.steampowered.com/kb_article.php?ref=2275-UFHC-2473](https://support.steampowered.com/kb_article.php?ref=2275-UFHC-2473)

^^ Link to steam knowledge base error

It seems wine on the other RAID array was causing this issue. After uninstalling steam on Ubuntu the error stopped.

Anyone had any experience of this issue?

Thanks,
Sam

---

### Post by lightstream on 2010-11-21
can you clarify - did you make a new install of steam on ubuntu, or just run the existing installation on your windows drive?

---

### Post by samham on 2010-11-23
> **lightstream said:**
> can you clarify - did you make a new install of steam on ubuntu, or just run the existing installation on your windows drive?

I made a new install of steam on Ubuntu and also kept the install of on Windows 7. So two installs on different Hard disks.

Thanks

---

