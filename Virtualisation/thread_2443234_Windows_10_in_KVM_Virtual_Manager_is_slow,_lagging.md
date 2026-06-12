---
title: "Windows 10 in KVM Virtual Manager is slow, lagging (Ubuntu 20.04)"
date: 2020-05-13
forum: Virtualisation
---

### Post by ceojosh24 on 2020-05-13
As the title says, Windows 10 in KVM is lacking some responsiveness and lags a little. It's not terrible, but I'm trying to run some audio editing software in it, and it just lags in the visualizers and scrolling. I've tried changing almost every single settings in the virtual manger and within Windows 10 after researching for hours but to no avail. 

1. Here are my Ubuntu specs:
Memory 31.0 GiB
Processor Intel® Core&#8482; i9-7900X CPU @ 3.30GHz × 20 
Graphics GeForce GTX 1650/PCIe/SSE2
Disk Capacity 1.0 TB SSD


2. Here are some of the settings I've done in virtual manager:
Allocated 100GB for the virtual disk
Logical host CPUs: 20
Current allocation: 4
Maximum allocation: 4
Memory allocation: 8192 MB
Maximum allocatoin: 8192 MB
Disk Bus: SATA
Storage format: qcow2
Cache mode: hypervisor default
Hypervisor Default for everything else: IO mode, Discard mode, Detect zeroes, 
Video Model: Virtio
3D Acceleration On

Also added SPICE to allocate a Shared folder in Virtual Viewer as explained in a tutorial.

3. Here are the Windows 10 settings I have:
Disabling unnecessary services after boot up
High Performance Mode
Display Settings for Best Performance, so no animation and all that
Uninstalling as many unnecessary programs as possible
Tried defragging and consolidating the disk
Scan and clean junk files after boot up
Scanned for viruses, got none 

Let me know if you have any further suggestions, or need any more information to get Windows 10 to run at the same speed and responsiveness as my regular Ubuntu OS.

---

### Post by vicsar on 2020-05-13
What has worked for me is the reverse you are doing. I keep Windows as my boot system and virtualize Linux. I tried the other way but it always gave me problems.

---

### Post by TheFu on 2020-05-13
Did this work better in earlier versions or is this all new under 20.04?
Are you accessing the Win10 GUI locally or over a network connection?  I almost always access VMs remotely.

Tuning guests is about sharing the physical aspects of the system, limiting any bottlenecks we have control over and having realistic expectations as far as graphics is concerned.

There are 5 major areas to be optimized:
[LIST]
[*]* storage
[*]* networking
[*]* graphics
[*]* RAM
[*]* CPU
[/LIST]

First, put VMs onto SSD storage.  If you cannot do that, use fully preallocated image files for the virtual-HDD presented to the guest system. We are talking raw, fully, preallocated, storage.  If you need 100GB, then there should be a file on the system that is 100GB in size holding the entire win10 VM storage. For example:
```
$ ls -lh /Data/1TB/Other/VMs/Win7ult/Win7Ult-os.img
-rw-r--r-- 1 root root 59G May 10 17:04 /Data/1TB/Other/VMs/Win7ult/Win7Ult-os.img 
```
My old Win7 VM really used 59G of storage.
Additionally, the most efficient way to access storage is to use virtio drivers.  These are provided by Redhat. The gain over SATA or SCSI storage is less than 2%, but every bit helps.  The
-rw-r--r-- 1 root root 63166218240 May 10 17:04 /Data/1TB/Other/VMs/Win7ult/Win7Ult-os.imgre are hassles when virtio is used, since MSFT's OS doesn't include them and troubleshooting boot problems requires loading those drivers in the Win Recovery mode.
Using an SSD is the easy answer. Use the fastest storage you can.  A fast WD Black 7200 HDD or Raptore 10,000 HDD are better than cheap Blue or Green disks. There is a noticeable performance different.  All spinning disks need preallocated storage.

Second, use virtio for the networking device.  This is fairly painless and does have lower overhead than the 2nd best option, Intel PRO/1000. With virtio network drivers, I routinely see 32 Gbps network transfers within the same host, whereas the Intel PRO/1000 is limited to about 940 Mbps.

