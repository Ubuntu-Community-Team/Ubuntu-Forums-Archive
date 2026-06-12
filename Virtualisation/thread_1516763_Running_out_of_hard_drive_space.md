---
title: "Running out of hard drive space"
date: 2010-06-24
forum: Virtualisation
---

### Post by orlandodawn on 2010-06-24
Hi there

I am running VirtualBox on Ubuntu 10.04 and have the following setup:

HD1 - 1TB formatted Ext4 containing 950GB vdi file (WHS1.vdi)
HD2 - 1TB formatted Ext4 containing 950GB vdi file (WHS2.vdi)

both dynamically setup.

I have created a virtual machine running Microsoft Windows Home Server with both of these drives added. HD1 is the boot drive. Home Server has been happily using both drives spanning the data the way its supposed to.

At the moment the virtual machine is pausing and Linux is reporting that HD1 is running out of space (8k left)

However, on looking via VirtualBox it is saying the WHS1.vdi filesize is only 850GB. 

So Im wondering how the physical hard drive can be running out of space...?

---

### Post by bondo101 on 2010-06-28
Or is it your virtual drive is running out of space? Try to remember how you set up your virtual drive.I know it sounds stupid but it was just a thought.Just trying to help

---

### Post by stlsaint on 2010-06-29
Are you saying that you gave your entire hdd space to the virtual machine? Vbox will allocate some of that space physically if you use some hdd space for the vdi. So for instance if you have a 40gb harddrive and you allocate a vdi for a vm 20gb. Than you will have per'say 34gb left on the physical drive. So if your giving your entire hdd to the virtual machine that is why your getting that error.

---

