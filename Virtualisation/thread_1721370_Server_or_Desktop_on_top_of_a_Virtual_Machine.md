---
title: "Server or Desktop on top of a Virtual Machine?"
date: 2011-04-04
forum: Virtualisation
---

### Post by Amit Miller on 2011-04-04
Hi everyone,

I have access to several unused Windows machine. Want to utilize their cpus.

The plan is to install VirtualBox VM and then 64bit Ubuntu on top. 
I am trying to arrange "compute servers" --
* a machine that will run my own code [scientific stuff I code]
* need to access it from afar, via ssh, to start jobs and then process/collect data


I wonder if the guest OS [the "compute server"] should be desktop or server version? 
- I have no need for a GUI in this setup, but are there some differences with the kernel? what are their implications?
- do I need "virtual kernels", are these installed automatically, or what?


I am experienced only with the standard desktop Ubuntu, which I use daily.


Many thanks,
AM

---

### Post by CharlesA on 2011-04-04
I haven't seen any real difference between the "virtual kernel" and the regular kernel.

If you don't need a GUI and feel comfortable using something like SSH, I'd say install Ubuntu server.

---

