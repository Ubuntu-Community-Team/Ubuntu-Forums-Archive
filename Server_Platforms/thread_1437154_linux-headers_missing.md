---
title: "linux-headers missing?"
date: 2010-03-23
forum: Server Platforms
---

### Post by Jimoid on 2010-03-23
Hi there,

I have installed 8.04 as a VM using VirtualBox and now want to install the guest additions. In order to install it I need to have the kernel header installed as it will be used for compiling a kernel module against.

I can't find the header however. Can someone tell me where it is or how to install it?


```

jimmy@mail2:~$ uname -r
2.6.24-23-server
jimmy@mail2:~$ dpkg --get-selections | grep linux
libselinux1					install
linux-headers-2.6.24-16				install
linux-image-2.6.24-23-server			install
linux-image-server				install
linux-libc-dev					install
linux-server					install
linux-ubuntu-modules-2.6.24-23-server		install
util-linux					install
util-linux-locales				install
jimmy@mail2:~$ sudo apt-get install linux-headers
[sudo] password for jimmy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.24-27-xen 2.6.24-27.68
  linux-headers-2.6.24-27-virtual 2.6.24-27.68
  linux-headers-2.6.24-27-server 2.6.24-27.68
  linux-headers-2.6.24-27-rt 2.6.24-27.68
  linux-headers-2.6.24-27-openvz 2.6.24-27.68
  linux-headers-2.6.24-27-generic 2.6.24-27.68
  linux-headers-2.6.24-27-386 2.6.24-27.68
  linux-headers-2.6.24-27 2.6.24-27.68
  linux-headers-2.6.24-26-xen 2.6.24-26.64
  linux-headers-2.6.24-26-virtual 2.6.24-26.64
  linux-headers-2.6.24-26-server 2.6.24-26.64
  linux-headers-2.6.24-26-rt 2.6.24-26.64
  linux-headers-2.6.24-26-openvz 2.6.24-26.64
  linux-headers-2.6.24-26-generic 2.6.24-26.64
  linux-headers-2.6.24-26-386 2.6.24-26.64
  linux-headers-2.6.24-26 2.6.24-26.64
  linux-headers-2.6.24-25-xen 2.6.24-25.63
  linux-headers-2.6.24-25-virtual 2.6.24-25.63
  linux-headers-2.6.24-25-server 2.6.24-25.63
  linux-headers-2.6.24-25-rt 2.6.24-25.63
  linux-headers-2.6.24-25-openvz 2.6.24-25.63
  linux-headers-2.6.24-25-generic 2.6.24-25.63
  linux-headers-2.6.24-25-386 2.6.24-25.63
  linux-headers-2.6.24-25 2.6.24-25.63
  linux-headers-2.6.24-24-xen 2.6.24-24.61
  linux-headers-2.6.24-24-virtual 2.6.24-24.61
  linux-headers-2.6.24-24-server 2.6.24-24.61
  linux-headers-2.6.24-24-rt 2.6.24-24.61
  linux-headers-2.6.24-24-openvz 2.6.24-24.61
  linux-headers-2.6.24-24-generic 2.6.24-24.61
  linux-headers-2.6.24-24-386 2.6.24-24.61
  linux-headers-2.6.24-24 2.6.24-24.61
  linux-headers-2.6.24-16-xen 2.6.24-16.30
  linux-headers-2.6.24-16-virtual 2.6.24-16.30
  linux-headers-2.6.24-16-server 2.6.24-16.30
  linux-headers-2.6.24-16-rt 2.6.24-16.30
  linux-headers-2.6.24-16-openvz 2.6.24-16.30
  linux-headers-2.6.24-16-generic 2.6.24-16.30
  linux-headers-2.6.24-16-386 2.6.24-16.30
  linux-headers-2.6.24-16 2.6.24-16.30
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
jimmy@mail2:~$

```

---

### Post by KB1JWQ on 2010-03-23
It should match the output of uname -a.  That'll give you a kernel string to target.

If the headers don't match your running kernel, you wind up in an interesting place. :-)

---

### Post by Jimoid on 2010-03-23
In my original post I gave the output of uname -r, and a list of the available headers, none of which match my kernel :-(

---

### Post by KB1JWQ on 2010-03-23
Could be out of date.  What's the most recent kernel you have installed?  You have to reboot to use the new one, and I *think* you're a rev or two behind?

---

### Post by Jimoid on 2010-03-23
I have run update then upgrade and rebooted the system to run a new kernel.

---

