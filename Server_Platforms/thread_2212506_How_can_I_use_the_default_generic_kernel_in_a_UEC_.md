---
title: "How can I use the default generic kernel in a UEC Ubuntu Cloud Image?"
date: 2014-03-21
forum: Server Platforms
---

### Post by CyberAngel on 2014-03-21
I download a UEC style Ubuntu Precise image from [http://cloud-images.ubuntu.com/](http://cloud-images.ubuntu.com/) that I want to use in an OpenStack cloud, but I want to make some modifications to it before booting the VM.

Installing additional packages in the image is straight forward. I mount **precise-server-cloudimg-amd64.img** and use apt-get after chroot-ing to the mounted folder. However, I also want to remove the default linux-image-virtual kernel (and precise-server-cloudimg-amd64-vmlinuz-virtual) and install and use the linux-image-generic one.

Anyone knows how can I achieve this in a chroot environment that I have mounted the cloud image?

When I remove the virtual and installing the generic, my VM simply doesn't boot at all.
I have already copied the kernel and initrd files, and register the image in glance using the new kernel and initrd for the kernel_id and ramdisk_id properties (not the default one which is precise-server-cloudimg-amd64-vmlinuz-virtual).

---

