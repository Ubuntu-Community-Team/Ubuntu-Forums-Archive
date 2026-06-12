---
title: "lvextend increase size to max physical disk"
date: 2009-08-25
forum: Server Platforms
---

### Post by shebangs on 2009-08-25
In all virtualization technologies, you can increase the raw size of the virtual disk.

Inside the guest OS (Ubuntu 64bit) I have a non-root disk created as LVM+EXT3.  

Is it possible to tell lvextend "resize to the end of the physical disks"?  Instead of "resize +500M".

When you resize a virtual disk, the hypervisor adds raw unused space to the end of the disk.   

I was planning on "lvextend && resize2fs".

---

### Post by linuxford on 2011-07-30
I had some trouble adding a volume initially when using the gui LVM tool, system-config-lvm

It seemed like I could create the volume group (gulp, not sure on lingo and still a little confused), but when I tried to resize, it complained about a ext2fs error, so I ended up doing some searching and used your two suggestions and it worked, so thanks. Here is the two commands I used.

```
sudo lvextend -L+300G /dev/mapper/lws01-root
sudo resize2fs /dev/mapper/lws01-root
```

Seems to be working fine. I love the LVM capability, just a little tricky.

---

