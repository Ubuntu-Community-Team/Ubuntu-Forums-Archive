---
title: "Virtualization flavour of the month"
date: 2017-05-11
forum: Virtualisation
---

### Post by teknopaul on 2017-05-11
What is the Ubuntu Virtualization flavour of the month.  I want to create RPMs, and attempts with alien and cross-compiling tricks within Ubuntu are not working for me.

I need a minimal CentOS with gcc and rpmbuild, (no gui) ideally scriptable setup.

XEN borked grub, took a while to get my laptop able to boot again.
LXC/D works fine but does not work with redhat RPM builds, somehow picks up glibc deps from the Ubuntu kernel.
virt-install with default options as root either paniks or enters infinite loop at 100% CPU.  Should I be using some specific quemu version/setup?

Running new laptop hardware with Intel(R) Core(TM) i7-6700T CPU @ 2.80GHz

    kvm-ok
    INFO: /dev/kvm exists
    KVM acceleration can be used

Modern standard ubuntu kernel Linux 4.4.0-77-generic

stretch/sid  Ubuntu 16.04 LTS

---

### Post by vasa1 on 2017-05-11
> **teknopaul said:**
> ...
    kvm-ok
    INFO: /dev/kvm exists
    KVM acceleration can be used

Modern standard ubuntu kernel Linux 4.4.0-77-generic

stretch/sid  Ubuntu 16.04 LTS

Which command did you use to generate the above information?
What is "Modern standard ubuntu kernel"?
What is "stretch/sid  Ubuntu 16.04 LTS"?

---

### Post by teknopaul on 2017-05-12
kvm-ok  is the command, it outputs

 INFO: /dev/kvm exists
KVM acceleration can be used

"Modern standard ubuntu kernel"  is one that is downloaded from apt repos with no messing around, I mean by that I have not done anything complicated and I am running a "standard" Ubuntu, and I'm looking for a "standard" virtualization solution.  I'm aware that "standard" changes over time. I use LXC for preference, but its not a good fit in this case.

stretch/sid
is the output from cat /etc/debian_version

I presume you do really know what "Ubuntu 16.04 LTS" is?

---

### Post by vasa1 on 2017-05-12
> **teknopaul said:**
> ...
I presume you do really know what "Ubuntu 16.04 LTS" is?
I'll leave that to you.

But I really do not know what "stretch/sid Ubuntu 16.04 LTS" is which is what I asked :)

---

### Post by TheFu on 2017-05-12
LXD and LXD are not virtualization. Containers are not virtualization.
Xen has been problematic on Ubuntu for years - since before 2010. I ran Xen for a few years.
KVM is the default whole machine virtualization on Ubuntu and has been extremely stable since 2010. Personal experience.

You probably want to find a KVM *how-to* that achieves your desired outcome.  
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Desktop users will want different things than server users. Similarly, people deploying 50 physical servers for VMs will want different things that a 1 or 2 physical server setup or a 500-50K server setup.  Just depends on what you want and how you want to manage things which is the right stuff to use.  Few people directly use kvm.  We tend to use virt-install, virsh, and/or virt-manager.   I use libvirt to help with management.  On a RHEL system, folks tend to use oVirt (which is a mess of 30+ projects) which provides a web interface into VMs for end-users and admins. oVirt needs a dedicated machine just for it, really. oVirt is a layer over libvirt, like most of these tools are.  Don't think it works on an ubuntu host.

If you want networking, there are a few choices to make too - depending on the complexity of your network needs and the type of throughput.  Home users can get by with normal bridge-utils, but if you have 10Gbps or many different NICs in your servers, you'll want openvswitch. It is more complex to setup, but provides more throughput.
I've never had luck with the default networking provided by virt-manager.  Poor performance and dropped packets, but I haven't bothered with it in 5+ yrs. Have a solution that works, so why screw around?

Then there's virtualbox.  This is VERY popular among desktop Ubuntu users.  Last time I tried it (after years as a Windows virtualbox user), it locked up my entire machine.  BTW, that exact, same, machine has been running KVM 24/7/365 with 10-20 VMs the last 5+ yrs. Rock solid on that and many other systems.

I even run KVM and a few VMs on my chromebook.  Rock solid, provided you understand the resources required.

Anyway, hope this is helpful. Post back what you want and the type of environment and we can probably make better suggestions.  The "standard virtualization" answer is kvm.  I've never used alien and don't mix debian stuff with Ubuntu stuff, unless I'm extremely desperate. That hasn't happened in many, many, years.

BTW, we are more likely to look at /etc/lsb-release, not the debian-version.

---

### Post by vasa1 on 2017-05-12
> **TheFu said:**
> ...
BTW, we are more likely to look at /etc/lsb-release, not the debian-version.
And it's more usual to provide information with```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```
and```
uname -a
Linux vasa1-Inspiron-1545 4.4.0-77-generic #98-Ubuntu SMP Wed Apr 26 08:34:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
As regards,> Then there's virtualbox. This is VERY popular among desktop Ubuntu users.Part of the reason could be that Vbox used to work (sufficiently to check out other distros) on hardware that failed *kvm-ok*.

---

