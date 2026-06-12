---
title: "Run separate instances of linux for each socket (quad socket mobo)"
date: 2019-01-12
forum: Virtualisation
---

### Post by ragnarr2 on 2019-01-12
Hello everyone, I have a particular configuration that needs to run separate instances of linux for maximum efficiency ... A friend told me it could be done by
VM, but it's not easy, so I asked here ... I hope it's possible, thanks

---

### Post by TheFu on 2019-01-12
Yes. It is possible.
You can use Xen, KVM, Virtualbox, Docker, lxc, lxd, or just use 1 OS install with each of the different services listening on different ports. 

The linux kernel does a good job of multi-tasking across different CPUs.
There ARE very good reasons to run separate instances of the OS, efficiency isn't one.
Maintainability is one reason. Keeping separate services separate simplifies maintenance work and makes interactions between different components separate.  Compartmentalized services is a good thing, based on the risks for each service involved. For example, don't run an email gateway on the same equipment that is used for authentication or DHCP or DNS.  Don't run anything else on a php web-app server.  Php web-apps are extremely high risk services, extremely.

If you can, use lxd for the lightest overhead, but the container should only run 1 service and not be treated like an OS. No shell or general purpose tools should be installed inside the container. The best practice for containers is to rebuild them if you need to make any changes. There are build tools and scaling tools to bring up more services as demand requires.  Docker is very popular and not Ubuntu specific.  LXD is Ubuntu specific, a little better with security and a little more flexible for people new to containers.  Containers aren't virtualization, but from a logical view, they seem similar.

If you want separate full OS installs, then KVM is the most efficient and well supported hypervisor.  It is better than the commercial offerings if you need less than 50 VMs.  I use KVM to run 10-20 servers on each physical machine. I started with VMware Workstation in the 1990s, moved to virtualbox, then to Xen and finally ended up with KVM+qemu.  Did other hypervisors on other platforms - nPARs, vPARs on HP-UX, LPARs on AIX and both domains and zones on Solaris.

Linux containers have about 10x less overhead than full VMs, but they are fairly new in production use and most people haven't learned how to properly secure containers.  It takes a different way of deploying software stacks to properly secure linux containers.

Anyway, those "buzzwords" should get you started. Good luck.

---

### Post by ragnarr2 on 2019-01-14
> **TheFu said:**
> Yes. It is possible.
You can use Xen, KVM, Virtualbox, Docker, lxc, lxd, or just use 1 OS install with each of the different services listening on different ports. 

The linux kernel does a good job of multi-tasking across different CPUs.
There ARE very good reasons to run separate instances of the OS, efficiency isn't one.
Maintainability is one reason. Keeping separate services separate simplifies maintenance work and makes interactions between different components separate.  Compartmentalized services is a good thing, based on the risks for each service involved. For example, don't run an email gateway on the same equipment that is used for authentication or DHCP or DNS.  Don't run anything else on a php web-app server.  Php web-apps are extremely high risk services, extremely.

If you can, use lxd for the lightest overhead, but the container should only run 1 service and not be treated like an OS. No shell or general purpose tools should be installed inside the container. The best practice for containers is to rebuild them if you need to make any changes. There are build tools and scaling tools to bring up more services as demand requires.  Docker is very popular and not Ubuntu specific.  LXD is Ubuntu specific, a little better with security and a little more flexible for people new to containers.  Containers aren't virtualization, but from a logical view, they seem similar.

If you want separate full OS installs, then KVM is the most efficient and well supported hypervisor.  It is better than the commercial offerings if you need less than 50 VMs.  I use KVM to run 10-20 servers on each physical machine. I started with VMware Workstation in the 1990s, moved to virtualbox, then to Xen and finally ended up with KVM+qemu.  Did other hypervisors on other platforms - nPARs, vPARs on HP-UX, LPARs on AIX and both domains and zones on Solaris.

Linux containers have about 10x less overhead than full VMs, but they are fairly new in production use and most people haven't learned how to properly secure containers.  It takes a different way of deploying software stacks to properly secure linux containers.

Anyway, those "buzzwords" should get you started. Good luck.

What i need is the best option for assign a specific cpu for linux instance,like real separate PCs..for example cpu1 on the first cpu2 on second and so on (i mean real cpu not virtual)..i'm quite new to linux so even the simplicity is an non trascurabile factor...if you can provide me one more advice i appreciate it...thank you

---

