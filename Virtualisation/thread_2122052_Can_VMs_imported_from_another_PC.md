---
title: "Can VMs imported from another PC"
date: 2013-03-03
forum: Virtualisation
---

### Post by satimis on 2013-03-03
Hi all,

Host - Ubuntu 12.04 desktop 64bit
Guest - Ubuntu 12.04 desktop/MSWindows Server 2008
Virtualizer - Oracel VirtualBox

I have following questions;

1)
Can VMs built on an AMD 4-core PC works on an AMD 8-core PC?
I have imported several VMs, Ubuntu 12.04 and Windows Server 2008 from AMD 4-core PC to an AMD 8-core PC. Those VMs are working on the former PC without problem. Re-config has been made on them after import such as networking, uname, etc. It comes to my notice that one/two Ubuntu 12.04 doesn't work properly such as broadcasting on web without sound, screen diming and then returning normal etc.

2)
Do I need to reinstall Guest Addition on a cloned VM?
I have to reinstall Guest Addition on cloned VMs

Please advise. TIA

B.R.
satimis

---

### Post by TheFu on 2013-03-06
In my experience, migrating a VM between machines works.  It is easier if I "export VM" than if I just move the VM.vdi/.vmdk/.img files around, however.
I have migrated VMs from ESXi --> vbox --> KVM this way.
From Xen-paravirtual --> to KVM is a little harder. Basically, the OS needed to be installed under KVM, then all the non-OS app and data files from Xen restored.

The real key to doing these migrations is to watch the virtualized hardware between the source and target VM.  ESXi defaults to an LSI disk controller. At the time, that specific controller driver was not available in either VBox or KVM or Xen.

I don't really use sound in VMs, sorry.  Check that the virtualized hardware is correct.

---

### Post by satimis on 2013-03-06
> **TheFu said:**
> 
I have migrated VMs from ESXi --> vbox --> KVM this way.

It is really interesting to me, migrating guests of vbox to KVM.

Could you please explain in more detail about the steps performed.  Thanks

Regards
satimis

---

### Post by TheFu on 2013-03-06
> **satimis said:**
> It is really interesting to me, migrating guests of vbox to KVM.

Could you please explain in more detail about the steps performed.  Thanks

Google for "virtualbox to kvm migration."  It is pretty easy, depending on your specific needs.  

There are caveats. Don't migrate desktops looking for better graphics performance.  Virtualbox is the best Free/OSS solution for desktop-on-desktop VMs today.  KVM is great for server-on-server virtualization.  I've migrated Xen, Vbox and ESXi VMs to KVM. These were for servers, except 1 office-productivity-type desktop, which I connect to using NX from the same room or 12 timezones away.

Always know the virtual hardware on the source VM and on the target VM. If these are easier today if you select virtIO for network, disks and ICH for everything else.  Remove things that do not work on the next virtual hardware ... like guest additions.

I don't have any detailed notes about vbox to KVM migrations, so it must have been trivial. Sorry. [http://blog.jdpfu.com/2012/10/23/remote-desktops-rock](http://blog.jdpfu.com/2012/10/23/remote-desktops-rock) is all that I have - the **vboxmanage** command was used.

---

### Post by satimis on 2013-03-06
> **TheFu said:**
> Google for "virtualbox to kvm migration."  It is pretty easy, depending on your specific needs.  

There are caveats. Don't migrate desktops looking for better graphics performance.  Virtualbox is the best Free/OSS solution for desktop-on-desktop VMs today.  KVM is great for server-on-server virtualization.  I've migrated Xen, Vbox and ESXi VMs to KVM. These were for servers, except 1 office-productivity-type desktop, which I connect to using NX from the same room or 12 timezones away.

Always know the virtual hardware on the source VM and on the target VM. If these are easier today if you select virtIO for network, disks and ICH for everything else.  Remove things that do not work on the next virtual hardware ... like guest additions.

I don't have any detailed notes about vbox to KVM migrations, so it must have been trivial. Sorry. [http://blog.jdpfu.com/2012/10/23/remote-desktops-rock](http://blog.jdpfu.com/2012/10/23/remote-desktops-rock) is all that I have - the **vboxmanage** command was used.

Thanks for your advice and link.

I found the steps via googling.  Also it is possible exporting virtualbox snapshot as a raw disk image.

When time allows I'll test vSwitch with KVM.  I have this plan pending for sometimes wondering that I have to create new guests.

Re remote desktop (I haven't run it sometime);
In the past:
for Linux and Linux I ran ssh with X forwarding
for Linux and Windows I ran VNC

B.R.
satimis

---

### Post by TheFu on 2013-03-06
> **satimis said:**
> 
Re remote desktop (I haven't run it sometime);
In the past:
for Linux and Linux I ran ssh with X forwarding
for Linux and Windows I ran VNC

On a LAN, VNC and X/Windows work fine. Over 14miles way, not so much, plus both a insecure without a VPN.
NX blows every other remote GUI tool away on performance ... perhaps the ICA stuff is close but I am not interested in that license cost.

Spice is supposed to be pretty good too. I've screwed with it on the LAN here, but found it lacking the stability I needed.  NX is very stable AND very secure AND trivial to setup and use.

---

