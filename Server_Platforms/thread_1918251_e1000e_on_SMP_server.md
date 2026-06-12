---
title: "e1000e on SMP server"
date: 2012-01-31
forum: Server Platforms
---

### Post by ersatzsplatt on 2012-01-31
I have a server install on a system with an Intel gigabit chip (82574L).  The driver for this loads automatically (yay) ... but then I don't see any connectivity.  :frown:  My first suspicion was dhclient ... but that does not seem to be a problem when the same disk is in another system (with a different ethernet conroller).  When I run another Linux install (FC) on the same system, the network connection seems to be fine.  I have seen some posts about the e1000e driver having problems years ago ... is it really still broken on the latest up-to-date server install?  If so, I suppose I could try to patch and build the driver.  ... but wouldn't it be better to fix it for everyone?

Maybe it is not a problem with the driver -- since it seems to find the hardware fine.  ... does anyone else find it strange that the driver enumerates eth0 and eth1, but ifconfig -a shows eth1 and eth2?

Here is what I've got going:

dmesg | grep -iE 'eth | e1000e'
[    4.121422] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    4.121429] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    4.121672] e1000e 0000:06:00.0: Disabling ASPM L0s 
[    4.121689] e1000e 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.121708] e1000e 0000:06:00.0: setting latency timer to 64
[    4.121906] e1000e 0000:06:00.0: irq 67 for MSI/MSI-X
[    4.121913] e1000e 0000:06:00.0: irq 68 for MSI/MSI-X
[    4.121919] e1000e 0000:06:00.0: irq 69 for MSI/MSI-X
[    4.228050] e1000e 0000:06:00.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:25:90:0d:2d:18
[    4.228055] e1000e 0000:06:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    4.228141] e1000e 0000:06:00.0: eth0: MAC: 3, PHY: 8, PBA No: 0101FF-0FF
[    4.228321] e1000e 0000:07:00.0: Disabling ASPM L0s 
[    4.228341] e1000e 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.228364] e1000e 0000:07:00.0: setting latency timer to 64
[    4.229184] e1000e 0000:07:00.0: irq 70 for MSI/MSI-X
[    4.229189] e1000e 0000:07:00.0: irq 71 for MSI/MSI-X
[    4.229193] e1000e 0000:07:00.0: irq 72 for MSI/MSI-X
[    4.341551] e1000e 0000:07:00.0: eth1: (PCI Express:2.5GT/s:Width x1) 00:25:90:0d:2d:19
[    4.341557] e1000e 0000:07:00.0: eth1: Intel(R) PRO/1000 Network Connection
[    4.341692] e1000e 0000:07:00.0: eth1: MAC: 3, PHY: 8, PBA No: 0101FF-0FF

sudo ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 92:1axxxx
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo ifconfig -a   [mac address blunted to protect the innocent]
eth1      Link encap:Ethernet  HWaddr 00:25xxxx  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:fbde0000-fbe00000 

eth2      Link encap:Ethernet  HWaddr 00:25xxxx  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:fbce0000-fbd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 92:1axxxx  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by ersatzsplatt on 2012-01-31
Can anyone using a 82574L ethernet chip confirm if the e1000e driver is working for them ... running 11.10 server?  ... please?
If not, did you have to build a new driver instead of using what was in the standard install (to get it to work)?

---

