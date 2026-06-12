---
title: "Help diagnosing a persistant kernel panic"
date: 2007-04-03
forum: Server Platforms
---

### Post by StarMonkee on 2007-04-03
I've got a dedicated mysql server using my-huge.cnf as it's config. The specs are:

2x AMD Opteron 280 (2.4ghz dual core)
12gb RAM
Areca ARC-1110 RAID card, with 4x200gb SATA in RAID10
Tyan S2882G3NR-D Motherboard (BIOS version 3.07)
Ethernet: Broadcom Corporation NetXtreme BCM5704 (this will become relevant).

It was running debian sarge (patched areca install) with a custom 2.6.15 kernel, and recently every 4-5 days I'd get a kernel panic and have to do a hard reboot to get everything running again.

I thought it might be the kernel, or something old in sarge causing troubles, so instead of building a custom kernel for Etch, I installed Ubuntu server (which has the arcmsr driver by default). Everything went perfectly for 4 days, and yesterday I got a kernel panic with an identical message to the debian install.

The actual message is:
[img]http://kris.essex-web.com/panic.jpg[/img]

tg3 is the network driver (which is why I noted the model). Google didn't seem to help.

I have another identical server which doesnt have this problem (same bios version, and it had the same sarge setup and kernel).

I'm not sure what the problem could be. Someone has recommended trying booting with 'acpi=off' to disable ACPI on the board. I'm also thinking it could be a hardware problem with the ethernet port.

My thoughts on what to try are:
- Update to Ubuntu 7.04
- Downgrade to 6.06 (apparently the tg3 driver is more stable in that release)
I'm not sure the above two will help, because I've had the same problems on 2 different kernels in 2 distro's
- Use acpi=off in grub but I've heard this can break SMP
- Try using another ethernet port on the motherboard (it's got 2 broadcom gigabit ports and one intel 100mbit one)

As the server is 50 miles away from my office and I have to arrange access to the data center to get in, I don't know which one(s) of the above might make a difference, so I'm hoping someone here will understand the problem and offer some definite advice. Also the server is a busy production mysql server so I really have to keep downtime to a minimum.

---

### Post by huygens on 2007-04-03
I do not know if it will help. But I had a problem with kernel cpu lock-up on my laptop (also using tg3 driver for the gigabit ethernet adapter). When looking at the log, tg3 messages were never far from the kernel crash...
However, the problem was only hardware and related to the motherboard (I started having the issue with the other OS installed on my laptop, which was XP, and Dell was able to diagnostic a motherboard problem from there). After changing the motherboard, everything went back to normal (without having to re-install the system!!)

Perhaps you are also experiencing a hardware problem that changing of distribution won't solve...
Just sharing my thought and experience... so take the above suggestion with care.

---

### Post by StarMonkee on 2007-04-03
Thanks, I am starting to think that myself.

I think the best first move would be to try another ethernet port. That way if it is the port then it should work, and if not then it may be the motherboard itself.

---

