---
title: "Audio glitches in Ubuntu Studio 16.04"
date: 2016-11-14
forum: Ubuntu Studio
---

### Post by rick.s on 2016-11-14
This is my first posting to this group so please be gentle. :-) I am running UbuntuStudio 16.04.  I have an issue when recording guitar into Ardour, playing video or playing audio, the system produces random audio glitches, short buzzing sound for about half a second combined with a pause in playback. Once the glitch passes, everything seems to work fine. Glitches not withstanding I am getting great sound, PulseAudio control seems to work, I can record with no Xruns in Ardour.  The CPU load when recording is in the 10% range.


Things I have tried:
Turning off all sound cards in PulseAudio except the Scarlett.
Setting sound card priority to Scarlett using command line.
Increasing frame/period, Periods/Buffer in Jack until latency was noticeable (Current setting 48000, 128, 4.)

None of the above fixed the problem.  I thought it might be a timing issue between sound cards (read that somewhere) but I don't know how to fix that.


I recently transitioned to Ubuntu after using Win10 for about 3 weeks.  Even if I can't fix this audio glitch, there is no going back.  That said, I would welcome any ideas you may have that could fix the problem.


Machine Specs:

    product: M32CD_A_F_K20CD_K31CD (SKU)
       product: M32CD_A_F_K20CD_K31CD
          product: Intel(R) Core(TM) i7-6700 CPU @ 3.40GHz  (16GB)
             product: HMA41GU6AFR8N-TF
             product: HMA41GU6AFR8N-TF
          product: Sky Lake Host Bridge/DRAM Registers
             product: Sky Lake PCIe Controller (x16)
                product: Curacao PRO [Radeon R7 370 / R9 270/370 OEM]
                product: Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
             product: Sunrise Point-H USB 3.0 xHCI Controller
                product: xHCI Host Controller
                   product: My Passport 0748
                      product: My Passport 0748
                      product: SES Device
                product: xHCI Host Controller
                   product: Scarlett 2i2 USB
                   product: Bluetooth Radio
                   product: Natural
                   product: USB Receiver
             product: Sunrise Point-H CSME HECI #1
             product: Sunrise Point-H SATA controller [AHCI mode]
             product: Sunrise Point-H PCI Express Root Port #5
                product: ASM1142 USB 3.1 Host Controller
                   product: xHCI Host Controller
                   product: xHCI Host Controller
                      product: UM-ONE
                      product: USB2.0 Hub
                         product: USB2.0-Print
                         product: Microsoft
             product: Sunrise Point-H PCI Express Root Port #7
                product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
             product: Sunrise Point-H PCI Express Root Port #8
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
             product: Sunrise Point-H PCI Express Root Port #9
             product: Sunrise Point-H LPC Controller
             product: Sunrise Point-H PMC
             product: Sunrise Point-H HD Audio
             product: Sunrise Point-H SMBus
             product: TOSHIBA DT01ACA2
             product: RAM GHD1N an 



