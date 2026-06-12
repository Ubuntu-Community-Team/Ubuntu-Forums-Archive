---
title: "cant create a new empty VM beacuse QEMU failed to run feature checks"
date: 2024-02-15
forum: Virtualisation
---

### Post by marhatom on 2024-02-15
I would like to create a new empty VM using windows image 

```
lxc init win11 --vm --empty
```

But that fails with the information that 

>  Creating win11
Error: Failed creating instance record: Instance type "virtual-machine" is not supported on this server: QEMU failed to run feature checks


After a while i got this message when I tried to initialize lxd again 

> 
ERROR  [2024-02-15T16:45:15+01:00] Failed to start the daemon                    err="LXD is already running"
ERROR  [2024-02-15T16:45:15+01:00] Unable to run feature checks during QEMU initialization: Unable to locate the file for firmware "OVMF_CODE.4MB.fd" 
WARNING[2024-02-15T16:45:15+01:00] Instance type not operational                 driver=qemu err="QEMU failed to run feature checks" type=virtual-machine
Error: LXD is already running


So I assume that the problem is the missing "OVMF_CODE.4MB.fd" file in /usr/share/OVMF/. 

Installing 
```
sudo apt install ovmf
```

wont do the job, so where can I get the file from.

---

### Post by TheFu on 2024-02-15
Just to clarify, you want to use LXD to manage full virtualized machines, not Linux containers.  I've never used or even tried to use LXD for that purpose. I'd read that it was possible, but we're so used to using libvirt for VM management the last 15 yrs that using LXD isn't something we ever considered.

[https://ubuntu.com/blog/lxd-virtual-machines-an-overview](https://ubuntu.com/blog/lxd-virtual-machines-an-overview) has this:
> Running Windows

If you would like to run a Windows VM, you would first need to repackage the Windows ISO file, using **distrobuilder**, before proceeding to install it into an LXD virtual machine.

The process is then relatively simple, and you can follow the steps in this video.

Sorry, I don't have any real knowledge to pass on.  Did you use **distrobuilder**?

---

### Post by marhatom on 2024-02-16
Yes, I was following this tutorial [https://ubuntu.com/tutorials/how-to-install-a-windows-11-vm-using-lxd#2-prepare-your-windows-image](https://ubuntu.com/tutorials/how-to-install-a-windows-11-vm-using-lxd#2-prepare-your-windows-image)

---

