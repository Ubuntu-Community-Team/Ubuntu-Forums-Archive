---
title: "Hardware or software VMs?"
date: 2019-04-22
forum: Server Platforms
---

### Post by Heeter on 2019-04-22
Hi All,

I am updating onto a new server machine, Currently, the only thing that I have done is setup the hardware RAID 5 across 4 drives.

I am at a crossroads about VM management. Don't know which would better at being secure and overall performance, if I should install the VM manager right onto the hardware or onto a main Ubuntu server OS.

Of course Google searches end up being more confusing than helping.

Would like your guy's input instead.

Regards

---

### Post by TheFu on 2019-04-22
Sorry, you've lost me. What is "VM manager?" I've been doing virtualization since the 1990s and on Linux since 2008-ish.

BTW, RAID5 isn't usually a good choice these days, unless you are using very small HDDs. Stick with RAID1 or RAID10 for 1TB and larger disks.

Security isn't a yes/no checkbox. There are levels of grey depending on the hardware, networking, and how the software will be used.
In general, the fewer programs running, especially GUIs directly on the hardware, the more secure, in general, the system will be.  How the networking is setup matters greatly. If you can, use PCI passthru for the NICs and assign them to only 1 VM.  6 NICs in 6 different PCI slots, means you can support 5 VMs. Not everyone can do this, so putting similar security level traffic on the same bridge might be the best of the less-than-great options.

There are all sorts of best practices for security and performance using virtualization. Google a bit. The specific hypervisor often doesn't matter all that much.

Also, you didn't mention which hypervisor.  People tend to become familiar with 1-2 hypervisors and ignore the others.

---

### Post by Heeter on 2019-04-23
My apologies

Did not know the proper word for the VM OS that the VM's are listed in. Thank you for pointing out the word I forgot "hypervisor"

This is a 4x1TB setup. Definitely will switch to RAID10 if it is a better option for me.

I have had XenServer 5.6 all these years operating solidly, was thinking of installing Xenserver 7.6. 

Standard 1 port GIG NIC Intel card (Pro1000 I believe).

Your Thoughts on which hypervisor would be greatly appreciated for me. 

Regards

---

### Post by LHammonds on 2019-04-23
I am not sure you will see much performance increase going from RAID5 to 10.  RAID5 tends to have faster read and RAID10 tends to have faster write and they even out most of the time for general purpose VMs from my experience.

I have been running on VMware's ESXi for years.  Been switching to Nutanix hardware and the initial setup was running VMware on top of that but also have some nodes running just Acropolis (their version of Linux KVM).  You can also run Linux KVM or Windows Hypervisor.

I also run XenApp 7.6 and it is pretty buggy.  Our support ran out before there was a good version to upgrade past it.  But at this point, it is in the process of fading away and won't exist 6 months from now.

If you have time, give KVM a try and see if it works for you.  If you don't have time, you might need to fall back on what is most-familiar to you.

Of coarse, there is always the hypervisor compatibility you have to worry about.  Even if you want ESXi to run on it, the hardware might not be compatible with it so make sure you check that out before getting too deep into it.

LHammonds

---

### Post by Heeter on 2019-05-01
Thank you so much for your help guys,

I will try that KVM, heard good things about, and thank you for the heads up on the XEN.

Regards

---

### Post by TheFu on 2019-05-01
I ran Xen for a few years in paravirtual mode.  It was ok, but about 3 times a year, just after patching, some of the guests would refuse to boot a new kernel. Usually, I had to wait a week for all the device drivers to catch up, then everything would be fine.

Moved to KVM in 2010-ish from Xen and ESXi inside our business.  ESX/i was always very picky about hardware and I didn't like that their backup solution was a hack. Basically, everyone spent $1000-$5000 on a commercial backup tool.

Ran ESX and ESXi for clients about 6 yrs.  VMware corporate decided to change how things were licensed which was going to cost our clients at least 2x more, so we dropped all VMware use and spent the next 6 months migrating everyone to KVM. We've NEVER regretted moving.  Not once.

