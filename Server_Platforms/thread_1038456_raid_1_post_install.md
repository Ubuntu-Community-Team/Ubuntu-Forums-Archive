---
title: "raid 1 post install"
date: 2009-01-12
forum: Server Platforms
---

### Post by Sylphid on 2009-01-12
Im trying to convert my single disk install to a 2disk raid 1 setup. I followed instructions here [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch) however when i try to reboot into the raid volume it fails to an initramfs prompt and also fails when trying to boot to the original volume with the same kernel ... I believe that the update-initramfs -u command screwed it up but im not sure how to repair this.

Any advice?
Sylphid

---

### Post by Sylphid on 2009-01-13
ok solved this ... was related to a initramfs-tools bug here

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177)

---

