---
title: "[Help] Want to virtualise but what do I do with RAID?"
date: 2013-08-03
forum: Virtualisation
---

### Post by KillerKelvUK on 2013-08-03
I currently have a home server running 12.04.2, the hardware supports virtualisation and I've already played around with a few options but am stuck with the right approach.  I currently have a small mSata SSD for boot only, I also have 4x 2TB HDDs which I create a _software_ RAID10 volume with (mdadm) and then an lvm on-top the RAID.  I use the RAID simply as a filestore which is served using samba to my clients primarily for media playback.

I want to preserve the above approach but have several guests running on the host e.g. a guest for VMware Zimbra, another for log capture and analysis etc, primarily though I want to retain the RAID across the 4 disks and to continue serving this as a samba share, likely the other guests on the server won't even need to see/access the samba share as this is really for my clients e.g. media streaming.

I've been reading around about virtualisation to learn basically but I'm stuck with what approach I should be taking...

[LIST=1]
[*]Have been looking at Xen, even built a Xen 4.3 on my test box and successful got a Dom0 up and running.
[LIST]
[*]Can I use Xen to dedicate my 4x HDDs to a guest which can run the RAID array and serve using samba?
[*]Does this require some kind of "Passthrough" support e.g. Intel Vt-d on my CPU and mobo?
[/LIST]

[*]My mobo has RAID built into the EFI (fake raid), should I be re-creating the raid with this to simplify/achieve my goal?
[*]I've looked at VMware vSphere Hypervisor 5.1 but struggled to find the config/support (likely was searching using incorrect terms?)
[LIST]
[*]I did see and read up on VMware's DirectPath IO which sounds very much like "Passthrough" with Xen.  Still not sure what's limiting me with this however e.g no Vt-d support?
[/LIST]

[*]Finally I've done some reading about the free version of XenServer 6.1, I understand the free version doesn't support any dedication of devices to guests and that I'd need the commercial variant.
[/LIST]

Would appreciate any advice and/or points about what to search for and read.

Thanks,

K

---

### Post by TheFu on 2013-08-03
First, VMware makes like 6 different virtualization products. Some make sense for servers-only and some work for desktops only.  I worked at a company using ESX and ESXi with vsphere when VMware decided to screw around with the license agreements and cost model. Within 6 months, we'd dumped VMware-everything.  I won't be burned again and will not load VMware anything (not even Player) anywhere in the company or at home.  Karma is a bitch.

Second, we ran Xen systems here for 4 yrs.  About twice a year, always after a kernel update, the main physical servers would refuse to reboot and I'd have to manually drop back to the old kernel for 2 weeks or so, then move forward again. I opened a support case. Never saw any movement.  Xen is gone from here too.

KVM is built into the Linux kernel.  Guests don't need to know they are running inside a VM environment.  OpenStack, Redhat, IBM, and many, many others have thrown their support behind KVM as the defacto standard for Linux virtualiation.  There are more efficient methods for special case use, like LXC.  We switched to KVM slowly over the last 18 months or so.  It has **never** crashed a VM or a physical host. If has never refused to boot. It has never performed poorly, unless we didn't pre-allocate the storage in advance.

Ok, some random thoughts about your questions.
* FakeRAID usually requires an OS driver. Seldom, if ever, are their FakeRAID drivers for Linux - so that really isn't an option.
* If you want real RAID performance, get a nice hardware RAID card from LSI or 3Ware, but be prepared if the card fails for all that data to be inaccessible. In a home environment, it is hard to justify having a spare RAID card "just-in-case."  Software RAID is usually good enough and extremely flexible.  I've migrated complete external disk arrays with software RAID twice - zero issues.
* I've never used passthru access to partitions on a VM. Using direct img files has always performed more than good for our needs, but we're a small shop.  I can't imagine **any** passthru solution working without VT-d.

As long as you follow the best practices for performance of virtualization, all the RAID, LVM stuff probably isn't necessary.  Lots of VPS vendors use iSCSI or even NFS to provide storage for VMs.  Setting up an iSCSI network at home isn't hard. Might consider using AoE instead of iSCSI to get a little more performance.  It also lets you play with VM migrations, which you cannot do without network-storage for VMs.

You didn't way what sort of clients you want to run. This is an important question - if mostly servers, your choices are greater. If you want to run a local desktop with desktop OSes inside a VM and want good video GPU performance, then you've knocked out all but 2 options - VMware Player or VirtualBox.  KVM, Xen, ESX do not support local graphics, so accessing any desktop-like OS means going through a VNC layer or maybe a Spice layer from a different machine. ESX and ESXi need a Windows machine somewhere else to run vsphere to manage the ESX/i VMs.  It is possible to put the vsphere Windows machine inside a VM, but when there is an issue with that VM, how do you manage the ESX/i infrastructure?  I suppose if you have a fallback Windows machine somewhere, this can work.  I just hate the idea of running ESX and only Linux VMs, but being forced to have MS-Windows anywhere. Can't do it.

If your intent is to learn the coolest new tech that can get you paid - then either OpenStack or VMware ESX is where I'd spend my time.  For a small IT shop, these are overkill.  If you have less than 10 physical servers and 100 VM, then KVM + libvirt + virt-manager is perfect, simple, easy, and stable.  If you are in the USA, learning Redhat and getting a RHEL Cert can help you earn. Overseas, where redhat support is less or non-existent, this doesn't make any sense at all.

Sorry, if I missed any details that you specified that would have provided better assumptions.

---

### Post by keishou76 on 2013-08-04
1. You could keep the RAID like it is and let Dom0 in Xen own it and share it. Or keep it where it is and use KVM for your guest. Either way, you should not need to do any changes apart from installing Xen/KVM and don't need VT-d/AMD-Vi for it wither. Use Xen or KVM depending on what you like, want to learn or is able to get support from friends for.

2. No.

3. DirectPath IO is pretty much identical to passthrough with Xen (you can even do passthough of a videocard if you're lucky). With no VT-d or AMD-Vi support on your hardware, you can't use it. Xen is more likely to give more more devices to pass through then VMWare, especially USB controllers. And ESXi 5.1 can't pass through USB controllers due to a bug, use 5.0 instead if passthrough of USB controllers are needed. You can pass through USB devices, however.

My personal advice: Go with Xen or KVM. I manage ESXi clusters at work. It's great for a professional environment, but not so much at home, unless you want/need to train your professional skills, ESXi requires you to use a second machine to access the desktop of the guests, for instance. Using Xen or KVM, you can access them from the desktop of the host, since you have a desktop on the host. (At home I use Xen, Linux and ZFS for virtualization.)

---

### Post by KillerKelvUK on 2013-08-06
Thanks both for the feedback/advice, I've ditched VM and XenServer and successfully managed to stand-up a Xen 4.3.0 dom0 with PV and HVM guests.  I believe I achieved my goal of passing directly through one of my block devices so the guest can have full access, basically I RTFM and edited the xen config file and mapped the physical disk through.  So I'll look to replicate this for all 4 of my block devices and then use mdadm to rebuild the array from within the guest.

However you've both now go me interested in KVM so I'll start playing around with that now, this is all a learning exercise for me with little practical benefit in my work life.

Kudos to you both for the assist.

K

---

### Post by TheFu on 2013-08-06
Great!  Though you are the first person I've heard that elected to perform RAID **inside** the guests instead of at the hostOS level.

---

