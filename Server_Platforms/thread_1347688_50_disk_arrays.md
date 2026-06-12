---
title: "50 disk arrays"
date: 2009-12-06
forum: Server Platforms
---

### Post by Vegan on 2009-12-06
I noticed a couple of vendors of 8U 100 TB storage servers. So can Linux tell me which disk is sick?

I assume RAID6 will be used for obvious reasons.

They plug right into the LAN. 10 of them for a 1 PB system.

Linux up to it?

---

### Post by insane_alien on 2009-12-06
Linux could yes, but it is highly probable that the device itself will detect it, throw up an indicator light on the device itself and send out an ICMP packet that tells a service running on one of the admins computers that a disk has went down and he better go replace it pronto.

---

### Post by Vegan on 2009-12-06
I use my Windows machine as my main workstation. I use Linux as a server appliance.

So I am correct that signals are available all over to identify a failed disk. In RAID6 you get 2 dead disks before the array fails.

So I wanted to be aware of sick disks, some message or another to alert a sleepy operator.

---

### Post by falconindy on 2009-12-06
> 1 PB system
[img]http://www.dangerousminds.net/images/uploads/pedobear.jpg[/img]
Got nothin'.

---

