---
title: "Network bridging problem in ubuntu 9.10 and Virtualbox"
date: 2010-02-21
forum: Virtualisation
---

### Post by Mirage ha on 2010-02-21
Hi all,
I have problem in setting up network in VB using bridged adapter/host interface 
I am using virtualbox v 3.1.4 and ubuntu v 9.10 and wired network not wireless and i follow this link [https://help.ubuntu.com/community/VirtualBox/Networking](https://help.ubuntu.com/community/VirtualBox/Networking) but i still do not have network in VB guset os.
So how can get network to work in Virtualbox?

Any help will be appreciated.

Mirage.

---

### Post by kiranmurari on 2010-02-22
Hi,

Please check if the correct wired interface (ethX) is bridged on the VMs network settings. Also please check the log files present in $(HOME)/.VirtualBox/Machines/<VM>/Logs/VBox.log

   You get the list of bridged interfaces available by issuing the following command:
```
$ VBoxManage list bridgedifs
```

---

