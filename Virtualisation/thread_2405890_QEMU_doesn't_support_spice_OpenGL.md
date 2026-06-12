---
title: "QEMU doesn't support spice OpenGL"
date: 2018-11-12
forum: Virtualisation
---

### Post by behbahani on 2018-11-12
Hi there, 
I'm trying to use KVM on my machine (threadripepr 2950 CPU and AMD WX7100 GPU) running ubuntu 18.04.
I have followed KVM and virtual machine manager and bridge networking procedure and first step was ok.
I have an issue of using OpenGL ( by selecting the option on Display Spice setting).
I found this webpage explained the steps for activation openGL. [https://at.projects.genivi.org/wiki/display/GDP/QEMU+with+hardware+graphics+acceleration]("https://at.projects.genivi.org/wiki/display/GDP/QEMU+with+hardware+graphics+acceleration")
Apart of last step verification which is:
[# dmesg | grep gl [drm] virgl 3d acceleration enabled] 
the rest of the result was ok. 
Would anyone please let me know how I can use and set properly openGL and graphic acceleration on KVM on ubuntu 18.04?

Cheers

---

### Post by richard378 on 2019-04-22
Try this blog page it is Ubuntu specific. The page you refer to is Fedora tested.: [URL="https://zingmars.info/2018/07/15/Virgl-with-qemu-and-libvirt-on-ubuntu/"]https://zingmars.info/2018/07/15/Virgl-with-qemu-and-libvirt-on-ubuntu/
[/URL]
Also look at this bug report [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/1540692](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/1540692) it seems that you can enable the OpenStack unsable repository 
```
   
sudo add-apt-repository cloud-archive:stein
sudo apt update
sudo apt full-upgrade

```

---

