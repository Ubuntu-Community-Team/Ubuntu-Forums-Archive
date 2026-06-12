---
title: "maudio 2496"
date: 2013-03-15
forum: Ubuntu Studio
---

### Post by Matthewexeter on 2013-03-15
Hi I often have the problem of my soundcard vanishing, it may be to do with updates. I have fixed this problem before with a few commands. Or sometimes removing somethings and reinstalling them. If someone could tell me how to get my soundcard back in the command line, that would be great

alsamixer
> cannot open mixer: No such file or directory

aplay -l
> aplay: device_list:252: no soundcards found...


lspci
> 00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:08.0 Non-VGA unclassified device: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

I know that
> 01:08.0 Non-VGA unclassified device: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
is my soundcard, although I have forgotten how to reattach it as my soundcard in ubuntustudio

I will note it down this time as I tend to forget things, and have become frustrated with looking it up, and uninstalling and reinstalling the wrong things until trial and error gets it done.

Thanks in advance

---

### Post by jejeman on 2013-03-15
Give us output from
```
lspci -knn
```
for the audio card only.

p.s.
Put output from terminal in CODE tags, not in QUOTE. It is more readable.

---

### Post by Matthewexeter on 2013-03-15
Thank you for your reply

the result of

```
lspci -knn
```

is

```
00:00.0 RAM memory [0500]: NVIDIA Corporation MCP61 Host Bridge [10de:03e2] (rev a1)
    Subsystem: ASRock Incorporation Device [1849:03e2]
00:01.0 ISA bridge [0601]: NVIDIA Corporation MCP61 LPC Bridge [10de:03e1] (rev a2)
    Subsystem: ASRock Incorporation Device [1849:03e1]
00:01.1 SMBus [0c05]: NVIDIA Corporation MCP61 SMBus [10de:03eb] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03eb]
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2
00:01.2 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03eb]
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP61 USB 1.1 Controller [10de:03f1] (rev a3)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03f1]
    Kernel driver in use: ohci_hcd
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP61 USB 2.0 Controller [10de:03f2] (rev a3)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03f2]
    Kernel driver in use: ehci_hcd
00:04.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:06.0 IDE interface [0101]: NVIDIA Corporation MCP61 IDE [10de:03ec] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ec]
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth
00:08.0 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03f6]
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv
00:08.1 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03f6]
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv
00:09.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0b.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0c.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] [10de:03d6] (rev a2)
    Subsystem: ASRock Incorporation Device [1849:03d6]
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:08.0 Non-VGA unclassified device [0000]: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller [1412:1712] (rev 02)
    Kernel modules: snd-ice1712

```

a friend suggested 
```
sudo modprobe snd_ice1712
```
that did not work

thanks

---

### Post by Matthewexeter on 2013-03-15
Oh and this is on a fresh install of ubuntustudio 12.04
I tried linux mint with xforce desktop, it was just the same and the borders of programs were in some way dificult to work with

---

### Post by ibjsb4 on 2013-03-15
I don't have one, but got some hits that may help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=maudio+2496&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=maudio+2496&sa=Search&cof=FORID:9)

---

### Post by Sylos on 2013-03-15
You could try checking dmesg:

```
dmesg | grep snd-ice1712
```

Might show if the module is failing to load on boot.


You could also try:

```
sudo rmmod snd-ice1712
```

then

```
sudo modprobe snd-ice1712
```

Cheers

---

### Post by Matthewexeter on 2013-03-15
Thankyou sylos, the dmseg command as you posted returned nothing, I entered the others in also and this did not help.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) I tried everything in the comprehensive sound guide, up to and including the alsa compilation using the module assistant. I had an error, it was inside the terminal in a shell of somekind, and would not allow me to select all the text within it. I am going to try taking my machine apart and switching pci slots, as I would of thought by now it could well be a hardware problem.

---

### Post by Matthewexeter on 2013-03-15
After an initial display of white text on boot up, with no way to escape, and a manual shutdown, the problem has been solved by switching the pci channels of the card.
My motherboard must be suffering from old age.
Thank you all for your help :0)

---

### Post by varunendra on 2013-03-15
Thread marked as [SOLVED] on OP's request -
> I wanted to mark this thread as solved, the option is not there as it was described in this help thread [http://ubuntuforums.org/showthread.p...51#post4527051](http://ubuntuforums.org/showthread.p...51#post4527051)

@ Matthewexeter,
That option is broken in the upgraded forum. A temporary workaround is given in the 'See how' link in my signature.
We hope it will get fixed soon.

Thanks for your interest in marking threads Solved.

---

