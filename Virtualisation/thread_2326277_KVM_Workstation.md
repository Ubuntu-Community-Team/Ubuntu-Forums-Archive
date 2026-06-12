---
title: "KVM Workstation"
date: 2016-05-30
forum: Virtualisation
---

### Post by csc2 on 2016-05-30
Hi I am planning on building a new workstation this summer and would like some guidance on my choice of hardware. I primarily use Autodesk Inventor and 3Ds Solidworks at work (windows softare) and have been asked if I can teach people basic CAD on my own time (read I need need 2 pcs that can run this software). Right now I don't have a PC at home remotely capable of running these applications and I plan on assembling one. In order to keep cost down I would like to buy only one CPU,motherboard etc and use KVM with GPU passthrough for at least two windows guests. So far I've used ESXI at home with good results and played a little with KVM/virt-manager.

Right now I am looking at purchasing the following:

1x Super Micro X11SAE-F
1x I3 6100 (I just need decent single thread performance and would like ECC) I could move up to a xeon if need be
2x 16GB ECC DDR4 DIMMS
2x Nvidia GPUs (probably 960ti used)
1x 1000w power supply

It has to: 
passthrough GPU to 2 windows guests
Run 2 windows guests with inventor/solidworks
Be stable under load

Are there any problems I should be expecting with my current list of hardware? I know Nvidia doesn't like their consumer GPUs being used in VMs but it looks like KVM has that taken care of. Do I need any special instruction set available to run more than one guest with GPU passthrough?

Thanks!

---

### Post by deadflowr on 2016-05-30
*Thread moved to **Virtualisation**.*

---

### Post by KillerKelvUK on 2016-05-30
Hey, what are you plans for host side...just cli or will you be putting a desktop their too?  Was just thinking 16gb RAM for 2 windows desktops seems like you might be skimping on the host but then depending on what your host is doing that might be just fine.  That said I would certainly recommend you configure HugeTables for memory paging with the guests to improve performance in your use case.  Also what's your storage solution, this will have a performance impact on your guests so are you planning on using local disks in your workstation or a NAS/similar?

---

### Post by csc2 on 2016-05-30
Host side would be cli with ipmi/ssh to access console. I don't want a lot of things to break on the host so a desktop is something I'd like to avoid. 

Storage would be a MDADM raid 1 or 10 with ssds on the host. I have a NFS server that would be used for storage of data. I was considering zfs but I would trust it to survive random power outages without a UPS. 

16gb RAM would probably be enough but I'm planning on getting two 16gb dimms for a total of 32gb memory.

---

### Post by T.J. on 2016-05-30
> 
Are there any problems I should be expecting with my current list of hardware? I know Nvidia doesn't like their consumer GPUs being used in VMs but it looks like KVM has that taken care of. Do I need any special instruction set available to run more than one guest with GPU passthrough?



Only one guest can use passthrough on a video card at a time.  It's not a software problem.  The actual GPU was designed to only process signals from one source at a time.  Once the GPU is allocated to a guest, no one else can use it, not even the host, until it is released. Naturally, a guest will not release hardware, unless it is shut off.  Operating systems and hardware are designed around the idea of exclusive use. (It's annoying, I know, but that is "just the way it is" as they say.)

In order to have two guests using GPU passthrough at the same time, you would need a GPU for each one (and one for the host).  You can, however, run any combination of virtual GPUs alongside a GPU passthrough simultaneously.

I've made notes and scripts I can share if you are interested.

---

### Post by csc2 on 2016-05-30
Haha I guess I wasn't very clear about buying two video cards in my first post. Any advice and scripts would be appreciated though.

What I was worried about is if there are special requirements for passing more that one graphics card to more than one guest simeltsneously.

Can a GPU be used for more than one guest if they are never running at the same time? This would be nice if available.

---

### Post by houstonbofh on 2016-05-30
It just takes careful routing. :)  (easy to get them flipped)  But make sure AutoCad will work with your consumer card.  it may require a Quadra.  And more memory is always good!

---

### Post by T.J. on 2016-05-30
> **csc2 said:**
> Can a GPU be used for more than one guest if they are never running at the same time? This would be nice if available.

Yes, of course. Assigned GPU's are actually bound to a special driver called vfio-pci when they are used for passthrough.  That is then passed to the VM, where the GPU's control is given to the guest's video driver.  It can't be released without shutting down the guest VM or causing a crash.  There is nothing stopping you from using the card for a different VM as long as only one attempts to lock control of the GPU at a given time.

When you want to discuss the subject in detail, please let me know and I'll help get you a working passthrough enabled.   The first thing you need to do is verify that your motherboard is capable of IOMMU.  If your chipset is not able to perform IOMMU operations, you can still use a KVM, but passthrough is not possible without it, at least not as far as I know.

---

### Post by csc2 on 2016-05-31
I'm still at the purchasing stage so it will be a month or two before I am ready to start setting up the software side of it but I do appreciate the help so far. My budget for this might mean one VM gets a 560ti I have sitting around instead of a good video card. Will using non-UEFI cards make a difference with setup?

---

### Post by T.J. on 2016-05-31
> **csc2 said:**
> I'm still at the purchasing stage so it will be a month or two before I am ready to start setting up the software side of it but I do appreciate the help so far. My budget for this might mean one VM gets a 560ti I have sitting around instead of a good video card. Will using non-UEFI cards make a difference with setup?

The Nvidia card model itself is *almost *immaterial as long it as at covered by the existing Nvidia universal driver if you are planning a Windows VM.  AMD cards can be a bit trickier.

As far as UEFI is concerned, I actually prefer UEFI cards because they respond better to the firmware embedded in a KVM, at least for me.  On the other hand, UEFI can be a serious PITA if your host UEFI has bugs.  I highly recommend that you make certain your motherboard's firmware is at the highest available stable version.  Don't use beta versions, that's asking for trouble.

You should also test the cards to make certain your system is stable with the configuration before you attempt to use it.  I had an issue where my machine refused to boot properly until I flashed the firmware.

---

### Post by MAFoElffen on 2016-06-01
With one important note that some missed and misunderstand: Passthrough refers to the hardware of the Hypervisor Host, not on the connected host of that is displaying the VM Guest. If that connected machine is the same mchine as what is running the hypervisor, then this is moot.

If not, then this needs to be understood, where this needs to be and what it means. Is does not matter as much, what hardware is present on a remote connected host, except that is be able to display the resolkution of that VM guest session. In this respect, you can play games and share virtualized hrdware between remote users, one at a time (4 at a time on VMware, 16 at a time with Grid).,,

I promote and support virtualization. I am also brutally honest. On the same machine... as a player of games, there is a drawback from setting up as a dual-boot machine. You have to accept that there will be some noticeable lag. It will not be the same as running it on native hardware, as you would be doing on a dual-boot. If you can accept that lag, then you are golden.

---

