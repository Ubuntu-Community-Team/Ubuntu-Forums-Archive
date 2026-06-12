---
title: "Starting from scratch - best vm option?"
date: 2014-05-28
forum: Virtualisation
---

### Post by pcal on 2014-05-28
Hi guys,

I have never attempted any form of virtualisation - due to having hardware I though too low end to cope with it.

My main PC (an AMD64bit one of the first quad cores ever) is teetering on the brink of oblivion, and having lots of issues with heating and the like. Sometimes it needs multiple reboots before it comes up at all. It's dual boot between 12.04 and WinXP(32bit) at the moment.

I'm thinking of buying a whole new pc and installing a 64 bit version of ubuntu as the os, and trying to run some virtualisation system to link into the old hdd from the current machine installed into the new box as a second drive. My goal is to not loose all the stuff in the existing XP install, or have to start over with a fresh xp install. About 80% of what I do can now all be done directly in ubuntu, but there is that troublesome last 20% I can't afford to loose access to.

Is this plan even possible to implement? If so, what is the best way to go about it in terms both of virtualisation software, and hardware specifications for the new pc?

Thanks for any advice.

Regards,

Pcal

---

### Post by TheFu on 2014-05-28
There is a difference between "possible" and "easy."  It is almost always easier to reinstall Windows than to attempt to migrate a hardware-locked installation (which can't be done legally). You can look for "P2V" conversion tools. I've never gotten those to work for Windows.  Linux migrations are easy and if you do backups correctly, shouldn't be any issue for someone familiar with grub and partition management. It will not "just work" if you insist on using the same HDD for the new VM.  This might help: [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)

As for new hardware - it is amazing what $300-$450 can do to an old system.  I've been using the same case, PSU, RAM, HDDs for years, but build out completely new motherboards, CPUs (and sometimes RAM) every 3-4 yrs which almost doubles performance.  I don't game, so a $50 GPU is fine - actually I get fanless GPUs, since being quiet is much more important to me than graphics speed.  Of course, I've only bought new GPUs when the bus change (ISA --> PCI --> AGP --> PCIx ---> PCIe) forced it.

So - what exact RAM do you have today? Can it be reused?  If DDR3 - the answer is almost certainly yes.

The new system should run 14.04 as the baseOS and should have 8G+ of RAM.  Any Core i5 or better CPU will be fine, but getting a 3rd or 4th gen version really helps with performance.

I think buying a whole new computer is a foolish waste of money. Upgrade. Start with the CPU/MB and work up the plans from there.  
What is your budget so we don't overshoot the capabilities to purchase?

---

### Post by pcal on 2014-05-28
> **TheFu said:**
> There is a difference between "possible" and "easy." 

Just as I feared... I was hoping there would be a system I could use to create a vm with the same specifications as the original pc, and essentially boot the existing XP image with it. I'll research the links you provided - thanks.


> **TheFu said:**
> As for new hardware - it is amazing what $300-$450 can do to an old system.  I've been using the same case, PSU, RAM, HDDs for years, but build out completely new motherboards, CPUs (and sometimes RAM) every 3-4 yrs which almost doubles performance.  I don't game, so a $50 GPU is fine - actually I get fanless GPUs, since being quiet is much more important to me than graphics speed.  Of course, I've only bought new GPUs when the bus change (ISA --> PCI --> AGP --> PCIx ---> PCIe) forced it.

So - what exact RAM do you have today? Can it be reused?  If DDR3 - the answer is almost certainly yes.

The new system should run 14.04 as the baseOS and should have 8G+ of RAM.  Any Core i5 or better CPU will be fine, but getting a 3rd or 4th gen version really helps with performance.

I think buying a whole new computer is a foolish waste of money. Upgrade. Start with the CPU/MB and work up the plans from there.  
What is your budget so we don't overshoot the capabilities to purchase?

Yes. My old pc has already been through almost as many regenerations as Dr Who. At least 3 or 4 motherboards, several ram upgrades from the original 1024k. From memory (no pun intended), it has 2G of DDR at the moment (note there isn't even a 2 on that!), which if I remember correctly, is the limit of its current expansion ability. But my concerns are: That the psu is old, underpowered for a new system, and suspected to be contributing to my issues. That the HDD is getting quite long in the tooth (had one in a nas unit that failed last year due to a dried out capacitor, costing me heaps of data).  My GPU card is in an AGP slot and wouldn't survive a transition. And I'm sick of the boring old case I've had sitting under my desk for nearly 15 years.

Keeping the XP image on a secondary drive should presumably minimise the work it does, thereby maximising its remaining life.

Foolish or not, I think it's time for a fresh start. Even with our expensive Australian pc prices, I can pick up a brand new machine on-line from around $300 - $400 if I choose not to pay the Micro$oft tax and get it without an OS.

I was looking at an AMD 6 core system earlier today around the $600 mark - thinking I could dedicate 2 cores to virtualising XP, and leave the other 4 for Ubuntu.

If just booting the old image is too hard, would I be better off reinstalling XP from my original media (given service packs and updates etc aren't available any more), or just trying to find all the installation packages for the collection of applications I still need and trying to get them all running in wine?

Thanks,

Pcal

---

### Post by TheFu on 2014-05-28
Oh.  DDR - now that IS old.  In the USA, getting a PC without Windows usually costs more - MS has strongly, strongly, strongly, encouraged PC makers to pre-install it for $20/ea - then those same makers provide 50 preloaded crapware and get paid from the crapware vendors making the PC price less than the raw hardware. It is sad.

I have a case from 1999 here - everything inside has been replaced a few times (except the fans). I love that case.  I stopped using AMD CPUs when the Intel C2D became available.  Intel is so far beyond what AMD does for less power.  Power means heating, noise, more cooling, which wears on parts faster.  My power bill is unimportant.  PSUs are actually smaller these days than 5 yrs ago. Only high-end gamers need more than 400W PSUs - due to the GPUs.  If you don't game, you can support a 4-8 core CPU, 16G of RAM, 6 HDDs, and low-end GPU on 400W easily.

2G on a DDR box is impressive. I didn't think most systems back then went that high, but my memory fades.  I think I had an AMD-XP 2000+ CPU with 2G of DDR.  The MB/CPU/RAM is here somewhere. ;)

A fully new PC will cause some install issues thanks to UEFI. Be prepared. Do your research first.  Pick from vendors who provide clean Linux kernel compatibility, so you don't be sad later.  I think the most compatible parts are either on the VMware Whitebox HCL or the FreeNAS HCL.  For virtualization, look to server MBs ... list SuperMicro to get lots of RAM and network ports built-in.

If you want to run a desktop inside a VM and access that desktop from a local "head" ... then any thing I've mentioned here will be fine.  I like to start my price estimates from pricewatch.com .... pick the CPU I want, then MB, then RAM, then other things.  Add all that up, then look for a better deal from a maker (like Dell) .... to see if I can't get more from them. Sometimes vendors do stupid things like using custom PSU connections - beware. This will make later updates hard, if not impossible.

XP - I think the SPs and old patches ARE still available. There just aren't any new ones.  DO NOT let XP on the internet. Use it for local-only processing.  I'd put it behind a VM NAT that isn't routed - this is inside the VM NAT network, not just on your normal NAT inside the house.

1 vCPU is more than enough for XP MS-office-like stuff.  Actually, 1 vCPU is enough for 99% of Linux stuff inside a VM too. Only add more vCPUs after you've proven that 1 doesn't handle the workload.  Of course, with XP, 1 vCPU will install a different HAL than 2+ vCPUs - it is a tough choice. Perhaps giving it 2 vCPUs during installation to load the multiprocessor HAL, then reduce that to 1 for normal running?

HDD life is more about stop/starts than spinning. Any drive over 5 yrs old should be migrated out of main use - perhaps used only for backup data?

Booting the old XP image will be next to impossible.  The VM will NOT match the old chipset (north/south bridge) or MB or SATA or ... basically XP will see a completely different PC and freak out (then blue screen).  Yep - reinstall into a VM and hope you have a retail copy of WinXP (not OEM) or those HW changes will prevent installation onto any new HW anyway.

In VMs, you'll probably want to create virtual-HDDs - not use real HDDs. There are many reasons for this and if you are new to virtualization, only time and experience will teach why. Mainly it provides flexibility.

---

### Post by jakke1975 on 2014-05-29
I've had some success with vmware's p2v software in combination with Proxmox, but I suppose it would work for VirtualBox as well. Note the "some" success... BUT, those were done  on the same hardware. If you're dealing with OEM licenses, it can only legally be run on the same hardware. If you want to run it on different hardware, you need to have a retail version (i.e. not pre-installed).

I would say to give it a try. All you need is to attach your disk to a computer that runs vmware's p2v software ([http://www.vmware.com/uk/products/converter](http://www.vmware.com/uk/products/converter)) and create a vmware virtual disk from it. VirtualBox can use VMware's format and I'm pretty sure the non-vbox format has pretty much the same performance as vbox's native format.

If it doesn't work first time, I'd definitely look into the reinstall options. Messy solution but it'll save you time in the end.

That being said ... I strongly recommend to stop the use of Windows XP. There are no security patches anymore, virus scanner support drops so it's a free game for malicious hackers, rendering the online XP machine a danger to everything on your network and ultimately, the internet. What is the exact reason that you have to stick to Windows XP to do "some tasks"? Can't you run the software under WINE? Aren't there alternatives for the software you use(d) on XP? 
It's pretty hard to imagine that people stop doing the things they do when a Windows upgrade comes out (or is forced upon us). Software is updated for newer systems, run in compatibility mode or is replaced with new packages that do pretty much the same...

---

### Post by heiko_s on 2014-05-30
Here is a tutorial on how to run a Windows 7 partition from within VirtualBox, KVM, etc.: [http://http://fds-team.de/cms/articles/2013-12/use-a-real-windows-7-partition-in-virtualbox-kvm-vmware-player-u.html]("http://fds-team.de/cms/articles/2013-12/use-a-real-windows-7-partition-in-virtualbox-kvm-vmware-player-u.html"). Not sure it works for Windows XP.

About hardware purchase: Selecting hardware that supports VT-d (Intel) or AMD-Vi or IOMMU (AMD) virtualisation technology will give you more options. But beware that quite often the motherboard BIOS is badly programmed and breaks such support (most vendors give a damn about it, but ASrock does seem to care). Look for VGA passthrough capable hardware, including CPU, motherboard (and chipset), and a BIOS that is known to work. If you upgrade, get a new power supply.

---

### Post by jakke1975 on 2014-05-31
+1 on the PSU. Even though your old one may be even more powerful than you need, even though it seems to work fine:
a) it costs a fraction of the motherboard, cpu and ram combination. If it blows up (old age), it tends to take those expensive parts with it!
b) new PSU's are much more efficient and give cleaner power to the electronics, extending their life expectancy.
Don't even try to make savings on PSUs, it's the un-smartest way of saving money. Just get a decent bronze-grade or better PSU with your new mobo.

---

