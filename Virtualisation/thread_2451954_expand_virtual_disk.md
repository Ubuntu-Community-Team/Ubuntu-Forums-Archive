---
title: "expand virtual disk"
date: 2020-10-13
forum: Virtualisation
---

### Post by tech-jeff on 2020-10-13
Hi,

I setup a wiki named Hudu and platform is only on Ubuntu version 18.04.4 LTS. It is a virtual machine that resides in a Hyper-V host. I set the virtual disk to 128GB initially and noticed that because of the attachment of pictures, it rapidly grown bigger and I want to expand the disk. I scheduled it for a shutdown maintenance in order for me tio expand the vhd/virtual disk, add free space, it now has 250GB but correct me if I'm wrong, I turn on the virtual machine I thought it would automatically occupy or add those free space but it didn't. Tried the command 'df' but stil shows the same free space. 

How do I add the free space on this?

Thanks in advance
tech-jeff

---

### Post by deadflowr on 2020-10-13
*Thread moved to **Virtualization***

---

### Post by Dennis N on 2020-10-13
I have used the procedure described here:

[https://fatmin.com/2016/12/20/how-to-resize-a-qcow2-image-and-filesystem-with-virt-resize/](https://fatmin.com/2016/12/20/how-to-resize-a-qcow2-image-and-filesystem-with-virt-resize/)

---