Third, having reasonable expectations for the graphics capabilities of the VM is necessary.  The GPU presented to the guest system is 100% virtual, so it uses the QXL "fake" GPU drivers when spice is uses.  The QXL drivers come from Redhat, in the same package as the virtio for storage and networking.  
Another option is to setup GPU passthru, but that requires 100% exclusive access to the GPU by the guest. The host cannot have any access, which presents a problem to systems with a single GPU. In short, it won't work with only 1 physical GPU.

Forth, RAM needs to be shared between the host and the guestOS. In general, leave at least 1GB of RAM to the host, but if you are running a bloated desktop, I'd say leave 4GB to the hostOS.

Fifth, CPU needs to be shared between all the VMs, containers, etc, running on the system.  During the install of Windows, there are different kernels installed (or there were) based on whether 1 or 2+ CPUs were seen by the installer.  For me, I've always just installed using 2 vCPUs for Windows VMs.  More hasn't helped with needed performance, but I don't do heavy computing on Windows.  Just had Windows Media Center running inside a VM to gain access to free TV schedule data. I never watched any recordings in the VM.  I have seen where people have giving more vCPUs to guests thinking that would help make it faster, but the opposite happened.  Start with 2, see what happens. Close and disable programs on the hostOS that could kick off heavy CPU usage. That would include anything that pops up notifications.

For non-GPU intensive programs, we should get 95% of native performance doing these things.  I've had 20 concurrent VMs running on a Core2 Duo system. That included 1 Win7 VM. All the rest were linux servers without any GUI. These weren't real-time sensitive programs.  Handling requests within 1 second was fine.

Music really needs a real-time subsystem.  Virtual machines just don't provide real-time controls, at least, not that I'm aware. Many people are using Ubuntu-Studio these days. I think that provides a real-time kernel.

---

### Post by ceojosh24 on 2020-05-13
This is my first time using Linux after using a Mac for 9 years, so everything you're talking about just kind of went over my head. Also the hard drive is a SSD. I'm using virtual manager within Linux, so just as a separate virtual desktop to run Windows programs.

---

### Post by ceojosh24 on 2020-05-13
I'm going to try Looking Glass and see if it helps boost the graphics display.

---

### Post by CatKiller on 2020-05-13
> **TheFu said:**
> Third, having reasonable expectations for the graphics capabilities of the VM is necessary.  The GPU presented to the guest system is 100% virtual, so it uses the QXL "fake" GPU drivers when spice is uses.  The QXL drivers come from Redhat, in the same package as the virtio for storage and networking.  
Another option is to setup GPU passthru, but that requires 100% exclusive access to the GPU by the guest. The host cannot have any access, which presents a problem to systems with a single GPU. In short, it won't work with only 1 physical GPU.

From the description this does seem to be the issue. And my understanding is that you can't do GPU passthrough with consumer Nvidia cards.

---

### Post by ceojosh24 on 2020-05-13
I think you're right. I'm going ahead and ordering the same graphics card and seeing if that works with the KVM running on its own graphics card. Shall update when that happens.

---

### Post by slickymaster on 2020-05-13
*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2020-05-13
> **ceojosh24 said:**
> I think you're right. I'm going ahead and ordering the same graphics card and seeing if that works with the KVM running on its own graphics card. Shall update when that happens.

Setting up GPU passthru is non-trivial.  Doubtful that someone will little experience will be successful.  

[LIST]
[*]There are very specific hardware requirements for this to work. Check your motherboard and GPU for the specific possibility to accomplish this.
[*]There are very specific kernel requirements for this to work. IOMMU. Be certain that your MB allows this setting to be enabled AND that is works with your kernel.  I've had the BIOS prevent this.
[*]Every new kernel will need to be re-setup to allow the passthru, I would expect.
[/LIST]


Last time I looked at doing this, there were 20 pgs of instructions to make it happen.  Hopefully, it is down to 5 pgs now.

---

### Post by ceojosh24 on 2020-05-14
Are these the correct instructions for GPU passthru with a Windows 10 VM on Linux? [https://wiki.gentoo.org/wiki/GPU_passthrough_with_libvirt_qemu_kvm](https://wiki.gentoo.org/wiki/GPU_passthrough_with_libvirt_qemu_kvm). I don't know any other way to get the visuals in Windows 10 to work properly without lag, so this is the last option as far as I know.

---

