---
title: "KVM/Qemu hot failover on separate machine?"
date: 2014-01-09
forum: Virtualisation
---

### Post by 1clue on 2014-01-09
Hi,

I'm trying to set up a multi-subnet network which will be largely on VMs, including the networking appliances but which will also have physical machines on it.

What I want to do is have two or more KVM/Qemu hosts with multiple NICs in them.  The NICs will be donated to router/firewall VMs.  For safety, I want to duplicate the critical VMs (both networking-related and other) across the wire to the other host, so I have failover of the entire VM. I would configure critical networking components such that the entire system is contained in each VM, so if one host goes down I'm still up.

I've never tried this on Linux-KVM.  Is there somebody here who can make recommendations on how to proceed?

Thanks.

---

### Post by CharlesA on 2014-01-09
I don't know if this will do what you want, but it sounds like it will:
[https://pve.proxmox.com/wiki/High_Availability_Cluster](https://pve.proxmox.com/wiki/High_Availability_Cluster)

Also here:
[http://ubuntuforums.org/showthread.php?t=1952485](http://ubuntuforums.org/showthread.php?t=1952485)

:)

---

### Post by 1clue on 2014-01-09
Wow.

I guess I made an assumption that Proxmox was commercial software.  My bad.

Without having read the entire page, it appears that Proxmox is a contender.  That second link takes it a bit further, and it's my scenario too.

Thanks.

---

### Post by CharlesA on 2014-01-09
> **1clue said:**
> I guess I made an assumption that Proxmox was commercial software.  My bad.

It kinda is. You can use the free version, which is what I use at home, or you could get a subscription that has some benefits over the free version.

---

### Post by 1clue on 2014-01-09
Once you pointed it out, I paid more attention to the website than I had the first time through on my own.  I had originally dismissed it as payware, and since this is a SOHO project I wasn't all that interested.

Now I see it's sort of the Crossover/Wine type arrangement.  Which is fine IMO.

---

