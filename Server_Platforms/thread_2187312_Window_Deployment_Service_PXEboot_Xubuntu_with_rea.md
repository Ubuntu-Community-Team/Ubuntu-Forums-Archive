---
title: "Window Deployment Service PXEboot Xubuntu with read/write filesystem"
date: 2013-11-11
forum: Server Platforms
---

### Post by Lee_Machine on 2013-11-11
All,

So I'm working on a solution to PXEboot Xubuntu on Dell Wyse boxes using Windows Server 2008 R2 running Window Deployment Service. That up and running for a read-only squashfs image is not too hard and is great for pxebooting a custom image and then installing on a local HDD. 

My problem is I want to pxeboot a full read/write system and I got it to boot but the system is REALLY slow and buggy as hell. Here is my pxelinux.cfg/default file:

```
#For the static Read-Only image
LABEL Xubuntu-12.04
MENU LABEL Xubuntu-12.04
MENU PASSWD $PASSWORDHASH
MENU PASSWORDMARGIN 26
MENU PASSWORDROW 12
kernel /Linux/Xubuntu-12.04/casper/vmlinuz
append priority=high boot=casper vga=normal netboot=nfs nfsroot=<ip.for.server:/RemoteInstall/Boot/x64/Linux/Xubuntu-12.04 initrd=/Linux/Xubuntu-12.04/casper/initrd.gz

#For the dynamic Read/Write image
LABEL Xubuntu-12.04-rw
MENU LABEL Xubuntu-12.04-rw
MENU PASSED $PASSWORDHASH
MENU PASSWORDMARGIN 26
MENU PASSWORDROW 12
kernel /Linux/Xubuntu-12.04-rw/init-kernel/vmlinuz-3.2.0-56-generic nfsroot=rw
append priority=high root=/dev/nfs vga=normal netboot=nfs nfsroot=ip.for.server:/RemoteInstall/Boot/x64/Linux/Xubuntu-12.04-rw initrd=/Linux/Xubuntu-12.04-rw/init-kernel/initrd.img-3.2.0-56-generic rw
```

Here is the clients fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc       defaults        0       0
/dev/nfs       /               nfs          defaults,bg,init,hard,nolock,noatime          1       1
none            /tmp            tmpfs    defaults        0       0
none            /var/run        tmpfs   defaults        0       0
none            /var/lock       tmpfs   defaults        0       0
none            /var/tmp        tmpfs  defaults        0       0
```

So as I said both systems boot up but the static one using squshfs is much more responsive and not buggy. The full read-write system is very slow, and buggy, to include the file browser Thunar not working.

any ideas?

-Brandon

---

### Post by Lee_Machine on 2013-11-18
So an update to this thread. I never got it to work using Windows Server 208 R2. Microsoft's NFS implementation is just too non-standard and not only are read/write speeds horrendous there were too many NFS IO errors. I switched to using RHEL6 instead and it works just fine bar a weird cp bug where permissions were not being preserved so I had to pull the rootfs from the client rather than push it to the RHEL6 server.

---

