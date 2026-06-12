---
title: "Diskless boot problem: can't get rid of NFS v2 mount."
date: 2009-02-26
forum: Server Platforms
---

### Post by Cracauer on 2009-02-26
I'm a little puzzled.

This diskless machine cannot create files > 2 GB on the server.

I initially thought that the problem is that the default mount created by the kernel on boot (as opposed to by fstab) does a NFS v2 mount.

So I create a fstab entry like this:
```

172.16.30.1:/home/diskless/debian-amd64-root1   /       nfs nfsvers=3,wsize=204 8,nolock 0  0

```

I mount fine and I get
```

 mount | grep root
rootfs on / type rootfs (rw)
172.16.30.1:/home/diskless/debian-amd64-root1 on / type nfs (rw,nfsvers=3,wsize=2048,nolock,addr=172.16.30.1)

```

So that's what? The old mount or the new mount?

Either way, I cannot create files > 2 GB in that filesystem.

I then mounted a different directory from the server, and I can create files > 2 GB in there. So the problem is specific to the root filesystem.

%%

So, the question I end up with: how do I either
[list]
[*]Make the kernel do a v3 mount automatically during diskless boot?
[*]Or how to I really replace this mount? Obviously the "mount-over" didn't do it.
[/list]

Any suggestions?

---

### Post by promodus on 2009-02-28
when I run:
```
nfsstat
```
I get statistics only for nfs v3


my diskless client fstab has:
```
10.0.0.1:/nfsroot  /   nfs,defaults  1 1
```

Boot parameters: (for pxelinux)
```
LABEL linux
KERNEL boot/linuxnetboot/netkernel
		APPEND root=/dev/nfs initrd=boot/linuxnetboot/netinitrd nfsroot=10.0.0.1:/nfsroot ip=dhcp rw
```

I have in /etc/initramfs-tools/initramfs.conf
I have MODULES=netboot, BOOT=nfs, DEVICE=etho, NFSROOT=auto

I believe those are all the changes I had made (less DHCP, TFTP server settings, etc.) I also symlink the boot files from nfsroot... so if I do an apt-get update on the nfs diskless client it also updates the tftp boot kernel & initrd.

Anyway, I was able to create a 2+GB file. A bit slow, but no problem.

---

### Post by Cracauer on 2009-02-28
Thanks, promodus.

What does 'mount' say?

Do you have separate "rootfs on /" and "server:/fs on /" lines in nfsstat and mount?

Or does the old "rootfs" entry disappear in your setup?

The only way around this I have found is to manually over-mount each directory such as /usr, /lib etc one by one. Then I get the v3 mount. But I haven't been able to replace "/", all I get is a double "/" mount and apparently v2 stays effective.

---

### Post by promodus on 2009-02-28
```
root@disklessnode:/$ mount
10.0.0.1:/nfsroot on / type nfs,defaults (rw,1)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
none on /tmp type tmpfs (rw)
none on /var/run type tmpfs (rw)
none on /var/lock type tmpfs (rw)
none on /var/tmp type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
```

and 
```
root@disklessnode:/$ nfsstat
Client rpc stats:
calls      retrans    authrefrsh
22444      63         0       

Client nfs v3:
null         getattr      setattr      lookup       access       readlink     
0         0% 11257    50% 29        0% 1051      4% 3721     16% 110       0% 
read         write        create       mkdir        symlink      mknod        
699       3% 4955     22% 20        0% 0         0% 0         0% 0         0% 
remove       rmdir        rename       link         readdir      readdirplus  
31        0% 0         0% 6         0% 14        0% 0         0% 84        0% 
fsstat       fsinfo       pathconf     commit       
0         0% 2         0% 0         0% 464       2% 
```

On the server:
/etc/exports
```
/nfsroot	10.0.0.0/255.255.255.0(rw,no_root_squash,no_subtree_check
```

---

### Post by Cracauer on 2009-02-28
Thanks.

So the difference is that the fstab mount for "/" replaced the original "rootfs" mount, there's no trace of it on your computer. While for me /etc/rc doesn't mount root, leaves the boot rootfs in place and a later manual mount of "/" from fstab doesn't upgrade me to NFSV3 as specified in fstab.

What distro and kernel are you on?

---

### Post by promodus on 2009-02-28
> **Cracauer said:**
> Thanks.

So the difference is that the fstab mount for "/" replaced the original "rootfs" mount, there's no trace of it on your computer. While for me /etc/rc doesn't mount root, leaves the boot rootfs in place and a later manual mount of "/" from fstab doesn't upgrade me to NFSV3 as specified in fstab.

What distro and kernel are you on?

Hardy Heron 
Kernel: 2.6.24-18-server

[https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot](https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot)

I'm guessing it's an intiramfs issue.

---

### Post by Cracauer on 2009-02-28
Those instructions have no fstab entry for "/", so certainly the kernel in that setup mounts v3 by itself - if it's v3.

But that doesn't seem to be the setup that you have, since you have a "/" fstab entry. And we don't know whether those instructions result in a v2 or v3 mount.

I think the most straightforward way might be to disallow v2 on the server and/or remove NFS v2 from the diskless machine's kernel.

---

