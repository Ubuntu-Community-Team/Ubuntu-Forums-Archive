---
title: "vmware workstation15.1 in ubuntu 19.04 not allowed to load vmmon &amp; vmnet-secure boot"
date: 2019-08-10
forum: Virtualisation
---

### Post by zekavat on 2019-08-10
[COLOR=#000000][FONT=MetropolisRegular]On Linux host with secure mode enabled, it is not allowed to load any unsigned drivers. Due to this, VMware drivers, such as [/FONT][/COLOR][FONT=Courier New][SIZE=2][COLOR=#000000]vmmon[/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=MetropolisRegular] and [/FONT][/COLOR][FONT=Courier New][SIZE=2][COLOR=#000000]vmnet[/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=MetropolisRegular], are not able to be loaded which prevents virtual machine to power on, how to sign vmmon and vmnet to load when secure boot enabled,[/FONT][/COLOR]

---

### Post by TheFu on 2019-08-10
I think you'll need to contact VMware support for an answer.

---

### Post by rbmorse on 2019-08-10
This may help:

[https://kb.vmware.com/s/article/2146460](https://kb.vmware.com/s/article/2146460)

---

### Post by zekavat on 2019-08-11
I tried this before, It doesn't work in disco dingo,

---

