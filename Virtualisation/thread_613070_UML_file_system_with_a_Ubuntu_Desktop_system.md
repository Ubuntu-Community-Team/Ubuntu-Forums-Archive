---
title: "UML file system with a Ubuntu Desktop system?"
date: 2007-11-14
forum: Virtualisation
---

### Post by astrashe on 2007-11-14
I have a vps account at linode.com, which uses user-mode linux.  I'd like to run an ubuntu desktop system as my vps and control it via FreeNX.

Linode lets you pick your distro, and they have an ubuntu server option, but I've had trouble getting an actual desktop running with it.  I think there's something a little off about linode's ubuntu server base I was starting with.

Does anyone have a UML file system for an Ubuntu desktop system pre-rolled?  I've never built my own UML file system from scratch, so it would be easier to use someone else's.

Thanks...

---

### Post by daflame on 2007-11-18
I don't have a UML dist of Ubuntu, but I have current packages of FreeNX 0.7.1.

If you are interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If you need other dist packages, please let me know and I'll start a VM to build one.

---

### Post by hashstat on 2007-11-27
Creating an Ubuntu file system for UML is simple.  Just use debootstrap.

First, build a disk image.  The commands below creates a 1GB sparse disk image with an ext3 file system
```
dd if=/dev/zero of=ubuntu-fs bs=1024 seek=1M count=1
mkfs.ext3 ubuntu-fs
```

Next, install debootstrap, mount your disk image, and install your system.  You can replace gutsy with your preferred ubuntu release.
```
sudo apt-get install debootstrap
sudo mount -o loop ubuntu-fs /mnt
sudo debootstrap --arch i386 gutsy /mnt http://us.archive.ubuntu.com/ubuntu
```

Finally, chroot into the filesystem and install ubuntu-desktop and any other packages you require.  debootstrap installs a minimal command-line system, so you need to install and configure your new system.
```
host$ sudo chroot /mnt /bin/bash --login -i
uml guest# apt-get install ubuntu-desktop ...
```

Once you have your file system configured, you need to unmount it before using it with uml.
```
sudo umount /mnt
./linux ubda=ubuntu-fs mem=128M
```

There are plenty of tutorials out there.  Just google for "ubuntu debootstrap" or just "debootstrap".  Enjoy.

---

### Post by daflame on 2007-11-27
BTW If you still need packages for Ubuntu of FreeNX 0.7.1 just visit my forum here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

Oh, here is a UML site I found very interesting:
[http://cosi.clarkson.edu/docs/kernel/setup/uml/uml.html](http://cosi.clarkson.edu/docs/kernel/setup/uml/uml.html)

Although for Gutsy, packages are in the universe repos for user mode linux.  I recommend using them.
The best option is to start with guml:
```
sudo apt-get install guml
```

Use your favorite editor and open /usr/share/doc/guml/README
```
nano /usr/share/doc/guml/README
```
follow the instructions to create UML configuration files.  Then run guml.

---

