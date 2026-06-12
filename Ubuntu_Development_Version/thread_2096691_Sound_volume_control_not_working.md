---
title: "Sound volume control not working"
date: 2012-12-20
forum: Ubuntu Development Version
---

### Post by ubername on 2012-12-20
Hi

The volume control is not working from the top panel icon or from sound settings (It is effectively greyed out) but I am getting sound from the speakers. The sound settings shows no devices, nor any applications even when e.g. bbc is playing in firefox. This has happened in the past day or so.

Alsamixer works to control the volume.

```
lspci
``` gives 
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

```
alsactl init
``` gives 
```
Found hardware: "HDA-Intel" "SigmaTel STAC9227" "HDA:83847618,102801dd,00100201" "0x1028" "0x01dd"
Hardware is initialized using a generic method
```

Any clues?

---

### Post by kevpan815 on 2012-12-20
Are you running the latest Nightly Build? If not, then first i would try updating to the latest Nightly Build using either Zsync and/or Rsync.

---

### Post by Precipitous on 2012-12-21
> **ubername said:**
> Hi

The volume control is not working from the top panel icon or from sound settings (It is effectively greyed out) but I am getting sound from the speakers. The sound settings shows no devices, nor any applications even when e.g. bbc is playing in firefox. This has happened in the past day or so.

Alsamixer works to control the volume.

```
lspci
``` gives 
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
``````
alsactl init
``` gives 
```
Found hardware: "HDA-Intel" "SigmaTel STAC9227" "HDA:83847618,102801dd,00100201" "0x1028" "0x01dd"
Hardware is initialized using a generic method
```Any clues?
@ubername - I just started experiencing the exact same problem.  Running lspci and alsactl init produce identical results to your as well...  This is obviously not an isolated issue.

---

### Post by VinDSL on 2012-12-21
Hrm...

I had this problem, a while back.  Lasted for a month, or so.

Then, one day, an "indicator" upgrade fixed it.

I'm in GS right now, and the volume control is working fine.

I'll switch back to Unity, and see if we got a regression going on.

Er... you guys are running Unity, right?!?!?

---

### Post by VinDSL on 2012-12-21
I'm in Unity now.

Working fine.  Sorry!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-21-dec-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-21-dec-2012-2.png")[/INDENT]

---

### Post by ventrical on 2012-12-21
Works great here too.

```

dale@dale-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:03.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
dale@dale-desktop:~$ 

```

---

### Post by ventrical on 2012-12-21
Here's the pic of my sound board.

---

### Post by kevpan815 on 2012-12-21
I'm in Unity too and everything is working fine here.

---

### Post by nico1038 on 2012-12-21
Same problem here.

[Edit] The solution describes in this bug report works for me: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1078543]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1078543")

---

### Post by ubername on 2012-12-22
> **nico1038 said:**
> Same problem here.

[Edit] The solution describes in this bug report works for me: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1078543]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1078543")

Fixed for me too. Trying to figure out how I ended up with the i386 version of pulseaudio-esound-compat installed.

---

### Post by nico1038 on 2012-12-23
Did you install Steam recently?

---

### Post by ubername on 2012-12-23
> **nico1038 said:**
> Did you install Steam recently?

Nope

---

### Post by moma on 2012-12-27
VinDSL: Impressive screenshot.

---

