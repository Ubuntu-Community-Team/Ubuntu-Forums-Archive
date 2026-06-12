---
title: "VMWare server is going really really slow"
date: 2008-09-25
forum: Virtualisation
---

### Post by hofa on 2008-09-25
I am running VMWare server 1.0.7 (primarily for school)
But VM's run reaaaaally slow and it's just nog workable. Base installation of Debian takes half an hour to boot...

Anyone have the solution for this?

---

### Post by hofa on 2008-09-25
I couldn't solve the problem.
I heard the problem exists in the fact that a module for using multicore cpu's has been removed in the 2.6 kernel (It had problems with lock-ups...).

The problem is fixed in VMWare Server 2.0 (beta)

---

### Post by fjgaude on 2008-09-25
Are you using 2.0 now? Is the problem with multiple cores fixed?

---

### Post by trmentry on 2008-09-26
> **hofa said:**
> I couldn't solve the problem.
I heard the problem exists in the fact that a module for using multicore cpu's has been removed in the 2.6 kernel (It had problems with lock-ups...).

The problem is fixed in VMWare Server 2.0 (beta)

can you post more info on this?

I was running 1.0.7 for over a year on a dual core proc with no issues.  i just installed 2.0 on a dual core proc server and not having any issues... yet. :/

---

### Post by veloce on 2008-09-27
The problem is with running dual core vms.  This is particularly true where windows is the host.  

I understood it was more an issue with windows that with vmware but I could be wrong.  Windows is not very good at smp.

On the other hand, using a dual core as host running Ubuntu is much more efficient.

---

### Post by fjgaude on 2008-09-27
If the multi-core issue is truly fixed in 2.0 VMware server, that's enough reason to change over.

---

### Post by daduNo1 on 2008-09-27
I am running VMWare 2 with Ubuntu 8.04 with Cor2Q and VMware is very Very slow just like unusable I am using 2 cup for my Vm machine running XP

---

### Post by fjgaude on 2008-09-27
> **daduNo1 said:**
> I am running VMWare 2 with Ubuntu 8.04 with Cor2Q and VMware is very Very slow just like unusable I am using 2 cup for my Vm machine running XP

You are using 2 cores... don't understand?

---

### Post by hofa on 2008-10-11
Sorry for not responding, I lost sight of this topic...

vmware 2.0 is working like a charm on Ubuntu 8.04 here

---

### Post by fjgaude on 2008-10-11
Are you using one or more cores? Seems that anything more than one core causes VMware to run slowly.

---

### Post by hofa on 2008-10-14
Hmmm I think I'm using Win2k3 server on dual core (in a VM of course)...

---

### Post by fjgaude on 2008-10-14
Using the Settings, with the VM powered off, you can set the CPU to one core... that makes the VM run fast, quick.

---

