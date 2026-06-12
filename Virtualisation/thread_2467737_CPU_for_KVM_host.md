---
title: "CPU for KVM host"
date: 2021-10-06
forum: Virtualisation
---

### Post by aljames2 on 2021-10-06
On an older machine I have an Intel i5-3570k cpu.  Still a formidable cpu for gaming.  It has 4 cores.  Thinking of using it to host KVM & some VMs (not gaming).  I am reading that this processor has VT-x but not VT-d.  The VT-d is to allow hardware to pass through to the VMs & helps with I/O device performance.  The KVM site seems to recommend it.  Are there issues with not having the vt-d?

Debating whether to use the 3570, or pick up a newer one.  The i5-10400F is only $99 at newegg.

Edit:  … plus the cost for a new motherboard and ram.

---

### Post by TheFu on 2021-10-06
If you don't use I/O passthru, like you would for a system hosting daemons for internet use, then vt-d isn't really important for most enterprise needs.
If you host stuff on the internet, then you probably want a different NIC than is used by LAN hosted stuff so a different bridge can be setup for internet-facing services.

The other uses are to exclusively have access to a GPU or disk controller, but that would be more for gamers, not in an enterprise running email, nextcloud, DNS, DHCP, document management.  To me vt-d is more about VM security than performance.

I'm a huge believer in using AMD Ryzen CPUs, but some of the i5/i7 CPUs have become cost effective, assuming you are willing to upgrade the motherboard with every new version.  With Ryzens, the same MB can support all AM4 CPUs ... which is across 4+ generations.  There's no chance that $100 i5-10400F (12000 passmarks) will go into the same MB as used by the 3570 (4900 passmark), so add $150-$250 to the total cost when you determine what a "deal" it may be.

Of course, for a server, having the onboard iGPU means not having to spend even $50 extra for a cheap GPU like most Ryzen's would need.  If you have a spare GPU, then you can setup a console-only Ubuntu server and pull the GPU out and use a $7 serial connector.  Perhaps you already have a KVM switch that does serial?

4 cores vs 6 cores - assuming you have hyperthreading disabled to mitigate some CPU attack vectors.

There is usually more to determining what a deal any option is than 1-for-1 CPU comparisons.  Have to look at everything.

So ... how many and what type of VMs do you expect?  Will you migrate any to Linux containers, which can have 10x-100x less overhead.  RAM requirements?  Everything becomes a moving target.

---

### Post by aljames2 on 2021-10-09
My VMs on the machine would include primarily a “daily driver” desktop, and a nextcloud server.  I was also thinking of trying to put a VPN server in a VM, but I also have a raspberry pie that I may use for that.

What about using a VM for home network routing?  Currently I have a dedicated computer running pfsense that serves as my router.  I have read that it is possible to virtualize this?

I currently do not host any websites or email servers.

I misquoted the price on that i5 processor, it is roughly $170.  It was an i3 that I saw for $99.  I am looking at a Ryzen setup as well.  Heck, perhaps the one I have is enough.

---

### Post by MAFoElffen on 2021-10-09
Seems I am on this adventure again also. But taking my time. Long term goal lots of CPU thread count for vCPU and Memory capacity. My VHost currently is 9 years old, and still Legacy Boot. 

I have all my other VHosts in storage because they were Server Hardware, which I needed the redundancy at the the time (profession wise), but over time... They are noisy, and add way too much to my power bill to be justified. That, and I had to downsize in how I live. One I kept on for a while as a media server, but I ended replacing it with a Rasp Pi 4 with USB drives. Much quieter, very little power usage and no noise.

I still do Dev and Testing, so I need to simulate what I am supporting. But code compiles do take a toll on resources. Some of that I can do on simulated, virtual hardware, to do cross-platform work.

Lots of things I've done in the past with many machines, I have consolidated those into just a few. I'm down to one workstation, a server, and two laptops. One laptop is for work, because I have to have something to create and adapt toolsets on-site. The other is a MAC Notebook, because I have to support things that includes MAC hardware, and it is just another animal. I know how to visualize those...  but it still isn't the same on some of the idiosyncrasies.

I brought up those things, because you mention you will use one as your "Daily Use"... So you probably need to include the resources needed for that into your plan.

---

### Post by TheFu on 2021-10-09
> **aljames2 said:**
> My VMs on the machine would include primarily a &#8220;daily driver&#8221; desktop, and a nextcloud server.  I was also thinking of trying to put a VPN server in a VM, but I also have a raspberry pie that I may use for that.

What about using a VM for home network routing?  Currently I have a dedicated computer running pfsense that serves as my router.  I have read that it is possible to virtualize this?

I currently do not host any websites or email servers.

I misquoted the price on that i5 processor, it is roughly $170.  It was an i3 that I saw for $99.  I am looking at a Ryzen setup as well.  Heck, perhaps the one I have is enough.

