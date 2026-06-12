---
title: "configure samba dc inside an ubuntu 14.04 lxc container"
date: 2016-02-05
forum: Virtualisation
---

### Post by doktor2 on 2016-02-05
Hello,

this is my first post after a year and a half using ubuntu as my primery personal system and i'm very happy with it!.

nowdays am trying to make a home server running some services like groupware, owncloud, personal website,C, python and ruby dedicated development servers.
 usually my choise is to use one of the following free hypervisors: esxi ,xen server, ubuntu desktop vith virtualbox or ubuntu server virtualbox with php gui.

in order to max my x3220 quad core server with 6 gig of ram i thought about doing it in a light whight virtualization platform and i chose to do it with lxc.
my first challange is to make a primery domain controller for centrelized permissions etc'.. while following a setup guide here: [https://jimshaver.net/2014/07/13/setting-up-an-active-directory-domain-controller-using-samba-4-on-ubuntu-14-04/](https://jimshaver.net/2014/07/13/setting-up-an-active-directory-domain-controller-using-samba-4-on-ubuntu-14-04/) 

i am stuck at the fstab editing adding to the / partition these values: user_xattr,acl,barrier=1 
when i try to edit fstab there is only one line: UNCONFIGURED FSTAB FOR BASE SYSTEM

the author says:
"Because samba makes use of some extended filesystem attributes that  EXT3/4 don’t normally support we have to set them in fstab.  Not that  the packages acl and attr are required for this to work."

please assist,
Doktor

---

### Post by MAFoElffen on 2016-02-07
And what filesystem are you using? I would suppose ext4, since ext4 journaling has advantages over ext3... and is the current default. You said you are using 14.04.

The Samba wiki says for ext4, for your one added line, added after that one comment in your container's fstab, it would be something like this:
```

/dev/sdc3          /srv/samba/demo          ext4          defaults,barrier=1          1 1

```
If you were still using ext3, then 
```

/dev/sdc3          /srv/samba/demo          ext3          user_xattr,acl,barrier=1          1 1

```

---

### Post by doktor2 on 2016-02-07
I'm using ext4 as it's 14.04 default.

this is the host /etc/fstab: 

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md1 during installation
UUID=01b70957-6abb-4a96-afab-dbf2090e3e17 /               ext4    errors=remount-ro 0       1
# swap was on /dev/md0 during installation
UUID=3497e586-fe09-48a6-9e79-1d69af8a1ca8 none            swap    sw              0       0

I thought it should be somethin like this at the conatiner fstab

```

/dev/sda             /               ext4            user_xattr,acl,barrier=1            1 1 

```

should i list devices and choose my own container /etc/sdx ?
/srv/samba/demo ? 

Thanks again,
Doktor

---

### Post by MAFoElffen on 2016-02-07
Samba says ext4 and current kernels have those 1st 2 options as default. You can say those explicitly (for safety, and the just in cases), but according to them, not needed for ext4. (Required for ext3.)

Also note that LXC containers have a few peculiarities ... and a new fstab options, just for themselves.  I don't think you are needing them, but... 

What are you trying to mount from where to what? Have you tried that mount successfully "manually" yet?

---

### Post by doktor2 on 2016-02-08
do you mean those 2 options? (user_xattr,acl)> 
What are you trying to mount from where to what?

mount the container rootfs as / partition.

In /var/lib/lxc/container_name/config add a line:
lxc.mount.entry = /var/lib/lxc/Container_name/rootfs / none bind 0 0

I will test it and update.

Tnx,
Doktor

source
[http://unix.stackexchange.com/questions/69072/lxc-how-do-i-mount-a-folder-from-the-host-to-the-container](http://unix.stackexchange.com/questions/69072/lxc-how-do-i-mount-a-folder-from-the-host-to-the-container)

---

### Post by MAFoElffen on 2016-02-08
Yes, as a method ... That is one of 3 methods. That method is now the accepted LXC "external" mount method from the host, as that also works with unprivileged LXC containers. Other ways are to either pass-through the mount as a shared host resource, or mounted as a network share. The last is less secure .. as in the first two, the wiring never leaves the physical machine.

But as a practice... When I get home tonight, I'll have to look at some of my LXC containers. I think that might be... I want to look at something in mine. When you boot a container image as an instance, that image's filesystem is local, not external. I don't want to blurt something out on the specifics, until I confirm something tonight on mine.

EDIT-- I'll leave it a that for now. I think LXC fstab's are a different animal as it relates to it's own local filesystem... But I need to confirm that. 

In the meantime:
> **ROOT FILE SYSTEM***The root file system of the container can be different than that of the host system.*
***lxc.rootfs***
*specify the root file system for the container. It can be an image file, a directory or a block device. If not specified, the container shares its root file system with the host.*
*For directory or simple block-device backed containers, a pathname can be used. If the rootfs is backed by a nbd device, then nbd:file:1 specifies that file should be attached to a nbd device, and partition 1 should be mounted as the rootfs. nbd:file specifies that the nbd device itself should be mounted. overlayfs:/lower:/upper specifies that the rootfs should be an overlay with /upper being mounted read-write over a read-only mount of /lower. aufs:/lower:/upper does the same using aufs in place of overlayfs. For both overlayfs and aufs multiple /lower directories can be specified. loop:/file tells lxc to attach /file to a loop device and mount the loop device.*

***lxc.rootfs.mount***
*where to recursively bind lxc.rootfs before pivoting. This is to ensure success of the pivot_root(8) syscall. Any directory suffices, the default should generally work.*
***lxc.rootfs.options***
*extra mount options to use when mounting the rootfs.*


---

### Post by MAFoElffen on 2016-02-09
This is from my management console:
```

mafoelffen@snoopy:~$ sudo lxc-start --name xenial01 -d

mafoelffen@snoopy:~$ sudo lxc-ls --fancy
NAME      STATE    IPV4  IPV6  AUTOSTART  
----------------------------------------
xenial01  RUNNING  -     -     NO         

mafoelffen@snoopy:~$ sudo lxc-attach --name xenial01

root@xenial01:/# ls 
bin  boot  dev    etc  home  lib    lib64  media  mnt  opt    proc  root  run  sbin  srv  sys  tmp  usr  var

root@xenial01:/# cat /etc/fstab
# UNCONFIGURED FSTAB FOR BASE SYSTEM

root@xenial01:/# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial

root@xenial01:/# uname -a
Linux xenial01 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

root@xenial01:/#exit 


mafoelffen@snoopy:~$ sudo lxc-stop --name xenial01

```
So like I thought, the filesystem in an LXC container in virtualized. YOu only need to add something to the fstab unless you are creating an external mount -or- when changing a pivot from sharing a root filesystem with it's host (see last post and this:)
> 
[B]lxc.rootfs
[/B]specify the root file system for the container. It can be an image file, a directory or a block device. If not specified, the container shares its root file system with the host.
So you would use lxc.rootfs.mount

---

### Post by doktor2 on 2016-02-24
thank you for you help.
Doktor

---

