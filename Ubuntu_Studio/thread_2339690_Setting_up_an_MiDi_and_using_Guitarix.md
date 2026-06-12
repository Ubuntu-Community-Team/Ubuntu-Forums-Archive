---
title: "Setting up an MiDi and using Guitarix"
date: 2016-10-11
forum: Ubuntu Studio
---

### Post by muddpup64 on 2016-10-11
Hello everybody!

I'm very new to the ubuntu/linux recording community and don't really have much of a clue what I'm doing. I bought an old used Tascam iUR2 MiDi and am trying to use it to hook my guitar up to my computer. To start off when I start guitarix I get this message ```
 [20:38:49]  system init  ***  failed to lock memory: Cannot allocate memory
[20:38:49]  system init  ***  failed to lock memory: Cannot allocate memory
[20:38:52]  PitchTracker  ***  error creating realtime thread - tuner not started 
```

My dialog box also shows this:

```
 [20:57:29]  system init  ***  failed to lock memory: Cannot allocate memory
[20:57:29]  system init  ***  failed to lock memory: Cannot allocate memory
[20:57:30]  loaded state  ***  from file /home/muddpup/.config/guitarix/gx_head_rc
[20:57:30]  Jack init  ***  The jack sample rate is 44100/sec
[20:57:30]  Jack init  ***  The jack buffer size is 1024/frames ... 
[20:57:30]  PitchTracker  ***  error creating realtime thread - tuner not started 
```

I made sure pulseaudio wasn't running at the same time by adding a ```
pasuspsender --
``` to the server prefix. Has not solve my problem. Furthermore, I manually added myself to the permission (group) for Jack with no luck.

aplay -l Produces:

```
 **** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: iUR2 [iUR2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```

arecord -l Produces:

```
 **** List of CAPTURE Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: iUR2 [iUR2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```

amidi -l Produces: (Assuming I require my MiDi to be plugged in.)

```
 Dir Device    Name
IO  hw:1,0,0  iUR2 MIDI 1
IO  hw:1,0,1  iUR2 MIDI 2
 
```


  I did manually add myself into   the group just to be sure I was there. Checking with "groups" does   confirm this.


And finally, 
lspci -vnn Produces:

```
 00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Lenovo Core Processor DRAM Controller [17aa:2193]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Core   Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if   00 [VGA controller])
    Subsystem: Lenovo Core Processor Integrated Graphics Controller [17aa:215a]
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset HECI Controller [17aa:215f]
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at f2827800 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
    Subsystem: Lenovo 82577LM Gigabit Network Connection [17aa:2153]
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f2600000 (32-bit, non-prefetchable) [size=128K]
    Memory at f2625000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series   Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06) (prog-if 20   [EHCI])
    Subsystem: Lenovo 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [17aa:2163]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f2828000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset High Definition Audio [17aa:215e]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f2620000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series   Chipset PCI Express Root Port 1 [8086:3b42] (rev 06) (prog-if 00  [Normal  decode])
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series   Chipset PCI Express Root Port 2 [8086:3b44] (rev 06) (prog-if 00  [Normal  decode])
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f2400000-f24fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series   Chipset PCI Express Root Port 4 [8086:3b48] (rev 06) (prog-if 00  [Normal  decode])
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0000000-f1ffffff
    Prefetchable memory behind bridge: 00000000f2900000-00000000f29fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series   Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06) (prog-if 00  [Normal  decode])
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
    Memory behind bridge: f2500000-f25fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series   Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06) (prog-if 20   [EHCI])
    Subsystem: Lenovo 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [17aa:2163]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f2828400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation QM57 Chipset LPC Interface Controller [8086:3b07] (rev 06)
    Subsystem: Lenovo QM57 Chipset LPC Interface Controller [17aa:2166]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series   Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06) (prog-if 01   [AHCI 1.0])
    Subsystem: Lenovo 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [17aa:2168]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 25
    I/O ports at 1860 [size=8]
    I/O ports at 1814 [size=4]
    I/O ports at 1818 [size=8]
    I/O ports at 1810 [size=4]
    I/O ports at 1840 [size=32]
    Memory at f2827000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset SMBus Controller [17aa:2167]
    Flags: medium devsel, IRQ 11
    Memory at f2828800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1880 [size=32]
    Kernel modules: i2c_i801

00:1f.6 Signal processing controller [1180]: Intel Corporation 5   Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset Thermal Subsystem [17aa:2190]
    Flags: fast devsel, IRQ 19
    Memory at f2626000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1311]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f2400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

0d:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 01)
    Subsystem: Lenovo MMC/SD Host Controller [17aa:2133]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f2500000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci

0d:00.1 System peripheral [0880]: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 /   R5U241) [Memory Stick Host Controller] [1180:e230] (rev 01)
    Subsystem: Lenovo R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [17aa:2134]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f2500400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

