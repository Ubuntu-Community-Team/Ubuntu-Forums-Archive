---
title: "Ubuntu as a Xen guest?"
date: 2009-10-22
forum: Virtualisation
---

### Post by ttabbal on 2009-10-22
I'm running a big box with OpenSolaris as a server. It has Xen installed. I would like to run Ubuntu as a domU guest. I have been able to get it to install in hvm mode, but I was wondering if it's possible to install in para-virtualized mode? I'd like to get this working so I can run a Myth master backend and boot server from there. As it's running Solaris, KVM and Linux Dom0s are not an option. If Ubuntu had ZFS, I'd consider switching, but I'm not willing to lose ZFS on the server after using it for a while. 

The other question, since hvm works, is how much of a performance difference is there? The install in hvm was pretty slow compared to a CentOS install in para-virt mode. I really want to use Ubuntu here as the Myth packages are really well done. 9.10 is an option if that will work better. 

Any help or tips would be appreciated.

---

### Post by kameleon25 on 2009-10-22
I am not that familiar with OpenSolaris, but it should be as simple as setting up your configration file or passing all the proper switches to the "xen-create-image" command. The command I use to create my VM's is as follows:

```
xen-create-image --hostname=vm1.example.com --size=10Gb --swap=512Mb --ip=192.168.1.200 --netmask=255.255.255.0 --gateway=192.168.1.1 --force --lvm=vg0 --memory=512Mb --arch=i386 --kernel=/boot/vmlinuz-`uname -r` --initrd=/boot/initrd.img-`uname -r` --install-method=debootstrap --dist=hardy --mirror=http://archive.ubuntu.com/ubuntu/ --passwd
```

That is for an LVM domU. If you want a file-based (slower performance) just remove the "--lvm=vg0" and change it to "--dir=/home/xen" where the /home/xen is where you store all your VM's. Hope that helps some.

---

### Post by ttabbal on 2009-10-23
Thanks for the info. I got it working. Apparently, the OpenSolaris network drivers don't support jumbo frames. Once I disabled them, I was able to get networking working in PV mode. The kernel Ubuntu ships works with Xen, so that much was fine. I did install in HVM mode, but that was as much because I had already downloaded the CD as anything else. Apparently, Linux installs from an ISO don't work right when installing in PV mode unless you create an NFS mount for it or something. Debian has a cool network installer you can pass a URL to the "virt-install" command (Solaris doesn't have a "xen-create-image") and it downloads everything you need on the fly. I didn't see anything like that for Ubuntu. It would be nice if it were available, but this worked fine.

---

