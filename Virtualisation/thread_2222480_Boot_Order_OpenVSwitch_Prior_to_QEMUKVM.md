---
title: "Boot Order: OpenVSwitch Prior to QEMU/KVM"
date: 2014-05-06
forum: Virtualisation
---

### Post by jasonvp on 2014-05-06
Hey folks -

I'm at a bit of a loss here.  My Ubuntu server is running KVM with several VMs.  I'm also making use of OpenVSwitch for the VMs' networking.  The challenge that I'm running into is the run order of processes on the hypervisor.  I need the openvswitch-controller and openvswitch-switch init scripts to start before the libvirt management daemon.  By default, they start after libvirt, and only 1 of my VMs will auto-start given the unavailability of the VSwitch.

I can reproduce this at will by killing the VSwitch processes and then trying to start one of the VMs.  It won't go.  As soon as the VSwitch processes are running, it starts right up.

The openvswitch init scripts are linked to /etc/rc3.d as I'd expect (with an S20... prefix).  But libvirt's init script is nowhere to be found.  How's it started upon machine boot?  How do I force it to wait until the openvswitch daemons are running?

Thanks!

---

### Post by TheFu on 2014-05-09
Change the kvm startup to be delayed using **update-rc.d** -- that is just a guess. Isn't upstart great?

---

### Post by jasonvp on 2014-05-09
> **TheFu said:**
> Change the kvm startup to be delayed using **update-rc.d** -- that is just a guess. Isn't upstart great?

It's a good guess, but I don't think it'll work because KVM is started by its /etc/init script, not the scripts found in /etc/init.d.  Yes, upstart is great for... um..  hm.  I'm not sure, actually.

I think I actually figured out the problem, so I'll set this to solved.  The rc script for openvswitch's controller was set to run, but the rc script for the openvswitch switch was not.  Which is kinda interesting.  Anyway, I used update-rc.d to enable the actual switch script, and that appears to do the deed.

---

