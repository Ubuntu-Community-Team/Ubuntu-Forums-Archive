---
title: "Can't get near theoretical network maximum speed"
date: 2010-03-10
forum: Server Platforms
---

### Post by sherl0k on 2010-03-10
[img]http://shiningpolaris.com/images/thrashing.png[/img]

With three 1.5TB, 7200RPM drives in RAID0, they thrash. And yet the network out, 4 gigabit ports LAG'd together to create a single 4 gigabit connection, can't even push a single gigabit a second.

Here's what I've done so far:

I've enabled jumbo frames on the bond:
ifconfig bond0 mtu 9000

Tweaked SAMBA performance:
socket options=TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=65536 SO_SNDBUF=65536
use mmap = no
use sendfile = yes
blocking locks = no

Tweaked hdparm:
hdparm -a 2048 /dev/mapper/isw_images


I haven't enabled jumbo frames on the switch but I'm almost sure that won't help me much after trying all this.

I'm running out of ideas here guys. The clients connected are pulling down images in both Ghost and WIM (ImageX) format. Large files too, upwards of 12 gigabytes.

---

### Post by juancarlospaco on 2010-03-10
Samba (SMB) is the slowest protocol i ever used to transfer files.
Use something more Unix-like, NFS, SSH, and such.

I think you need a good Cisco Layer3 Switch, 
configured properly, remember that the CPU power is important,
or store'n'forward things, broadcast storm monitoring.

---

### Post by sherl0k on 2010-03-10
Servers are i7's and we're using linksys gigabit switches.

Because clients are Windows-based, SAMBA is the practical route to choose.

---

### Post by BobVila on 2010-03-11
> **sherl0k said:**
> 

With three 1.5TB, 7200RPM drives in RAID0, they thrash. And yet the network out, 4 gigabit ports LAG'd together to create a single 4 gigabit connection, can't even push a single gigabit a second.

Here's what I've done so far:

I've enabled jumbo frames on the bond:
ifconfig bond0 mtu 9000

Tweaked SAMBA performance:
socket options=TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=65536 SO_SNDBUF=65536
use mmap = no
use sendfile = yes
blocking locks = no

Tweaked hdparm:
hdparm -a 2048 /dev/mapper/isw_images


I haven't enabled jumbo frames on the switch but I'm almost sure that won't help me much after trying all this.

I'm running out of ideas here guys. The clients connected are pulling down images in both Ghost and WIM (ImageX) format. Large files too, upwards of 12 gigabytes.

I'd enable jumbo frames on the switch just so you can rule out weird fragmentation issues. Also, if there's another machine around, run some iperf tests in both TCP and UDP mode. Results from those would be helpful.

---

### Post by wirelessmonkey on 2010-03-11
Your linksys devices are probably single crossbar, with a slow backplane, and low processing power.  

Your NICs, unless fully integrated or on multiple full speed pci bus', running 64 bit driver code, are unlikely to be getting anywhere near their full speed.

Samba is slow. Multiple SMB connections slow it further.

There's 3 fairly good reasons.


Best of Luck.

---

### Post by Xianath on 2010-03-12
Are you sure jumbo frames are actually in use by the NICs? Broadcom Nextreme II NICs are notorious for ignoring pretty much any kernel network tunable (notably MTU and PMTU related). In this case I've found that the only thing to do was to disable the segmentation offloading engine altogether.

Also, consider tuning TCP windows sizes to at least 2*bandwidth*RTT. If client machines are running recent Windows OS'es like Vista/2008/Win7, try disabling TCP autotuning and TCP chimney:

```
netsh interface tcp set global autotuninglevel=disabled chinmey=disabled
```
It could also be a Nagle/DACK issue. Try disabling Nagle on the server side and delayed ACKs on the client side.

Your best bet is to run a network analyzer and look for clues. For example, 200ms delays then bursts would be a pretty clear giveaway of a Nagle/DACK issue, and of course an incorrect MTU size would stick out like a sore thumb.

Those are all shots in the dark of course. Try some of them anyway, might be your lucky day.

Cheers,
Peter

---

### Post by sherl0k on 2010-03-13
Thanks for the suggestion, I'll check on the autotuning level. They're WinPE (Vista) clients so I'll give that setting a shot and see what happens.

The NICs are actually only one - an Intel quad gigabit NIC. I would hope that a card costing upwards of $400 wouldn't ignore jumbo frames. :-)

---

