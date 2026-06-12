---
title: "How to install Nvidia 8400GS driver in Guest  Win 7."
date: 2010-10-07
forum: Virtualisation
---

### Post by prashantvrm on 2010-10-07
Currently i am using Win7 and Ubuntu 10.04.Is it possible to install 8400GS gfx card driver in Win 7 which i have installed in vbox via ubuntu.If it will be possible then i could remove my host win 7 and use only 1 os that is ubuntu as my host.

---

### Post by nevius on 2010-10-07
> **prashantvrm said:**
> Currently i am using Win7 and Ubuntu 10.04.Is it possible to install 8400GS gfx card driver in Win 7 which i have installed in vbox via ubuntu.If it will be possible then i could remove my host win 7 and use only 1 os that is ubuntu as my host.

A VM inside virualbox doesn't have direct access to your video card. You can enable 3D acceleration by checking the box on the general properties tab of your VM's settings and then installing the guest additions (which will load up the special virtualbox graphics driver).

---

