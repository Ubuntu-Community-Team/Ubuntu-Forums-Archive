---
title: "Suggestions for (cheap) Windows 10 virtualization server?"
date: 2016-08-10
forum: Virtualisation
---

### Post by csete on 2016-08-10
If I were going to build a new machine (from parts) to support a KVM installation of Windows 10 with reasonable performance, can anyone suggest CPU/Motherboard/RAM for such a machine?  This is a home machine, so it does not have to be super high performance.  My ideal would be to build a new machine for $500 or less.

Thanks,
Craig

---

### Post by MAFoElffen on 2016-08-10
What I would recommend:
```

CPU Quad Core-- Needs to support hardware virtualization. That could be either Intel or AMD.

Motherboard that supports that CPU, with a BIOS that supports hardware virtualization.

8 GB Minimum RAM, the faster the better. 16 GB is comfy.

1TB Sata 7200 rpm HDD. (6Gb/S) 

2 Mainstream NIC's ports, could be onbaord or not. But one for host & NAT, other for a Bridge.

```
Other than that, anything else can be whatever. You don't need a high-end graphics card, unless you are going to do a GPU pass-through. 

On a budget, the first thing is to get something that will get you started, but not end up as a dead-end if you need at add to your resources. In KVM, Win 10 runs best, with less trouble when you copy over the host CPU or emulate at least a Core2-Duo. 

A cheap board with an iCore 3 is only a dual-core... but would get you started, and a lot of boards that support that will upgrade to an iCore 5 & iCore7. I always look at the board & case combination, and how many drives it might support. The thing with virtual's, is that each one you add takes memory and HDD space. It can share CPU% and run slower, but if you don't have memory or HDD space for your guests. It just doesn't work. So remember you can start small, but plan for scale-ability.

What is recommended by most Hypervisors for running a Win10 VM Guest is at least 4 GB of RAM and at least 40 GB of disk for the VM image.  I've done it with 2 GB each Win10 VM and been happy. They did just fine. Even though 38-40 GB will get you by on a Win10 VM, plan and add for what you are going to install on it program-wise. That can add up fast. To keep the performance up, it runs better if you go 40 GB for the boot and system partitions, then add 40 GB volume slices (separate 40 GB VM Image files), and add then in as "storage space" type disk. That is Win's take on LVM. That way the system runs faster, has more integrity than a single image file... and is dynamically expandable.

On my KVM host system <-- I install on LVM so I can dynamically grow my storage. On image file type, I prefer to use qcow2 so I can do VM Guest snapshots.

Is that enough info for a start?

---

