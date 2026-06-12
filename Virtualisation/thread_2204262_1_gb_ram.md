---
title: "1 gb ram"
date: 2014-02-07
forum: Virtualisation
---

### Post by pdrollins on 2014-02-07
Can I get any advice on running an Ubuntu VM with a laptop with only 1 GB of RAM? If I allocate 512MB of RAM to Ubuntu for the VMware Virtual Machine, will it still take up that RAM when the VM is closed? If so, are there any ways around this? Thanks.

---

### Post by sudodus on 2014-02-07
I think you need 2 GB RAM for a virtual machine to run well with a modern linux as well as Windows XP or newer guest system. It is probably possible to run with 1 GB RAM (to share 50% for the host and 50% for the guest). But I'm afraid you would get heavy swapping and a very slow system.

If the virtual machine is switched off, it will only occupy disk space, not any RAM. This assumes that you have a linux host system. I'm not sure how a Windows host will manage the RAM.

I would recommend a dual boot system with only 1GB RAM.

---

### Post by pdrollins on 2014-02-07
Thanks!

---

### Post by TheFu on 2014-02-09
As @sudodus says, 1G is very tight. Don't forget that the allocated RAM to the VM is not all the RAM it needs. Video-RAM and just the overhead of having a VM running eat some too.  For a WinXP client, it might be possible, but for any new Windows - forget it.  If the client VM is Linux, then you can make it work, provided it is a lighter distro - something like Puppy, DSL, or TinyCore should work. Don't expect a full-Ubuntu desktop to work.  

Don't know what hardware you are on, but CPU type and performance also matters.  The best answer is to get a Core2Duo CPU and 2G of RAM as a minimal VM platform to start.

If you can, getting to 2G of RAM should cost less than $40.

Oh ---- any VMware makes 6 different virtualization products. Which were you looking at using?

---

