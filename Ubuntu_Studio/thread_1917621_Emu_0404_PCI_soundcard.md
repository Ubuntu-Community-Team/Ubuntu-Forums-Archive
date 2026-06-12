---
title: "Emu 0404 PCI soundcard"
date: 2012-01-30
forum: Ubuntu Studio
---

### Post by magicguitarman on 2012-01-30
Hi guys,

New to US but not totally new to Linux. I have been using Fedora and Ubuntu for a number of years on and off now but am by no means an expert and my know how is patchy.

Fedora 16 is proving far too unstable to do any DAW work on, so I am having a crack at Ubuntu Studio. 

Problem is I have no sound. I had the card working on Fedora using the guide here:

[http://fedoraforum.org/forum/showthread.php?t=245159](http://fedoraforum.org/forum/showthread.php?t=245159)

But I cannot find anything on Google that helps me in Ubuntu. Ubuntu knows the card is there, but ALSA doesn't, I cannot select it in alsamixer.

Here is the output of lspci

> 00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 PCI bridge: Pericom Semiconductor Device e111 (rev 02)
**03:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value**
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
05:05.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
06:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


Please tell me if I need to post more information. If I get it working I'll post a guide for others.

Thanks

magicguitarman

---

### Post by jejeman on 2012-01-30
I have audigy 2 value, and all I had to do is to switch from digital output to analog output. This is common for creative cards.
Give us output from
```
aplay -l
```
to see if it is recognized by alsa.

---

### Post by magicguitarman on 2012-01-30
harry@HarryPC:~$ aplay -l
aplay: device_list:240: no soundcards found...

Sadly it would seem not. Alsa detected it no problem in Fedora. I had to turn off my MB sound in BIOS.

---

### Post by jejeman on 2012-01-30
How about 
```
lsmod | grep snd
```
and 
```
sudo lshw -C multimedia
```

---

### Post by magicguitarman on 2012-01-30
> harry@HarryPC:~$ lsmod | grep snd
harry@HarryPC:~$ sudo lshw -C multimedia
[sudo] password for harry: 
  *-multimedia UNCLAIMED  
       description: Audio device
       product: Juniper HDMI Audio [Radeon HD 5700 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:fe6bc000-fe6bffff
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB0400 Audigy2 Value
       vendor: Creative Labs
       physical id: 4
       bus info: pci@0000:03:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=20 mingnt=2
       resources: ioport:b800(size=64)
  *-multimedia UNCLAIMED
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:fe5f8000-fe5fbfff
harry@HarryPC:~$ 


I don't know what I'm looking for in there, but I can see the same sound card again.

---

### Post by jejeman on 2012-01-30
Look here
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
And try from step 5.

---

### Post by magicguitarman on 2012-01-30
Had a crack through that and got all the way to manual install. That also didn't seem to do anything other that get Ubuntu to remind me I had proprietary ATI drivers installed?

Tried the purge and reinstall and got this:

> harry@HarryPC:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
[sudo] password for harry: 
Couldn't find any package whose name or description matched "linux-ubuntu-modules-3.0.0-15-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-3.0.0-15-generic"
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-3.0.0-15-generic 
  linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/38.7 MB of archives. After unpacking 0 B will be used.
E: Internal Error, No file name for libasound2
                                         
harry@HarryPC:~$ 
 

Not sure if that means I have something missing?

---

### Post by jejeman on 2012-01-30
Did the command
```
find /lib/modules/`uname -r` | grep snd
```
gave any result? If it did, then you have sound modules instaled. So maybe no need to reinstall.

as for output above, maybe the command is old, I need to check.


There are no linux-ubuntu-modules-`uname -r`, skip that.

---

### Post by magicguitarman on 2012-01-30
Yeah it did. Massive list of stuff, too long to post unless you really need to see it?

---

### Post by jejeman on 2012-01-30
Not, really need, but you can refine it with this
```
find /lib/modules/`uname -r` | grep emu10
```
because snd-emu10k1.ko is the modul you need to use for that card.

---

### Post by magicguitarman on 2012-01-30
Yeah it's installed alright.

```
/lib/modules/3.0.0-15-generic/kernel/sound/pci/emu10k1
/lib/modules/3.0.0-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.0.0-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.0.0-15-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.0.0-15-generic/kernel/drivers/input/gameport/emu10k1-gp.ko

```

I tried, out of interest some of the things in the Fedora guide, and the one that brought a response was 

```
modprobe snd-pcm-oss
```

Nothing to do with OSS can be found. Although I assume that's something to do with Ubuntu/Fedora differences?

---

### Post by jejeman on 2012-01-30
There is no oss in ubuntu now.
Try this 
```
sudo modprobe snd-emu10k1
```
After that see in
```
aplay -l
```
for sound card

---

### Post by jejeman on 2012-01-30
Also see this
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/58914](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/58914)

---

### Post by magicguitarman on 2012-01-30
> **jejeman said:**
> There is no oss in ubuntu now.
Try this 
```
sudo modprobe snd-emu10k1
```After that see in
```
aplay -l
```for sound card

Again, got the same response.

> **jejeman said:**
> Also see this
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/58914](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/58914)

Installed this, still nothing but now alsamixer won't open at all.

```
cannot open mixer: No such file or directory
```

---

### Post by jejeman on 2012-01-30
try to reboot after installing alsa firmware.

---

### Post by magicguitarman on 2012-01-30
Installed, and reinstalled. Still nothing and no alsamixer.

---

### Post by jejeman on 2012-01-30
Somethnig is wrong with your ubuntu instalation. Because it's not that EMU is not working, non of the sound cards are working. Sound modules are not loading.
Try for a test, to remove EMU card, and see if onboard will make alsa to load modules. Or disable onboard in bios.

Everything else beats my scope of knowledge at this moment.

---

### Post by magicguitarman on 2012-01-30
> **jejeman said:**
> Somethnig is wrong with your ubuntu instalation. Because it's not that EMU is not working, non of the sound cards are working. Sound modules are not loading.
Try for a test, to remove EMU card, and see if onboard will make alsa to load modules. Or disable onboard in bios.

Everything else beats my scope of knowledge at this moment.

Tried both of those, and nothing seems to be working. Might try another reinstall of the OS. But was really hoping Ubuntu would behave!

Anyhow, thank you very very much for your time this evening. Very much appricated!

---

### Post by sgx on 2012-02-02
Hi, this may help, although not from ubuntu, it seems
pulse audio was snatching sound from the ears of victory
and sending it to the sound chip on your video card

01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]

The newer hardware is sometimes not supported. Try to duplicate the steps
that led to success here:

[http://www.pclinuxos.com/forum/index.php?topic=101755.0](http://www.pclinuxos.com/forum/index.php?topic=101755.0)

Cheers

---

