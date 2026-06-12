---
title: "About cpu option on vmbuilder - KVM"
date: 2009-05-30
forum: Virtualisation
---

### Post by satimis on 2009-05-30
Hi folks,

On reading the help manual```

# vmbuilder kvm ubuntu --help

```

There is an option;```

--cpus=CPUS

```
Number of virtual CPU's. [default: 1]

If the PC runs a dual core (2X) cpu whether entering```

--cpus=2

```

For 4X (quadcore)```

--cpus=4

```

TIA

B.R.
satimis

---

### Post by veloce on 2009-06-01
Sorry, what is the question?

---

### Post by satimis on 2009-06-01
> **veloce said:**
> Sorry, what is the question?
Hi veloco,

On running the command```

vmbuilder kvm ubuntu --suite=intrepid --flavour=virtual --arch=i386 --mirror=http://192.168.0.10:9999/ubuntu -o --libvirt=qemu:///system --tmpfs=- --ip=192.168.0.11 --part=vmbuilder.partition --templates=mytemplates --user=admin --name=Admin --pass=apassword --addpkg=vim-nox --addpkg=unattended-upgrades --addpkg=acpid --firstboot=boot.sh --mem=256 --hostname=vm1 --bridge=br0

```
whether adding the option;
--cpus=2 (for dualcore CPU)

and

--cups=4 (for quadcore CPU)
?

Default is --cpus=1

Thanks


B.R.
satimis

---

### Post by veloce on 2009-06-02
I'm still not sure I understand the question, it sounds like you are confusing cores in the host with cores in the vm.  If I'm wrong then this answer will be no help:

The command is to do with the number of cores you wish to assign to the vm not the number (or arrangement) of cores within the host.

The number of cores that you assign to the virtual machine is independent of the number of cores in the host machine (except that there is little point making the vm have more cores than the host - so some systems disallow that option).

So on a machine with 4 cores (whether that's 4 individual or 2 times 2 core or 1 times quad core ...) you can assign 1,2,3 or 4 cores to the vm.

I would be wary of allocating all of the cores to the vm particularly if you will be running more than one vm.

Further, if your vm will run windows XP then you may get best performance from just assigning one core.  The host will break up the vm's load into multiple threads anyway and linux handles SMP much much better than windows.

---

### Post by satimis on 2009-06-02
> **veloce said:**
> I'm still not sure I understand the question, it sounds like you are confusing cores in the host with cores in the vm.  If I'm wrong then this answer will be no help:
Hi veloce,

You're right.  Before reading your previous posting I was confused with cores in host, i.e. cores in the CPU of PC.  I thought on a quadcore PC that each time creating a new VM, the guest, I have to select "--cpus=4" and to select "--cups=2" on a dualcore PC.


> 
The command is to do with the number of cores you wish to assign to the vm not the number (or arrangement) of cores within the host.

The number of cores that you assign to the virtual machine is independent of the number of cores in the host machine (except that there is little point making the vm have more cores than the host - so some systems disallow that option).

So on a machine with 4 cores (whether that's 4 individual or 2 times 2 core or 1 times quad core ...) you can assign 1,2,3 or 4 cores to the vm.

I would be wary of allocating all of the cores to the vm particularly if you will be running more than one vm.

If I understand your advice correctly, to Linux VM I can assign "--cpus=1/2/3/4" (a quadcore PC or a 2x2 dualcore PC) on building a new VM.  If there are 4 Linux VMs each allotted with "--cpus=1" then I can't build a 5th VM.  Because there will be no more core available.  If I'm wrong please correct me.  Thanks.


> 
Further, if your vm will run windows XP then you may get best performance from just assigning one core.  The host will break up the vm's load into multiple threads anyway and linux handles SMP much much better than windows.
That mean that specific core will be exclusively used by Windows XP only?  Same principle will be applied to Windows server 7/8


B.R.
satimis

---

### Post by veloce on 2009-06-03
> **satimis said:**
> 
If I'm wrong please correct me.  Thanks.
B.R.
satimis

Correcting as requested: :)  

You can run as many virtual cores as you want.  They don't get exclusive access to any of the physical cores.

For example, I have six vms running on a quad core machine. For a while one of them was a dual core vm so that was seven virtual cores on the four core machine.  

Watching the output of "htop" I could see several processes for each vm and the host would run them, together with the other system processes, on which ever core it chose.  In fact, a vm working hard on a particular task would take one core to 100% then it would shift to take a different core to 100% while releasing the first one.  

There may be some advantage with a linux vm to giving it multiple cores.  The vm will attempt to break up it's processes and assign them to virtual cores.  This may allow the host to allocate processes over cores easier.  However, it does mean twice the SMP overheads.  The windows overhead means it's not worth it for windows vms.

---

