---
title: "surround sound"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by ronb19495 on 2014-04-04
Hi
Has anybody managed to get 5.1 surround sound working on trusty.I have played around with this all day cant get it to work ,front speakers work ok back speakers no but they work fine on windows,has any body got any clue as why it wont work
regards Ron
 [http://www.alsa-project.org/db/?f=2a4ce47f9d8fc7601671272327060a8977ca3faa](http://www.alsa-project.org/db/?f=2a4ce47f9d8fc7601671272327060a8977ca3faa)
```
lspci 00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
03:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
05:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
lspci -v Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: ASRock Incorporation Device 0c00
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
    Subsystem: ASRock Incorporation Device 0412
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASRock Incorporation Device 8c31
    Flags: bus master, medium devsel, latency 0, IRQ 40
    Memory at f0720000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: ASRock Incorporation Device 8c3a
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f073b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei_me

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)
    Subsystem: ASRock Incorporation Device 153b
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at f0700000 (32-bit, non-prefetchable) [size=128K]
    Memory at f0739000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASRock Incorporation Device 8c2d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f0738000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
    Subsystem: ASRock Incorporation Device 1020
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at f0730000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f0600000-f06fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f0500000-f05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f0400000-f04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASRock Incorporation Device 8c26
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0737000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 04)
    Subsystem: ASRock Incorporation Device 8c44
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Device 8c02
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at f0d0 [size=8]
    I/O ports at f0c0 [size=4]
    I/O ports at f0b0 [size=8]
    I/O ports at f0a0 [size=4]
    I/O ports at f060 [size=32]
    Memory at f0736000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: ASRock Incorporation Device 8c22
    Flags: medium devsel, IRQ 10
    Memory at f0735000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]

03:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 47
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e030 [size=8]
    I/O ports at e020 [size=4]
    I/O ports at e000 [size=32]
    Memory at f0600000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: ahci

04:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
    Subsystem: ASRock Incorporation Device 1539
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f0500000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=32]
    Memory at f0520000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: igb

05:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: ASRock Incorporation Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 49
    I/O ports at c050 [size=8]
    I/O ports at c040 [size=4]
    I/O ports at c030 [size=8]
    I/O ports at c020 [size=4]
    I/O ports at c000 [size=32]
    Memory at f0400000 (32-bit, non-prefetchable) [size=512]
    Capabilities: <access denied>
    Kernel driver in use: ahci

ron@ron-desktop:~$
 aplay -L && aplay -l
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=PCH
    HDA Intel PCH, CA0132 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, CA0132 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, CA0132 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, CA0132 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, CA0132 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, CA0132 Digital
    Hardware device with all software conversions
sysdefault:CARD=Headset
    Logitech G930 Headset, USB Audio
    Default Audio Device
front:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    Direct sample mixing device
dsnoop:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    Direct sample snooping device
hw:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Headset,DEV=0
    Logitech G930 Headset, USB Audio
    Hardware device with all software conversions
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CA0132 Digital [CA0132 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech G930 Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ron@ron-desktop:~$
```

---

### Post by cariboo on 2014-04-04
Have you tried alsamixer, to make sure all the volume levels are set high enough to hear anything? See the screenshot:

---

### Post by ronb19495 on 2014-04-04
yes tried that also all I get is the first 2 master and pcm I am going to reinstall trusty and see what happens will reply when i have done that
regards ron

---

### Post by ronb19495 on 2014-04-04
still the same after reinstalling ubuntu have tried switching jacks still nothing will put screenshot of alsamixer

---

### Post by SeijiSensei on 2014-04-05
Try installing **pavucontrol** and see if that works better than alsamixer.

---

### Post by ronb19495 on 2014-04-05
yes have pavucontrol installed nothing wants to pick up these rear speakers on trusty thanks for your help
regards ron

---

### Post by snkiz on 2014-04-05
Do This, [http://www.webupd8.org/2009/06/enable-surround-sound-in-ubuntu-linux.html](http://www.webupd8.org/2009/06/enable-surround-sound-in-ubuntu-linux.html) then wipe out any pulse config in you home and .config dir You'll need to show hidden files to find everything. reboot and selsect you output with sound settings.

23 hours 120 views and no one? wow.

---

### Post by sdowney717 on 2014-04-05
See if alsamixer can slide over horizontally using right arrow key to select 6 channel sound.
That comes up on main boards with 3 mini jacks in the back to reassign sound ports.

---

### Post by ronb19495 on 2014-04-05
@sdowney777 heres 2 screenshots of alsamixer see what you can make of this[ATTACH=CONFIG]251744[/ATTACH][ATTACH=CONFIG]251745[/ATTACH]

---

### Post by sdowney717 on 2014-04-05
I know it wont likely help, but here is my alsamixer showing channels where I selected 6.
After this, in sound settings, 5.1 sound was a selectable profile and simply worked as expected.

Realtex 888 sound chip on the mainboard having 3 minijack sound ports in back panel.

What sound chip and model mainboard do you have?

---

### Post by ronb19495 on 2014-04-05
HDA Intel PCH card
Creative CA0132 chip
my mainboard is a  asrock fatal1ty z87 profesional series
I have a strang feeling this sound card doesnt like ubuntu the 2 front speakers work ok and when I boot I can hear a click from the rear speakers but thats it
regards Ron
I did what snkiz suggested but that hasnt worked either
Iedited a little bit more but that didnt work either
E: [pulseaudio] daemon-conf.c: [/etc/pulse/daemon.conf:80] Invalid channel map 'front-left,front-right,rear-left,centre,rear-right,lfe'.

---

### Post by sdowney717 on 2014-04-05
[http://www.phoronix.com/scan.php?page=news_item&px=MTEwNTg](http://www.phoronix.com/scan.php?page=news_item&px=MTEwNTg)

I notice the word 'basic' here, so IMO, the driver support for this chip is as your experiencing.

> One year after the Creative audio processors first were announced with Microsoft Windows support, there's finally Linux audio support coming from this latest hardware. 

Being pulled into the Linux 3.5 kernel will be support for Sound Core3D. As indicated by this ALSA patch, "The controller is compatible with HD-audio 1.0a with some specific restrictions. - The BDLE entries can't be over 4k boundary - No position-buffer and no MSI." 

As such, for this basic support at least, it comes via just modifying the Intel HDA PCI driver. You're dreaming though if you think this Linux support/patch comes from Creative, but rather it comes from Takashi Iwai -- the prolific Linux audio developer who maintains the kernel sound sub-system upstream and is employed by SUSE. 


And

> It's nice to see that Linux will finally support Creative Sound Core3D hardware when the Linux 3.5 kernel is introduced (the 3.5 sound pull request was sent this morning), but it's unfortunate that it's taken one year to materialize and that **Creative remains an unfriendly company towards Linux.**

So the driver is basic, and maybe you should get an add on audio card that will work with linux.?

It might never get better support, or it might, there is no way to know.

---

### Post by ronb19495 on 2014-04-05
yes I have been thinking of buying a pcie sound card but not sure what to buy have you any ideas
regards Ron

---

### Post by sdowney717 on 2014-04-05
I know the Realtek ALC888 chip works, and this
which I have in this PC
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

And this one in another mb I have  Realtek ALC655 6-channel S/W audio codec.
Dont buy Creative.:D

---

### Post by ronb19495 on 2014-04-05
thanks for the input folks looks like my creative chip wont give me surround sound on linux creative need to lift there game anyway thats it
regards Ron

---

### Post by ronb19495 on 2014-04-09
just a quick reply I thought I had my problem fixed with an asus xonar d2x pcie card but no then my motherboard cooked and it cooked the sound card as well an expensive day.so next move try and get motherboard fixed no wont happen ,so buy new motherboard,throw fatal1ty in the bin along with asus sound card,buy a new motherboard asrock z87 extreme 4 and to my amazement surround sound works on ubuntu out of the box.alc chip did the trick

---

