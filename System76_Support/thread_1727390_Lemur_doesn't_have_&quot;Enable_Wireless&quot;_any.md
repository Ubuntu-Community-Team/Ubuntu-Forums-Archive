---
title: "Lemur doesn't have &quot;Enable Wireless&quot; anymore (no wireless at all)"
date: 2011-04-12
forum: System76 Support
---

### Post by Tyler_Nieman on 2011-04-12
Hey, opened my laptop up like normal today and noticed that there is not any sort of "Enable Wireless" like there was previously, meaning I can't connect to any sort of wireless as a consequence. I've tried rebooting multiple times as well as pressing fn+f11 to see if that would toggle it back on.. but no luck. Anything I'm missing? Am I not pressing fn+f11 right or something? Haha. Thanks for any help.

---

### Post by isantop on 2011-04-12
Press Fn+F11 so that the wireless indicator light turns on. Then, what do you get if you left-click on the wireless icon in the upper panel?

---

### Post by Tyler_Nieman on 2011-04-12
> **isantop said:**
> Press Fn+F11 so that the wireless indicator light turns on. Then, what do you get if you left-click on the wireless icon in the upper panel?

Ah, right. I forget that light exists until I have a problem.. Here's what I get after the light's on:

```

Wired Network
disconnected
--------------
VPN Connections >
&#10003; Enable Networking
--------------
Connection information
Edit Connections

```

Nothing about the wireless like there used to be.

---

### Post by isantop on 2011-04-13
Are you using Natty? There shouldn't be any Enable options in the left click menu.

---

### Post by Tyler_Nieman on 2011-04-13
> **isantop said:**
> Are you using Natty? There shouldn't be any Enable options in the left click menu.

I am using Natty (probably should've mentioned that. sorry!), and there's just that one enable option and no wireless networks show up at all (and I know I'm near a ton of them), and I can't find any way to connect to them. I suppose I was alpha testing and knew the risks.. I have nothing against installing the new beta that comes out tomorrow to see if it fixes it if you're out of ideas, as well.

---

### Post by isantop on 2011-04-13
Let's try a bit more troubleshooting first. What do you get if you run lspci? Just go ahead and paste the output here, and I'll have a look.

---

### Post by Tyler_Nieman on 2011-04-13
> **isantop said:**
> Let's try a bit more troubleshooting first. What do you get if you run lspci? Just go ahead and paste the output here, and I'll have a look.

Here ya go

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
03:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

---

### Post by isantop on 2011-04-13
Well, it looks like you have a bad wireless card, since Ubuntu isn't seeing it. Let's handle this through email: support...at...system76...dot...com.

---