For that workload, any Core2 Duo from 2010 would be fine.  I run nextcloud on a 1GB VM with 2 other php webapps in the same VM (until a few weeks ago).
I have a dedicated VPN VM.  I wouldn't use a rasp-pi for that due to less than great AES-NI support in ARM compared to the amd64-class CPUs.

Your WAN router needs to be a stand-alone device, but for inside the LAN, if you want/need a router, then using a VM for that is fine. Just carefully consider your bridge setup and strongly consider having VT-d with passthru for any NIC needs on the router.  It's a security thing.

A few days ago, I ordered a new MB ($90) and Ryzen 5600G CPU ($240). I've been looking to have a VM failover system that matched the current VM host in performance and retire a few 6-11 yr old systems, and reduce my power needs. I'd been looking for a Ryzen deal about 18 months.

BTW, I ran 15 VMs on a Core2 Duo in 2010 within 16G of RAM. This was before all the Ubuntu bloat happened. 20.04 really is bloated compared to all prior versions.

Only 1 of my production systems uses UEFI booting. All the others are legacy boot.  Which is production?  A laptop.  My 3 VM hosts all use legacy boot.  I've just never seen any reason to change.  They are running except the 2 minutes after a patch that requires a reboot (sometime that day I reboot), so any claimed boot speed improvements just-don't-matter.  They use GPT disks just fine, including booting.  Why bother?  I don't want to deal with MSFT holding certs or secure boot flags or wondering if grub is used for the boot or not or 2-stage booting or ... whatever else these new fangled kids came up with to fix problems I don't have.

---

### Post by aljames2 on 2021-10-13
Thanks all for the discussion.  I do this about every 8-10 years or so,  takes some time to catch up on what's new w/hardware.

UEFI is not hard but a pain to set up a new  OS boot disk for, in my opinion.  Legacy MBR seems simpler and to me the 2 TB  limitation is irrelevant because I would never use a 2 TB disk for  booting.  I suppose there are some redundencies with GPT disks that are supposed to make recovery more possible if there are issues with a header, but with having a backup  process for critical files from my OS drive, its not a problem for me.  I may go the MBR way  on the new setup, and just leave my storage drives GPT.

> **TheFu said:**
> A few days ago, I ordered a new MB ($90) and Ryzen 5600G CPU

TheFu, for your new MB did you go with a B550 or X570 chipset board?  Like you pointed out, and I agree, the potential longer life for using the MB & RAM is nice for future upgrading of the cpu.

Thanks again All!

---

### Post by TheFu on 2021-10-13
UEFI doesn't preclude GPT.  That's an arbitrary thing for MSFT systems, not Linux.  Linux doesn't care and will happily legacy boot GPT partitions.

> TheFu, for your new MB did you go with a B550 or X570 chipset board? Like you pointed out, and I agree, the potential longer life for using the MB & RAM is nice for future upgrading of the cpu.

Neither.  I got the same board that my Ryzen 2600 uses. 
I don't need newest stuff and I'm certainly not willing to pay outlandish prices to get it.

---

### Post by MAFoElffen on 2021-10-16
Adding To TheFu's answer...

Linux does not care, but... 

On GPT disks, if it boots GPT as UEFI, it looks for an "/EFI/" directory, where the UEFI boot files (which includes the grub efi file) are located (and later mounted with the /boot directory)... which points to the /boot directory or /boot partition.

If the boot mode is Legacy on a GPT disk, then it looks for a "/boot_bios" partition, which is the grub files that Grub uses on a MBR disk... and points to the partition where the other Grub files are locate in (/boot directory in /root or separate /boot directory).

If the disk is MBR, then it installs that grub boot pointer file in a raw space before the first partition. If like that, it only boots as Legacy.

I try to install on my own, as all being GPT disks, and for the root drives, as dual boot for both UEFI and Legacy boot modes. That way, if all goes wrong, I can move the disks to another machine.

Note that I have come across some older UEFI systems that were "UEFI only"... but those are rare.

---

### Post by ajgreeny on 2021-10-23
I use that exact same CPU in my desktop machine with 8G RAM to run all my VMs (Linux distros, not Windows, though I did have a Windows 10 VM for a while, now deleted). I think you will find that CPU is absolutely fine, depending on other hardware, for running VMs for general use but I can't comment on gaming as I'm not a gamer

I allocate 2 of the 4 cores and usually 4G of the 8G RAM to these VMs, all of which run with no real or obvious differences between them and some bare metal installations i have.  My VMs are all for testing of distros, not running as daily drivers, though there is no reason why they could not be used in that manner.

When I first started using KVM/QEMU all my systems were installed using legacy BIOS, mainly because I was not even aware at the time that UEFI was available, and they all ran fine but now when I install I always chose UEFI in the Overview tab of the configuration settings window (console) in virt-manager when installing.

---

