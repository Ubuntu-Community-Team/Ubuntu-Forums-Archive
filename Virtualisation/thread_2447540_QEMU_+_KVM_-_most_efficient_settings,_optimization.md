---
title: "QEMU + KVM - most efficient settings, optimizations?"
date: 2020-07-21
forum: Virtualisation
---

### Post by glorsh66 on 2020-07-21
[COLOR=#242729][FONT=Arial]uys I am quite new to QEMU + KVM stack, so my questions may seem stupid for someone more experienced, But I have honestly tried to search all of this online, and most of the articles that I found were about initial configuration, not about fine tuning for getting maximum performance.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What are the most efficient settings to set up the VM hypervisor? My guess is that for disk devices and network cards the best is way to set Virtio type and install corresponding drivers on the client OS?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What about CPU? Is this line necessarily? Will it be better just to delete all of this  <model fallback='allow'>Skylake-Client</model> and get QEMU virtual CPU? Does it simply create additional level of virtualization with obvious performance losses?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What exactly placement='static' does?
[FONT=Consolas]
[/FONT]```

[FONT=Consolas]<vcpu placement='static'>1</vcpu>[/FONT]
```[/FONT][/COLOR]```

[COLOR=#242729][FONT=Arial][FONT=Consolas]  <cpu mode='custom' match='exact'>[/FONT][/FONT][/COLOR]
    <model fallback='allow'>Skylake-Client</model> [COLOR=#242729][FONT=Arial][FONT=Consolas]</cpu>
[/FONT][/FONT][/COLOR]
```
[COLOR=#242729][FONT=Arial][FONT=Consolas]

[/FONT]What is the best way to run multiple cores (Not sockets) for windows clients? Because, as we all will know desktop versions of windows operation system could not work with more that 2 cpu sockets! Will that be enough? Won't I eventually run out of the "real" cores on the host PC?[FONT=Consolas]

[/FONT][FONT=Consolas]

<vcpu>4</vcpu>
[/FONT][FONT=Consolas] <cpu>
[/FONT]<topology sockets='1' cores='4' threads='1'/>
[FONT=Consolas]</cpu>
[/FONT][FONT=Consolas]

[/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]is it really beneficial for some really demanding task to configure passtrough?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Are there any additional secrets how to configure my virtual machines in more efficient way?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Has "Ballooning" feature ever been properly implemented? Or it in the test state? So my virtual machines will consume exactly of amount of memory allocated to them nothing more nothing less?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What is the difference between these two lines? Is it somehow related to the "Ballooning" feature?
[/FONT][/COLOR]
```
<memory unit='KiB'>2097152</memory>
<currentMemory unit='KiB'>2097152</currentMemory>
```

---

### Post by TheFu on 2020-07-21
What is the workload?  Tuning will completely depend on that.
Most of the tuning begins by not over subscribing VMs to hardware and sharing the system resources between all the running VMs.  In general, I give a VM 1 vCPU and 1GB of RAM, then adjust up/down based on the proven workload and RAM needs.  For Windows, I give 2 vCPUs because they still install a different kernel for single vCPU vs multi-vCPU systems.  Reinstalling Windows is something I avoid. Actually, I avoid touching Windows as much as possible.

I can't imagine needing to provide 4 vCPUs for a Windows machine.  Talk about bloat.  But only you know the workload. I might provide 4vCPUs for a Geo-spatial DBMS.

Kernel.org and [https://www.linux-kvm.org/page/Tuning_KVM](https://www.linux-kvm.org/page/Tuning_KVM) have all that is published from those teams.  Redhat has a bunch. Storage architecture choices matter the most and are the hardest to change, so get the correct storage architecture for your needs first and avoid all file-based VM storage.

Best not to force a specific CPU model. You'll forget that it was done and when you move to something different, it won't boot. I've never noticed the difference.

Windows is a hog.  Only run Windows if there isn't any other choice. I routinely find my single Windows VM using all the CPU allocated for no reason.  GPU passthru only matters if the workload is GPU-based.  Doing that would be stupid outside a home system for a gamer.  If you need GPU performance, run on the real hardware.

I've never used balloon memory. Never saw the point in my world. Doubled the RAM on my main VM host last month after it started getting close to fully used. No*w* 50% of the system RAM is used for network and disk buffers.  ;(

Most of the time, my VM host, running 10 VMs, is nearly idle. It was a $430 machine - total cost.  I have friends with $7K monster Dell servers with 32 vCPUs and 256G of RAM. From what I've seen, my little box would handle their workloads fine. *My newer CPUs are almost as fast as their Xeon CPUs from 7 yrs ago. Of course, I don't have server PSUs or multiple server back plains for different PCIe adapters, or ECC RAM, but 2 x $430 is pretty cost efficient should 100% redundancy ever become necessary.  Plus, my systems are nearly silent and use under 100W of power most of the time even including external storage arrays. Of course, when the workload spikes, all the cores become full powered and whatever is needed gets handled PDQ (Barney Fife voice). ;)*

---

### Post by glorsh66 on 2020-07-22
Sadly - my workload will consist mostly of Windows virtual machines. 

Btw - I have noticed a difference between 

<model fallback='allow'>Skylake-Client</model> </cpu>

and without explicit definition of the CPU model.


In case if you don't define cpu model explicitly - CPU-Z considers it to be pentium 2 CPU. And it obviously have limited set of CPU instructions.
If you define it like a Skylake-Client (It was a default setting in my case by some reason) - it has much more available CPU Instructions.
Don't know if it somehow affects the performance though..

---

