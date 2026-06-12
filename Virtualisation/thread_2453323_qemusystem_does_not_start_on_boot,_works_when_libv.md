---
title: "qemu:///system does not start on boot, works when libvirtd is restarted"
date: 2020-11-07
forum: Virtualisation
---

### Post by jwbrase on 2020-11-07
I have a VM set to start on boot, and libvirtd itself does indeed start. However, qemu:///system fails to come up at boot, along with all of its VMs. If I try to access it in virt-manager, I get a connection refused error on /var/run/libvirt/libvirt-sock . Web searches have come up with results with remedies for /var/run/libvirt/sock not existing (but it exists in my case), and for other errors in connecting to the socket than "connection refused", but I haven't found any remedy for exactly this issue.

Simply restarting libvirtd does bring up qemu:///system and its VMs, but this is a manual step after boot. It almost seems like libvirtd is being brought up before one of its prerequisites, or something like that.

Can anyone provide insight?

---

### Post by ajgreeny on 2020-11-08
I use KVM/QEMU but have no need to start any VM at boot.

However, it may be worth adding a **sleep 20s** to the autostart command, wherever that is, to delay the start of virt-manager by 20 seconds; you may have to try other time delays if that is not long enough to allow the prerequisite to start before virt-manager.

---

### Post by jwbrase on 2020-11-08
> **ajgreeny said:**
> I use KVM/QEMU but have no need to start any VM at boot.

However, it may be worth adding a **sleep 20s** to the autostart command, wherever that is, to delay the start of virt-manager by 20 seconds; you may have to try other time delays if that is not long enough to allow the prerequisite to start before virt-manager.

No, virt-manager is not being started at boot, or even with my X session. You're confusing virt-manager with libvirtd. libvirtd is a daemon started at boot time, that should be bringing up the VM in question when it starts. virt-manager is a graphical application for managing virtual machines. It can manage both virtual machines that are and aren't handled by libvirtd. When I start virt-manager, it is able to pick up user-specific VMs in qemu:///session (which aren't handled by libvirtd), but it is unable to pick up system VMs in qemu:///system (because libvirtd has failed to set up qemu:///session), until I restart libvirtd. As soon as libvirtd is restarted, the VMs come up, whether or not I have virt-manager open.

---

### Post by ajgreeny on 2020-11-09
Fair enough; I am fairly new to KVM/QEMU, so I was a bit confused.
Nevertheless, it may be worth trying to add a delay to the start of libvirtd to make sure that whatever is missing in your system is up and running before libvirtd tries to start.

I'm not sure how to do that or how it is supposed to start at boot but there must be some way to do it; perhaps a system process of some sort?

---

### Post by jwbrase on 2020-11-10
The various systemd unit files are supposed to contain dependency information that systemd uses to make sure that it starts services after the services they need. I suspect something there may be misconfigured, but I am not certain. In any case, if it is indeed a matter of libvirtd starting before things it depends on, it would be a matter of reconfiguring the dependencies in the unit files than of adding an explicit delay to the startup of libvirtd.

---

### Post by ActionParsnip on 2020-11-11
If you make /etc/rc.local then mark it as executable with
```

exit 0

```
As the last line then you can add the restart command to the boot up easily #oldschool

---