**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: USB [Scarlett 2i2 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by CrocoDuck on 2016-11-15
Hi!

Please, enclose the output of your commands into code blocks like this:
```



**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: USB [Scarlett 2i2 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 		

```

Give us the outputs of
```

lspci -vnn

```

```

lsusb

```

These issues are usually caused by hardware sitting on the same USB bus where you connected your soundcard. Fixing it might be as simple as switching the USB port. We might have more details after you repost the output of your commands. If that does not fix it we might proceed to disable hardware selectively to try to find the device spanning the issue. Very often it is the wifi card. There is also the remote possibility of it being correlated with clock jitter (see [this thread]("https://www.linuxmusicians.com/viewtopic.php?f=6&t=11991"), the user solved it by slaving the device through an external clock).

Finally: double check the hardware: make sure none of the cables is dodgy. My Scarlelett 2i4 jack connectors are a little bit teared out, so sometimes the jack connection is unsteady (even if it looks alright) and makes pops and other artefacts.

---

### Post by rick.s on 2016-11-15
Thanks for the reply CrocoDuck.  The whole system is less than 1 month old so wear should not be an issue.  I'll recheck the cables in case.

Here is the output of lspci -vnn.

```
00:00.0 Host bridge [0600]: Intel Corporation Skylake Host Bridge/DRAM Registers [8086:191f] (rev 07)
    Subsystem: ASUSTeK Computer Inc. Skylake Host Bridge/DRAM Registers [1043:8694]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Skylake PCIe Controller (x16) [8086:1901] (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: dfe00000-dfefffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller [8086:a12f] (rev 31) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-H USB 3.0 xHCI Controller [1043:8694]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at dff10000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-H CSME HECI #1 [8086:a13a] (rev 31)
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dff2d000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] [8086:a102] (rev 31) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-H SATA controller [AHCI mode] [1043:8694]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
    Memory at dff28000 (32-bit, non-prefetchable) [size=8K]
    Memory at dff2c000 (32-bit, non-prefetchable) [size=256]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at dff2b000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #5 [8086:a114] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: dfd00000-dfdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #7 [8086:a116] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfc00000-dfcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.7 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #8 [8086:a117] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: dfb00000-dfbfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #9 [8086:a118] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 88800000-889fffff
    Prefetchable memory behind bridge: 0000000088a00000-0000000088bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-H LPC Controller [8086:a143] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-H LPC Controller [1043:8694]
    Flags: bus master, medium devsel, latency 0

00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-H PMC [8086:a121] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-H PMC [1043:8694]
    Flags: fast devsel
    Memory at dff24000 (32-bit, non-prefetchable) [disabled] [size=16K]

00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-H HD Audio [1043:86a6]
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at dff20000 (64-bit, non-prefetchable) [size=16K]
    Memory at dff00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-H SMBus [8086:a123] (rev 31)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-H SMBus [1043:8694]
    Flags: medium devsel, IRQ 255
    Memory at dff2a000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c_i801

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Curacao PRO [Radeon R7 370 / R9 270/370 OEM] [1002:6811] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Curacao PRO [Radeon R7 370 / R9 270/370 OEM] [1043:86a4]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dfe00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at e000 [size=256]
    Expansion ROM at dfe40000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
    Subsystem: ASUSTeK Computer Inc. Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1043:aab0]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at dfe60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

02:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller [1b21:1242] (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. ASM1142 USB 3.1 Host Controller [1043:8675]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dfd00000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave RTL8821AE 802.11ac PCIe Wireless Network Adapter [1a3b:2161]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at d000 [size=256]
    Memory at dfc00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8821ae
    Kernel modules: rtl8821ae

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:861d]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at c000 [size=256]
    Memory at dfb00000 (64-bit, non-prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

Here is the output of lsusb.

```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 045e:0779 Microsoft Corp. LifeCam HD-3000
Bus 003 Device 004: ID 1a86:7584 QinHeng Electronics CH340S
Bus 003 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub
Bus 003 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 004: ID 13d3:3414 IMC Networks 
Bus 001 Device 003: ID 1235:8202 Focusrite-Novation 
Bus 001 Device 002: ID 0582:009a Roland Corp. EDIROL UM-3EX
Bus 001 Device 006: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by CrocoDuck on 2016-11-15
> **rick.s said:**
> The whole system is less than 1 month old so wear should not be an issue.  I'll recheck the cables in case.

Mine worn out pretty quickly, connector quality is pretty bad on this series I think. Mine even make springy noises...

I would try your USB 3 ports if you didn't already. You might find links around the web suggesting to interface sound cards to USB 2, but I think that was a good advice back in the days when USB 3 driver implementation was new. Nowadays most of the early bugs should be ironed out. Usually internal peripherals use USB 2 internal hubs, so USB 3  hubs should clearer, with less stuff running on them.

By the way, give us also the output of 
```

cat /proc/interrupts

```

If changing port does not fix it we will try to figure out what to switch off to try identify the root of the issue.

---

### Post by rick.s on 2016-11-15
I tried different USB jacks.  As far as I can tell I have the same problem.

Here is output for interrupts.

```
            CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
   0:         59          0          0          0          0          0          0          0  IR-IO-APIC    2-edge      timer
   1:          1          0          0          0          0          1          0          0  IR-IO-APIC    1-edge      i8042
   7:         46          0          0          0          0          0          0          0  IR-IO-APIC    7-edge    
   8:          1          0          0          0          0          0          0          0  IR-IO-APIC    8-edge      rtc0
   9:          0          0          0          0          0          0          0          0  IR-IO-APIC    9-fasteoi   acpi
  12:          0          0          2          0          2          0          0          0  IR-IO-APIC   12-edge      i8042
  16:       4272       1252        569        408    1356813        866        481        385  IR-IO-APIC   16-fasteoi   xhci-hcd:usb1, xhci-hcd:usb3, 0000:00:17.0, radeon, mei_me, snd_hda_intel
  17:          0         40          5          2       1565        327        151        136  IR-IO-APIC   17-fasteoi   snd_hda_intel
  18:         11          3          3         30          2          3          0        647  IR-IO-APIC   18-fasteoi   rtl_pci
  19:          0          0      16803          0          0          1      45954          0  IR-IO-APIC   19-fasteoi   enp4s0
 120:          0          0          0          0          0          0          0          0  DMAR-MSI    0-edge      dmar0
 NMI:          6          5          5          5         10          3          2          2   Non-maskable interrupts
 LOC:     204319     217831     200969     202887     105280      93048      67771      65827   Local timer interrupts
 SPU:          0          0          0          0          0          0          0          0   Spurious interrupts
 PMI:          6          5          5          5         10          3          2          2   Performance monitoring interrupts
 IWI:          0          0          0          0          0          0          0          0   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:      84819      32388      13779      12634       3331      14143       9739       7944   Rescheduling interrupts
 CAL:      14508       4264       5387       3715     507954       3077       3178       2824   Function call interrupts
 TLB:       1123       1686       1397       1190        731       1383        855        713   TLB shootdowns
 TRM:          0          0          0          0          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
 DFR:          0          0          0          0          0          0          0          0   Deferred Error APIC interrupts
 MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
 MCP:          6          6          6          6          6          6          6          6   Machine check polls
 ERR:         46
 MIS:          0
 PIN:          0          0          0          0          0          0          0          0   Posted-interrupt notification event
 PIW:          0          0          0          0          0          0          0          0   Posted-interrupt wakeup event
```

I thought I didn't have xruns but the messages from Jack indicate otherwise.  

 ```
Tue Nov 15 20:02:20 2016: ERROR: JackEngine::XRun: client = Calf Reverb was not finished, state = Triggered

 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:02:20 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 [COLOR=#cc66cc]20:04:26.900 XRUN callback (21).[/COLOR]
 [COLOR=#cc66cc]20:05:29.793 XRUN callback (22).[/COLOR]
 Tue Nov 15 20:05:29 2016: ERROR: JackEngine::XRun: client = Carla was not finished, state = Triggered
 Tue Nov 15 20:05:29 2016: ERROR: JackEngine::XRun: client = Calf Reverb was not finished, state = Triggered
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 Tue Nov 15 20:05:29 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
 [COLOR=#cc99cc]20:05:31.093 XRUN callback (1 skipped).[/COLOR]

```

---

### Post by CrocoDuck on 2016-11-16
> **rick.s said:**
> 

  ```
16:       4272       1252        569        408    1356813        866        481        385  IR-IO-APIC   16-fasteoi   xhci-hcd:usb1, xhci-hcd:usb3, 0000:00:17.0, radeon, mei_me, snd_hda_intel
```



I think this is the seed of evil. You have a lot of hardware sitting on the same IRQ of your USB devices. I am at work now, I will try to came up with something to you to try tonight. In the meanwhile here few useful links:

[http://wiki.linuxaudio.org/wiki/system_configuration#solve_irq_conflicts_by_unbinding_devices](http://wiki.linuxaudio.org/wiki/system_configuration#solve_irq_conflicts_by_unbinding_devices)
[http://wiki.linuxaudio.org/wiki/system_configuration#priorities](http://wiki.linuxaudio.org/wiki/system_configuration#priorities)
[http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)
[https://linuxmusicians.com/viewtopic.php?t=15309](https://linuxmusicians.com/viewtopic.php?t=15309)

However, beware that the the first 3 are kinda old and perhaps we will need some adjustments to make it work under modern day Ubunutu. I am using Arch Linux, so I don't know whether your rtirq conf file is in the same location of mine either. We should be able to figure it out tho!

Hey, I am back!

So, first of all let's double check that xhci-hcd is the module governing the USB devices your Scarlett gets plugged in. With your device **unplugged** boot into Ubuntu and run

```

dmesg

```

and take note of the last line. Then plug your Scarlett, wait for 30 seconds and run dmesg again. Copy and paste here all the lines from the line you previously noted to the bottom.

Then, we should make sure rtirq is installed in your system and properly configured. First of all, let's see if you are booting with threadirqs. Report the output of:

```

cat /etc/default/grub

```

Next, we need to locate where your rtirq files are. I think the locate utility should be installed on your system. Give the output of these **2** commands:
```

locate rtirq
systemctl list-units

```

**These** next ones assume that rtirq is installed under Ubuntu as it is installed under Arch Linux. If they don't give valid output the commands above should be able to suggest how to modify them:
```

systemctl status rtirq
/usr/bin/rtirq status
cat /etc/conf.d/rtirq

```

Once we have these info, we can proceed editing the rtirq conf file (and/or the grub conf file), so that we can try to see if that avoids having your USB hubs, video card, video card audio codec and HECI all on the same IRQ. This proven to be beneficial in many similar situations.

You might want to check also [this video]("https://www.youtube.com/watch?v=MJbzWAVV198") I recorded. It is no audio, so I don't think it is very clear, but it shows how to use few of the commands above in combination with [realTimeConfigQuickScan]("https://github.com/raboof/realtimeconfigquickscan") to check the audio configuration of your system (together with possible IRQ issues).

---

### Post by rick.s on 2016-11-16
Thanks for all the help CrocoDuck. This is definitely a journey that requires an experienced guide. :)

For brevity, here is the difference between the first and second run of dmesg.

```
1129a1130,1134
> [ 1163.425538] usb 3-2: new high-speed USB device number 3 using xhci_hcd
> [ 1163.592746] usb 3-2: New USB device found, idVendor=1235, idProduct=8202
> [ 1163.592753] usb 3-2: New USB device strings: Mfr=1, Product=3, SerialNumber=0
> [ 1163.592757] usb 3-2: Product: Scarlett 2i2 USB
> [ 1163.592760] usb 3-2: Manufacturer: Focusrite
```

Output from grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="i915.preliminary_hw_support=1 quiet splash pci=nomsi"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```


Locate rtirq
```
/etc/default/rtirq
/etc/init.d/rtirq
/etc/rc0.d/K01rtirq
/etc/rc1.d/K01rtirq
/etc/rc2.d/S03rtirq
/etc/rc3.d/S03rtirq
/etc/rc4.d/S03rtirq
/etc/rc5.d/S03rtirq
/etc/rc6.d/K01rtirq
/usr/share/doc/rtirq-init
/usr/share/doc/rtirq-init/changelog.Debian.gz
/usr/share/doc/rtirq-init/copyright
/var/lib/dpkg/info/rtirq-init.conffiles
/var/lib/dpkg/info/rtirq-init.list
/var/lib/dpkg/info/rtirq-init.md5sums
/var/lib/dpkg/info/rtirq-init.postinst
/var/lib/dpkg/info/rtirq-init.postrm
/var/lib/dpkg/info/rtirq-init.prerm
```

...part 1

..part 2

Lost me a little here.   Ran systemctl status rtirq, got this. Command never finished?
```
 rtirq.service - LSB: Realtime IRQ thread tunning.
   Loaded: loaded (/etc/init.d/rtirq; bad; vendor preset: enabled)
   Active: active (exited) since Wed 2016-11-16 17:20:54 AST; 1h 29min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 964 ExecStart=/etc/init.d/rtirq start (code=exited, status=0/SUCCESS)

Nov 16 17:20:51 StudioPC systemd[1]: Starting LSB: Realtime IRQ thread tunning..
Nov 16 17:20:52 StudioPC rtirq[964]: Setting IRQ priorities: start [HDA-Intel] i
Nov 16 17:20:52 StudioPC rtirq[964]: Setting IRQ priorities: start [HDA-Intel] i
Nov 16 17:20:52 StudioPC rtirq[964]: Setting IRQ priorities: start [i8042] irq=1
Nov 16 17:20:52 StudioPC rtirq[964]: Setting IRQ priorities: start [i8042] irq=1
Nov 16 17:20:54 StudioPC systemd[1]: Started LSB: Realtime IRQ thread tunning..
lines 1-12/12 (END)
```

No /usr/bin/rtirq file.  /etc/init.d/rtirq status gives..

```
  PID CLS RTPRIO  NI PRI %CPU STAT COMMAND    
  506 FF      90   - 130  0.0 S    irq/17-snd_hda_    
  538 FF      90   - 130  0.0 S    irq/16-snd_hda_    
  114 FF      80   - 120  0.0 S    irq/1-i8042    
  113 FF      79   - 119  0.0 S    irq/12-i8042    
   58 FF      50   -  90  0.0 S    irq/9-acpi    
  110 FF      50   -  90  0.0 S    irq/16-xhci-hcd    
  111 FF      50   -  90  0.1 S    irq/16-xhci-hcd    
  115 FF      50   -  90  0.0 S    irq/8-rtc0    
  185 FF      50   -  90  0.0 S    irq/16-0000:00:    
  202 FF      50   -  90  0.0 S    irq/16-radeon    
  444 FF      50   -  90  0.0 S    irq/16-mei_me    
  575 FF      50   -  90  0.0 S    irq/18-rtl_pci    
 1284 FF      50   -  90  0.0 S    irq/19-enp4s0    
  445 FF      49   -  89  0.0 S    irq/16-s-mei_me    
    3 TS       -   0  19  0.0 S    ksoftirqd/0    
   14 TS       -   0  19  0.0 S    ksoftirqd/1    
   19 TS       -   0  19  0.0 S    ksoftirqd/2    
   24 TS       -   0  19  0.0 S    ksoftirqd/3    
   29 TS       -   0  19  0.0 S    ksoftirqd/4    
   34 TS       -   0  19  0.0 R    ksoftirqd/5    
   39 TS       -   0  19  0.0 R    ksoftirqd/6    
   44 TS       -   0  19  0.0 S    ksoftirqd/7   
```

No /etc/conf.d/rtirq file.  Cat /etc/default/rtirq gave this.

```
#
# Copyright (C) 2004-2015, rncbc aka Rui Nuno Capela.
#
#   This program is free software; you can redistribute it and/or
#   modify it under the terms of the GNU General Public License
#   as published by the Free Software Foundation; either version 2
#   of the License, or (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License along
#   with this program; if not, write to the Free Software Foundation, Inc.,
#   51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
#
# /etc/sysconfig/rtirq
# /etc/default/rtirq
#
# Configuration for IRQ thread tunning,
# for realtime-preempt enabled kernels.
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License version 2 or later.
#

# IRQ thread service names
# (space separated list, from higher to lower priority).
# RTIRQ_NAME_LIST="rtc snd usb i8042" # old
RTIRQ_NAME_LIST="snd usb i8042"

# Highest priority.
RTIRQ_PRIO_HIGH=90

# Priority decrease step.
RTIRQ_PRIO_DECR=5

# Lowest priority.
RTIRQ_PRIO_LOW=51

# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=0

# On kernel configurations that support it,
# which services should be NOT threaded
# (space separated list).
RTIRQ_NON_THREADED="rtc snd"

# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
# RTIRQ_HIGH_LIST="timer"
```

Apologies for the multi-part message but I keep getting a broken security token error that prevents me from posting.  I broke up the message and it looks like the problem is when I try to post the output from the systemctl list-units command.  Is there specific information you need in the output?

Here is what I could find related to the Scarlett
```
ASUS_DVD_RAM_GHD1N
  sys-devices-pci0000:00-0000:00:1c.0-0000:02:00.0-usb3-3\x2d2-3\x2d2:1.0-sound-card4.device loaded active plugged   Scarlett_2i2_USB
  sys-devices-pci0000:00-0000:00:1c.6-0000:03:00.0-net-wlp3s0.device                         loaded active plugged   RTL8821AE
```

I tried to follow your video as much as possible.  The video was low on my browser.  Combined with my old eyes, I couldn't get one of the commands to work. Here is output of realTimeConfigQuickScan.

```

== GUI-enabled checks ==
Checking if you are root... no - good
Checking filesystem 'noatime' parameter... 4.4.0 kernel - good
(relatime is default since 2.6.30)
Checking CPU Governors... CPU 0: 'performance' CPU 1: 'performance' CPU 2: 'performance' CPU 3: 'performance' CPU 4: 'performance' CPU 5: 'performance' CPU 6: 'performance' CPU 7: 'performance'  - good
Checking swappiness... 10 - good
Checking for resource-intensive background processes... none found - good
Checking checking sysctl inotify max_user_watches... >= 524288 - good
Checking access to the high precision event timer... readable - good
Checking access to the real-time clock... readable - good
Checking whether you're in the 'audio' group... yes - good
Checking for multiple 'audio' groups... no - good
Checking the ability to prioritize processes with chrt... yes - good
Checking kernel support for high resolution timers... found - good
Kernel with Real-Time Preemption... not found - not good
Kernel without real-time capabilities found
For more information, see http://wiki.linuxaudio.org/wiki/system_configuration#installing_a_real-time_kernel
Checking if kernel system timer is high-resolution... found - good
Checking kernel support for tickless timer... found - good
== Other checks ==
Checking filesystem types... ok.
not found.
** Warning: no tmpfs partition mounted on /tmp
   For more information, see:
   - http://wiki.linuxaudio.org/wiki/system_configuration#tmpfs
   - http://lowlatency.linuxaudio.org
** Set $SOUND_CARD_IRQ to the IRQ of your soundcard to enable more checks.
   Find your sound card's IRQ by looking at '/proc/interrupts' and lspci.
```

I tried to set Sound_Card_IRQ variable but got a file not found error.  From video it looked like command should be 
```
env SOUND_CARD_IRQ-16 perl ./realTimeConfigQuickScan.pl
```

I get No such file or directory.

---

### Post by CrocoDuck on 2016-11-17
Cool, let's go with order.

From dmesg:

> **rick.s said:**
> 

```

> [ 1163.425538] usb 3-2: new high-speed USB device number 3 using xhci_hcd

```


Indeed, the Focusrite is using xhci_hcd, so we need to take care of that.

The grub configuration does not show threadirqs as a boot option. Usually that is needed in order for ritirq to work properly, but apparently (according to the output of /etc/init.d/rtirq status) rtirq appears to be running ok, so let's leave that for now. Seems like you have located the rtirq configuration file yourself: /etc/default/rtirq :guitar:. Open it with a text editor (you will probably need sudo, like sudo gedit /etc/default/rtirq) and edit the RTIRQ_NAME_LIST variable to this:
```

RTIRQ_NAME_LIST="xhci"

```

Let's leave only the usb stuff to take high priority for now. The other parameters seem ok to me. Once you modify the file, reboot.

systemctl status rtirq output is good. Yes, you have to hit q to exit, I should have mentioned that. It shows that rtirq runs as a background service in your system and it is correctly loaded at startup.

The output of realTimeConfigQuickScan looks very good, sorry for my bad video (I should have talked on it... but I have a bad mic), the commands is like that:

```

env SOUND_CARD_IRQ=16 perl ./realTimeConfigQuickScan.pl

```

it is configuring the environment variable SOUND_CARD_IRQ to 16 for the run of realTimeConfigQuickScan, so that the script will read it and check for IRQ conflicts at that value.

So, you can try the new rtirq configuration and see if it makes any improvement. If you don't have any benefit, repost here cat /proc/interrupts and /etc/init.d/rtirq status again to see if we changed something.

We have few backup plans in case this fails (I will assist you on this if we need to):


[LIST=1]
[*]Boot with threadirqs (Ineffective, see below) 
[*]Disable on board audio 
[*]Disable your realtek wifi 
[*]Kill PulseAudio and/or try [this]("https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Glitches.2C_skips_or_crackling"). 
[*]Try a RT kernel 
[*]Try some device unbinding (not sure whether this can be done) 
[*]Have a deeper look at what your Video Card is doing 
[/LIST]

The last two seem unrelated, but I have seen many times the wifi giving troubles also in absence of IRQ conflicts (on my old laptop, for example). Also, your video card and its onboard audio codec not only sit on the same IRQ of the USB controllers (hopefully the new rtirq conf solves that) but the radeon driver might be spawning quirks with the lowlatency kernel and we might want to try another driver.

But let us know how it goes with rtirq new configuration first ;-). Sorry it is getting a little messy, but these sort of problems are the hardest to deal with, as it is always hard to figure out *what* is actually producing them.

---

### Post by rick.s on 2016-11-17
Hi CrocoDuck, 

I modified the configuration file to include the RTIRQ_NAME_LIST="xhci".  I rebooted and tested audio.  It might be my imagination but it seems a bit better, ie less momentary lockups and less buzzing but I still get xruns with minimal cpu load.

Here is output of interrupts.
```
            CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
   0:         59          0          0          0          0          0          0          0  IR-IO-APIC    2-edge      timer
   1:          0          1          0          0          0          1          0          0  IR-IO-APIC    1-edge      i8042
   7:         46          0          0          0          0          0          0          0  IR-IO-APIC    7-edge    
   8:          0          1          0          0          0          0          0          0  IR-IO-APIC    8-edge      rtc0
   9:          0          0          0          0          0          0          0          0  IR-IO-APIC    9-fasteoi   acpi
  12:          1          1          0          0          0          0          2          0  IR-IO-APIC   12-edge      i8042
  16:       3972       1041        697        290   10650968        600        399        245  IR-IO-APIC   16-fasteoi   xhci-hcd:usb1, xhci-hcd:usb3, 0000:00:17.0, radeon, mei_me, snd_hda_intel
  17:         40        298          1         45       1073        222        231         50  IR-IO-APIC   17-fasteoi   snd_hda_intel
  18:          9          1          0        382         22          1          4      29962  IR-IO-APIC   18-fasteoi   rtl_pci
  19:          5          0      64479          0          7          0     779610          0  IR-IO-APIC   19-fasteoi   enp4s0
 120:          0          0          0          0          0          0          0          0  DMAR-MSI    0-edge      dmar0
 NMI:         56         55         54         54         82         25         24         24   Non-maskable interrupts
 LOC:    4010689    4055121    3844071    4147093    1067941     832565     926141     780876   Local timer interrupts
 SPU:          0          0          0          0          0          0          0          0   Spurious interrupts
 PMI:         56         55         54         54         82         25         24         24   Performance monitoring interrupts
 IWI:          0          0          0          0          0          0          0          0   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:     614915     252822     114655      82180     373902      80013      38833      37372   Rescheduling interrupts
 CAL:      45579      10547      10028       9237    2885213       7420       7219       8201   Function call interrupts
 TLB:      55336      49460      47124      57869      20511      36517      35536      27859   TLB shootdowns
 TRM:          0          0          0          0          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
 DFR:          0          0          0          0          0          0          0          0   Deferred Error APIC interrupts
 MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
 MCP:        197        197        197        197        197        197        197        197   Machine check polls
 ERR:         46
 MIS:          0
 PIN:          0          0          0          0          0          0          0          0   Posted-interrupt notification event
 PIW:          0          0          0          0          0          0          0          0   Posted-interrupt wakeup event
```

Here is output of rtirq
```
  PID CLS RTPRIO  NI PRI %CPU STAT COMMAND    
   58 FF      50   -  90  0.0 S    irq/9-acpi    
  110 FF      50   -  90  0.1 S    irq/16-xhci-hcd    
  111 FF      50   -  90  0.5 S    irq/16-xhci-hcd    
  113 FF      50   -  90  0.0 S    irq/12-i8042    
  114 FF      50   -  90  0.0 S    irq/1-i8042    
  115 FF      50   -  90  0.0 S    irq/8-rtc0    
  174 FF      50   -  90  0.0 S    irq/16-0000:00:    
  195 FF      50   -  90  0.1 S    irq/16-radeon    
  465 FF      50   -  90  0.0 S    irq/16-mei_me    
  526 FF      50   -  90  0.0 S    irq/17-snd_hda_    
  608 FF      50   -  90  0.0 S    irq/16-snd_hda_    
  617 FF      50   -  90  0.0 S    irq/18-rtl_pci    
 1243 FF      50   -  90  0.0 S    irq/19-enp4s0    
  466 FF      49   -  89  0.0 S    irq/16-s-mei_me    
    3 TS       -   0  19  0.0 S    ksoftirqd/0    
   14 TS       -   0  19  0.0 S    ksoftirqd/1    
   19 TS       -   0  19  0.0 S    ksoftirqd/2    
   24 TS       -   0  19  0.0 S    ksoftirqd/3    
   29 TS       -   0  19  0.0 S    ksoftirqd/4    
   34 TS       -   0  19  0.0 R    ksoftirqd/5    
   39 TS       -   0  19  0.0 S    ksoftirqd/6    
   44 TS       -   0  19  0.0 S    ksoftirqd/7  
```  

Here is output of realtimeconfig set at 16
```
== GUI-enabled checks ==
Checking if you are root... no - good
Checking filesystem 'noatime' parameter... 4.4.0 kernel - good
(relatime is default since 2.6.30)
Checking CPU Governors... CPU 0: 'performance' CPU 1: 'performance' CPU 2: 'performance' CPU 3: 'performance' CPU 4: 'performance' CPU 5: 'performance' CPU 6: 'performance' CPU 7: 'performance'  - good
Checking swappiness... 10 - good
Checking for resource-intensive background processes... none found - good
Checking checking sysctl inotify max_user_watches... >= 524288 - good
Checking access to the high precision event timer... readable - good
Checking access to the real-time clock... readable - good
Checking whether you're in the 'audio' group... yes - good
Checking for multiple 'audio' groups... no - good
Checking the ability to prioritize processes with chrt... yes - good
Checking kernel support for high resolution timers... found - good
Kernel with Real-Time Preemption... not found - not good
Kernel without real-time capabilities found
For more information, see http://wiki.linuxaudio.org/wiki/system_configuration#installing_a_real-time_kernel
Checking if kernel system timer is high-resolution... found - good
Checking kernel support for tickless timer... found - good
== Other checks ==
Checking filesystem types... ok.
not found.
** Warning: no tmpfs partition mounted on /tmp
   For more information, see:
   - http://wiki.linuxaudio.org/wiki/system_configuration#tmpfs
   - http://lowlatency.linuxaudio.org
** multiple devices found at the sound cards' IRQ
```

---

### Post by CrocoDuck on 2016-11-18
Hey! Sorry for the late reply, I have been very busy at work.

realTimeConfigQuickscan confirmed what /proc/interrupts showed to us. Good.

The output of rtirq is good, it shows we indeed bumped up xhci.

Not sure whether it will change anything, but let's try to boot with the threadirqs option. We need to edit, with rood privileges, /etc/default/grub. So:

```

sudo gedit /etc/default/grub

```

Locate this line:
```

GRUB_CMDLINE_LINUX=""

```

and add the threadirqs option:
```

GRUB_CMDLINE_LINUX="threadirqs"

```

Then, regenerate the grub configuration (we will use the command suggested by the conf file itself):
```

sudo update-grub

```

Once the above finishes, reboot. Post again the output of interrupts and rtirq.


By the way, have a look at your BIOS for any IRQ related setting. Maybe we can just bump manually a port.

I am gonna edit my backup plan list with a new option to try.

---

### Post by rick.s on 2016-11-19
No worries! One does not complain when getting free help. ;)

Changed setting in grub.

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="i915.preliminary_hw_support=1 quiet splash pci=nomsi"
GRUB_CMDLINE_LINUX="threadirqs"

```

Did some audio testing, still getting same results.  One thing I noticed when recording in Ardour, the most audible glitches seems to be happening with a distinct pattern.  First glitch at 30secs, then a glitch every minute (+/- a few seconds) after that. 

I checked the BIOS for IRQ related options but could not find any.  Here are a few that I thought might be related.
```
Hyperthreading Technology - Supported
Hyperthreading - Enabled
XCHI Hand-Off - Disabled
```

Here is new output of rtirq

```
  PID CLS RTPRIO  NI PRI %CPU STAT COMMAND    
   58 FF      50   -  90  0.0 S    irq/9-acpi    
  111 FF      50   -  90  0.5 S    irq/16-xhci-hcd    
  112 FF      50   -  90  3.4 S    irq/16-xhci-hcd    
  114 FF      50   -  90  0.0 S    irq/12-i8042    
  115 FF      50   -  90  0.0 S    irq/1-i8042    
  116 FF      50   -  90  0.0 S    irq/8-rtc0    
  186 FF      50   -  90  0.2 S    irq/16-0000:00:    
  202 FF      50   -  90  1.0 S    irq/16-radeon    
  457 FF      50   -  90  0.2 S    irq/16-mei_me    
  492 FF      50   -  90  0.0 S    irq/17-snd_hda_    
  538 FF      50   -  90  0.2 S    irq/16-snd_hda_    
  600 FF      50   -  90  0.0 S    irq/18-rtl_pci    
 1247 FF      50   -  90  0.0 S    irq/19-enp4s0    
  458 FF      49   -  89  0.0 S    irq/16-s-mei_me    
    3 TS       -   0  19  0.1 S    ksoftirqd/0    
   14 TS       -   0  19  0.0 S    ksoftirqd/1    
   19 TS       -   0  19  0.0 R    ksoftirqd/2    
   24 TS       -   0  19  0.0 S    ksoftirqd/3    
   29 TS       -   0  19  0.0 S    ksoftirqd/4    
   34 TS       -   0  19  0.0 S    ksoftirqd/5    
   39 TS       -   0  19  0.0 S    ksoftirqd/6    
   44 TS       -   0  19  0.0 S    ksoftirqd/7  
```  

Here is new output of interrupts
```
            CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
   0:         55          0          0          0          0          0          0          0  IR-IO-APIC    2-edge      timer
   1:          0          1          0          0          0          1          0          0  IR-IO-APIC    1-edge      i8042
   7:         42          0          0          0          0          0          0          0  IR-IO-APIC    7-edge    
   8:          0          0          0          0          0          1          0          0  IR-IO-APIC    8-edge      rtc0
   9:          0          0          0          0          0          0          0          0  IR-IO-APIC    9-fasteoi   acpi
  12:          0          1          0          1          1          0          1          0  IR-IO-APIC   12-edge      i8042
  16:       5114        292        702        155    2290515       1030        484        313  IR-IO-APIC   16-fasteoi   xhci-hcd:usb1, xhci-hcd:usb3, 0000:00:17.0, radeon, mei_me, snd_hda_intel
  17:         20        219        218         28       1356        313        118          2  IR-IO-APIC   17-fasteoi   snd_hda_intel
  18:         17          0          0        110          3          4          3        905  IR-IO-APIC   18-fasteoi   rtl_pci
  19:          0          0       1300          0          0          1       6851          0  IR-IO-APIC   19-fasteoi   enp4s0
 120:          0          0          0          0          0          0          0          0  DMAR-MSI    0-edge      dmar0
 NMI:         12         12         11         11         20          8          5          8   Non-maskable interrupts
 LOC:     369454     393651     358229     360608     203782     144032     234938     133037   Local timer interrupts
 SPU:          0          0          0          0          0          0          0          0   Spurious interrupts
 PMI:         12         12         11         11         20          8          5          8   Performance monitoring interrupts
 IWI:          0          0          0          0          0          0          0          0   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:     131331      60715      39457      38819     248104      26142       9015      14474   Rescheduling interrupts
 CAL:      10959       7579       8220       2935     958125       5049       3757       3098   Function call interrupts
 TLB:      12208       8497       6965       9802       2773       5197       5248       4034   TLB shootdowns
 TRM:          0          0          0          0          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
 DFR:          0          0          0          0          0          0          0          0   Deferred Error APIC interrupts
 MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
 MCP:          8          8          8          8          8          8          8          8   Machine check polls
 ERR:         42
 MIS:          0
 PIN:          0          0          0          0          0          0          0          0   Posted-interrupt notification event
 PIW:          0          0          0          0          0          0          0          0   Posted-interrupt wakeup event
```

Stupid question: Would installing a USB PCI card make a difference? I have one kicking around that I could test.

---

### Post by CrocoDuck on 2016-11-19
> **rick.s said:**
>  One thing I noticed when recording in Ardour, the most audible glitches seems to be happening with a distinct pattern.  First glitch at 30secs, then a glitch every minute (+/- a few seconds) after that.

Periodic XRUNs and glitches are a sign of interfering processes and hardware, another clue we are looking in the right direction. I really have the gut feeling that all of this spawns from the fact your video card is on the same IRQ of the USB controllers. Pretty unlucky really.

> **rick.s said:**
>  Stupid question: Would installing a USB PCI card make a difference? I have one kicking around that I could test.         
If we are lucky we might end up with a new port on a different IRQ that we can then bump with rtirq, so definitely worth the try.

I think that before committing full force to IRQ troubleshooting we should rule out the other two common causes of this behaviour, which are wifi cards and other sound-cards. In particular, I am kinda worried by the audio codec of your Radeon...

So, let's do this: install the new USB port and test it. You can report here lspci -vnn and cat /proc/interrupts after you boot with the new card. If we are unlycky with that, let's make a test shutting down wifi and other audio codecs.

I added few new items in the backup plan above (one concerning PulseAudio).

---

### Post by rick.s on 2016-11-20
To my surprise, adding the PCI USB card is not an option.  The machine  is a new Asus desktop and it has no expansion slots at all.  A sign of  cost cutting measures I guess.

I went to the next step in your plan and turned off the wifi using
```
sudo ifconfig wp3s0 down
```

You were right, it looks like the problem is related to the wifi card.  No more xruns or periodic audio glitches.  

Output from interrupts
```
            CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
   0:         54          0          0          0          0          0          0          0  IR-IO-APIC    2-edge      timer
   1:          0          0          0          0          0          1          0          1  IR-IO-APIC    1-edge      i8042
   8:          0          0          0          0          0          0          0          1  IR-IO-APIC    8-edge      rtc0
   9:          0          0          0          0          0          0          0          0  IR-IO-APIC    9-fasteoi   acpi
  12:          1          0          0          1          1          1          0          0  IR-IO-APIC   12-edge      i8042
  16:       3768        996        286        907   13543992       1107        242        248  IR-IO-APIC   16-fasteoi   xhci-hcd:usb1, xhci-hcd:usb3, 0000:00:17.0, radeon, mei_me, snd_hda_intel
  17:          4         65         24          3       1002        985         54         35  IR-IO-APIC   17-fasteoi   snd_hda_intel
  18:          8          1          1         64          5          0          5        812  IR-IO-APIC   18-fasteoi   rtl_pci
  19:         20          0       1121          7         18          5       7279          3  IR-IO-APIC   19-fasteoi   enp4s0
 120:          0          0          0          0          0          0          0          0  DMAR-MSI    0-edge      dmar0
 NMI:         17         17         16         15         42         11          8          9   Non-maskable interrupts
 LOC:     568376     572313     565929     549708     330177     207485     232068     182389   Local timer interrupts
 SPU:          0          0          0          0          0          0          0          0   Spurious interrupts
 PMI:         17         17         16         15         42         11          8          9   Performance monitoring interrupts
 IWI:          0          0          0          0          0          0          0          0   IRQ work interrupts
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries
 RES:     240562     108615      67265      71045       8276      38758      19564      20738   Rescheduling interrupts
 CAL:      16096      12588       5426       6191    1519149       6639       4585       3714   Function call interrupts
 TLB:      19355      18846      12497      14061       5943      11612      12027      12526   TLB shootdowns
 TRM:          0          0          0          0          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
 DFR:          0          0          0          0          0          0          0          0   Deferred Error APIC interrupts
 MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
 MCP:         12         12         12         12         12         12         12         12   Machine check polls
 ERR:          0
 MIS:          0
 PIN:          0          0          0          0          0          0          0          0   Posted-interrupt notification event
 PIW:          0          0          0          0          0          0          0          0   Posted-interrupt wakeup event
```

The machine is a desktop so I can turn off wifi permanently with no inconvenience.  

The interrupt info above shows CPU4 having way more interrupts on 16.  Is this normal?

---

### Post by CrocoDuck on 2016-11-20
> **rick.s said:**
> 
You were right, it looks like the problem is related to the wifi card.  No more xruns or periodic audio glitches.  


Oh dear, we should have checked that at the very beginning. Wi-Fi has been cause of frustration [for me as well]("https://ubuntuforums.org/showthread.php?t=1976254") in the past.

> **rick.s said:**
> 
The interrupt info above shows CPU4 having way more interrupts on 16.  Is this normal? 


I think it is your system default configuration to handle it that way and if I am not wrong it is a good thing: having only one core dealing with all those interrupts requests should make the queue fast. If I am not wrong, loading different cores to handle interrupts from different priorities is indeed good practice, as it avoids bottlenecks parallelizing interrupts requests. But I might be wrong as I only marginally made experiments with this and I don't really remember much.

Pretty much, you can configure which CPUs handle interrupts requests through smp_affinity. [This]("https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Performance_Tuning_Guide/s-cpu-irq.html") should explain to you the basics of how it works. Fine tuning of this stuff is pretty advanced, I can try to dig out the Linux Musicians forums posts were I found this discussed if you are interested.

---

### Post by rick.s on 2016-11-20
Thanks for all the help CrocoDuck! May you be blessed with great musical inspiration as a reward for helping others. ;)

---

### Post by CrocoDuck on 2016-11-20
Happy to have been useful :)! If you think your problem is solved mark the thread as Solved.

---

