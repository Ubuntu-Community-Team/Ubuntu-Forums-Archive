---
title: "Re: The possibility of a Virtually managed ZFS NAS &amp; Hypervisor Workstation."
date: 2013-12-28
forum: Virtualisation
---

### Post by YQ002lc2 on 2013-12-28
I'm looking to build one box to run:

1. A ZFS NAS home file server and archive.
2. A small linux hypervisor to run virtual machines for testing. 
I may migrate some of these VMs to physical machines at some point.

Additionally, if possible, I want to incorporate my existing heterogeneous hardware into my ZFS array. (old smart phones, laptop hard drives, desktop hard drives, external hard drives...)
I'm trying to stretch my dollars as far as they will go. 
I'm very new to ZFS, but I'm currently trying to test ZFS setups on VirtualBox VMs of FreeBSD, Debian kFreeBSD, Fedora, NAS4Free, Ubuntu Server, FreeNAS, OpenIndiana,...
The problem is I'm using a 32-bit lenovo t60p laptop with a dual core processor and 3 GB of RAM --my newest computer. It's about 7 years old and ZFS needs more RAM....


Questions:
1. Can a virtual machine be used to manage a physical ZFS NAS system? (Can a VirtualBox VM do this?)

2. Does anyone know of any use cases where this type of all in one box has been built?

3. Are there motherboards with 6-12 JBOD and/orRAID HDD slots, slots for 32 GB RAM, 8+ USB 3.0 ports, 3 external monitor ports...?
4. Are there sites that allow you to do advanced searches for motherboards?
5. Are there sites to check hardware compatibility?

6. Is it possible to reconstruct a ZFS array from a snapshot or are ZFS snapshots different?
7. What is the most stable ZFS system for NAS type configurations? FreeBSD?
8. Is anyone using ZFS on linux for NAS production environments? It seems rather unstable to me.

9. I plan to use an intel processor. Any suggestions on a processor, motherboard.....? I've looked at the IBM XEON E78870 10C 2.40G 30MB Microprocessor&#8203;, but it's way out of my price range.


Any suggestions, criticisms, or other inputs will be greatly appreciated. 
Thank you.

---

### Post by tgalati4 on 2013-12-28
I would buy a used, business-grade Dell PowerEdge or HP Proliant server--lots of those being surplused.  They will give you the RAM slots, big power supply, and pci slots needed for SATA cards, firewire cards, USB cards, etc.  Then you can plug in all of your storage devices and have plenty of power to spare.  A laptop makes a poor server.  Unless the screen is broken and you don't want to repair it, you would be better served with real server hardware.

I wouldn't put a hypervisor on it--keep it clean and put as many services on the machine that you need.  Find another machine (curbside or other surplus machine) for playing with other distros.  Adding a hypervisor to a home server means more maintanence and more to troubleshoot when something doesn't work.

As far as ZFS, I have a small whitebox pc running freenas for a few years.  Added a PCI SATA card and I have a few TB of storage.  It works OK.  ZFS is has a fair amount of overhead and is not super fast for home server use.  Running simple JBOD with ext4 would probably better for home use.  Unless you have specific needs for ZFS (which you have not mentioned yet), ext4 works best under linux.

---

