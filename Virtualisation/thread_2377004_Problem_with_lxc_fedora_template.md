---
title: "Problem with lxc fedora template"
date: 2017-11-08
forum: Virtualisation
---

### Post by luca-barazzuol on 2017-11-08
Hi,

I want to create a fedora based lxc container using a template on my new Ubuntu Desktop 17.10.

I use this command:
```
$ sudo lxc-create -t fedora -n example-fedora-25 -- --release=2
```

But I got this error:
```
Checking cache download in /var/cache/lxc/fedora/25-x86_64/rootfs ... 
Downloading x86_64 rootfs for Fedora 25 ...
Non-Fedora host detected. Checking for bootstrap environment ... 
Setting up new Fedora 25 (x86_64) bootstrap environment.
Using cached LiveOS squashfs image.
Mounting LiveOS squashfs file system.
mount: /var/cache/lxc/fedora/bootstrap_SGnQ4u/squashfs: wrong fs type, bad option, bad superblock on /dev/loop5, missing codepage or helper program, or other error.

Error: Mount of LiveOS squashfs image failed
--------------------------------------------
You must have squashfs support available to mount image. LiveOS image is now
cached. Process may be rerun without penalty of downloading LiveOS again. If
LiveOS is corrupt, remove /var/cache/lxc/fedora/install.img

Error: Fedora Bootstrap setup failed
Error: Failed to download Fedora 25 (x86_64)
Error: Failed to create Fedora container
lxc-create: example-fedora-25: lxccontainer.c: create_run_template: 1473 container creation template for example-fedora-25 failed
lxc-create: example-fedora-25: tools/lxc_create.c: main: 326 Error creating container example-fedora-25

```

The error seems to be caused by squashfs but I don't how fix it.

The strange thing is that I can create the container using the command ```
$ sudo lxc-create -t download -n example-fedora-25
``` and giving name of distro and release by hand.

Any ideas?

thanks in advance

LK

---

