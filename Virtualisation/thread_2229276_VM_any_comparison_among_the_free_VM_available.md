---
title: "VM: any comparison among the free VM available?"
date: 2014-06-12
forum: Virtualisation
---

### Post by fernandojosecabral on 2014-06-12
I am not unhappy with Oracle VirtualBox. Nevertheless, I have been hit by the curiosity bug about other virtual machines.
Can any one there point me towards some comparison among the freely available VM? Any bare metal VM available?

---

### Post by slickymaster on 2014-06-12
Myself, I do like Oracle's VirtualBox and so far haven't find any major issues to nag about it.

Anyway, not sure if it fits your requirements but I was able to find this (it's a start at least):
[Compare Open Source (Free) Virtualization Software]("http://virtualization.findthebest.com/d/l/Open-Source-(Free)")
[Compare Virtualization Software & Hypervisors]("http://virtualization.findthebest.com/")
[VMware Player vs. VirtualBox: performance comparison]("http://xmodulo.com/2013/07/vmware-player-vs-virtualbox-performance-comparison.html")

---

### Post by fernandojosecabral on 2014-06-12
Slickymaster, thank you for pointing me these links.

[Compare Open Source (Free) Virtualization Software]("http://virtualization.findthebest.com/d/l/Open-Source-%28Free%29")
[Compare Virtualization Software & Hypervisors]("http://virtualization.findthebest.com/")
[VMware Player vs. VirtualBox: performance comparison]("http://xmodulo.com/2013/07/vmware-player-vs-virtualbox-performance-comparison.html")

---

### Post by TheFu on 2014-06-12
I've used most of them over the years.  What is needed for desktop virtualization on the same machine is **very** different from what is needed for server or for remote desktops.

Looking for "bare metal VMs" really doesn't make sense for home users.  It means that supported hardware is EXTREMELY limited - out of 7 systems here, only 1 can run VMware ESXi due to the exact, specific, hardware required. Sadly, that has only gotten worse in recent years.  Of course thousands of people will chime in and say they didn't have any issue with their 1 machine. Fine. When picking VM hardware (I like to build 'em, not buy 'em), I've learned to get stuff supoprted by ESXi, if I can afford it.

Below is ***my opinion*** on each. Grouped by Server, then Desktop VM technologies.

**Servers**
* **KVM** - my current choice for servers and remote desktops. Extremely stable, fastest VMs out there of the HVM type, SPEC-Virt agrees. KVM is part of the Linux kernel and maintained by that team.
* Xen - previously ran production paravirtual systems on Xen. It was stable, once running and fast. 4-10 times annually, after a kernel update, the entire physical machine would refuse to boot.  That exact, same, machine has been running KVM for 2+ yrs. Once booted, not issues.  I understand that with CentOS, the refuse-to-boot issue never happened.  Xen has probably solved the stability issue by now.  Also, if you need dedicated video card passthru for Windows gaming, Xen and extremely specific CPUs, BIOS, and video cards appear to be the only way to do this. People claim 95% of native video performance for high-end games running inside a Windows VM.
* VMware ESX - replaced by ESXi - required a Windows desktop to manage it through vSphere. That just rubbed me wrong. Extremely stable. Fast. Closed source.
* VMware ESXi - see ESX - "bare metal hypervisor" meh. Fast. Treat a VM like a real machine.  Lots of commercial 3rd party support. Expect to pay for everything. After VMware management screwed around with license terms about 3 yrs ago - which would **double costs for our clients** - we made a concerted effort to dump everything from VMware. 6 months later, we were done. "Fool me once, shame on you ...." Never again.  If you look at the VMware corporate pedigree, it becomes clear where they learned to milk customers for every dime possible. Closed source.
* LXC - Linux containers. Hard to get started, steep learning curve. Currently, not well supported by libvirt and virt-manager. Needs to be easier for more use.
* OpenVZ - similar to paravirtual VMs under Xen.  Hopefully CharlesA will respond on this with his proxmox knowledge. I remember him liking Proxmox, OpenVZ and KVM.  Also know a few VoIP shops that use openvz for their virtualization. This is paravirtualization, not HVM.
* Docker - up and coming VM solution based on containers/jails. Probably too new for production use, but maturing rapidly. It will have the same issues with complex networking that openvz, lxc, uml, and jails have. Plus VMs cannot load kernel modules that the hostOS doesn't load.

**Desktops**
* VMware Workstation - amazing product for a price. However, I won't be fooled by VMware again. Suitable for commercial use, especially for testing teams on Windows. Closed source.
* VMware player - comparable to VBox. Only made free due to vbox. Closed source.
* **Oracle VirtualBox** - probably the best of the pseudo-free choices. Most corporate users are violating the license. Read the *guest additions* license carefully folks.  Had stability issues on some hostOS (brought down the entire hostOS, not just 1 VM).  Not suitable to run servers, IMHO.  Plus there is the entire "oracle-kills-F/LOSS" issue.
* Parallels - don't know anything about Mac stuff. Closed source.

Just for completeness these products are dead, but once in a while someone will ask about them:
* VMware Server
* UML

Microsoft Offerings - I haven't a clue. Never used them. I have stories about very large clients being sold Azure when it clearly couldn't provide what the salemen sold to extremely large (Fortune 50) corporations. I know 1 of them has deployed OpenStack since that time on over 2,000 physical systems. They have some issues with openstack too, but ... nothing is perfect.

**Summary:**
So ... for servers, today, I'd go with KVM and watch carefully for LXC and/or Docker solutions in the future.
For desktops, today, VirtualBox, but only if the VM runs on the same hardware I'm sitting behind and not used for Windows gaming.  Carefully read the license for the Guest Additions to ensure something you don't want isn't forced onto you.

Sorry that was so long. It is full of opinions. Hopefully others will provide balance.

---

