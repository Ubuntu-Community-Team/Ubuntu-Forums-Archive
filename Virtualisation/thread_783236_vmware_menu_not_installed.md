---
title: "vmware menu not installed"
date: 2008-05-05
forum: Virtualisation
---

### Post by dbrine on 2008-05-05
I followed the directions to the number installing vmware server on 8.04 and the menu in not in the apps menu.? I tried running vmware from the console and received the following erros

[HTML](firefox:24297): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

root@ULaptop:/media/ext-160/vmware-any-any-update116# apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ULaptop:/media/ext-160/vmware-any-any-update116#  ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
root@ULaptop:/media/ext-160/vmware-any-any-update116#  ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
root@ULaptop:/media/ext-160/vmware-any-any-update116# vmware
Launching VMware Web Access using /usr/bin/xdg-open
root@ULaptop:/media/ext-160/vmware-any-any-update116# 
(firefox:25710): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
[/HTML]

---

