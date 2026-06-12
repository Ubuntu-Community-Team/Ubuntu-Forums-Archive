---
title: "VirtualBox Alternatives"
date: 2020-01-06
forum: Virtualisation
---

### Post by zkab on 2020-01-06
Can anyone recommend a good stable virtualization software that works fine with Ubuntu 18.04 LTS.
I am not fond of Oracle and have had bad experience with VirtualBox.
My guest OS will be Windows10 and some other Linux distros.

---

### Post by slickymaster on 2020-01-06
Thread moved to **Virtualisation**

The default virtualisation technology supported in Ubuntu is KVM.

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by Dennis N on 2020-01-06
For my personal use, I now use QEMU/KVM for virtual machines rather than VirtualBox. I've not seen any stability problems. You have to try it and decide for yourself. I have it installed on two different hosts, Ubuntu 18.04 and Fedora. Fedora was easiest to set up - just one command installs all needed packages. But once installed, both implementations work equally well.

There are some minor differences in features - for example, I found Fedora automatically redirects USB devices to the guest OS, while Ubuntu 18.04 requires manual redirect. That was convenient.

---

### Post by zkab on 2020-01-06
Thanks ... I have been looking at QEMU/KVM and I will install it.

---

### Post by TheFu on 2020-01-06
> **zkab said:**
> Can anyone recommend a good stable virtualization software that works fine with Ubuntu 18.04 LTS.
I am not fond of Oracle and have had bad experience with VirtualBox.
My guest OS will be Windows10 and some other Linux distros.

There are a few.  Not all are great for different reasons.
* kvm - fastest, extremely stable. Requires AMD-v or VT-x CPU support. What Amazon and everyone in the world use except Microsoft and VMware. KVM is part of the Linux kernel and tested with it. Only x86 last time I checked, but efforts to get ARM were underway. That might be there today. IDK and don't care.
* qemu - extremely wide CPU architecture support, but slow.  If you are on Intel and need ARM or PowerPC or MIPS emulation, this is the tool for that.
* VMware Player, VMware Workstation - Workstation is commercial and requires paid upgrades to support newer Linux releases. VMware makes 6 different hypervisor products, so if you go this direction, be certain to always say which you are actually using. ESX, ESXi, Horizon, Fusion .... you get the idea. ESXi is free for limited use. It is not F/LOSS. No VMware software is F/LOSS.  We were happy clients and installed ESX at all our clients, before a VMware management decision effectively increased license costs 2-3x for our clients. VMware had no choice to change after the uproar, but they still increased prices.  We moved all our clients off anything VMware-related to KVM.  Our clients didn't mind paying $10K/yr, but $25K+ was an issue.  The whiplash from VMware's poor decisions impacted us, our clients, and everyone inside the VMware community for 4+ months.  All wasted effort.  Never again.  BTW, this all happened after VMware was bought by EMC.  EMC has a long history of charging as much as the market will bare.
* Xen - Fast. Some guestVMs can have driver issues.  Kernal implementation is more complex than KVM and was rejected multiple times.  Amazon used Xen before they switched to KVM.  I ran Xen in production for about 3 yrs. It was stable when it ran.  About once a year, after patching, the VMs would refuse to boot, but not after every patching.  Haven't used it since about 2011, so my first-hand knowledge is extremely dated. Some really big sites, non-public, use Xen very happily. OTOH, when you have 50K VMs, it is hard to migrate to any different VM hypervisor.

There are a number of GUI tools designed to make using KVM friendlier.  "*Boxes*" is one.  *virt-manager* is another.  Canonical has announced their version for this, but my initial look-see turned me off for some reason. I don't recall why or the name.  I've been using virt-manager to create new VMs for almost a decade, but not for access post-install. For that I use either ssh or x2go or ssh with X11 tunnelling.  virt-manager works remotely, using ssh, so we control remote, headless, hypervisors, using virt-manager which feels about the same as the virtualbox GUI you already know.

KVM is enterprise-class virtualization. I've never, ever, had a KVM VM fail.  Servers, desktops, whatever.  Rock solid and that's since 2010.  Prior to that, I used Xen, ESXi, VMware Server, Workstation and virtualbox for x86 VMs going back to the late 1990s.  On non-PC hardware, I've deployed lpars, vpars, npars, domains, Solaris Containers on AIX, HP-UX, Solaris systems.   KVM is equal or better than those solutions, though IBM's lpars are FREAKIN' amazing!

Anyone looking at VMs for Linux guests should probably look at Linux Containers too.  Ubuntu makes lxd, which is pretty good as an almost VM, but not quite as limited as docker containers.  "Linux Containers" have tiny overhead compared to other full VMs. If a physical system can support 20 full VMs, it can probably support 100-200 Linux Containers just providing a specific service, not a full OS.  Something for consideration.

