---
title: "Buzzing in speakers when headsets are plugged in and back jacks are muted"
date: 2017-01-16
forum: Ubuntu Studio
---

### Post by lutzux on 2017-01-16
Hello,

I have a problem with the audio device - it buzzes when the audio is switched to the headsets and the back jacks are 'muted'.
I have disabled power saving for the device with no success
Turning auto mute off fixes it, because the device is enabled, but this is not a solution for me as i need the audio to switch to the headsets when i plug them in and not output to both speakers and headset.

My audio is Realtek and i'm using it as 'generic' model ( otherwise auto mute does not even work ).
It seems to me like this is a problem with the realtek driver and/or the way it mutes the device.

Question is : is there any way i can force the speakers to be kept alive with a 0 volume signal or anything inaudible while the headsets are plugged ? Otherwise is there a proper fix for this ?

Let me know if i can provide any info that would be relevant.
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK110 [GeForce GTX 780] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK110 HDMI Audio (rev a1)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
06:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
06:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)



```
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Generic Analog [Generic Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: Generic Digital [Generic Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```
```

Linux MyComputerName 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

```

---

### Post by CrocoDuck on 2017-01-17
Hi. Often these problems are solved by telling ALSA the exact model of your audio codec (if it happens there is a suitable option). Have a look at your soundcards:

Use this to locate the affected card. Take note of the number on the left and use it in the next command.
```

cat /proc/asound/cards

```

```

cat /proc/asound/card1/codec* | grep Codec

```

Use cardX instead of card1, where X is the number you found above. Then, we will have a look if there are specific options for that codec. Worth to also post the output of

```

lspci -vnn

```

---

### Post by lutzux on 2017-01-24
Hi,
First off thanks for trying to help!
I tried that, and here are the results :
```

$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7420000 irq 45
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 17
 2 [VX800          ]: USB-Audio - Microsoft LifeCam VX-800
                      Microsoft Microsoft LifeCam VX-800 at usb-0000:00:1d.0-1.2, high speed
```


```

$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek Generic

Note: With the generic one, the auto-mute works, it did not work with the one it originally took ( though  i do not remember the one it initially had )


```


```

$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
	Subsystem: ASUSTeK Computer Inc. P8P67/P8H67 Series Motherboard [1043:844d]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: snb_uncore


00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 25
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f6000000-f70fffff
	Prefetchable memory behind bridge: 00000000e8000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f742c000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei_me
	Kernel modules: mei_me


00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
	DeviceName:  Onboard LAN
	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f7400000 (32-bit, non-prefetchable) [size=128K]
	Memory at f7429000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e


00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f7428000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: ASUSTeK Computer Inc. 6 Series/C200 Series Chipset Family High Definition Audio Controller [1043:8469]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f7420000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: e0100000-e02fffff
	Prefetchable memory behind bridge: 00000000e0300000-00000000e04fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f7300000-f73fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: f7200000-f72fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.6 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7100000-f71fffff
	Capabilities: <access denied>


00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7427000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:1f.0 ISA bridge [0601]: Intel Corporation P67 Express Chipset Family LPC Controller [8086:1c46] (rev 05)
	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:844d]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich


00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller [8086:1c02] (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
	I/O ports at f090 [size=8]
	I/O ports at f080 [size=4]
	I/O ports at f070 [size=8]
	I/O ports at f060 [size=4]
	I/O ports at f020 [size=32]
	Memory at f7426000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci


00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: ASUSTeK Computer Inc. P8 series motherboard [1043:844d]
	Flags: medium devsel, IRQ 10
	Memory at f7425000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f000 [size=32]
	Kernel modules: i2c_i801


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK110 [GeForce GTX 780] [10de:1004] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Palit Microsystems Inc. GK110 [GeForce GTX 780] [1569:1004]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (64-bit, prefetchable) [size=128M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at f7000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nouveau, nvidia_375_drm, nvidia_375


01:00.1 Audio device [0403]: NVIDIA Corporation GK110 HDMI Audio [10de:0e1a] (rev a1)
	Subsystem: Palit Microsystems Inc. GK110 HDMI Audio [1569:1004]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


03:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04) (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:8413]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7300000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd


04:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04) (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:8413]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd


05:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 01) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Bus: primary=05, secondary=06, subordinate=06, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7100000-f71fffff
	Capabilities: <access denied>


06:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL-8110SC/8169SC Gigabit Ethernet [1043:820d]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at d000 [size=256]
	Memory at f7121000 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at f7100000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


06:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Motherboard [1043:81fe]
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at f7120000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at d100 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire_ohci



```

---

### Post by CrocoDuck on 2017-01-25
No particular options [listed]("https://dri.freedesktop.org/docs/drm/sound/hd-audio/models.html") for your codec. However, are you on a Asus laptop? You could try this:

Edit /etc/modprobe.d/alsa-base.conf:

```

sudo gedit /etc/modprobe.d/alsa-base.conf

```

And add

```

options snd-hda-intel model=asus

```

This will be effective after reboot. If alsa-base.conf has other contents, post them here before to proceed.

---

### Post by lutzux on 2017-01-27
It's not a laptop, it's a i7 desktop.
Tried that anyway, still buzzes, but no negative side effects extra ( at least ).

---

### Post by CrocoDuck on 2017-01-29
Uhm... alright. I am thinking we might work around this using a shell script that makes muting of the speaker channels when the headphone insertion is detected. Let's start see if we can mute/unmute the required channels from command line. For example, these two will mute/unmute Master:

```

amixer set Master mute
amixer set Master unmute

```

Replace Master with the _case sensitive_ speaker channel name (It should be the same displayed in alsamixer). amixer is a command line version of alsamixer by the way. When we can make the switch with textual instruction we will first produce two scripts and then study what happens in your system when you plug/unplug the headphone.

Few references to guide us:
[http://unix.stackexchange.com/questions/21089/how-to-use-command-line-to-change-volume#21090](http://unix.stackexchange.com/questions/21089/how-to-use-command-line-to-change-volume#21090)
[https://bbs.archlinux.org/viewtopic.php?id=141910](https://bbs.archlinux.org/viewtopic.php?id=141910)
[http://unix.stackexchange.com/questions/25776/detecting-headphone-connection-disconnection-in-linux](http://unix.stackexchange.com/questions/25776/detecting-headphone-connection-disconnection-in-linux)

---

