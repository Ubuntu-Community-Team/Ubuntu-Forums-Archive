---
title: "Frequent LAN disconnections"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by calanor on 2012-02-15
Hi,

I am using a fully updated Ubuntu 12.04 install. From 3-4 days I have been having problems with my LAN. Ironically WLAN works fine, but LAN disconnects in somewhat regular time intervals, sometimes as frequent as every 5 minutes. No matter what I do it keeps disconnecting. How should I check what's wrong. Should I file a bug report ? But then I don't have any information to give !!! Please help.

Thanks.

---

### Post by dino99 on 2012-02-15
watch your logs

---

### Post by calanor on 2012-02-15
I don't know of any log that keeps track of network disconnections in linux. Can you please tell me which log should I be looking into ?

---

### Post by dino99 on 2012-02-15
> **calanor said:**
> I don't know of any log that keeps track of network disconnections in linux. Can you please tell me which log should I be looking into ?

~/.xsession-errors
/var/log/

---

### Post by calanor on 2012-02-15
I am pretty sure its a driver problem, as the light of the ethernet port itself goes down. I am not sure if this would be caught in xsession-errors or any log in /var/log. Anyway, I checked and I did not find any relevant information there.

---

### Post by effenberg0x0 on 2012-02-16
> **calanor said:**
> I am pretty sure its a driver problem, as the light of the ethernet port itself goes down. I am not sure if this would be caught in xsession-errors or any log in /var/log. Anyway, I checked and I did not find any relevant information there.

If the Ethernet port goes down logically, it will be in the logs. The following command will search for some possibly related words in a couple of your log files, output results to MyLog.log in your home directory and open MyLog.log in Gedit, so you can browse or search it for some clues.

```

sudo grep ' eth[0-9]\|ethernet\|ip\|dhcp\|route\|conn\|warning\|oops\|segfault\|error' -iHnr /var/log/dmesg /var/log/syslog /var/log/kern.log /var/log/messages > $HOME/MyLog.log && gedit $HOME/MyLog.log

```

Regards,
Effenberg

---

### Post by Gregory Lee on 2012-02-16
I see this:
```
/var/log# grep eth0 dmesg|more
[    5.659566] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.627555] r8169 0000:03:00.0: eth0: link down
[   14.627565] r8169 0000:03:00.0: eth0: link down
[   14.628475] ADDRCONF(NETDEV_UP): eth0: link is not ready

```
I don't know that these interruptions are pathological -- maybe they're normal.

---

### Post by prusswan on 2012-02-16
> **Gregory Lee said:**
> I see this:
```
/var/log# grep eth0 dmesg|more
[    5.659566] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.627555] r8169 0000:03:00.0: eth0: link down
[   14.627565] r8169 0000:03:00.0: eth0: link down
[   14.628475] ADDRCONF(NETDEV_UP): eth0: link is not ready

```
I don't know that these interruptions are pathological -- maybe they're normal.

Is that actually a realtek 8168B? could be the notorious problem of ubuntu using r8169 driver by default

---

### Post by Gregory Lee on 2012-02-16
> **prusswan said:**
> Is that actually a realtek 8168B? could be the notorious problem of ubuntu using r8169 driver by default
I don't know how to tell what it actually is.  I don't see an 8168B driver among the compiled Linux realtek driver modules,
```
/lib/modules/3.2.0-16-generic/kernel# ls drivers/net/ethernet/realtek/
8139cp.ko  8139too.ko  atp.ko  r8169.ko
```but there is an r8169 driver there, which is loaded, according to lsmod.

---

### Post by prusswan on 2012-02-16
> **Gregory Lee said:**
> I don't know how to tell what it actually is.  I don't see an 8168B driver among the compiled Linux realtek driver modules,
```
/lib/modules/3.2.0-16-generic/kernel# ls drivers/net/ethernet/realtek/
8139cp.ko  8139too.ko  atp.ko  r8169.ko
```but there is an r8169 driver there, which is loaded, according to lsmod.

you can check by running:

lspci -v


The r8168 driver is not part of the distribution, but can be installed from: [http://code.google.com/p/r8168/](http://code.google.com/p/r8168/)

---

### Post by Gregory Lee on 2012-02-16
> **prusswan said:**
> you can check by running:

lspci -v

That gives this:
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
        Subsystem: Hewlett-Packard Company Device 2acf
        Flags: bus master, fast devsel, latency 0, IRQ 44
        I/O ports at e000 [size=256]
        Memory at d0004000 (64-bit, prefetchable) [size=4K]
        Memory at d0000000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
        Kernel driver in use: r8169
        Kernel modules: r8169
```So evidently it is a 8168B, as you suspected.  I wouldn't jump to the conclusion that the r8169 driver won't work for it, though, without reading the driver source code.  (I don't even know whether I have that on my system -- haven't gotten around to looking.)

---

### Post by prusswan on 2012-02-16
> **Gregory Lee said:**
> That gives this:
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
        Subsystem: Hewlett-Packard Company Device 2acf
        Flags: bus master, fast devsel, latency 0, IRQ 44
        I/O ports at e000 [size=256]
        Memory at d0004000 (64-bit, prefetchable) [size=4K]
        Memory at d0000000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
        Kernel driver in use: r8169
        Kernel modules: r8169
```So evidently it is a 8168B, as you suspected.  I wouldn't jump to the conclusion that the r8169 driver won't work for it, though, without reading the driver source code.  (I don't even know whether I have that on my system -- haven't gotten around to looking.)

9 out of 10 that would be the explanation, and welcome to the loooong rank of affected users

---

### Post by calanor on 2012-02-16
Thanks for replying. I am attaching dmesg, syslog, kern.log with eth0 grep.
NIC-
Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)

In the logs, it shows frequent disconnections in eth0. I am not even sure about wlan now. Its disconnecting too.

---

### Post by calanor on 2012-02-16
This problem is not limited to Ubuntu. I tried Sabayon and the disconnections are there too !!!! Is the new kernel botched, or is my hardware faulty !!!!

Dmesg output : 

e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1190.525436] dell_wmi: Received unknown WMI event (0x0)
[ 1279.383744] e1000e: eth0 NIC Link is Down
[ 1284.473867] dell_wmi: Received unknown WMI event (0x0)
[ 1300.769015] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 1300.769027] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1305.763005] dell_wmi: Received unknown WMI event (0x0)
[ 1446.603329] e1000e: eth0 NIC Link is Down
[ 1451.663142] dell_wmi: Received unknown WMI event (0x0)
[ 1468.045413] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None

---

### Post by prusswan on 2012-02-16
I'm not sure if it is related either, but today I had my otherwise working wireless connection having the same symptoms at work.

---

### Post by Gregory Lee on 2012-02-16
> **prusswan said:**
> I'm not sure if it is related either, but today I had my otherwise working wireless connection having the same symptoms at work.
Do you wash your hands between using different computers?

---

### Post by effenberg0x0 on 2012-02-16
> **Gregory Lee said:**
> Do you wash your hands between using different computers?
With the broad spectrum of computer viruses we see today, that is good advice. 
Thanks, I LOL'ed. 
Effenberg

---

### Post by calanor on 2012-02-20
I found the problem was with the switch I was connected to. The ethernet rate auto negotiation was faulty hence the disconnections. The DMI event was just a scary message with no effect whatsoever on LAN.

---

### Post by calanor on 2012-02-20
Thanks everyone, for your help.

---

