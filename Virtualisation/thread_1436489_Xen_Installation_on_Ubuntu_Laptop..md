---
title: "Xen Installation on Ubuntu Laptop."
date: 2010-03-22
forum: Virtualisation
---

### Post by Sethu85 on 2010-03-22
Hi All, 

I am trying to install Xen in Ubuntu 9.04. I have a Dell XPS 1530.
I have followed these steps.

Downlaod and extract the tarball.
make world  KERNELS="linux-2.6-xen0 linux-2.6-xenU"
make install  KERNELS="linux-2.6-xen0 linux-2.6-xenU"
depmod 2.6.18.8-xen0
mkinitramfs -o /boot/initrd-2.6.18.8-xen0.img 2.6.18.8-xen0
Added the following entry to /boot/grub/menu.lst file
title           Xen 3.0 / XenLinux 2.6
root            (hd0,0)
kernel          /boot/xen-3.1.4.gz dom0_mem=262144
module          /boot/vmlinuz-2.6.18.8-xen0 root=/dev/sda1 ro console=tty0
module          /boot/initrd-2.6.18.8-xen0.img

When i boot my system, everything goes smoothly and i get my usual ubuntu login through the xen boot. But both my mouse and keyboard is not detected as a result i am uable to login to the system. 

Is this a common mistake? Am i missing something?

---

### Post by TheFu on 2010-03-23
What you are doing appears reasonable, but couldn't you just install the xen-server and xen-tools packages?  If you do it they way you are, I think you need to manually setup the networking.

I run Xen on 8.04 LTS, so I don't know whether 9.x changed anything. Pkg names are:
ubuntu-xen-server, xen-tools. There are others, but they will get installed via dependencies, I think. I used a howto on howtoforge to get up and running.  We have about 10 parav Xen VMs running on 2 physical machines in production for the last 18 months. 

After you get the Dom0 kernel working, use xen-create-image to create your img files. Don't use sparse files (the default) if you care anything about performance. We use "full" img files (--image=full) and have been happy with the performance.

Since KVM is becoming the preferred virtualization method across the Linux distros, I think you need to ask yourself, "why you are starting with Xen now?"

Here's a guide that google found which appears reasonable [http://cosi.clarkson.edu/docs/installingxen/](http://cosi.clarkson.edu/docs/installingxen/) for what I did. It shows the manual way and the package manager way.

---

