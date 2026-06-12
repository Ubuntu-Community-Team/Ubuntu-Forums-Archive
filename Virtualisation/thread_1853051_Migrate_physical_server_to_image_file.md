---
title: "Migrate physical server to image file"
date: 2011-10-01
forum: Virtualisation
---

### Post by kronicle on 2011-10-01
i have an ubuntu server configured as a LAMP server. i will like to migrate the server to an image file as in (.iso file) or any other image file that can be burned to a bootable disk so that when the image is burned and installed i will have my server back with all installed packages and settings. is this possiblw

---

### Post by CharlesA on 2011-10-01
Are you going to migrate it to a VM? If so why not just use something like clonezilla to image the box and restore it onto the VM?

---

### Post by dcstar on 2011-10-02
> **kronicle said:**
> i have an ubuntu server configured as a LAMP server. i will like to migrate the server to an image file as in (.iso file) or any other image file that can be burned to a bootable disk so that when the image is burned and installed i will have my server back with all installed packages and settings. is this possiblw

VMware have free tools to convert real systems to their VMs - but not "bootable" disks as that is basically impossible.

---

### Post by haqking on 2011-10-02
> **kronicle said:**
> i have an ubuntu server configured as a LAMP server. i will like to migrate the server to an image file as in (.iso file) or any other image file that can be burned to a bootable disk so that when the image is burned and installed i will have my server back with all installed packages and settings. is this possiblw

Remastersys or Clonezilla

---

