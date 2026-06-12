---
title: "Adding TCP Illinois to the kernel"
date: 2013-01-15
forum: Ubuntu Dev Link Forum
---

### Post by sholex on 2013-01-15
Hi,

I am exploring TCP Congestion Control algorithms and I want to add TCP Illinois to my kernel so I can test it.

Any idea how? I have never compiled kernel or added custom module. I use Ubuntu 12.04 with kernel 3.x.x.

Here is the source for TCP Illinois and others,

[www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/net/ipv4]("www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/net/ipv4")

Thanks

---

### Post by tgalati4 on 2013-01-15
First issue is that the source code is for kernel 2.6.31, so one would expect breakage trying to use this module with a newer kernel.  Either find an older version of Ubuntu to install or do some more digging to find a similar package for the 12.04 kernel.

I found this package under 12.10 (which is what I'm running) and it may be related to what you are trying to accomplish.  

kernel-patch-wrr - Extension to traffic Control/network bandwidth management

There is an Ubuntu wiki (sorry I don't have the link handy) for configuring and compiling your own kernel.  It's not difficult, but it takes 2 to 3 hours.  When you are done, you may or may not have a working kernel, but it's an interesting process to go through.

As far as compiling, you download the code to a local working directory:

```
 sudo apt-get install build-essential 
./configure
make
sudo make install


```

You may have to install header files and some development files, the configuration will alert you what is missing.

In this case, you are replacing an existing ipv4 driver with a new driver with traffic control capabilities.  I don't know enough about this ipv4 driver to know what kernel switches are needed--I assume Kconfig will list them in the kernel configurator.

But I would first do some more digging in the existing 12.04 distribution to see if there are some ready-made packages that you can install without a kernel recompile.

If this is for home-use, Quality-of-Service, then you might be better served buying a supported router and installing wrt-dd firmware and using the QoS capabilities of the router than dedicating a PC for routing.

Google is your friend:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

---

