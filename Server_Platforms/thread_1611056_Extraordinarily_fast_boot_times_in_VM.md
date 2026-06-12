---
title: "Extraordinarily fast boot times in VM"
date: 2010-11-01
forum: Server Platforms
---

### Post by eblume on 2010-11-01
At work, we use two very powerful servers to host a series of VMs to do some heavy-lifting analytical work. Part of my job has been to evaluate a variety of different virtualization environments, including changing the host OS (or dom0 kernel for Xen), changing the platform (KVM, Xen, ESXI, etc.), and changing the guest OS types.

I noticed a number of behaviors that Ubuntu exhibited that set it apart (almost always in a positive way) from the other OSes. Most astounding though was that when an Ubuntu 10.04 AMD64 server VM was booted from an Ubuntu 10.04 AMD64 server host (that is, same version of Host OS and Guest OS) in KVM, the guest boots in roughly 2 seconds. At least, the guest boots faster than the VNC connection can initialize.

I'm certainly not complaining, but I can't for the life of me figure out how this could be possible. I understand that the Upstart init daemon is very good about startup times... but still!

Is anyone else seeing similar behavior? Was this intended, or just a happy consequence of other development choices?

---

### Post by ian dobson on 2010-11-01
Hi,

Have a look at your IO speeds. My mythtv frontend boots to X in about 11 seconds including loading the frontend software from a CF card. When I tested the same configuration with a SSD the system boots in 7 seconds.

Note: The CF card reads at about 66Mbyte sec and the SSD about 200.

Maybe install bootchart to see what actually starts. Upstart does a good job at starting services in parallel, but the less upstart has to start the faster it's finished.

Regards
Ian Dobson

---

### Post by eblume on 2010-11-01
Hi Ian,

Good point! I haven't gotten the exact qualification of IO speeds on this setup, but it should be *very* fast - it's a JFS partition across about 24 RAID-6 disks. I guess in theory that could be speeding up boot times - but still, two seconds? It seems like magic is afoot!

---

