---
title: "sys76 panp7 Lucid 10.04 LTS Wireless card fails to detect wireless network"
date: 2010-10-05
forum: System76 Support
---

### Post by arch_o_median on 2010-10-05
Hello all!   I've recently purchased a panp7.   It has suspend and hibernate capabilities that just work!

  Because I can, I use hibernate instead of powering down.  I've update/upgraded several times since the last reboot.

  Today I rebooted for the first time in several weeks.   At that time the gnome restart applet informed me that the restart was "required".   I think I recall updating the kernel at some point recently which would explain the "required" bit.

  After rebooting my wireless card no longer detected the local wireless network, and I was unable to connect to it.

  I ran the system76 "Install Drivers" and "Restore System" utilities and rebooted.
  I then generated logs with the relevant system76 driver utility. (attached it to this message)

**sudo lshw -C network:**
[FONT=Courier New]
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 10
       serial: 74:f0:6d:84:fa:65
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:18 ioport:4000(size=256) memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: eth0
       version: 03
       serial: 00:90:f5:a6:a2:28
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=full ip=192.168.1.149 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:34 memory:f0400000-f0403fff ioport:5400(size=128) ioport:5000(size=256)
[/FONT]
  I notice that  there's no "CLAIMED, UNCLAIMED, ENABLED, or DISABLED" tag, is it possible my wireless card is powered off?   Is there a switch on the panp7 I accidentally toggled?

  The 3d led from the left which is associated with a glyph that looks like a wireless antennae to me, is amber.  I can toggle it on and off with Fn-F12..  maybe it's bluetooth?

**sudo iwconfig:**
[FONT=Courier New]
lo        no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry on   RTS thr off   Fragment thr off
          Encryption key off
          Power Management off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
[/FONT]

**sudo ifconfig:**

 [FONT=Courier New] eth0      Link encap:Ethernet  HWaddr 00:90:f5:a6:a2:28  
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fea6:a228/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17322393 (17.3 MB)  TX bytes:3715873 (3.7 MB)
          Interrupt:34 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1632 (1.6 KB)  TX bytes:1632 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:84:fa:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66 (66.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:ffffc90010930000-ffffc90010930100 
[/FONT]s

   At this point I am stumped.   Can anyone help me?
Thanks!
--Josh

---

### Post by isantop on 2010-10-05
Hi. Fn+F11 toggles the wireless. Try that one.

Also, I'd look into simply rebooting/shutting down. For me, it's a bit faster anyway.

---

### Post by arch_o_median on 2010-10-05
Yep, that fixed it.   Thanks!

---

### Post by arch_o_median on 2010-12-21
For future reference, the wireless card is off by default.  That is, on reboot it must be manually turned on.   This seems like odd behavior so I suppose I tweaked a config file at some point. 
  Does anyone know whether this is the "factory" default behavior?

---

### Post by isantop on 2010-12-21
It should be persistent, meaning that if it's of when you turn the system off, then it'll stay off. If it's on, it'll stay on. I have seen cases where the wireless will turn off on boot up. In that case, the best thing to do is to turn it on as soon as possible. That should help it stick.

---