### Post by TheFu on 2013-12-31
You are asking many "can I" questions when perhaps the questions should be "should I"?
A few comments (that probably aren't surprising to anyone who has read a few of my posts):
* ZFS likes RAM. There are some controls over how much by the specific features enabled. Follow the normal guidelines and it can SCREAM!  A business partner has ZFS on an 8 core 32G box managing about 64G of storage - he loves it, but had to disable dedup (not enough RAM).
* Storage is about the only purpose where I do NOT like virtualization. There are exceptions, like for tiny, specialized uses, but if more than 30G if storage is used, I am not going to use a VM.
* USB3 is great for single-purpose storage - backups.  Not so great when the storage will be accessed by many different processes concurrently. I've said this before and others have reported it too - USB3 has queuing issues.
* Adding SATA ports to a MB isn't hard. Research SATA cards that have Linux support built-into the kernel. Ensure you do not saturate any single PCI-whatever bus inside the MB. Most server-class MBs have multiple PCI buses so you can drop a 4 or 8 port SATA card on different backplanes.
* 32GB of RAM will be easy on a server-class MB
* Any high-end GPU will probably not fit into a server-class MB, if it even has a 16x slot.

For server-type workloads, I do not believe VirtualBox is upto the task. It just isn't that stable.  Look to KVM, ESXi, Xen for that sort of workload. This is my opinion after being burned by virtualbox (it locked up an entire VM host machine, not just a VM).  That exact, same machine has been happily running KVM VMs for 2+ yrs with ZERO lockups.

So ... I run lots and lots of VMs. NONE are for storage. Storage runs on real hardware.  If you really, really, really can't drop $150 for a home-built Atom storage server (RAM+GigE NICs), then I suppose I'd run it on the physical VM host OS to avoid slow VM access to storage.  I would love to hear about folks using PCI passthru to avoid the VM PCI card slowdowns.  Look for hardware that supports VT-d to make this happen.  That usually means Xeon and Core i7-type CPUs, MBs, etc.... 

Based on what I think I read above, I'd start looking into **SuperMicro** motherboards as a starting point. Then I'd look into 3ware 8-port SATA cards.

I'm positive that others will have different suggestions. Can't wait to read them.

Stability is the 2nd most important thing to me - including performance. Only data integrity has higher priority.

---

### Post by houstonbofh on 2014-01-01
First, if you want ZFS you need Solaris or FreeBSD.  That narrows down your VM choices quite a bit.

But, if you look in the nas4free forums, there is a big thread about people who have installed virtualbox inside nas4free, and that may give you just what you need...

---

### Post by YQ002lc2 on 2014-01-18
Thank you tgalati4, TheFu, and houstonbofh for your replies and expertise. 

You've provided me much to chew on. 

I realize I did not explain what I am trying to do. 

I'm trying to:
A. Securely and reliably archive irreplacible data and access it on a home network. 

I have a conservative estimate of 9 TB and growing of family movies, pictures, backups, and other irreplacible data.

Goals:
1. To store this data in the most secure, incorruptible file system....
AND
2. To make this data accesible to approved hardware (no more than 1-3 devices at a time) on my home network. (not over the internet)

From my initial research and testing, I believed ZFS to be the best option for storing this data, though the resources needed were worisome. 

B. Replace my computer in the process.

My current computer (laptop) is 7 years old. 
I've replaced the fan in it once and the backlight shuts off periodically. The power supply, which I've yet to find a replacement for, has a dangerous gash that exposes wires and is a fire hazard that can't be left unattended... 

I can't rely on it to run when I'm not around and the specs are too low for ZFS:


So if I'm spending money for new hardware, it would be nice if it also functioned as a new computer.



I was hoping to use deduplication because I probably do have a lot of duplicate data in backups and snapshots as well as files of a similar type... I have experience using rsync with ext4 for backups and I'm learning about and testing LVM, but I need something that can detect and prevent data corruption like ZFS. 

I've tested fdupes for deleting duplicates, but I was not pleased with it. If you have a symbolic link to a file, it is very easy to delete the file and leave only the symbolic link. Also, it requires you to manually do this for all duplicate files.

As houstonbofh noted, FreeBSD or Solaris seem to be the best options for ZFS implementation, but this limits my virtualization and other options... 

I've seen only one article which references using a VM to manage a "mass-storage ZFS pool". [http://nynim.org/blog/2012/06/04/all-in-one-home-file-server-vmware-esxi-openindiana-and-zfs/](http://nynim.org/blog/2012/06/04/all-in-one-home-file-server-vmware-esxi-openindiana-and-zfs/)

If I was able to run some other type of host and use a Solaris or BSD derivative VM for managing only the ZFS pool, I would feel better about it. 
(I'm aware this may be infeasible)

Also, I'm not sure if it is possible to backup/export and import information about a zfs pool. For instance, if I backed up my zfs configuration and switched hypervisors at some point, could I import the ZFS pool information from the backup and start where I left off?


Any further advice, criticisms, and other feedback are much appreciated. 
Thanks again!

---

### Post by tgalati4 on 2014-01-18
In theory, you should be able to move zfs pools between similar operating systems and remount them, however in practice you may run into problems.  And when you do, troubleshooting is difficult and time-consuming.

I'm still not sure why you need or want a hypervisor.  How many and what type of virtual machines do you need to run?

For backup, consider a 3-2-1 strategy.  3 copies of important files, on 2 separate physical devices, with 1 off-site.

---

### Post by YQ002lc2 on 2014-01-18
Thank you, tgalati4, for your reply and expertise!

I currently run 10 VirtualBox VMs. 
Two are Windows machines I use for proprietary software I need for school. 

The rest are Solaris, BSD, and Linux machines I use for testing.

---

### Post by houstonbofh on 2014-02-10
A little late, but better than never.

De-duplication on ZFS takes a LOT of memory.  (About 1gig per terabyte of data)  I have found hard drive space to be cheaper.

---

