---
title: "Udev renaming NIC eth2_rename_ren"
date: 2009-08-28
forum: Server Platforms
---

### Post by Gen2ly on 2009-08-28
Just installed a new network card in my computer and booted up and udev has trouble naming it:

```
# ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:14:d1:19:6b:70  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2052 (2.0 KiB)

eth0      Link encap:Ethernet  HWaddr 00:30:65:98:3f:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x2c00 

eth1      Link encap:Ethernet  HWaddr 00:14:d1:19:6b:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:53 

eth2_rename_ren Link encap:Ethernet  HWaddr 00:14:d1:17:52:73  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:54 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29682 (28.9 KiB)  TX bytes:29682 (28.9 KiB)
```

I think this has to do with eth1 and eth2 having nearly the same MAC address (same manufacture and type).  When I try to start networking I get errors because it can't locate eth2:

```
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
```

Any experienced this or have an idea on how to fix it?

---

### Post by Gen2ly on 2009-08-28
Well edited /etc/network/interfaces and replace eth2 with eth2_rename_ren and it appears to be ok.  So considering solved.

For any interested the only thing I could find on the internet referencing this is from a couple novell guys and they wrote some new udev rules to prevent renaming.  It didn't work for me and don't know enough about udev to fix:

[https://bugzilla.novell.com/show_bug.cgi?id=365501](https://bugzilla.novell.com/show_bug.cgi?id=365501)

---

### Post by Iowan on 2009-08-29
Now that it's a moot point...
Did you consider editing the udev file and "renaming" it back?
... or did udev just re-rename it?
Glad you found a solution.

---

### Post by Gen2ly on 2009-08-29
Yeah, I did discover that with /etc/udev/rules.d/70-persistent-net.rules I could rename devices and that they'll be persistent too.  Definitely a much better way of doing this.  Appreciate the tip.

---

