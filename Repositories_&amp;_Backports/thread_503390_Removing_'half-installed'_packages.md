---
title: "Removing 'half-installed' packages"
date: 2007-07-17
forum: Repositories &amp; Backports
---

### Post by Surbeh on 2007-07-17
I need help getting rid of two 'half-installed' packages:
vmware-server-kernel-modules-2.6.20-16 and
vmware-tools-kernel-modules-2.6.20-16

When I try running dpkg --remove,  apt-install remove, or even dpkg --force-remove-reinstreq, I get the error message "Package is in a very bad inconsistent state - you should reinstall it before attempting a removal."  I also get an error when I try to reinstall (via apt-get install) the packages.

Thanks in advance.

---

### Post by smartboyathome on 2007-07-18
Try running synaptic and see what you get. also, I am sure this has come up before, try searching the forums. ;)

---

### Post by bapoumba on 2007-07-18
Could you please paste the complete output to:
```
sudo dpkg --force-remove-reinstreq --remove <package_name here>
```
for both of your packages?

---

