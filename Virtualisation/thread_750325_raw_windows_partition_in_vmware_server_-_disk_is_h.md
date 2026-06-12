---
title: "raw windows partition in vmware server - disk is horribly slow"
date: 2008-04-09
forum: Virtualisation
---

### Post by ittayd on 2008-04-09
Hi,

I'm using vmware server from the ubuntu partner repo. I created a VM that uses a raw partition with a pre-installed windows.

Everything works, but the VM's disk performance is horrible. It takes it 15 minutest to boot. 

I tried googling, and found nothing, so I'm seeking help here.

System: Thinkpad T61, ubuntu 7.10, windows xp sp2. Disk is SATA.

Note: ubuntu treats the disk as scsi, but in the vmdk it is set up as IDE. The reason is that this is how it is created when creating it from the windows OS (booting it natively, installing vmware server, creating VM using partitions). If I create the vmdk from ubuntu, the disk is iscsi, but windows refuses to boot with 'disk read error' message.

I'd appreciate any help and would love to provide additional information.

---

### Post by lofftjm on 2008-04-09
All I can add is that I am seeing awful vmware performance lately as well.  I am not using a raw device but any type of operations (staring Internet Explorer for instance) in the vm causes massive disk I/O.  Operations  in the host (Ubuntu) does not cause this type of disk I/O.

---

### Post by ittayd on 2008-04-09
lofftjm:
i saw some suggestions to add these settings to the vmx:
mainMem.useNamedFile="FALSE"
sched.mem.pshare.enable="FALSE"
MemTrimRate=0

tried it, can't say it helped much.
mainMem.useNamedFile="FALSE"
sched.mem.pshare.enable="FALSE"
MemTrimRate=0

everybody else:
can this be related to cpu scaling? my windows is booting and yet the cpu stays 800Mhz most of the time (it is 2.4 core 2 duo)

---

### Post by fjgaude on 2008-04-09
Performance is greatly improved believe it or not by declaring only one core when you setup the VM. You can do this now by exiting the VM and then going to its Settings, Processors... Make it one only.

---

