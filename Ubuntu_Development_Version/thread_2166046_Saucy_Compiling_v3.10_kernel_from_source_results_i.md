---
title: "Saucy: Compiling v3.10 kernel from source results in black screen after boot"
date: 2013-08-07
forum: Ubuntu Development Version
---

### Post by sgehlich on 2013-08-07
Hey,

I just compiled a kernel for the first time, but after the ubuntu loading screen disappeared, the screen stays black. I can hear the login screen's sound though.
Basically I was trying to compile the following build from scratch: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/)

Here's how I compiled the kernel:

```
$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-saucy.git

# The BUILD.LOG tells me that it was compiled from Ubuntu-3.10.0-0.7
$ git checkout Ubuntu-3.10.0-0.7

# I want my current (3.8.0-19-generic) configuration
$ cp /boot/config-`uname -r` .config
$ make oldconfig

$ fakeroot make-kpkg --initrd --append-to-version=-sash kernel_image kernel_headers

# Install the kernel
$ cd ..
$ sudo dpkg -i linux*sash*.deb

# Update grub
$ sudo update-grub
$ sudo shutdown -r 0
```

What am I doing wrong?

---

