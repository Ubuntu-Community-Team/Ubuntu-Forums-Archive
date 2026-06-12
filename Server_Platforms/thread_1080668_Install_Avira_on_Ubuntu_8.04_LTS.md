---
title: "Install Avira on Ubuntu 8.04 LTS"
date: 2009-02-25
forum: Server Platforms
---

### Post by mariusft on 2009-02-25
Dears,

Perhaps someone managed to install Avira free antivirus on their servers, I want to install this antivirus since I'm satisfied with his performance, I'm not installing it for linux viruses but for windows viruses, I'm using the machine like a file server and also I want it to use it like a mail server.

The think I encounter is that the module needed for live scan is dazuko and I can't compile it, I have tried to compile the sources but I encounter the problems with the capability of kernel to load modules.

------------
verifying capabilities are not built-in... built-in :(
error: capabilities are built-in to the kernel:
       you will need to recompile a kernel with capabilities
       as a kernel module
------------

There could be any advice to this matter?

Thanks

---

### Post by mariusft on 2009-02-25
Hi everyone,

I have found a solution on a Chinese site, don't ask I don't know Chinese:
```

sudo apt-get install linux-headers-`uname -r`

```
```

wget http://dazuko.dnsalias.org/files/dazuko-2.3.6.tar.gz
tar -xvf dazuko-2.3.6.tar.gz

```
```

./configure --disable-local-dpath --disable-chroot-support --enable-syscalls --mapfile=/boot/System.map-`uname -r` --kernelsrcdir=/usr/src/linux-headers-`uname -r`
make
sudo make install

```

and now you have the dazuko.ko 

if when you try to load the module with modprobe you got the error "Segmentation fault" try to configure it with --sct-readonly

```

./configure --disable-local-dpath --disable-chroot-support --enable-syscalls --mapfile=/boot/System.map-`uname -r` --kernelsrcdir=/usr/src/linux-headers-`uname -r` --sct-readonly

```

after that you remove:
dazuko.ko
dummy_rule
and
/lib/modules/`uname -r`/extra/dazuko.ko

and you issue again the make commands

Hope this helped someone.

---