0d:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller [1180:e832] (rev 01) (prog-if 10 [OHCI])
    Subsystem: Lenovo R5C832 PCIe IEEE 1394 Controller [17aa:2136]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f2500800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci

ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath   Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Lenovo Core Processor QuickPath Architecture Generic Non-core Registers [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Lenovo Core Processor QuickPath Architecture System Address Decoder [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Lenovo Core Processor QPI Link 0 [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor QPI Physical 0 [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor Reserved [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor Reserved [17aa:2196]
    Flags: bus master, fast devsel, latency 0
 
```


Also, as I have no idea what I'm doing, I'm not quite sure how to set up my MiDi, and test it to make sure my laptop is getting the signal.
My MiDi is a Tascam iUR2. I did not see it on the sound interface support page ([http://wiki.linuxaudio.org/wiki/hardware_support](http://wiki.linuxaudio.org/wiki/hardware_support)), so who knows whether or not it will be supported.

Thank you guy and with luck you might have another sound head to add to the community.

---

### Post by CrocoDuck on 2016-10-12
Perhaps, [this]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack") will help. Have a good read and see how it goes. In the meanwhile, let's check the fundamentals:

Is your hardware working? Post the output of:
```

aplay -l
arecord -l
amidi -l

```

Are you in the audio group?
```

groups

```

Let's have a whole look at your hardware, just in case:
```

lspci -vnn

```

---

### Post by muddpup64 on 2016-10-12
> **CrocoDuck said:**
> Perhaps, [this]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack") will help. Have a good read and see how it goes. In the meanwhile, let's check the fundamentals:

Is your hardware working? Post the output of:
```

aplay -l
arecord -l
amidi -l

```

Are you in the audio group?
```

groups

```

Let's have a whole look at your hardware, just in case:
```

lspci -vnn

```


aplay -l Produces:

```
 **** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: iUR2 [iUR2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```

arecord -l Produces:

```
 **** List of CAPTURE Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: iUR2 [iUR2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```

amidi -l Produces: (Assuming I require my MiDi to be plugged in.)

```
 Dir Device    Name
IO  hw:1,0,0  iUR2 MIDI 1
IO  hw:1,0,1  iUR2 MIDI 2
 
```


I did forget to mention, and I apologize, I did manually add myself into  the group just to be sure I was there. Checking with "groups" does  confirm this.


And finally, 
lspci -vnn Produces:

```
 00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Lenovo Core Processor DRAM Controller [17aa:2193]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Core  Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if  00 [VGA controller])
    Subsystem: Lenovo Core Processor Integrated Graphics Controller [17aa:215a]
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset HECI Controller [17aa:215f]
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at f2827800 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
    Subsystem: Lenovo 82577LM Gigabit Network Connection [17aa:2153]
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f2600000 (32-bit, non-prefetchable) [size=128K]
    Memory at f2625000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series  Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06) (prog-if 20  [EHCI])
    Subsystem: Lenovo 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [17aa:2163]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f2828000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset High Definition Audio [17aa:215e]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f2620000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series  Chipset PCI Express Root Port 1 [8086:3b42] (rev 06) (prog-if 00 [Normal  decode])
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series  Chipset PCI Express Root Port 2 [8086:3b44] (rev 06) (prog-if 00 [Normal  decode])
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f2400000-f24fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series  Chipset PCI Express Root Port 4 [8086:3b48] (rev 06) (prog-if 00 [Normal  decode])
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0000000-f1ffffff
    Prefetchable memory behind bridge: 00000000f2900000-00000000f29fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series  Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06) (prog-if 00 [Normal  decode])
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
    Memory behind bridge: f2500000-f25fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series  Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06) (prog-if 20  [EHCI])
    Subsystem: Lenovo 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [17aa:2163]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f2828400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation QM57 Chipset LPC Interface Controller [8086:3b07] (rev 06)
    Subsystem: Lenovo QM57 Chipset LPC Interface Controller [17aa:2166]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series  Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06) (prog-if 01  [AHCI 1.0])
    Subsystem: Lenovo 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [17aa:2168]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 25
    I/O ports at 1860 [size=8]
    I/O ports at 1814 [size=4]
    I/O ports at 1818 [size=8]
    I/O ports at 1810 [size=4]
    I/O ports at 1840 [size=32]
    Memory at f2827000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset SMBus Controller [17aa:2167]
    Flags: medium devsel, IRQ 11
    Memory at f2828800 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1880 [size=32]
    Kernel modules: i2c_i801

00:1f.6 Signal processing controller [1180]: Intel Corporation 5  Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
    Subsystem: Lenovo 5 Series/3400 Series Chipset Thermal Subsystem [17aa:2190]
    Flags: fast devsel, IRQ 19
    Memory at f2626000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1311]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f2400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

0d:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 01)
    Subsystem: Lenovo MMC/SD Host Controller [17aa:2133]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f2500000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci

0d:00.1 System peripheral [0880]: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 /  R5U241) [Memory Stick Host Controller] [1180:e230] (rev 01)
    Subsystem: Lenovo R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] [17aa:2134]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f2500400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

0d:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller [1180:e832] (rev 01) (prog-if 10 [OHCI])
    Subsystem: Lenovo R5C832 PCIe IEEE 1394 Controller [17aa:2136]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f2500800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci

ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath  Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Lenovo Core Processor QuickPath Architecture Generic Non-core Registers [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Lenovo Core Processor QuickPath Architecture System Address Decoder [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Lenovo Core Processor QPI Link 0 [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor QPI Physical 0 [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor Reserved [17aa:2196]
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Lenovo 1st Generation Core i3/5/7 Processor Reserved [17aa:2196]
    Flags: bus master, fast devsel, latency 0
 
```



I also did forget to mention the MiDi I'm using is a Tascam iUR2. If we  can't figure it out, let's at least get Guitarix to work. I'll update my  orginal post with all this info.

---

### Post by CrocoDuck on 2016-10-13
Your tascam is recognized and should be working. Try to follow the tutorial I linked and revert back in case something does not work.

---

### Post by muddpup64 on 2016-10-13
> **CrocoDuck said:**
> Your tascam is recognized and should be working. Try to follow the tutorial I linked and revert back in case something does not work.


.
All my error messages went away. I used your handy dandy tutorial and am still getting no input. I've read the damn web page ten times, do I need to do some patch work? If so it doesn't really explain how.


Edit: I apologize. I answered my on question, yes I did need to do some patch work. Now I just need to set my latency. I think I can handle it from here. Thank you.

---

