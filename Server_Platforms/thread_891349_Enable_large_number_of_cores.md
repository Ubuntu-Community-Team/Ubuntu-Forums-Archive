---
title: "Enable large number of cores?"
date: 2008-08-16
forum: Server Platforms
---

### Post by xcaret on 2008-08-16
Hi,

I am trying to run Ubuntu 8.04.1 (2.6.24-19-server) on a machine that has 4 quad-core processors. However, I can only see 8 processors when I look at /proc/cpuinfo instead of the 16 I was expecting. Any ideas what I can do to fix this? The processors are Intel Xeon E7330s.

Thanks!

---

### Post by xcaret on 2008-08-16
I looked at the .config file for the kernel I am running and it specified CONFIG_NR_CPUS=8. That is a bummer as it means that I will have to recompile the kernel if I want it to work. Given that Ubuntu Server is targeted towards larger server platforms, I am surprised that NR_CPUS is not set to 32.

Cheers.

---

### Post by windependence on 2008-08-16
Good to know. I was not aware of that. I just had to take Ubuntu off one of my dual quad core servers because it would be stable for about 2-3 days and then kernel panic. SuSE is happily running on it now.

-Tim

---

### Post by insane_alien on 2008-08-16
i seriously doubt that config setting was the cause of your kernel panics. good to hear you got it working though.

and i do agree that the max number of cores whould be bumped up as intels next gen processors will have 8 cores on a single CPU. so multi processor servers would be right out except with a custom kernel. and that situation will only get worse with time. set it to 64 and you need not be concerned for a few years.

---

### Post by windependence on 2008-08-16
No, no, I never meant to infer that the panics were caused by that config setting but there are already 8 cores on that machine. It was most likely caused by an incompatible driver for my SCSI DLT tape drive, and I don't have time to futz with it to get it working, not to mention that it would take days to test it each time I made a change. I was really hoping it would work as I like the idea Canonical has putting out a server distro without a GUI installed by default along with the other kernel optimizations.

-Tim

---

### Post by Krupski on 2008-08-18
> **xcaret said:**
> Hi,

I am trying to run Ubuntu 8.04.1 (2.6.24-19-server) on a machine that has 4 quad-core processors. However, I can only see 8 processors when I look at /proc/cpuinfo instead of the 16 I was expecting. Any ideas what I can do to fix this? The processors are Intel Xeon E7330s.

Thanks!

This is sorta off topic (sorry) but I'm curious:

I built several NAS boxes running Ubuntu 8.04.1 Server 64 bit with Intel motherboards and Core 2 Duo CPU's (only dual core) and 8GB ram.

I find that with heavy network traffic, the HARD DRIVES (SATA-300) are the bottleneck. The gigabit LAN and the CPU usage are always typically low.

So my curious question is... why are you running so many processor cores? What advantage do you find using them? Am I possibly doing something wrong with my setup that makes my CPU usage always low?

Thanks in advance!

-- Roger

---

### Post by fjgaude on 2008-08-18
Disk I/O is usually the bottleneck... thus the big raid arrays with thruputs of up to 500MB/sec.

Modern, just out drives, have read thruputs of over 115MB/sec, and with 8 of those in raid5 or raid6 will have some great I/O. Just two years ago our drives were, are at 50-70 MB/sec.

What kinds of drives are yours?

---

