---
title: "Migrating Ubuntu/Linux through different hardware"
date: 2010-03-24
forum: Virtualisation
---

### Post by x_men on 2010-03-24
Hi
I have a tricky question for the linux/ubuntu gurus out there.

First off, I'm a windows guy. No offense but that's what I've grown up with, but I am in a linux forum and interested in linux here. I'm planning on remodeling my network soon, and when I do so, I want to segregate the server tasks to different servers (MySQL, Apache, DNS, DHCP, etc...). This is entirely home scale project and I want to make room for growth in the future. For now I'm thinking of using a bunch of VMs on a single good machine. I like the advantages of VMs in regard to its mobility (just transfer the file over to a different hardware) and if I set them up that way, I can keep the same network model for later.

My question is when I do decide to expand and actually migrate one of the VM into its own hardware (probably when Apache gets hit enough to deserve its own server), how well does Linux/Ubuntu do with new/unfamiliar hardware (we're going from legacy virtual hardware to real hardware). I'm thinking of simply making an image of the virtual machine and clone it to the new hardware using Norton Ghost or something similar. I know Windows won't even load if I do that.

That probably expands into several other questions: if cloning the Norton Ghost style isn't the preferred way in the Linux world, then what is?
If it doesn't work, are there ways to inject drivers/repair the installation to make it work?

This whole thing is because I don't want to set the server up from scratch each time, but I may be asking too much. But since I'm newbie in Linux, who am I to judge?

Don't know where this should go, so I post it under Virtualization.

---

### Post by TheFu on 2010-03-24
I've migrated completely physical Ubuntu installs between different machines with different types of disk controllers successfully.  The only issue at the first boot was that network devices are added for the new ethernet controller when MAC addresses don't match.  It is trivial to correct  - google for "network udev ubuntu" and it will tell you how to reset the ethernet settings.

I've moved Xen virtual machines between different physical servers too. The great thing about virtualization is that the hardware is virtualized too.  No matter how busy my VMs get, I won't go back to a physical server. Not ever, unless there's a specific hardware requirement that can't be passed thru to a VM.

To clone a disk in UNIX, there are many, many ways.  The easiest (not the fastest) is to use `dd`.  I did this 2 weeks ago to make an exact system backup that I could simply swap the drive connectors and reboot back to the original setting.

dd if=/dev/sda of=/dev/sdb bs=10240

This cmd will completely mirror all partitions and all data between two identical disks. The 2nd disk just needs to be larger than the first for it to work. In the first 10 seconds, the partition table is mirrored.  To exactly mirror just 1 partition, use

dd if=/dev/sda1 of=/dev/sdb6 bs=10240

Where the partition numbers match what you want.  You can also shove the output into a file.

dd if=/dev/sda1 of=/export/sda1-part-backup.img bs=10240

Just be certain you have booted from a live CD or are in a true single-user mode if you want this to be completely safe. Using a different boot medium is safest.

There are other, more optimized ways like "partimage" to clone disks and partitions. These will clone and compress the image on the fly. When I have time to hunt the program and re-learn how to use it, I do.

Anyway, you don't have to worry about a system not booting due to video card  or disk controller changes like with Windows. You probably don't want to take an x64 install and drop it on x32 CPUs, but beyond that, I think you'll probably be fine. I've done this disk swap between systems 4 times in the last 4 years.  

OTOH, with all the weird hardware out there, you could be the first for which this method doesn't work.

---

### Post by TheFu on 2010-03-24
There is an issue if you try to migrate from 1 VM hypervisor to a different type, since you'll be changing the hardware used.  For Linux VMs, this is less of an issue, but for Windows it is **the issue** and I don't know that anyone has solved it without performing a reinstall.

As an example, I've failed to migrate a VirtualBox WinXP VM to run under Xen or KVM hypervisors. That doesn't mean some VM ninja can't get it to work, just that I haven't. IMHO, I see this as a MS-Windows failure.

---

### Post by x_men on 2010-03-25
Wow... thanks for the super detailed reply, TheFu. I'd probably be  referring back to your post as a reference when I do the real thing.
So I guess my options are
- Move the VM to its own machine, just virtualize it, so I don't have to  deal with different hardware.
- Clone the VM to a real machine, like a machine-to-machine clone, and  deal with the hardware differences
- Reinstall the entire thing.

Your response addresses only storage controller and network.... but I  guess that's all there is. As long as CPUs doesn't crap out with the  whole 32/64 bit stuff.

---

### Post by codfather on 2010-03-25
If I read your post correctly, you were potentially asking about how to do a virtual to physical migration. This can be done, and here is an outline for doing it with VMware:

[http://www.vmware.com/support/v2p/index.html]("http://www.vmware.com/support/v2p/index.html")

I would however agree with my fellow poster, that once you virtualize , the best way is to keep it that way, and just buy the hardware to cope. With modern tier1 hypervisors (KVM,Xen,ESX, Hyper-V) , you are only going to lose between 5-10% of performance on common tasks. 

Moving from one server platform to another - same CPU architecture - is simple as its the virtualization layer that takes care of the compatibility , so the virtual machine won't know or care that it has moved. Different CPU architectures require a little more work but can still be done.

---

### Post by x_men on 2010-04-10
Sorry for the late response here, codfather.

The thing you brought up about tier 1 hypervisors is interesting. I must admit I'm also noobish in this whole virtualization thing, not just linux. I've only thought of virtualization as having a host OS (linux or windows) already, then have a virtualization client on it (like VMWare workstation) to run the guest OSes.

So, back to the tier 1 hypervisor thingie. I want to dig a bit deeper into this. What tier 1 options do you recommend, and are they free? VMWare has academic licensing thing which I'm hoping when I get my professor to process it, I'll be able to get VMWare ESX or something.
Assuming you're a VMWare expert, [http://en.wikipedia.org/wiki/VMware#Products](http://en.wikipedia.org/wiki/VMware#Products) help me understand this chart. If I'm only looking for free solution here, I can get the VMWare ESXi, and use vSphere to manage it, no need for license manager? What is your opinion about performance in this path if it's viable? And the VMs are easily transferable between different VMWare versions, I assume?

---