KVM has been rock solid.  Had an odd networking issue last year for a few months that could have been due to the bridge, not KVM. It impacted only 1 VM that had been working fine for over a year.  Magically, it started working a few days later (not a critical VM).  About 3-4 months later, it happened again to the same VM. Moved it to a different VM host and haven't seen the issue again.  The other 10 VMs on the old machine never saw any issue.  It was a 14.04 host, so a few weeks ago, I moved all those VMs to new hardware with a 16.04 KVM host.  Again, no issues except self-inflicted ones. ;)   Like the old VMs were Intel so the hypervisor didn't like our settings saying "Intel CPU" when the new machine has an AMD CPU.  Trivial to fix.  Also moved from RAID1 to SSD storage and moved from file-based storage backend to LVM managed by the hypervisor.   

Did a few OS and system version migrations recently too. Got to expand the LVM storage for 1 of the VMs, which was pretty easy - LVM rocks - but people reading this already know that.

The only real advice I have for KVM is to setup your bridges external to libvirt and don't use the libvirt bridge.  Libvirt NAT stuff is fine, for quicky tests.  virsh, libvirt and virt-manager all work well.  The built-in spice display stuff is working fine under 16.04. 

I don't have any 18.04 stuff here. I'm still seeing complaints in these forums about netplan not working. Don't know how to take it, but I'm happy to give it another year to mature.  Perhaps by then systemd and snaps will be production ready too?  I won't hold my breath.

You did want opinions, right? ;)

Now I need to figure out a clean way to migrate a blog from extremely outdated RoR software into static pages without losing comments, tags, categories.  Every year or so, I look for a solution and give up.

---

### Post by Heeter on 2019-05-01
Thank you Thank you Thank you TheFu!!

Exactly what I am looking for, real life assessments.

---

### Post by TheFu on 2019-05-07
> **Heeter said:**
> Thank you Thank you Thank you TheFu!!

Exactly what I am looking for, real life assessments.

The problem with real life is that personal failures/misunderstandings can cloud the report. Best to look for a few other, independent, experiences.  Plus, there are entangle reasons to choose certain solutions.  For example, clients who are prepared to pay $20K for VMware licenses, are more likely to have money to spend on an expert to guide them with bi-annual migrations. If they become used to paying, then they will always have budget allocated annually.  The trade off is doing what is best today for them might not keep them updated next year, if there isn't any budget approved for annual or bi-annual migrations.

VMware servers demand server-class hardware and generally businesses expect to buy new HW every 3-5 yrs.  For a business, replacement of servers every 5 yrs is probably about the longest time between replacement, since servers become more efficient, need fewer cores, less cooling, less power, and more reliable over the years.  KVM runs on any AMD/Intel box you have (pretty much), so taking an old desktop and making that into a "VM Server" is possible. It won't have server-class redundancy, and really cheap places probably won't have time to setup redundant desktops so if 1 machine fails, the downtime is minutes, not days.

Lots of trade-offs, not all are purely technical and not all can be shared with upper management at the client to get the best results for this and the next 10 yrs.

But using VMs, regardless of the hypervisor, **is** definitely an overall savings for every company.  I've seen (22) 7 yr old servers, all out of warranty, replaced by 2 VM hosts. The client didn't realize that their backups hadn't been working for at least a year.  They were running them daily and weekly, but nobody tried to restore.  At least until we showed up and planned to restore the backups into a fresh VM and none of them worked.  By getting 20 servers out of their computer room, it didn't need much cooling, 1/20th the electrical power, etc. It also didn't need a 36KVA UPS. 
We swapped out their per-server storage for a small SAN device, increasing performance, but reducing space, power, heat, ... ... ...
After all those things were moved out, we could upgrade their network equipment, since 48-port switches weren't needed, 12-port versions was fine for each network.  The savings rippled throughout their IT infrastructure, even with a 1-for-1 physical server to VM migration.

The noise in that part of their building dropped from a rumble to a low hum.

All things you probably know already.

---

