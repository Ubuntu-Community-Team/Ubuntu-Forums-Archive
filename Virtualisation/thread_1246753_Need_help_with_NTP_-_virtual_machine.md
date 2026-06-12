---
title: "Need help with NTP - virtual machine"
date: 2009-08-22
forum: Virtualisation
---

### Post by ruipedroca on 2009-08-22
Hi,

Can someone please shed some light here?:
I have a fedora virtual machine that's working for more than a year, always with correct time, which is NTP set to my hypervisor (vmware server by the way).

About a week ago, I've set up an ubuntu 904 virtual machine and after that the fedora time started to accelerate about an hour per day.
But the ubuntu machine is also set up with NTP and its time is always correct.

I've tried some changes, but nothing works and I'm feeling tired about this issue. 

How could this be possible?

---

### Post by rjking on 2009-08-22
There are some known issues with Ubuntu Host/VMs and NTP (try searching the forums here). Any reason you're not syncing to an external NTP server (like the ones found at [http://www.pool.ntp.org/)?](http://www.pool.ntp.org/)?)

---

### Post by ruipedroca on 2009-08-26
> **rjking said:**
> There are some known issues with Ubuntu Host/VMs and NTP (try searching the forums here). Any reason you're not syncing to an external NTP server (like the ones found at [http://www.pool.ntp.org/)?](http://www.pool.ntp.org/)?)

Thanks, I'm aware of those issues and I had already dealt with them, namely, the cpu clock.

But I have found the problem/solution to my particular case:

I had 2 ntp client machines with the same broadcast client ip address (both ending on .255) in ntp.conf.

When I changed one to .253 and restarted the the machines, including the servers, they all became working correctly.

Regarding that public NTP server, I didn't try it because I was syncing to my internal ntp server.

Regards

---

