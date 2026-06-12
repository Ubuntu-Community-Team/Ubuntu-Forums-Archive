---
title: "Help with Running VMware Player... installed fine, can't get it to run"
date: 2010-06-16
forum: Virtualisation
---

### Post by steven.smith on 2010-06-16
Hi all! I ran into a problem with VMware that is frustrating for me.

I run Ubuntu 9.04 Jaunty Jackalope. I wanted to use a virtual machine using VMware, so I installed VMware Player on my machine. Everything installed fine, however when I open up the application a problem occurs. It first comes up with a message saying "Your kernel was compiled with gcc version 4.1.3 while the version located is 4.3.3. Compiling kernel modules with this version is not recommended..." 

So I continue on anyways and the next message that occurs is "C header files matching your running kernel were not found." 

I press ok, then the next message occurs "before you can run VMware several modules must be compiled and loaded into the running kernel. {Kernel headers 2.6.26-2-openvz-amd64}. Kernel headers for version 2.6.... were not found. If you installed them in a non-default path you can specifiy the path below...."

So then it asks me for the location, and this is where I get stuck. I try browsing to Usr/Src/(kernel).../include but that doesn't work. I've also tried lib/modules/(kernel).../include and that doesn't work either. I've already tried to update the kernel by using the terminal. 

I've tried "apt-get install build-essential linux-headers-`uname -r`" and come up with "build-essential is already the newest version.
E: Couldn't find package linux-headers-2.6.26-2-openvz-amd64"

I've seen other topics with the same problem, but none of the solutions have worked for me.

One of the things I haven't tried is installed an older version of Vmware Player, however ubuntu forums tutorial for installing VMware player for 9.04 says to install the _latest_ version, so I'm not quite sure what to do.

Any help would be much appreciated.

---

