---
title: "Looking for a way to shutdown guest systems when VMware Server host goes down"
date: 2008-05-23
forum: Virtualisation
---

### Post by uoirej on 2008-05-23
Hi, I'm running VMWare Server 2 on Ubuntu Server 8.04. Just wondering if there is a way to automatically shutdown guest systems when the host goes down? vmware does print something like "stopping autostart virtual machines" on the console during host shutdown, but it doesn't seem to really shut down anything, the result looks like a "virtual poweroff"...

Any ideas?

PS Running VMware Server 2.0 beta e.x.p build-84186 under UbuntuServer 8.04 (2.6.24-16-server).

PPS Does anoyne know what that "e.x.p" means?

---

### Post by LeoSolaris on 2008-05-23
For the real issue, I have no idea, but I can tell you that the e.x.p. stands for experimental.

---

### Post by jure1873 on 2008-05-24
```
vmrun list
vmrun stop ubuntu.vmx
...
```

maybe vmrun stop *.vmx?

---

### Post by loners on 2011-06-14
Try using **vmrun** ***runProgramInGuest*** option to run the **shutdown** command in the guest.

---

