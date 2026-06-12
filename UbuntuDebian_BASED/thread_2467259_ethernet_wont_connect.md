---
title: "ethernet wont connect"
date: 2021-09-21
forum: Ubuntu/Debian BASED
---

### Post by yigitus on 2021-09-21
i am new to Ubuntu and need help, i can connect to internet with wifi adapter but ethernet cable doesnt work. result of nmcli is ```

enp2s0: connecting (getting IP configuration) to Profile 1
        "Realtek RTL8111/8168/8411"
        ethernet (r8168), F4:4D:30:AD:8B:65, hw, mtu 1500

lo: unmanaged
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536


```

---

### Post by TheFu on 2021-09-21
a) which version and release of Ubuntu?

b) which kernel?

c) exactly which version of the NIC?  Realtek has a bad habit of using the same name across 50 different hardware configs.  They change the "version" of the card to denote something changed. Often, that tiny version difference is what changes the driver needed.

For example, these commands would be how I got the needed information:
```
lsb_release -a
uname -a
lshw -C network
```

And my answers are:
a) Description:    Ubuntu 18.04.6 LTS
b) 5.4.0-84-generic
c)
```
  *-network [COLOR="#FF0000"]DISABLED[/COLOR]        
       description: Ethernet interface
       product: **RTL8111/8168/8411** PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       [COLOR="#FF0000"]version: 0c
[/COLOR]       serial: fc:aa:14:a7:aa:aa
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="#FF0000"]driver=r8168[/COLOR] [COLOR="#FF0000"]driverversion=8.045.08-NAPI[/COLOR] duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:31 ioport:e000(size=256) memory:f7b00000-f7b00fff memory:f0000000-f0003fff
```

I'm not using the Realtek NIC in that machine for a number of reasons. It worked fine for about 4 yrs, then started dropping packets so I disabled it and started using a different NIC instead.  I've had a 4-port Intel PRO/1000 NIC to install into the machine for a few years, but just haven't gotten around to doing that yet.

I'm not a fan of Realtek stuff and go out of my way to avoid their network stuff in all my newer computers. I just don't need the hassle.

---

### Post by yigitus on 2021-09-22
a) I am using Ubuntu 21.04 based Pop!_OS  but unfortunately i cant register to Pop!_OS forum because of an error, so i need help from here.

b) This is the output of uname -a ```
 Linux yigit **5.13.0-7614-generic** #14~1631647151~21.04~930e87c-Ubuntu SMP Fri Sep 17 00:24:58 UTC  x86_64 x86_64 x86_64 GNU/Linux
```

c) Output of lshw -C network
```

  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: f4:4d:30:ad:8b:65
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.048.03-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:123 ioport:d000(size=256) memory:df104000-df104fff memory:df100000-df103fff

```

And i noticed that when i reset the router, internet works but when i restart the computer the problem occurs again.
Yes, this NIC might be problematic, I was only able to get it to work on windows easily.

---

### Post by jeremy31 on 2021-09-22
Moved to Ubuntu/Debian based

---

### Post by TheFu on 2021-09-22
> **yigitus said:**
> a) I am using Ubuntu 21.04 based Pop!_OS  but unfortunately i cant register to Pop!_OS forum because of an error, so i need help from here.

I've never touched Pop.

First, 21.04 isn't an LTS release, so expect issues, especially with new hardware.

5.13.x is a VERY NEW kernel.  I don't know **any** Ubuntu using it yet.  I think the most current is 5.11.x.  My 20.04 kernel is 5.4.x and with extra effort by loading the HWE kernel, Ubuntu users can get 5.11.x kernels.

Don't make the mistake of confusing "new" for "better".  When it comes to hardware support, that is seldom the answer on Linux. Most hardware vendors don't test with Linux at all, so it isn't surprising when hardware works on Windows.  That's 90+% of the market, so why would they spend 50% of their development and testing budget on 5% of the users, especially for low-end devices? Hint: they don't.

Realtek does make drivers for Linux, but their QC in the HW and SW has always seemed to be lacking from what I've seen.  Lots of people have fine experiences with their hardware, so it isn't all bad.

What would I do?
I'd run the current LTS version of Pop with a 5.4.x kernel or older.  The trick is to have the LTS and the right kernel.
I'd search these forums for people who have realtek NICs with exactly the same version (15) of the NIC that you have and see what they did to solve the issue.  Do that.

Never confuse "new" with "better."  That isn't how computers work.  This applies to both hardware AND software.

---

### Post by cigtoxdoc on 2021-09-22
This is a major problem and it effects 21.04 itself, not the Debian version. One of my PCs gives essentially the same lists as reported above by yigitus.  PC is duel boot with Windows 10 Pro. To get Ethernet on 21.04, I need to boot into Win 10 first.  Shutdown PC and immediately restart and let it boot into 21.04.  John

---

### Post by TheFu on 2021-09-22
> **cigtoxdoc said:**
> This is a major problem and it effects 21.04 itself, not the Debian version. One of my PCs gives essentially the same lists as reported above by yigitus.  PC is duel boot with Windows 10 Pro. To get Ethernet on 21.04, I need to boot into Win 10 first.  Shutdown PC and immediately restart and let it boot into 21.04.  John

When booting Windows first, then a soft-reboot makes it work on Linux, that has been traced back to bad driver initialization.  In C, we are supposed to initialize all variables to known values.  That's easy:
```
int some_interger=0;
```
But it is extremely common for programmers - all programmers - to be lazy and just use:
```
int some_interger;
```
instead.  Different compilers implement static allocation of variables differently.  Some will zero out the entire DS first, so all variables are effectively zero.  But others don't do anything and whatever the RAM had from prior use, by different programs on the system will hold random values.

The first method will be optimized away by the compiler, if it isn't needed.
The second may work fine or it may not. Just depends on the compiler and the settings for the compiler.

I know of no fix other than to get the source code and fix all the uninitialized variables, recompile, then make fresh objects and drivers for each kernel version.

Of course, the issue could be something completely different and setting all variables to known values can cause the driver to crash, since known is usually 0.  You'd think that having a pointer set to a random location rather than 0 would be bad ... and it is, but it often doesn't crash. Instead, it returns bogus information and in a network driver that bogus information could be dropped because the packets would be out of order and re-assembly would fail - i.e. drop that single packet. Nobody would likely notice, since it had bogus information anyway.

So ... how's your C coding?  Can you get the source and fix it?

---

### Post by cigtoxdoc on 2021-09-22
Thank you, but not into C

Motherboard is MSI CSM-B85M-P32

---

### Post by yigitus on 2021-09-23
Thanks for the suggestions, i don't know much about drivers so i'll just try using an older ubuntu and kernel with LTS

---

### Post by yigitus on 2021-09-23
i installed Ubuntu 20.04, configured network settings manually and it worked.

---

### Post by kurt18947 on 2021-09-23
There was an issue with some RealTek ethernet drivers in 20.04 when it first came out. I had just purchased a new mother board that had a RealTek 8169H ethernet chip. RealTek 8169 had been supported for a long time, 8169H had been problematic. Happily the problem with 8169H had been fixed by the time I installed mine. That's why the advice when choosing hardware for a linux system is to not buy the latest and shiniest (or cheapest). There's a very good chance that hardware from a linux friendly vendor that's been around for 6 months+ will work.

---

### Post by cigtoxdoc on 2021-10-08
How did you configure the network settings manually?  When I look at wired connection 1, there is nothing to change.  John

---

