---
title: "How essential is the bios setting VT-d for running VMs?"
date: 2016-02-27
forum: Virtualisation
---

### Post by Toast2120 on 2016-02-27
Looking to buy a laptop that doesn't support Intel VT-d in the bios, seems like the option is generally available on desktops.

How much will this impact the few VMs I might be running?

---

### Post by MAFoElffen on 2016-02-28
Intel VT-x (Intel Virtualization Technology for IA-32 and Intel 64 Processors) is hardware virtualization support of the Intel Processor. AMD has parallel virtual hardware support technologies in their CPU's (AMD-Vi). VT-x It is a generic reference to (but not limited to) the technologies listed below:.
- Intel VT-i (Intel Virtualization Technology for Itanium Processors)
- Intel VT-d (Intel Virtualization Technology for Directed I/O)
- Intel VT-c (Intel Virtualization Technology for Connectivity)

You asked how important it is. Well, it allows hypervisors to be able to run virtual 64 bit operating systems. With VirtualBox, VMware, Qemu, KVM, Xen, Hyper-V etc... It allows A system to be able to pass thrugh physical access to hardware, while still running as a Secure Virtual Machine (with a protected Host).

Basically, you can run some hypervisors without it, but they will be limited to 32bit operating systems and run much slower. All hardware will be simulated by software. Notice I said some? Current Type I hypervisors now require you to have VT-x enabled.

VT-d -- The biggest bottleneck currently with hypervisors is direct I/O. The current and next generation of hypervisors are making improvements in this area... which should help with the performance of I/O intensive virtualization. (And with the performance of all VM's in general.) The current hypervisor leader leader in I/O stats is now VSphere, which will shift this year with the pending release of KVM. (pending, in dev). It has to do a lot with IOPS and shared storage for virtualization. It was major topic at this month's DevConfcz 2016.


VT-c-- Which is a collection of input/output (I/O) virtualization technologies. It also includes Acceleration Technology for the reduction of CPU loads, VM device queues (VMDq) for the reduction of system latency, and Single Root I/O Virtualization (SR-IOV) for the improvement of network I/O throughput. We can create VM's; Now we need to be able to interact with them in an efficient manner...

So how important? From what I've seen in virtialization over the past 6 years ... If you are just running VirtualBox, VM Player, and just need to run an additional occasional OS... then not that important. If you are providing a virtual service, hosting guests, running something where you need the performance of running on metal ... then very important.

---

