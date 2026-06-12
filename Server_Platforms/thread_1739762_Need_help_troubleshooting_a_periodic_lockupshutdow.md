---
title: "Need help troubleshooting a periodic lockup/shutdown"
date: 2011-04-26
forum: Server Platforms
---

### Post by wct097 on 2011-04-26
I purchased a Foxconn NT525, installed 2gb of RAM, and a 320gb hard drive.  It's loaded with Ubuntu Server (10.4 or 10.10, can't remember off the top of my head).  There have been at least two occasions in the last several months, maybe three, where the machine has locked up completely.  Won't respond to ping, can't SSH into it, etc.  It's not powered off, and I have to power cycle it to bring it back up.

I suspect it's a hardware issue, but I don't know for sure.  Can anyone point me in the right direction to try to figure out what is causing the problem?  I'm comfortable with Linux, but I don't know it well enough to adequately troubleshoot the problem.  Are there any particular logs I should look into?

---

### Post by TheFu on 2011-04-26
> **wct097 said:**
> I purchased a Foxconn NT525, installed 2gb of RAM, and a 320gb hard drive.  It's loaded with Ubuntu Server (10.4 or 10.10, can't remember off the top of my head).  There have been at least two occasions in the last several months, maybe three, where the machine has locked up completely.  Won't respond to ping, can't SSH into it, etc.  It's not powered off, and I have to power cycle it to bring it back up.

I suspect it's a hardware issue, but I don't know for sure.  Can anyone point me in the right direction to try to figure out what is causing the problem?  I'm comfortable with Linux, but I don't know it well enough to adequately troubleshoot the problem.  Are there any particular logs I should look into?

dmesg
/var/log/syslog

Look for a stack trace that shows where the issue is.  If you can't figure it out from that, post the important parts of the log as an attachment here.

If you get a lead from the syslog or dmesg output, look for the log file connected to that lead program.  My experience has been either the graphics drivers as a likely cause, so upgrading them manually may be desired.

---

### Post by matt_symes on 2011-04-26
Hi

Is it a kernel panic ? Are the shift or cap lock lights flashing ?

Can you shutdown using the magic key combination ?

Have a look in /var/log/messages as well.

Kind regards

---

### Post by wct097 on 2011-04-27
When I turned on the TV (box is using the TV as a monitor), I had no video output.  The keyboard (a USB variety) would not even light up the caps lock light, or elicit any response from the system.  I ended up pulling the plug and plugging it back in.

Reviewing the logs I'm seeing a constant stream of messages that read:
<date> <system> kernel: [number] rt18192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
<date> <system> kernel: [number] ======>rt18192_set_chan()====ch:{1-13}

The machine has internal wireless, and I've plugged in an external USB card as well, but I'm not using the wireless currently.  If did an 'ifconfig wlan0 down' and now I'm getting messages:
<date> <system> wpa_supplicant[1053]: Failed to initiate AP scan.

---

### Post by wct097 on 2011-04-27
So reviewing the log, it appears that the rt18192 messages were showing up 14 lines at a time every minute until half way through it's loop at Apr25 12:13:17.  The last two and a half messags on the 25th are:

```

Apr 25 12:13:17 <sysname> kernel: [758391.440031] =====>rtl8192_set_chan()====ch:6
Apr 25 12:13:17 <sysname> kernel: [7583Apr 26 21:05:24 <sysname> kernel: imklog 4.2.0, log source = /proc/kmsg started.

```And yes, it appears that the last message about proc/kmsg hit the log in the middle of the previous message, on the same line even.

The next message appears to be 5pm yesterday when I got home from work and bounced the system.

edit:  And I'm running 10.10.  The system is generally kept upgraded, though it's telling me 12 packages can be updated now that I'm logged in.

---

### Post by matt_symes on 2011-04-29
Hi

> Apr 25 12:13:17 <sysname> kernel: [758391.440031] =====>rtl8192_set_chan()====ch:6


What wireless cards do you have ? With them all plugged in type (from a terminal and case sensitive).

```
sudo lshw -C network
lsusb
lspci -nnk | grep -iA2 network
```

Post the results back here.

> Apr 25 12:13:17 <sysname> kernel: [7583Apr 26 21:05:24 <sysname> kernel: imklog 4.2.0, log source = /proc/kmsg started.

This is kernel message logging.

Kind regards

---

### Post by wct097 on 2011-04-29
sudo lshw -C network:
```
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:48:b9:d6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:d800(size=256) memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: d0:27:88:0e:1c:db
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=172.25.25.77 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:46 memory:febc0000-febfffff ioport:ec00(size=128)

```

lusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d8a Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lspci -nnk | grep -iA2 network:
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171]
    Kernel driver in use: rtl819xSE

```

---

### Post by matt_symes on 2011-04-29
Hi

> The machine has internal wireless, and I've plugged in an external USB card as well, but I'm not using the wireless currently. If did an 'ifconfig wlan0 down' and now I'm getting messages:
<date> <system> **wpa_supplicant[1053]: Failed to initiate AP scan.**

That would make sense as you have dropped the interface and wpa cannot scan on that interface so that is not a problem. 

I am wondering if it is not a wireless card issue. Specifically your internal wireless card.

```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171]
    Kernel driver in use: rtl819xSE
```

Can you disable that and use your external USB card for a while ?

Kind regards

---

### Post by wct097 on 2011-04-29
Disable the internal wireless card and use the external wireless card?  What about just using the internal wired card like I am now, and killing all wireless?  How can I kill the internal wireless besides having the interface down and not using it?

---

### Post by matt_symes on 2011-04-29
Hi

> **wct097 said:**
> Disable the internal wireless card and use the external wireless card?  What about just using the internal wired card like I am now, and killing all wireless? 

Yes that would also work. If we can identify/eliminate the wireless card it is one less thing to troubleshoot.

> How can I kill the internal wireless besides having the interface down and not using it?

Unload the kernel module using modprobe. To persist between reboots add to blacklist.conf. 

Or you could try to disable it in the BIOS if it has that option.

Kind regards

---

