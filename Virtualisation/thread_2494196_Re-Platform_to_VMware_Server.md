---
title: "Re-Platform to VMware Server"
date: 2024-01-08
forum: Virtualisation
---

### Post by stevefxp on 2024-01-08
Hello all,

I am migrating/re-platforming a CentOS 7.9.2009 physical server to a VMware virtual server, with Ubuntu 22.04.3 being the new OS. As I begin this journey I want to ensure that I am on the best LTS for not only the OS but the kernel. I see that HWE is available and that will give me kernel 6.2, but it looks like kernel 6.6 is the next LTS kernel. Has anyone combined Ubuntu 22.04.3 and kernel 6.6 on a VMware virtual instance? Am I barking up a bad tree?

Thanks,
Steve

---

### Post by SeijiSensei on 2024-01-08
What specific features of that kernel do you need? Unless you can identify why you need that kernel, just accept the defaults.

I'd consider Debian 12 as well. It comes with 6.1.0 by default.

---

### Post by stevefxp on 2024-01-08
> **SeijiSensei said:**
> What specific features of that kernel do you need? Unless you can identify why you need that kernel, just accept the defaults.

I'd consider Debian 12 as well. It comes with 6.1.0 by default.

Its not about what features I need...its really about LTS and having both the kernel/OS on the right LTS stream. Right now I see HWE supports kernel 6.2 but its not LTS, so my thought process was to move to 6.8 since its the latest LTS.

---

### Post by TheFu on 2024-01-08
BTW "VMware Server" as a product was discontinued over a decade ago. I think the last time I saw it used with support was around 2008.  VMware isn't known for supporting the newest kernels and certainly not on any unsupported product.

VMware makes lots of different hypervisor products, so it is important to be very, very, clear on which hypervisor you will use.  Bleeding edge kernels have been known to cause problems with VMware ESXi, which is likely what you really are talking about using - at least I hope so.

---

### Post by stevefxp on 2024-01-09
Lol...yes it will be a virtual server on an ESXi hypervisor.

---

### Post by TheFu on 2024-01-09
> **stevefxp said:**
> Lol...yes it will be a virtual server on an ESXi hypervisor.

Beware that Canonical LTS kernels have NOTHING to do with kernel.org LTS.  Zero. nada.  Right now, I'm on 5.15.x across all my Ubuntu systems (20.04 and 22.04) and I only run LTS in production.

I can't help with ESXi.  When VMware screwed over their customers around 2011, we dropped them and took all our clients to KVM/QEMU instead.  By far, that has been the best virtualization choice we've ever made and I started with VMs in the late 1990s.  I ran VMware Server, Workstation, ESX, ESXi, Player, Virtualbox, Xen, and a few others.  KVM/QEMU with libvirt is the most flexible and fastest, regardless of what VMware marketing claims. If you want to do anything that isn't buijlt-in, expect a $1000-$20K bill.  For example, want a VMware ESXi-aware backup tool?  I think the cheapest is $1000 and it didn't do versioned backups.  Every backup was a full backup and if you have large storage, it can take hours and blow the backup window.  At one client, we had to split backups into even-odd days to complete backups within the allowed nightly window.

VMware ESXi is good for 2 reasons.
a) Nobody gets fired for choosing it.
b) 1 phone call to blame someone else. Lots of companies like that, regardless of what is actually best. For them, it is about having a support number who will come out tomorrow for $300/hr and work the issue.  

I've worked places like this and we demanded support. At one place, we had multiple on-sight VMware engineers, basically extending our architecture staff and helping out in our labs before we made choices.

Getting off CentOS and skipping RHEL in a corporate environment seems odd.  VMware isn't exactly cheaper.  There aren't any free ESXi licenses that can be used in production, if that's the plan.

If you treat your VMs like physical machines, especially for backups, then the hypervisor doesn't matter. We switched to this method using F/LOSS backup tools and dropped backups from over 8 hrs nightly to less than 1 hour and we got versioned backups. Today, we have 90-365 days of daily, automatic, backups and they don't take all that much storage. It is really impressive.  OTOH, a restore isn't 1 command - so there are trade-offs, but a restore for any single system is less than 45 minutes, often between 15 and 30 minutes for nearly all our servers.  I can't see any reason that this wouldn't work regardless of the hypervisor.  I use the same method for our LXC containers too.

---

### Post by SeijiSensei on 2024-01-09
> **TheFu said:**
> b) 1 phone call to blame someone else. Lots of companies like that, regardless of what is actually best. For them, it is about having a support number who will come out tomorrow for $300/hr and work the issue.
Truer words were never spoken.

---

### Post by MAFoElffen on 2024-01-09
Right now (today) Jammy 22.04.3 LTS is 6.2.0-39-generic. Dev-Noble 24.04 (LTS) is not officially released until April. It is currently on Kernel 6.6.0-14...

We are not RHEL branch, and Long Term Support Releases in Debian Branch work a bit differently. That is why Debian Branch has a reputation for "Stability". That is why, especial for Server Edition, we stay with LTS releases.

Yes, I do Dev-Testing, but that is a choice to test & verify things for the Server Team, the Community, and for Ubuntu. For a daily driver, I use LTS. I

I personally use the HWE stack, but that is not the norm with server.

---

