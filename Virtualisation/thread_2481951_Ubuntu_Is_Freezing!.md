---
title: "Ubuntu Is Freezing!"
date: 2022-12-14
forum: Virtualisation
---

### Post by phillipjelinek on 2022-12-14
Hello friends, I recently updated Ubuntu in the latest version. But friends, I am having a problem Ubuntu is freezing in Virtualbox. Could anyone please help me to help the issue?

---

### Post by slickymaster on 2022-12-14
Thread moved to **Virtualisation** for a better fit

---

### Post by TenPlus1 on 2022-12-14
Listing the specs of your system and specs of the virtualbox you set may help.

---

### Post by TheFu on 2022-12-14
Always look at the log files.  You can google for how to accomplish that.  I'd use 'journalctl', but there are many ways.

---

### Post by MAFoElffen on 2022-12-15
As they implied, there are two logs to look at, the host's run run log for a guest, and the guests syslog.
> 
The log file is called VBox.log and         resides in the VM log file folder, which is         $HOME/VirtualBox         VMs/*VM-name*/Logs by         default.       

Then as specs go, suspect for freezing would be running out of memory or disk space in either the guest or host.

---

### Post by phillipjelinek on 2022-12-15
Thank you everyone for your help. But after posting the thread here, I searched online and came across [this useful guide]("https://www.thewindowsclub.com/ubuntu-freezing-or-not-starting-in-virtualbox"). I followed some methods from here. First I turned off the 3d acceleration and reinstalled Ubuntu. After doing the methods perfectly, the problem got solved.

---

### Post by TheFu on 2022-12-15
[https://bugs.launchpad.net/ubuntu/+bug/1992155](https://bugs.launchpad.net/ubuntu/+bug/1992155) might be related.  Hard to say from the information provided.

---

