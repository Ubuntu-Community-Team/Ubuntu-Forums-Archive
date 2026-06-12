---
title: "More memory used on a bigger server"
date: 2014-07-08
forum: Server Platforms
---

### Post by james.w.krych on 2014-07-08
Hello,

I am running Ubuntu Server 14.04 as a headless VirtualBox server-with Apache and phpVirtualBox. Part of my learning curve was to run this on a VM under VirtualBox and then on real hardware. The first real hardware was an HP workstation (Core i5) with four total cores and 16GB of memory. Initial overhead after install was about 170MB with an extra 250MB of memory used once VirtualBox was running. Hard drive space was 512GB.

After having learned from that, I got real server hardware to work with. These are Dell R610 servers with dual 6-core CPUs (24 total cores to utilize) and 96GB of memory and 1-2 TB of hard drive space depending on my RAID configuration. After install, I have found that my overhead is now ~800MB and just over 1GB with VirtualBox running. 

I have noticed that when being installed on "real" server CPUs the throttling is not loaded and the CPUs run at full speed. For those who want it, I have created a "Grand system speed script" (Gsss.sh) that checks for root, cleans the cache, finds out what CPU you have and its current and maximum speed, finds out how many cores you have, and then uses that number in a loop to set all CPUs to performance-if the throttling has been loaded. 

Is it possible when the installation is being run that Ubuntu Server will recognize real server CPU's and resources and then once loaded, run with greater initial usage as compared to running on a machine with lesser resources? 

Regards,

James

---

### Post by TheFu on 2014-07-08
Don't use virtualbox for stuff like this. Use Xen or KVM.  Please.  virtualbox is great for desktop virtualization, not so much for servers.  Review the SPEC-Virt stats to see what I mean.

RAM can be used for programs or for buffers.  Unused RAM is a waste, so when RAM is used for buffers, that is a good thing and speeds up the system.  When programs need more RAM, the buffers are cleared. It is good. The system will use RAM in this way, as needed.

To really know what is happening on a server, start doing performance monitoring.

---

### Post by CharlesA on 2014-07-08
Sweet cripes, that's a beefy machine! I thought my i7 with 16GB of RAM was a beefy machine...

FWIW, I used to run VirtualBox with phpvirtualbox a long time ago, but I've migrated to KVM/OVZ now. OVZ only exists as a test bed for me.

I've got a whole 3 VMs running atm:

```
free -m
             total       used       free     shared    buffers     cached
Mem:         15899      12721       3178          0        831       4190
-/+ buffers/cache:       7699       8200
Swap:        19322        168      19154

```

4GB of that is VM memory usage but the box itself has been up for a long while. :)

---

### Post by TheFu on 2014-07-09
Here's a C2D with a few actively used KVM VMs running. These run 24/7/365 except approved maintenance periods weekly for patching and daily backups. 

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          7920       7235        685          0        232        414
-/+ buffers/cache:       6588       1331
Swap:         8123         47       8076
$ virsh list
 Id Name                 State
----------------------------------
  1 redmine              running
  2 zcs43                running
  3 xen41                running
  4 spammer              running
  5 lubuntu              running
  6 ubudesk              running

