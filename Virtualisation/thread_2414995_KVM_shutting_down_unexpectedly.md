---
title: "KVM shutting down unexpectedly"
date: 2019-03-18
forum: Virtualisation
---

### Post by logendrae on 2019-03-18
Hi there,

I'm running KVM on Ubuntu 16.4.6 LTS, and the VM is unexpectedly shut down often. Can you please help me to find out the root cause of this. Host is a DELL PE R430, which is a Ubuntu certified hardware.

Thanks in advance.
Regards,
Logendra

---

### Post by TheFu on 2019-03-18
I've had 1 Win7 VM "suspend" without any request for that about once a month the last year or so.  Traced it back to failing storage.  I'd changed the storage access from SATA to virtio and then SCSI drivers.

What sort of shutdown? Cold? Reboot? Suspend? Something else?

Other VMs, not running Windows, have continued running, most without any issues.  These are located on RAID1 storage where storage performance wasn't as important.

On the same VM host, all internet networking would drop from 1 VM occasionally. After 2 of those failures, that VM was moved to a different VM host and the issue hasn't happened again. None of the other VM guests were impacted, even those sharing the same bridge.  I never figured out how the VM with internet connection issues, configured like 8 other Ubuntu Server VMs - same bridge, all static IPs, all virtio drivers - would have any different results.

My VM host was running 14.04.5 at the time, but it had run 14.04.4/3 as well.

Anyway, to help lots more facts will be necessary.  Which drivers (network, storage, video, others)? Which model motherboard is emulated?  What is the guest OS? What is the storage backend - KVM/QEMU has like 15 different backend storage options.

Anything in the logs for the guests and the host?

---

### Post by logendrae on 2019-03-19
Hi TheFu,

Thanks for your response. The VM is completely cold shut down. There are no issue with the hardware, we have confirmed with DELL support. I was going through the libvirtd.log file, but unable to find any clue, all seems to be normal. Let me wait for next unexpected shutdown, and see whether i can find some clue for this strange behavior, and we can start from there. Again, thanks for your time.

Cheers,
Logendra

---

### Post by TheFu on 2019-03-19
Sorry - I said RAID5 storage, but we moved to RAID1 years ago when we swapped out the 320G disks for 2TB disks. Don't think that matters.  I'll fix my post above to reflect it.  We're currently planning to move to a new host with an NVMe SSD for most VMs.

I have doubts about Dell Support recognizing hardware issues.

I asked a number of questions. No answers? There have been strange interactions.

---

### Post by logendrae on 2019-03-26
Hi TheFu,

DELL Support engineer has confirmed that there are no hardware related issues on the box, after upgrading Storage controller, BIOS and iDRAC firmware. But I can see, that the following error message on the console. Appreciate, if you could feedback by looking at the error, DELL Support suggest to escalate to Ubuntu support.

[ 39.673582 ] kvm [2883]: vcpu3 unhandled rdmsr: 0x34
[ 39.673775 ] kmm [2883]: vcpu3 unhandled rdmsr: 0x606

But, still i did not experience the unexpected KVM shutdown. Please shed some lights around this issue.

Thanks,
Logendra

---

### Post by Doug S on 2019-03-26
> **logendrae said:**
> ... But I can see, that the following error message on the console. Appreciate, if you could feedback by looking at the error, DELL Support suggest to escalate to Ubuntu support.

[ 39.673582 ] kvm [2883]: vcpu3 unhandled rdmsr: 0x34
[ 39.673775 ] kmm [2883]: vcpu3 unhandled rdmsr: 0x606
They indicate that the MSR (Machine Specific Registers) don't actually exist in your virtual CPU. I get those, or similar, errors/warnings when I run VM's and have always ignored them.

I don't have any good ideas about your main issue.

---

### Post by houstonbofh on 2019-03-27
Is it only one VM that is shutting down?

---

### Post by TheFu on 2019-03-27
I think the OP believes this is formal Canonical support.  We are not.  Nobody here works for Canonical. Just volunteers.

> 
Anyway, to help lots more facts will be necessary. Which drivers (network, storage, video, others)? Which model motherboard is emulated? What is the guest OS? What is the storage backend - KVM/QEMU has like 15 different backend storage options.

Anything in the logs for the guests and the host? 

---

