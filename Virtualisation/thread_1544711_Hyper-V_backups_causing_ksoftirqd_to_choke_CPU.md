---
title: "Hyper-V backups causing ksoftirqd to choke CPU"
date: 2010-08-02
forum: Virtualisation
---

### Post by doctorjbeam on 2010-08-02
Hi everyone,

I've done a few Google and in-forum searches but I've come up dry, and I can't be the only one in the world with this problem...

A bit of background: we are in the process of migrating our old and cobbled-together servers to a Hyper-V platform running ontop of Server 2008 R2, and during the testing process I've noticed that whenever the built in Windows backups try to back up the Hyper-V VHD files ksoftirqd starts to choke up the CPU. 

Yes, I'm aware that Ubuntu is not supported on Hyper-V. Yes, I have tried installing the Linux Integration Components but that failed - can supply the error logs if required. When it comes to make and gcc I'm way out of my depth. 

Can anyone provide some insight? What does ksoftirqd do, why would pausing and resuming the VM cause it to freak out, and can anything short of no backups or scheduled reboots be done to fix it?

Changing host OS or hypervisor is not an option. We are a government school and do not have the funds :)

Thanks :)
Michael.

---

### Post by sh1ny on 2010-08-03
You can always use KVM instead of Hyper-V - no funds required.
I do exactly that for backups with kvm ->

1. pause vms
2. make lvm snapshot
3. resume vms
4. mount snapshot and backup images
5. destroy snapshot

All for free and supported :D

---

