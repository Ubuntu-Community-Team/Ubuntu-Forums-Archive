---
title: "Reparar GRUB"
date: 2012-09-23
forum: Uruguay Team
---

### Post by danielmato on 2012-09-23
Desde un live cd.

sudo mkdir linux
sudo mount /dev/sdXY linux/
sudo mount -t proc /proc linux/proc
sudo mount --bind /dev linux/dev
sudo chroot linux/ 

grub-install /dev/sda


el grub está aca

sudo gedit /etc/default/grub

---

