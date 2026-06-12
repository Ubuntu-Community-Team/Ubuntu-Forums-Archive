---
title: "VMware tools install/config core dumped on guest Ubuntu 22.04"
date: 2022-05-10
forum: Virtualisation
---

### Post by hixuco on 2022-05-10
Hi,
     Host OS: win11
     Guest OS: Ubuntu 22.04
     VMware player: 15.0 ~ latest  16.2.3 (downloaded on 5/10)
     VMware player, install VMware tools, an ISO mounted on guest Ubuntu, 
        sudo ./vmware-install.pl
     during  vmware-config-tools.pl  , it  reports  "segmentation fault (core dumped)"
    It seems like a VMware problem,  but I tried to rerun config tools and failed to know the crash step, does any one know how to fix it?
    Thanks in advance!
    I noticed that someone mentioned to apt install open-vm etc.

---

### Post by hixuco on 2022-05-11
After i uninstall  vmware tools, and remove/install open-vm, it seems like copy/paste text clip and  10MB small file works, but big file like 1GB causing application Files crashed.

sudo apt-get autoremove open-vm-tools
sudo apt-get install open-vm-tools
sudo apt-get install open-vm-tools-desktop

---

