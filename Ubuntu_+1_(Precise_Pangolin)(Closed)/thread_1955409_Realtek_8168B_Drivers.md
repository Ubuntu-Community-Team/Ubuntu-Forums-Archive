---
title: "Realtek 8168B Drivers"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ayozito on 2012-04-09
Just installed 12.04 and I'm seeing the same problem I had on 11.10. 

The default driver it is loading always is the 8169 but my NIC is the 8168. So always that the kernel will be updated I have to change it to the 8168 manually.

I'm wondering if developers can fix it before the final release because really it's very annoying.

---

### Post by ratcheer on 2012-04-09
With the 3.2 Linux kernel on 12.04, the r8169 driver is now working on my system. This has also been true on Sabayon and Arch Linux.

Tim

---

### Post by ayozito on 2012-04-09
With the r8168 card?

---

### Post by ratcheer on 2012-04-09
Yes:

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at ee00 [size=256]
    Memory at fbeff000 (64-bit, prefetchable) [size=4K]
    Memory at fbef8000 (64-bit, prefetchable) [size=16K]
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

```

Tim

---

### Post by ayozito on 2012-04-14
Ok it is working well, but haven't you the issue of freeze when shutdown/restart? I using the R8169 most of times it freezes.

---

### Post by Pilot6 on 2012-04-14
The driver in kernel 3.2 seem to work well with this NIC. If you are paranoid, you can download latest Realtek r8168 driver with dkms module from Debian repo. You will not need to reinstall it every time you upgrade kernel. The package is called r8168-dkms.
It installs well into Ubuntu. But I see no reason to do it now.

---

### Post by santosh83 on 2012-04-14
Apparently even my NIC is an 8168b/8111b, but ever since I installed Maverick in 2010, the default 8169 driver has been used, and I've not had any problems, though mine is not a laptop.

dmesg output:
```
santosh@santosh-desktop:~$ dmesg | grep eth
[    1.279749] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xffffc900001ee000, 00:19:d1:88:bd:94, XID 98500000 IRQ 44
[   29.040828] udev[318]: renamed network interface eth0 to eth1
[   30.319848] r8169 0000:02:00.0: eth1: link up
[   30.319855] r8169 0000:02:00.0: eth1: link up
[   31.501699] bridge-eth1: up
[   31.501705] bridge-eth1: attached
[   41.160070] eth1: no IPv6 routers present

```

---

### Post by ratcheer on 2012-04-14
> **ayozito said:**
> Ok it is working well, but haven't you the issue of freeze when shutdown/restart? I using the R8169 most of times it freezes.

No, that hasn't happened to my system. Knock on wood. ;)

Tim

---

### Post by jerrylamos on 2012-04-14
Beats me.  This old notebook (2006 Thinkpad T40) has a built in Cisco Aironet Wireless 802.11b that was supported up through 11.10.  Now ubuntu disconnect it all the time.

So I plugged in a pci card
Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
which has been working.  

Linux is somewhat confused since it keeps trying to use the Cisco, connects, then ubuntu kernel disconnects, repeat ad nauseum.  Meanwhile the Realtek is running so I try to manually disconnect the Cisco.

I don't have a clue on where the RTL8180L driver is?  Or the Aironet?

Jerry

---

### Post by ayozito on 2012-04-15
> **ratcheer said:**
> No, that hasn't happened to my system. Knock on wood. ;)

Tim

knock knock xD Because since I changed to the R8168 didn't freeze any time xD

---

### Post by ratcheer on 2012-04-15
> **ayozito said:**
> knock knock xD Because since I changed to the R8168 didn't freeze any time xD

Look, I had been using r8168 for almost a year on all distros and with all kernels up through 3.1.5. But, starting with kernel 3.1.6 and everything later, r8169 has been working with no problems.

Tim

---

