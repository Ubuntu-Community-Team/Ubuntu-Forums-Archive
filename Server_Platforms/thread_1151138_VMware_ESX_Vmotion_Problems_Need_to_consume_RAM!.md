---
title: "VMware ESX Vmotion Problems: Need to consume RAM!"
date: 2009-05-06
forum: Server Platforms
---

### Post by dataciph3r on 2009-05-06
Does anyone know of a way to consume all available memory on a system? I’m looking for code or a script if possible. We’re running RHEL4 in a VMware ESX environment. RHEL is running Oracle 10g. Each RHEL VM has 5GB of RAM allocated to it. With Oracle running it uses just about all that memory. When we try to VMotion the VM to another ESX server we experience a network outage for about 30 seconds which is causing us all kinds of problems. We’re suspecting the problem is the high memory usage by Oracle or something else we’ve done along the way to the VM to cause the problem. A fresh install of RHEL or Ubuntu server without Oracle does not have this issue. So like I said, we’re looking for a way to consume just about all the system memory without installing Oracle so we can try a VMotion and see if we still lose network. Any help would be appreaicted.

---

### Post by windependence on 2009-05-07
How much memory have you left for the host? People always forget that it's the host that does all the networking and things like Vmotion. You should probably have at least 2 Gigs left for the host to use. 5 gigs is a lot to give to each VM, but viewing that you are running Oracle and it's really a pig, I can see why you wanted to do that. I'm thinking it's not the VMs but the system that is being starved for resources. the system must cache all that stuff while it's doing the transfer and it needs space to do it. I have never run into the issue you are having. Sorry I can't help you out with a script to consume memory. One thing you should know is that Linux will use all the memory that is available to it regardless of whether it actually needs it for running programs. This makes it appear as if it's resource starved when in fact it's working as it should.

-Tim

VMware Partner

---

### Post by dataciph3r on 2009-05-07
The host is showing that it's using about 42GB of the 64GB total. The CPU usage is less than half. I can see what those resources jump to during a Vmotion. 

When we first started using RHEL and setup Cacti I was really confused as all the memory graphs were showing that ALL the memory was consumed ALL the time. After researching I did find that answer; Linux will use the available memory if it can. 

Thanks for the response. I'll keep looking for a script or something along those lines.

---

### Post by dataciph3r on 2009-05-07
Found the issue. It was the smp kernel.

---

### Post by windependence on 2009-05-07
Ah, that's another thing. Don't use virtual SMP. VMware will allocate CPU to the VMs as needed even if you don't specify more than one CPU, in fact, if you do, it doesn't work the way you think it would. It actually ties up cores on the CPU and allocates resources for that VM even if CPU isn't needed. This causes a big problem when all the VMs are set up with more than one VCPU. VMware does not recommend it unless you have a very specific reason to do so, usually for graphics rendering or similar applications. Take a look at this:

> Virtual SMP Best Practices
Virtual machines in an SMP system should be configured to use multiple CPUs only if they are
running applications that are multi-threaded or implemented to use multiple processes. Also, as
mentioned earlier, single-threaded workloads cannot make use of the second virtual processor
in a virtual machine. Depending on the guest operating system scheduling behavior, the
second virtual CPU may still consume resources and reduce the flexibility of the ESX Server
scheduler, without enhancing application performance.
[B]This best practice recommendation differs from the common practice of configuring physical
enterprise servers with at least two CPUs. While in typical business environments such a practice
normally enables standardization and the possibility of system reuse, in virtual infrastructure,
where provisioning is virtually free, having the second CPU just in case, does not carry similar
benefits. In addition, virtual infrastructure changes the nature of the trade-off between scaling
up and scaling out your platforms.[/B] In many cases, ESX Server running a combination of SMP and
single-virtual CPU virtual machines can utilize the physical CPUs most efficiently.The whole document is here and explains the whole scenario:

[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.vmware.com%2Fpdf%2Fvsmp_best_practices.pdf&ei=CGIDSr-3F5GatAObu9DcAQ&usg=AFQjCNHLbGW2yGpfR5cNR623pU49xU8lHA&sig2=7xOBZd_3Oa6m9pxKgjDp0A]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.vmware.com%2Fpdf%2Fvsmp_best_practices.pdf&ei=CGIDSr-3F5GatAObu9DcAQ&usg=AFQjCNHLbGW2yGpfR5cNR623pU49xU8lHA&sig2=7xOBZd_3Oa6m9pxKgjDp0A")

HTH,

-Tim

---

