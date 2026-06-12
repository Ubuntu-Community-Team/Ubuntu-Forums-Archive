---
title: "KVM/QEMU, VMware, and VBox benchmarks"
date: 2007-10-28
forum: Virtualisation
---

### Post by Redmumba on 2007-10-28
I had a lot of problems trying to find some comparable benchmarks between some of the more common virtual machines, so I decided to make my own.  Each machine ran using its _native image format_ (I.e., VDI for VBox, VMDK for VMware, etc.), and each one started out with a completely clean, reinstalled version of Windows (running the Standard PC HAL, ACPI disabled).

Intel VT technology was enabled on both VBox and KVM/Qemu (obviously, kvm_intel is required for it to run at all...), although in VMWare WS6.0.1, I could not find an option to enable it. /shrug

Both VMWare and VBox come with included "helpers" that allow things like clipboard sharing, etc., but I noticed no difference in the benchmarks w/ or w/o the added software.

Surprisingly enough, here's what I got running SuperPI to 1M digits

**KVM/Qemu**
22.322
22.553
22.353
Average: 22.409s

**VMWare Workstation 6.0.1**
46.086
45.165
43.222
Average: 44.824s

**Virtualbox 1.5.0_OSE** (from apt)
22.683
22.552
23.103
Average: 22.779s

**Virtualbox 1.5.2** (from deb)
22.814
22.563
22.373
Average: 22.583

Obviously, these are by no means conclusive, but I can't figure out for the life of me why VMWare is so high (almost twice as slow as the other two!).  I'm also planning on perhaps trying out Xen and a few more options, although I don't think anything will beat KVM/Qemu's speed.

Thinkpad T61
Intel Core 2 Duo 2.2ghz (Virtualization enabled)
2GB RAM (750MB allocated to each VM)
100GB 7200RPM hard drive (6GB ":growable" partitions)

EDIT: Added Virtualbox 1.5.2

---

### Post by tribble222 on 2008-02-22
Thanks for the benchmarks!  I've noticed that VMWare player is much faster than VMWare server.  I haven't tried VMWare workstation, but if it's like server, I'm not surprised it's much slower than Qemu and Virtualbox

---

### Post by Ace2016 on 2008-04-01
Very interesting, could you possibly do some graphics testing? just like the difference in xorg between running the nvidia driver and the nv driver, when you move apps in xorg with nv it feels laggy and slow, whereas with nvidia app rendering and moving is faster, its the same in widnows but worse i think, so could you benchmark the graphics too since a smoother ui is always much nicer to work with.

:KS

---

### Post by dcstar on 2008-04-01
> **Redmumba said:**
> 
........
Intel VT technology was enabled on both VBox and KVM/Qemu (obviously, kvm_intel is required for it to run at all...),** although in VMWare WS6.0.1, I could not find an option to enable i**t. /shrug
.........
Obviously, these are by no means conclusive, but I can't figure out for the life of me why VMWare is so high (almost twice as slow as the other two!)
.......

If VMware was only using one CPU, then that would explain why it was **twice** as slow, wouldn;t it?

---

### Post by willtriv on 2009-05-26
> If VMware was only using one CPU, then that would explain why it was twice as slow, wouldn;t it? 

It's a single threaded application. Also Virtualbox (AFAIK) only supports single CPU emulation. These are a bit dated now anyhow. I believe vmware-server 2 can hook to the SVM/VMX extensions.

---

