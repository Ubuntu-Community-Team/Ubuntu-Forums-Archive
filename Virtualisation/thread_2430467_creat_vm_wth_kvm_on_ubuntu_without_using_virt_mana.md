---
title: "creat vm wth kvm on ubuntu without using virt manager installation"
date: 2019-11-02
forum: Virtualisation
---

### Post by rezghju on 2019-11-02
i want to create a virtual machine with kvm on my ubuntu , i want to this with just command line in 1 minute without using virt manager and graphical installation
please help me about this

---

### Post by Doug S on 2019-11-02
I suggest the [Ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/libvirt.html#libvirt-virt-install") as a reference. For that virt-install example I would increase the memory allocated. Here is a recent example for myself:

```
sudo virt-install -n serv-ee -r 8192 --disk path=/media/newhd/serv-ee.img,bus=virtio,size=50 -c eoan-server-amd64-20190709.iso --network bridge=br0,model=virtio,mac=52:54:00:0d:ed:07 --video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```but it takes more than 1 minute, and still needs a vnc connection to interact with the installer.

---

### Post by deadflowr on 2019-11-02
*Thread moved to **Virtualization** *

---

