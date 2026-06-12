---
title: "Studio 8.04 - need help configuring audio"
date: 2008-07-30
forum: Ubuntu Studio
---

### Post by badmotor on 2008-07-30
Hi guys,

I don't know what has changed since Gutsy, but Ubuntu Studio 8.04 won't detect my mic input on laptop. Not really sure how to set it up, is Pulseaudio involved in this?
Also getting alot more x-runs with Jack now, when using Hydrogen/Ardour etc.

Any pointers on setup would be greatly appreciated thanks. :)

---

### Post by Stochastic on 2008-07-30
Okay, lets start with the basics:
1) do you have the ubuntustudio-audio package installed?
2) what does the output of lspci give you?
3) can you post an example error message from an application that can play audio and should be able to record audio, but can't record?

---

### Post by badmotor on 2008-07-30
> **Stochastic said:**
> Okay, lets start with the basics:
1) do you have the ubuntustudio-audio package installed?
2) what does the output of lspci give you?
3) can you post an example error message from an application that can play audio and should be able to record audio, but can't record?

1) I am using Ubuntu Studio 8.04.  Are there extra packages on top of the std. studio I should install?
2)todd@Studio:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
todd@Studio:~$ 

3)No error, I'm trying to get Ardour and/or Audacity to record from a mic plugged straight into my laptop, and get nothing but silence.

---

### Post by Stochastic on 2008-07-30
> **badmotor said:**
> 1) I am using Ubuntu Studio 8.04.  Are there extra packages on top of the std. studio I should install?

You probably have it installed from the ubuntu studio intstallation, but to double check do ```
apt-cache policy ubuntustudio-audio
``` and if it shows as installed, then you're all good.

> **badmotor said:**
> 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

This is your soundcard - the bad news is that it's not very well supported from what I've read, the good news is that you already have playback.
Can you do ```
lspci -vv
``` and only post the section concerned with this soundcard.

> **badmotor said:**
> 
3)No error, I'm trying to get Ardour and/or Audacity to record from a mic plugged straight into my laptop, and get nothing but silence.

If no error message shows up, then there's a good chance your alsamixer settings are to blame.  Run ```
alsamixer
``` and look for any channels (particularly ones labeled mic) that are turned down or have the mute function on.


Oh, and one more thing to be safe, can you do ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by badmotor on 2008-07-30
Here's the output of lspci -vv:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 0133
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by badmotor on 2008-07-30
all my volumes are turned up on the alsamixer, still nothing coming in.

---

### Post by badmotor on 2008-07-31
Anyone?

---