```
Big servers aren't needed always. This isn't the slowest machine here and there are 3 others running a similar number of VMs each for different clients. The server VMs are tuned so that no swap is provided. The remote desktops have swap, since humans aren't as predictable. ;)

These aren't Windows VMs, so they don't need huge resource allocations. Half the VMs are less than 1G of RAM. It is the desktops and Zimbra that need more.

Of course, none of this helps determine virtualbox overhead. Sorry.

---

### Post by james.w.krych on 2014-07-09
Thanks for the responses.

It's not so much the VirtualBox overhead-that is a given. I am just curious as to why with the exact same set of software loaded, a "real" server will have twice the overhead.

I need these as I am running Oracle appliances on one server and Oracle Vision instances on the other server. 

I am aware of KVM and Xen-Oracle has the Oracle VM Server which is their re-branded XEN hypervisor with a web gui. I am simply running VirtualBox in a headless setup as my import of the appliances and instances was made that much easier.

Best,

James

---

### Post by TheFu on 2014-07-09
You could ask Oracle if you need a real answer. You are running their complete stack, except the hardware.

I'd guess that because the new machine is more than twice the size of the test machine. Managing the CPU sharing, cache swap, RAM, I/O sharing and disk all take more.  Plus when a VM host sees all those resources, I wouldn't be surprised that it sets up for highest performance, even if that wastes RAM.  Then there is the question about virtualbox - was it designed to run on larger hardware?  Sure, it CAN, but how many people do that relative to using other methods?

Is 1G of RAM out of 96G really that much?

---

### Post by james.w.krych on 2014-07-09
Oh no-it's not and I am not really complaining. I was just very curious.

The main difference I have noticed with running Ubuntu Server on a workstation compared to a real server is that the throttling is not loaded on the Dell R610 setup. It's no big deal as that makes life easier as all cores are running at maximum speed. You have probably guessed the reason as I have come to the conclusion of what is going on. Remember, both setups-workstation and Dell R610-have the exact same software installed and nothing more. When VirtualBox is running (but no VM's running) the overhead on the workstation is ~450MB and the R610 has ~1GB. I have noticed that the R610 server does have nearly twice the processes running. A ps -el | wc -l results in 135 on the workstation and 336 on the Dell R610.

TheFlu, that is probably the best reason-thanks!

Regards,

James

---

### Post by TheFu on 2014-07-09
In recent years, workstation CPUs have tried to be more energy efficient.  That means running slower unless the workload demands full speed. It also means shutting down cores unless they are needed.  Saving power is important to desktop CPUs. Could that be happening?
[https://en.wikipedia.org/wiki/SpeedStep](https://en.wikipedia.org/wiki/SpeedStep)

---

### Post by Gyokuro on 2014-07-09
Hi

I suggest you to go with KVM due most people either use VMware or KVM and in case you are intested in KVM I suggest to read RedHat's Virtualization Tuning Optimization Guide ([https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html-single/Virtualization_Tuning_and_Optimization_Guide/index.html#sect-Virtualization_Tuning_Optimization_Guide-Memory-Huge_Pages](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html-single/Virtualization_Tuning_and_Optimization_Guide/index.html#sect-Virtualization_Tuning_Optimization_Guide-Memory-Huge_Pages)) it's the best documentation concerning KVM.

- HTH

---

### Post by lukeiamyourfather on 2014-07-09
My guess is the system is probably being more aggressive with the buffer cache. I just checked a file server here with 128GB of memory and more than 100GB of that memory is being used for the buffer cache. Like already pointed out this is not a bad thing. If applications need more memory the buffer cache will get tossed. You can look at specifics of the memory usage with top or other resource monitors.

---

### Post by TheFu on 2014-07-09
Was doing to reading on tuning VM servers (I'm sick that way) and came across this [http://lwn.net/Articles/376606/](http://lwn.net/Articles/376606/) on using hugepages as a way to lower the overhead on servers with lots and lots of RAM.

---

### Post by james.w.krych on 2014-07-10
> **TheFu said:**
> In recent years, workstation CPUs have tried to be more energy efficient.  That means running slower unless the workload demands full speed. It also means shutting down cores unless they are needed.  Saving power is important to desktop CPUs. Could that be happening?
[https://en.wikipedia.org/wiki/SpeedStep](https://en.wikipedia.org/wiki/SpeedStep)

That may very well be the case with an install on desktop or mobile CPU's. 

Best,

James

---

### Post by james.w.krych on 2014-07-10
> **lukeiamyourfather said:**
> My guess is the system is probably being more aggressive with the buffer cache. I just checked a file server here with 128GB of memory and more than 100GB of that memory is being used for the buffer cache. Like already pointed out this is not a bad thing. If applications need more memory the buffer cache will get tossed. You can look at specifics of the memory usage with top or other resource monitors.

That and The Flu's answer probably make the most sense!

Thanks!

---

### Post by james.w.krych on 2014-07-10
> **Gyokuro said:**
> Hi

I suggest you to go with KVM due most people either use VMware or KVM and in case you are intested in KVM I suggest to read RedHat's Virtualization Tuning Optimization Guide ([https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html-single/Virtualization_Tuning_and_Optimization_Guide/index.html#sect-Virtualization_Tuning_Optimization_Guide-Memory-Huge_Pages](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html-single/Virtualization_Tuning_and_Optimization_Guide/index.html#sect-Virtualization_Tuning_Optimization_Guide-Memory-Huge_Pages)) it's the best documentation concerning KVM.

- HTH

Oh I understand. However, sometimes the best solution is the easiest one. And, it works well for us.

Best,

James

---

