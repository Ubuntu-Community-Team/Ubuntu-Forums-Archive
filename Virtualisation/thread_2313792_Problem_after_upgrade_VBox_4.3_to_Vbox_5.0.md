---
title: "Problem after upgrade VBox 4.3 to Vbox 5.0"
date: 2016-02-15
forum: Virtualisation
---

### Post by satimis on 2016-02-15
Hi all,

Host Ubuntu 14.04 running on SSD
VMs /Ubuntu 14.04/W80/etc on HD

HD	/media/satimis/xxxx/VirtualBox VMs

After upgrade on repo and restart VBox Manager all VMs disappear

-> Preference -> General
Default Machine Folder /media/satimis/xxxx/VirtualBox VMs

All VMs are there

Please help rather than importing them one by one.

Thanks in advance.

Regards
satimis

---

### Post by potato5 on 2016-02-20
GUI reads ~/.VirtualBox/VirtualBox.xml
Try to recover the file or repair it (adding VM)

---

### Post by satimis on 2016-02-20
> **potato5 said:**
> GUI reads ~/.VirtualBox/VirtualBox.xml
Try to recover the file or repair it (adding VM)
Hi,

Tks for your advice.

Problem already fixed.  For unknown cause the permission of /media/satimis changed to root:root

Ran sudo chown satimis:satimis /media/satimis

Now all VMs come back

Regards
satimis

---

