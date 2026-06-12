---
title: "Ubuntu 16.04.6 LTS xenial qemu package bug while provisioning a VM"
date: 2019-07-15
forum: Virtualisation
---

### Post by dhanesh2019 on 2019-07-15
Hi 

Am running a server with Ubuntu 16.04.6 LTS xenial, its having a bug am not able to provision a any NEW VM and its failed to set NBD socket for 

> 
sudo /usr/bin/env qemu-nbd -c /dev/nbd2 /mypartition/image.qcow2


Always am trying to fix this with sudo modprobe > nbd max_part=16 and sudo partprobe /dev/nbd2 but its failed not able to fix this and also I tried to downgrade the package thats also fail. 

Please help me to fix this otherwise I need to downgrade my system to Ubuntu 14.04 

And also suggest to downgrade or how to install the older & stable version of qemu-kvm package in Ubuntu 16.04.6 LTS

Thanks in advance.

---

### Post by TheFu on 2019-07-15
14.04 support ended a few months ago.  At this stage, any new server should install 18.04.
```
sudo /usr/bin/env qemu-nbd -c /dev/nbd2 /mypartition/image.qcow2 
```
doesn't look like a correct command. Please double-check for a typo with the env part.

I have no idea about using ndb. Sorry.  I use simple LVM storage pools.

---

### Post by dhanesh2019 on 2019-07-20
Thanks for your response, I have fixed this by installing the following packages -  linux-image-extra-virtual-hwe-16.04, linux-modules-extra-4.15.0-1021



Thx

---

### Post by TheFu on 2019-07-20
Please mark the thread as SOLVED - thread tools button near the top. Helps the community not waste time.

---