In general, I use KVM + libvirt + virt-manager.  Played with docker, lxd, and other restricted access tools like firejail for specific desktop programs. The docker container format has one that war.  LXD is a bridge between docker and full-VMs.  KVM is for full VMs.  All of them have security liabilities, so be certain to do some security research on whatever method is chosen. Mitigations are generally available for each. Unfortunately, all of them need some mitigation for security issues.

---

### Post by zkab on 2020-01-06
Thanks for excellent information ... sounds that KVM is the right way for me to go ...

---

### Post by TheFu on 2020-01-06
KVM is perfect for server -on- server virtualization. The trick is to always remember that the best performance comes by *sharing the physical hardware* in the smartest ways.  Setting up the virtual storage is key to getting good performance. If the storage is on SSDs, then it doesn't matter too much, but if it is on spinning disks, it matters VERY much. Besides the storage, almost everything else can be changed/fixed later.  Sometimes, the storage can be fixed later, but it is a hassle for point-n-click people.  **qemu-img** is the tool to correct poor storage choices. 
[https://blog.jdpfu.com/2012/07/30/improving-kvm-performance](https://blog.jdpfu.com/2012/07/30/improving-kvm-performance)  For disk and networking, choose the virtio interfaces/drivers when you can.  Linux versions should all support these out of the box.  I haven't touched Win10, but Win7 doesn't include virtio drivers.  The 2nd best  options for disk is SATA or SCSI and the 2nd best option for network cards is an Intel PRO/1000.  For Windows versions that don't include virtio drivers with the installer, it is easiest to start with those options. For more about virtio on Windows: [https://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers](https://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers)  On Windows, if there is a problem later, using virtio will cause issues trying to fix it because the safe-boot option won't load virtio drivers.  With Windows, there's always a CON to go with a PRO.

With Desktop -on- Desktop virtualization, honestly, virtualbox with the Guest Additions is easier and *good enough* for most casual users.  
> Any use of the VirtualBox software programs which cannot be licensed by the Personal Use and Evaluation License requires a commercial license for the Oracle VM VirtualBox Enterprise with the following licensing models...
Be very careful to understand how Oracle defines "Personal Use." It isn't what most people would think. Do you have 2 VMs running?  That isn't personal use from my understanding.  Only you can decide if virtualbox guest addition licenses are needed.

The trick to using KVM for Desktop -on- Desktop virtualization is to setup QXL video drivers inside any clients and tell virt-manager to use QXL + SPICE.  On the same physical machine, this should provide excellent GUI performance.  I know people using it for light autoCAD needs. I really don't have ANY experience with this type of virtualization, so hopefully, someone else can point to tips for getting the most from it. Regardless, following the server on- server performance ideas will be helpful.

---

### Post by kevdog on 2020-01-07
Honestly theFu seems very knowledgeable about using KVM -- he knows far more than I ever will about the topic.  I've spoken about this product before but just like to throw in my two cents -- xcp-ng hypervisor (CentOS is the base OS).  xcp-ng is the open source freeware version of Xen.  I'm not sure what your demands are, but using this product is just damn easy.  You can either use Xen Center (which unfortunately is a Windows only program), or Xen Orchestra (which again is free but must be installed within a working linux system -- I installed it on one of the Ubuntu VMs I installed within xcp-ng) as GUI frontends to manage the hypervisor.  I know a little but really know jack-crap about managing the hypervisor from the command line and such.  Working with both XenCenter (which I have installed on macbook with Virtualbox) and XO make it really easy to manage the hypervisor.  My only criticism of the installation is that it doesn't always do USB passthrough appropriately which kind of sucks in certain applications.

I'll get around to trying KVM likely on Debian Host one day.  Only so much spare time I have.

Another alternative is ProxMox which is run on Debian and basically is a front end for KVM.  I found the GUI management tools lacking and support forums very inactive so I dumped the hypervisor after  a while.  A good support forums or program is probably beneficial when researching virtualization particularly if you're doing it for the first time.

Maybe theFu could recommend a support forum and where to seek help with KVM.

---

### Post by CorporateMonkey on 2020-01-21
Wouldn't it be better to use windows 10 and make virtualization of Linux?

---

### Post by TheFu on 2020-01-21
> **corporate-monkey said:**
> Wouldn't it be better to use windows 10 and make virtualization of Linux?

Not if you want stability, performance, control.
One of my lab VM hosts.
```
$ uptime
 12:11:17 up 200 days, 22:45,
```

It runs Windows Media Center inside a VM which is used only for recording TV, internet access is highly restricted to specific outbound locations. Occasionally, that same VM does 2 other Windows-only things.  Everything else we do - EVERYTHING is done natively on Linux.

---

