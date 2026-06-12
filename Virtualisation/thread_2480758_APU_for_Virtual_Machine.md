---
title: "APU for Virtual Machine"
date: 2022-11-09
forum: Virtualisation
---

### Post by daniell59 on 2022-11-09
For setting up a virtual machine, would I be better off with a dedicated graphics card than an APU?

---

### Post by TheFu on 2022-11-09
> **daniell59 said:**
> For setting up a virtual machine, would I be better off with a dedicated graphics card than an APU?

Define "better"?  For typical office productivity stuff, it doesn't matter.  For non-graphical workloads, it doesn't matter.

If you are doing 8K video editing, do that on real hardware.
If you are doing high-end, brand new Windows Games, then spend $500 on a GPU (you'll need 2 in the system) and pass through the PCIe card using VT-d for exclusive use to the virtual machine.  This is a non-trivial task.  Cheap GPUs need not attempt this as those aren't supported.

At some point in the future, VTg from Intel will get good and using the same GPU/APU for VMs and the host will be much better.  They've been working on that since 2012-ish and the last demos I saw where very unstable.  There are some other competing methods like virtioG that are in active development, but I haven't seen them.  Expect to need at least 22.04 HWE for a stable solution, assuming that it becomes stable.

But since it is just a VM, why not do an install and see how it works on your hardware?   It isn't like VMs cost anything but storage for the day we play around before we learn what we need to know and delete the VM storage.

But "best" or "better" without clearly saying the expected hostOS, guest OSes, and workload will end up with vague answers ... like I've provided.  We can't read your mind. If you don't tell us, we'll make wrong assumptions based on guesses or what we need, not you, which probably ain't so useful.

---

### Post by daniell59 on 2022-11-09
> **TheFu said:**
> Define "better"?  For typical office productivity stuff, it doesn't matter.  For non-graphical workloads, it doesn't matter.

If you are doing 8K video editing, do that on real hardware.
If you are doing high-end, brand new Windows Games, then spend $500 on a GPU (you'll need 2 in the system) and pass through the PCIe card using VT-d for exclusive use to the virtual machine.  This is a non-trivial task.  Cheap GPUs need not attempt this as those aren't supported.

At some point in the future, VTg from Intel will get good and using the same GPU/APU for VMs and the host will be much better.  They've been working on that since 2012-ish and the last demos I saw where very unstable.  There are some other competing methods like virtioG that are in active development, but I haven't seen them.  Expect to need at least 22.04 HWE for a stable solution, assuming that it becomes stable.
Thanks for your informative reply. I have used VM very little in the past with a very old machine. I would use it for the most part to run other Operating systems, such as Windows 11. At some point, I will build another computer and want to be able run a VM.

But since it is just a VM, why not do an install and see how it works on your hardware?   It isn't like VMs cost anything but storage for the day we play around before we learn what we need to know and delete the VM storage.

But "best" or "better" without clearly saying the expected hostOS, guest OSes, and workload will end up with vague answers ... like I've provided.  We can't read your mind. If you don't tell us, we'll make wrong assumptions based on guesses or what we need, not you, which probably ain't so useful.
Thanks for your informative reply. I have very little experience running VM with an old machine. At some point, I will build a new one. For the most part I would want to run other operating systems such as Windows 11.

---

### Post by TheFu on 2022-11-09
> **daniell59 said:**
> Thanks for your informative reply. I have very little experience running VM with an old machine. At some point, I will build a new one. For the most part I would want to run other operating systems such as Windows 11.

Again, specifics help.  What is "old" machine?  Do you have a 386sx/16 from 1990?  That's "old" to some people.
Any Core2 Duo or faster CPU with 6GB of RAM should be sufficient to run 1 Windows VM, but you'd want to use the most efficient and lightest hypervisor.  For a number of years, I ran about 20 production systems on a Core2 Duo E6600 with 16GB of RAM. Just looked that CPU up and it is around ~900  passmarks.  Of course, most of those VMs were light Ubuntu servers, before Ubuntu and desktop programs became hugely bloated.  That system was replaced with a Core i5-750 (~2500 passmarks) after about 4 yrs, which is still being used, just not for VMs.  It is a backup and RAID server for storage.  For VMs, I have to Ryzen 5 systems. A 2600 (~13K passmarks) and a 5600G (~19K passmarks).  So, performance has greatly improved, at least for CPUs, over the last 15 yrs.  I saw a Ryzen 5600 for $119 yesterday, so get a mid-level B450 motherboard and reuse an existing GPU and you'll have about 20K passmarks for under $250.  This assumes you can follow instructions and have standard case, standard storage, standard PSU, ..... that can be reused and 30 minutes with a phillips screwdriver to put the system together.  It really is pretty easy.

When it comes to running VMs, don't over provision the guests.  I have a Windows guest VM here.  It gets 1.5GB of RAM and 2 vCPUs.  No more.  Mine is used for business and personal finance stuff. It used to be a WMC system.  It cannot edit videos. The software refuses to run without direct access to a GP, but it can do spreadsheets, Quicken, Quickbooks, tax software without problems. Generally, it isn't booted, so it sees maybe 10 minutes of use a week, if that and about every 3 months, I do some stock trades that need to be recorded.  The browser used to login to different brokerage accounts runs on Linux.  I'd never trust Windows on the internet.  Same for online banking.  That is all done on Linux ... using an ISO "Try Ubuntu" boot which goes directly to the bank(s) and nowhere else. Nothing is modified in the OS because it can't be changed. It is an ISO file - read-only.  This is following the advice from Brian Krebbs, a data security reporter: [https://krebsonsecurity.com/banking-on-a-live-cd/](https://krebsonsecurity.com/banking-on-a-live-cd/)  I use an Ubuntu-Mate ISO, not Puppy as he suggests.  The distro is less important, provided it has a modern browser that works with your financial institutions.

Anyway, you still haven't said what you expect to do with MS-Windows in a VM.  Will you play Solitaire, Chess, do MS-Office stuff? It matters.  VMs are good for many things, but they aren't good for everything, like gaming. If you want to run Windows games, don't use a VM.  There will be lots of hassles doing that. Every new kernel will break the setup, so you'll get to fix it every few weeks.  Go for a dual-boot setup instead .... or just keep the systems separate and spend $40 on a KVM switch to share the keyboard, mouse and monitor between 2 computers.  Then you'll keep Windows stuff separate from Linux stuff, which is good.  I gamed a bit in the late 1990s and wish I'd have kept a Pentium 90 loaded with all my games from that period to play exactly like it was back then.  I still have the floppies and some CDRoms for those games, but the setup on a modern system is so much hassle. Plus, I don't remember all the tweaks to get audio working or access to high-memory and the joystick controller. All that was working perfect.  Heck, even MSFT Flight Simulator was fun back then.  I'm too old to have the patience to hunt down all the fixes for those details again ... plus I don't have any working systems with IDE drives and Win2000 didn't support SATA (I don't really remember, but their are lots of issues like that).

---

### Post by daniell59 on 2022-11-10
> **TheFu said:**
> Again, specifics help.  What is "old" machine?  Do you have a 386sx/16 from 1990?  That's "old" to some people.
Any Core2 Duo or faster CPU with 6GB of RAM should be sufficient to run 1 Windows VM, but you'd want to use the most efficient and lightest hypervisor.  For a number of years, I ran about 20 production systems on a Core2 Duo E6600 with 16GB of RAM. Just looked that CPU up and it is around ~900  passmarks.  Of course, most of those VMs were light Ubuntu servers, before Ubuntu and desktop programs became hugely bloated.  That system was replaced with a Core i5-750 (~2500 passmarks) after about 4 yrs, which is still being used, just not for VMs.  It is a backup and RAID server for storage.  For VMs, I have to Ryzen 5 systems. A 2600 (~13K passmarks) and a 5600G (~19K passmarks).  So, performance has greatly improved, at least for CPUs, over the last 15 yrs.  I saw a Ryzen 5600 for $119 yesterday, so get a mid-level B450 motherboard and reuse an existing GPU and you'll have about 20K passmarks for under $250.  This assumes you can follow instructions and have standard case, standard storage, standard PSU, ..... that can be reused and 30 minutes with a phillips screwdriver to put the system together.  It really is pretty easy.

When it comes to running VMs, don't over provision the guests.  I have a Windows guest VM here.  It gets 1.5GB of RAM and 2 vCPUs.  No more.  Mine is used for business and personal finance stuff. It used to be a WMC system.  It cannot edit videos. The software refuses to run without direct access to a GP, but it can do spreadsheets, Quicken, Quickbooks, tax software without problems. Generally, it isn't booted, so it sees maybe 10 minutes of use a week, if that and about every 3 months, I do some stock trades that need to be recorded.  The browser used to login to different brokerage accounts runs on Linux.  I'd never trust Windows on the internet.  Same for online banking.  That is all done on Linux ... using an ISO "Try Ubuntu" boot which goes directly to the bank(s) and nowhere else. Nothing is modified in the OS because it can't be changed. It is an ISO file - read-only.  This is following the advice from Brian Krebbs, a data security reporter: [https://krebsonsecurity.com/banking-on-a-live-cd/](https://krebsonsecurity.com/banking-on-a-live-cd/)  I use an Ubuntu-Mate ISO, not Puppy as he suggests.  The distro is less important, provided it has a modern browser that works with your financial institutions.

Anyway, you still haven't said what you expect to do with MS-Windows in a VM.  Will you play Solitaire, Chess, do MS-Office stuff? It matters.  VMs are good for many things, but they aren't good for everything, like gaming. If you want to run Windows games, don't use a VM.  There will be lots of hassles doing that. Every new kernel will break the setup, so you'll get to fix it every few weeks.  Go for a dual-boot setup instead .... or just keep the systems separate and spend $40 on a KVM switch to share the keyboard, mouse and monitor between 2 computers.  Then you'll keep Windows stuff separate from Linux stuff, which is good.  I gamed a bit in the late 1990s and wish I'd have kept a Pentium 90 loaded with all my games from that period to play exactly like it was back then.  I still have the floppies and some CDRoms for those games, but the setup on a modern system is so much hassle. Plus, I don't remember all the tweaks to get audio working or access to high-memory and the joystick controller. All that was working perfect.  Heck, even MSFT Flight Simulator was fun back then.  I'm too old to have the patience to hunt down all the fixes for those details again ... plus I don't have any working systems with IDE drives and Win2000 didn't support SATA (I don't really remember, but their are lots of issues like that).

I would like to be able to install Windows 11, then install my Epson Perfection V30 scanner. I had no luck installing it on Ubuntu 20.04.

---

### Post by Tadaen_Sylvermane on 2022-11-20
Windows 11 requires TPM 2.0. If your bare metal doesn't have that then you won't be able to virtualize it either I'm sorry to say. Options in order of best to worst (in my opinion)

1 - Return that Epson and buy a scanner from HP or another brand that actively supports Linux stuff.

2 - Deal with a Windows 10 VM knowing it will be unsupported sometime in 2025.

3 - Get a new computer that can handle Windows 11 and go from there.

My current machine is more than capable of running pretty much what I want. But MS has decided it's to old so they won't allow me to run 11 on it. So they can take a hike. I eliminated my dual boot and run straight Debian at this point. Your best choice if being open matters at all to you is to bite the bullet and change to hardware that will run on open source with ease. Trying to make stuff work, while it can be done is really just pointless as it supports companies that have made it clear they don't want our business.

---

### Post by daniell59 on 2022-11-23
> **Tadaen_Sylvermane said:**
> Windows 11 requires TPM 2.0. If your bare metal doesn't have that then you won't be able to virtualize it either I'm sorry to say. Options in order of best to worst (in my opinion)

1 - Return that Epson and buy a scanner from HP or another brand that actively supports Linux stuff.

2 - Deal with a Windows 10 VM knowing it will be unsupported sometime in 2025.

3 - Get a new computer that can handle Windows 11 and go from there.

My current machine is more than capable of running pretty much what I want. But MS has decided it's to old so they won't allow me to run 11 on it. So they can take a hike. I eliminated my dual boot and run straight Debian at this point. Your best choice if being open matters at all to you is to bite the bullet and change to hardware that will run on open source with ease. Trying to make stuff work, while it can be done is really just pointless as it supports companies that have made it clear they don't want our business.
Thanks for your informative reply.
The scanner is way past any possibility of return. Sometime in the future I will build a new machine. Since I don't play games, I am thinking of an APU rather than a dedicated graphics card. I know that the APU will be using some of the RAM. I would like to set up virutal machines. With that in mind, would I be better off building one with a dedicated graphics card?

---

### Post by lammert-nijhof on 2022-11-29
I run a lot of desktop VMs on the 2nd slowest Ryzen, the Ryzen 3 2200G (4C4T; 3.7Ghz) and 16GB DDR4 (3000MHz).  My Host OS is a minimal install of Ubuntu 22.04 LTS, because I divided all my Apps over 6 VMs (4 Linux and 2 Windows (XP and 11).  I also run a Windows 11 Pro VM, basically by applying some small changes in the registry of Windows during the installation. Nowadays Virtualbox 7.0 officially supports TPM 2.0 and Secure Boot and thus Windows 11. However note that the Ryzen 3 2200G is NOT supported by Windows 11, so not supported CPU types might still cause an issue during the Windows 11 installation. 

I'm not a gamer, but using Virtualbox with 3D acceleration, I can play Linux games like Extreme Tux Racer and SuperTuxKart in a Linux VM.  The load on the iGPU is around 80% at 1080p 60Hz.  I run modern Linux VMs with 1.5 to 2.5GB of memory and for modern Windows (Vista or newer) I use 4GB. I always run the VMs with 4 cores, because I see no advantage is slowing down a VM artificially by limiting its number of cores. Besides Linux is perfectly capable of scheduling all processes of Host and VMs effectively over the available 4 hardware cores.

---

### Post by TheFu on 2022-11-30
> **daniell59 said:**
> Thanks for your informative reply.
The scanner is way past any possibility of return. Sometime in the future I will build a new machine. Since I don't play games, I am thinking of an APU rather than a dedicated graphics card. I know that the APU will be using some of the RAM. I would like to set up virutal machines. With that in mind, would I be better off building one with a dedicated graphics card?

No. It doesn't matter, assuming the system has sufficient RAM.  "Sufficient" depends on what you ask it to do.  Sometimes that is 4GB, sometimes 8GB, sometimes 64GB. It just depends.  I've run 2 VMs on a 4GB Chromebook (not using ChromeOS, but a lite-Ubuntu with no DE, just a WM).  My current laptop has 8GB and I use the iGPU to run VMs.  
My current desktop is actually running inside a VM.
```
$ inxi -b
System:    Host: regulus Kernel: 5.4.0-132-generic x86_64 bits: 64 Desktop: N/A 
           Distro: Ubuntu 20.04.5 LTS (Focal Fossa) 
Machine:   Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996) 
           v: pc-i440fx-xenial serial: <superuser/root required> 
           Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.10.2-1ubuntu1 
           date: 04/01/2014 
CPU:       2x Single Core (4-Die): AMD EPYC (with IBPB) type: MCM SMP speed: 3409 MHz 
Graphics:  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel 
           Display: server: X.Org 1.20.8 driver: none unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 
Network:   Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge 
           driver: piix4_smbus 
           Device-2: Red Hat Virtio network driver: virtio-pci 
Drives:    Local Storage: total: 40.00 GiB used: 23.59 GiB (59.0%) 
Info:      Processes: 202 **Uptime: 11d 5h 09m** Memory: 3.84 GiB used: 1.50 GiB (39.0%) 
           Shell: bash inxi: 3.0.38 

$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       1.1Gi       279Mi        38Mi       2.5Gi       2.4Gi
Swap:         4.1Gi        43Mi       4.1Gi
```
So, it is given 4GB of RAM and has a 4.1G swap area.  Runs great in the 40GB disk I've given it.  The physical computer for that desktop is a 6-core Ryzen with plenty of RAM and disk.  Virtualization is about allocating "sufficient" shared resources to each virtual machine.  BTW, did you notice that uptime?  It is very stable.

I don't use Windows much, but have a Win VM for tax and some stock trading software.  It is setup with ... 
2 vCPUs
1.5G RAM
and for storage, 
```
# du -h *
35G     WinUlt-Data2.img (11G free)
59G     WinUlt-os.img (20G free)

```
The Data2 storage used to be 200G, for some video work, but I've moved all that to Linux and made the Windows-data area much smaller.

I've had a Ryzen 5600G (19,800 passmark) the last year. The iGPU it has is faster than the nvidia 1030 in another system and much less hassle.  Shortly, I'll be getting another 5600G CPU ($120) to replace the older Ryzen and nvidia in the other machine.  I'm looking forward to much less hassles overall  and a 40% performance increase.  It is a pure CPU swap. Same RAM and same motherboard will be used.  Know anyone looking for a Ryzen 2600 (13,200 passmark) and fanless DDR5 1030 GT?

Where an APU scares me is when older or slower CPUs are part of the deal.  Any Ryzen 2xxx or newer or 10-series or newer Core i3 (or better) shouldn't be any issue.  If you plan to run more than a few VMs, get 16G or 32G of RAM. I saw 32G@3200Mhz for $80 over the weekend.  Reusing old parts, an impressive system can be built with a CPU+RAM+MB for under $300.

---

