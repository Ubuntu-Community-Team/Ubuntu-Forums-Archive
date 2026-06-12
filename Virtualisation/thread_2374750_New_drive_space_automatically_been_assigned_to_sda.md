---
title: "New drive space automatically been assigned to sda1"
date: 2017-10-18
forum: Virtualisation
---

### Post by pazuzu010 on 2017-10-18
Hi.

I am expanding a drive on a VM, but I really need the new space to remain unnasigned to any of the partitions. As soon as I boot Ubuntu, sda1 gets all the space. This from my kern.log:
```
Oct 18 21:00:12 ubuntutest-4 kernel: [   44.526736] EXT4-fs (sda1): resizing filesystem from 13078779 to 13340923 blocks
Oct 18 21:00:12 ubuntutest-4 kernel: [   44.545832] EXT4-fs (sda1): resized filesystem to 13340923
```
lsblk shows sda1 having all the new space.


How do I stop this automatic resize?

Thanks,

R.G.

---

### Post by DuckHook on 2017-10-18
Welcome to the forums, pazuzu010.

[LIST=1]
[*]What VM technology are you using???
[*]Did you allocate fixed or dynamic HDD size when you created the VM? (You must use fixed.)
[*]Did you partition prior to the install process or just select "automatic" partitioning during the install?
[/LIST]
As you can see, we need a lot more historical background and at least an outline of the steps you took before anyone can help.

---

### Post by pazuzu010 on 2017-10-18
Thanks!

1) Azure of the shelf Ubuntu. I believe is 17.10, but I am currently having issues accesing the portal, so I will verify later.
2) Used default. It creates a 30GB partition. 
3) Partition is automatic.

Later I deallocated the VM and added 2GB to the root partition for a total of 32GB. The new space was automatically allocated to sda1 after reboot. After looking around, I suspect cloud-init is installed and is set to auto grow. Will try to check as soon as can get to the portal again.

Edit: Cloud-init seems to be installed, but not configured.

---

### Post by DuckHook on 2017-10-19
*Thread moved to **Virtualisation** as the more appropriate forum.*

---

### Post by DuckHook on 2017-10-19
> **pazuzu010 said:**
> 1) Azure of the shelf Ubuntu. I believe is 17.10, but I am currently having issues accesing the portal, so I will verify later.The meaning of the question is: what virtual machine are you using? Is it VirtualBox? KVM? Xen? VMWare? Or something else?
> 2) Used default. It creates a 30GB partition. Most virtual machines allow you to determine whether you want the HDD to be static or dynamic when you first set it up. A static HDD carves out a set amount of space on your real HDD to act as the virtual HDD. This space is then dedicated to that VM alone and is not available to any other use. A dynamic HDD does not carve out a set amount of space. Instead, it grows as your need for virtual HDD space grows. This conserves physical HDD space at the cost of slower I/O and more fragmentation. If you want to set aside empty partition space, then you must define a static HDD when you first set up your VM.
> 3) Partition is automatic.When you install the guest OS, you must not go for "automatic" partitioning. This option will use all of the available virtual HDD space. Instead, the best way is to partition your virtual HDD beforehand, allocating the exact amount that you want for each directory. If you want everything under just one directory (simplest and easiest), then you must create a partition of a set size that is smaller than your virtual HDD, and choose "something else" at the partitioning phase of your setup. Choose the paritition you've just created and install the guest OS onto that. The rest of the virtual HDD will remain empty and unused.
> Later I deallocated the VM and added 2GB to the root partition for a total of 32GB. The new space was automatically allocated to sda1 after reboot. After looking around, I suspect cloud-init is installed and is set to auto grow. Will try to check as soon as can get to the portal again.

Edit: Cloud-init seems to be installed, but not configured.I am not familiar with cloud-init. Is this installation on a VPS?

Perhaps you had better post back the results of:```
sudo parted -l
``````
sudo fdisk -l
``````
df -h
``````
lsblk
```

---

