---
title: "VirtualBox very slow compared to Vmware"
date: 2015-02-06
forum: Virtualisation
---

### Post by machjiri22 on 2015-02-06
Hi,

I have Xubuntu 14.04 32bit host, where I have installed latest VirtualBox with latest extensions. In it I have Win 7 64bit guest, with 3GB RAM, 2 processors. Everything works great, but HDD operations are VERY slow. When i run HDtune test in guest, hdd speed is approximately 30Mb/s. (booth host and guest are on same SSD on separated partitions) So I made a little test. I have copied hdd content to .vdmk file and run it in VirtualBox. Hdd speed was still around 30Mb/s. Then I have installed Vmware player and created new virtual machine, but then added the same virtual HDD. When I run it in Vmware (similar setup as VirtualBox) and do HDtune test, average HDD speed is around 250MB/s !!! and whole system is much faster.

So how is this possible? I still would like to use VirtualBox, because it seems to have better USB devices support and I have some network issues in Vmware too. Thank you for your answers

---

### Post by TheFu on 2015-02-06
I don't use either of those tools, but common VM tuning includes:
* Don't run a 64-bit guest on a 32-bit host. I'm shocked that is even possible.
* Don't double buffer - either have the hostOS or the guestOS deal with disk caching, not both.
* Use virtio drivers if you can, not SATA and definitely not IDE - this also applies to networking.
* Use the native file format for each VM technology - that's VDI for Virtualbox. On SSD, it really shouldn't matter, but ... on spinning HDDs, RAW is almost always faster, but some of the other options added features can make the performance hit worthwhile.
* Install the guest additions. Make certain it is the correct version that matches the VM hypervisor. Every guest kernel update, reinstall. Every virtualbox hypervisor update, reinstall. This should be automatic, but might not be - depends on how you installed.

Hope this helps.

---

### Post by machjiri22 on 2015-02-07
I was shocked too, but it works pretty good except for these HDD problems. So I'm going to install clean Xubuntu 14.04 64bit just to give it a try, but I have my current 32bit installation nearly for four years and it's hugely tuned so I want avoid new system installation if it will be possible.


You wrote you don't use either of those tools, so is there another free virtualization software which you would recomend me?

---

### Post by TheFu on 2015-02-07
I run servers, not desktops.  These servers need to have good uptimes.

KVM is my server virtualization tool of choice after trying Xen, ESX, ESXi, Virtualbox, and a few others.  KVM has never crashed, never refused to boot a VM, been extremely predictable, FASTER than the others, and it is part of the linux kernel development process.  If you need HVM, KVM is it as far as I'm concerned.

It can also do remote desktops fine.  I routinely (daily) connect to my main desktop over the network. The servers have old, low-end GPUs - $20 at the purchase time ... er ... 6 yrs ago.

I have a grudge against VMware and Oracle - seen them screw over customers multiple times. When KVM became better for my use a few years ago, we migrated off all the others and have been happy.  Of course, **your requirements may dictate a different choice.**

---

