---
title: "ttyS0 does not start on boot up"
date: 2011-09-09
forum: Virtualisation
---

### Post by elventear on 2011-09-09
Hello,

I am trying to get the console working for a natty VM via libvirt in a maverick host.

I have followed the SerialPortHowto to enable ttyS0 on the VM. I had followed in the past for other VMs that used other versions of Ubuntu, and it worked fine.

The problem I have is that the console is being redirected correctly, but ttyS0 is not started by upstart, even though I am using the upstart script as proposed in the Howto. My VM was built with vmbuilder and it is pretty barebones, only the minimal packages. 

Has anybody run into a similar issue? Any suggested solutions to get the login prompt working via console?

Thanks!.

---

