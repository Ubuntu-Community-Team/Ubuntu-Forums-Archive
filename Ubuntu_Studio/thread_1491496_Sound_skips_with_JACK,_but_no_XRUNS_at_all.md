---
title: "Sound skips with JACK, but no XRUNS at all"
date: 2010-05-23
forum: Ubuntu Studio
---

### Post by svenskmand on 2010-05-23
I am running Ubuntu 10.04 with the realtime kernel 2.6.31-10-rt and the JACK settings as posted in the attached images and I am running this on a HP Pavilion dv7 1120eo with the specifications as [listed here (link)]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01580666&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=jm&lang=en&product=3819799"). I should say that I am new to music production and I have only played around with JACK, Ardour, Rosegarden and ZynAddSubFx for a week or so - on and off in my sparetime.

I have made a setup where I use ZynAddSubFx to generate sounds, which are played by Rosegarden. I get skips in the sound but no XRUNS at all during playback. I have recorded a sample of how it sounds by routing the output of ZynAddSubFx to Ardour, this sample is also attached in that tar.gz file.

As far as I have been able to find in the forums it might be that my audio card does not have a high enough priority, so I have tried to run the command
```

sudo chrt -f -p 82 `pidof hd-audio0`
sudo chrt -f -p 82 `pidof hd-audio1`

```
as I thought that these might be the process for the soundcard, but it did not help, so I suspect that I did something wrong :S

I did this as I read that it might help from this [thread (link)]("http://ubuntuforums.org/showpost.php?p=9162601&postcount=40").

I also read suggestions to do
```

sudo chrt -f -p 82 `pidof IRQ 16`

```
where IRQ 16 is the IRQ of my soundcard (I suppose this is 16, as far as I can read from lspci -v). But this just gave me the error message:
```

chrt: failed to get pid 82's policy: No such proces

``` 

Here is the output of lspci -v
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d2400000-d24fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: d1400000-d23fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1300000-d13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: d1200000-d12fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d1100000-d11fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at d2508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d2508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
	Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at d2400000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at d2420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1300000 (32-bit, non-prefetchable) [size=2K]
	Memory at d1300d00 (32-bit, non-prefetchable) [size=128]
	Memory at d1300c80 (32-bit, non-prefetchable) [size=128]
	Memory at d1300c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

08:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1300b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: fast devsel, IRQ 17
	Memory at d1300a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1300900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at d1300800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d1200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30fc
	Flags: bus master, fast devsel, latency 0, IRQ 30
	I/O ports at 2000 [size=256]
	Memory at d1100000 (64-bit, non-prefetchable) [size=4K]
	Memory at d1000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

This is the only thing that keeps me from having a perfect working environment using JACK, Ardour, Rosegarden and ZynAddSubFx :)

---

### Post by sgx on 2010-05-24
Hi, for now, untick Realtime in qjackctl, and reduce the priority
to 50. Restart the computer, start zyn, ardour and jackd/qjackctl
and record some songs in ardour. Make sure zyn and ardour are both at
48000, or both at 44100. Recording should work.

If not, Install timemachine  to record the zyn output.

Restart the computer, start qjackctl/jackd, zyn, and time machine,
connect them in qjackctl, press the record button in timemachine,
and play some tunes with zyn
They should be perfect. :)

Timemachine makes w64 wavefiles, like

tm-2009Ice-Castle.w64

audacity loads them by the
Files--> import audio    menu choice, to edit or convert to
mp3, ogg, wav etc.

Cheers

---

### Post by svenskmand on 2010-05-24
If I untick "Realtime" I cannot set the priority, and therefore I cannot set it to 50 as you say I should.

Also if I start Jack without "Realtime" ticked, and without starting anything else, I get XRUNS every 30 seconds, so I need the Realtime setting ticked.

Also Jack, Ardour, ZynAddSubFx and Hydrogen runs at the same rate, 44100 Hz, and I have also tried 48000 Hz, both cases gave skipping.

---

### Post by sgx on 2010-05-24
> **svenskmand said:**
> If I untick "Realtime" I cannot set the priority, and therefore I cannot set it to 50 as you say I should.

Also if I start Jack, without starting anything else, I get XRUNS every 30 seconds, so I need the Realtime setting ticked.

My mistake, you can adjust priority first, then untick. I never worry about xruns that are inaudible as long as you can get a basic recording done with zynaddsubfx, and ardour, or timemachine, that is free from odd pops, or audio dropouts. Then expand from a working beginning.

Do you have a webcam, wireless/bluetooth devices? 3D Desktop?
These sometimes cause audio glitches, also laptop Power management
is less than perfect, and can disturb pristine audio. Unused hardware can be shut off in the bios to solidify performance, and probably boost battery life a little. HP are noted for poor fan management, so be cautious with a hot laptop that gets hot.

the lspci output has two sound devices, this one:

Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] might be for high performance game co-processing.

If output of lsmod has something in it from this part of your hardware, then maybe that can be shut down too.

Cheers

---

### Post by svenskmand on 2010-05-24
> **sgx said:**
> My mistake, you can adjust priority first, then untick. I never worry about xruns that are inaudible as long as you can get a basic recording done with zynaddsubfx, and ardour, or timemachine, that is free from odd pops, or audio dropouts. Then expand from a working beginning.

Ok, but if I set a priority, and then untick Realtime, then it will not use the priority as far as I understand?
> **sgx said:**
> 
Do you have a webcam, wireless/bluetooth devices? 3D Desktop?

I can say yes to all. I have tried to disable the 3D Desktop before, but not with the setup I have now, where I do not get XRUNS, I will now try disabling the 3D desktop and the Bluetooth and see how it goes. I am also using wireless, but I need that to be on the internet and my webcam lights up when it is turned on, and I never have it turned on, so that should not interfere right?
> **sgx said:**
> 
These sometimes cause audio glitches, also laptop Power management
is less than perfect, and can disturb pristine audio. Unused hardware can be shut off in the bios to solidify performance, and probably boost battery life a little. HP are noted for poor fan management, so be cautious with a hot laptop that gets hot.

When I run Jack and all that I set both processors to performance, so they are always running at 2.1 GHz, doing this gives me better performance, and fan control appears to be working fine.
> **sgx said:**
> 
the lspci output has two sound devices, this one:

Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] might be for high performance game co-processing.

If output of lsmod has something in it from this part of your hardware, then maybe that can be shut down too.

Cheers
From lsmod I get this output (notice that I have turned off the Bluetooth here - I do not know if there is a noticeable difference)
```

Module                  Size  Used by
cryptd                  8120  0 
aes_x86_64              8976  3 
aes_generic            28464  1 aes_x86_64
binfmt_misc            10300  1 
ppdev                   8376  0 
bridge                 57008  0 
stp                     3028  1 bridge
bnep                   15632  2 
vboxnetadp              6528  0 
vboxnetflt             14832  0 
vboxdrv              1778028  2 vboxnetadp,vboxnetflt
snd_hda_codec_atihdmi     4432  1 
snd_hda_codec_idt      73472  1 
snd_hda_intel          31528  2 
snd_hda_codec          88048  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_pcm_oss            44992  0 
snd_mixer_oss          19728  1 snd_pcm_oss
snd_hwdep               9560  1 snd_hda_codec
snd_pcm                91896  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3540  0 
snd_seq_oss            33920  0 
snd_seq_midi            8448  0 
arc4                    2128  2 
snd_rawmidi            27232  1 snd_seq_midi
ecb                     3280  2 
snd_seq_midi_event      8656  2 snd_seq_oss,snd_seq_midi
snd_seq                61664  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27000  2 snd_pcm,snd_seq
ath5k                 136728  0 
snd_seq_device          8484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 13056  0 
uvcvideo               65340  0 
mac80211              212228  1 ath5k
hp_accel               12496  0 
psmouse                57460  0 
videodev               43712  1 uvcvideo
ath                    10288  1 ath5k
lis3lv02d               9328  1 hp_accel
snd                    79496  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
amd64_edac_mod         26944  0 
soundcore              10080  1 snd
sdhci_pci               9104  0 
v4l1_compat            17332  2 uvcvideo,videodev
jmb38x_ms              11188  0 
lp                     12740  0 
v4l2_compat_ioctl32    11792  1 videodev
snd_page_alloc         11072  2 snd_hda_intel,snd_pcm
btusb                  14596  0 
i2c_piix4              11936  0 
cfg80211              109752  3 ath5k,mac80211,ath
serio_raw               6772  0 
input_polldev           4864  1 lis3lv02d
sdhci                  20500  1 sdhci_pci
edac_core              49916  1 amd64_edac_mod
fglrx                2416408  39 
lirc_ene0100            9780  0 
memstick               12888  1 jmb38x_ms
video                  23436  0 
parport                41484  2 ppdev,lp
led_class               5272  3 ath5k,hp_accel,sdhci
output                  3792  1 video
lirc_dev               14440  1 lirc_ene0100
ohci1394               34500  0 
r8169                  38772  0 
mii                     6352  1 r8169
ieee1394              102048  1 ohci1394

```

Edit: I have just tried disabling Bluetooth, 3D desktop and wireless and I still have skips :S

---

### Post by svenskmand on 2010-05-24
Ok, I seem to have located the error. It is caused by ZynAddSubFx as far as I can see. In the first setup i used ZynAddSubFx as the synth which was played by Rosegarden. I have now swiched to using QSynth with the GM Soundfont played by Rosegarden, and now I have no skips, and still no XRUNS, so ZynAddSubFx must be where the error is.

If the error can be fixed by a tweak of ZynAddSubFx I do not know, but I hope it, else It might be an error in the code of ZynAddSubFx itself :S

I have attached a no-skip version using Qsynth as the synthesizer, you cannot hear any skips and if you inspect in Audacity you can also not see any skips, you could clearly see skips in the old sample I posted.

---

### Post by sgx on 2010-05-25
Can you record something with just zynaddsubfx, using timemachine or ardour or audacity to record? There should not be skips. It could be Rosegarden/zyn/qjackctl have a timing issue, was the bitrate equal? All 48000, or all 44100? 

Audacity lets you choose from alsa, jackd, or oss for recording,
but with jackd, audacity won't appear in qjackctl, until you start
recording, so press record, then press pause, then look in qjackctl, audacity will be there, but called 'portaudio', so connect zyn to that, and
press audacity pause button again, to resume recording.
Crazy times:) 

If audio issues persist, a textfile called blacklist can be
created in the folder  /etc/modprobe.d

putting these lines in it might help. 

snd_hda_codec_atihdmi
snd_hda_codec_idt
snd_hda_codec

snd_hda_intel is the motherboard soundchip kernel module. I think the
others are ritzy gaming helper graphics. If things ever go dark, you can load up the ubuntu livecd, and delete the blacklist file, or change edits
you kept notes on.

Cheers

---

### Post by svenskmand on 2010-06-11
> **sgx said:**
> Can you record something with just zynaddsubfx, using ... ardour ... to record? There should not be skips. ... was the bitrate equal? All 48000, or all 44100? 

Done, and all bitrates are 44100, I have attached a recording of two different instruments, both have clear skips in the waveform, but they are only very noticeable in the second recording. The latency I have in JACK is 5.8 ms but the skips are around 100 ms, so there is definitely something wrong. I did not get any XRUNS, but the cpu load peaked at 50 % in QJackCtl when playing the second instrument. I also tried to go completely crazy on the virtual keyboard in ZynAddSubFx and then I got XRUNS (they are not in the recorded file). So ZynAddSubFx is very cpu-intensive, but as I understand it I should not get skips at all unless I get XRUNS right? Or let me rephrase that I should at most get skips of 5.8 ms as this is the latency in QJackCtl, right?
> **sgx said:**
> 
Audacity lets you choose from alsa, jackd, or oss for recording,
but with jackd, audacity won't appear in qjackctl, until you start
recording, so press record, then press pause, then look in qjackctl, audacity will be there, but called 'portaudio', so connect zyn to that, and
press audacity pause button again, to resume recording.
Crazy times:)

Audacity did not show up in Jack, even though I pressed record, also I do not know how to tell Audacity to record from Jack :S, so I used Ardour
> **sgx said:**
> 
If audio issues persist, a textfile called blacklist can be
created in the folder  /etc/modprobe.d

I have all these files, which one should I choose?
```

$ less /etc/modprobe.d/blacklist
blacklist-ath_pci.conf      blacklist-modem.conf
blacklist.conf              blacklist-oss.conf
blacklist-firewire.conf     blacklist-watchdog.conf
blacklist-framebuffer.conf  

```
> **sgx said:**
> 
putting these lines in it might help. 

snd_hda_codec_atihdmi
snd_hda_codec_idt
snd_hda_codec

snd_hda_intel is the motherboard soundchip kernel module. I think the
others are ritzy gaming helper graphics. If things ever go dark, you can load up the ubuntu livecd, and delete the blacklist file, or change edits
you kept notes on.

Cheers

PS: Sorry for the late reply, but I have had some stuff to do.

---

### Post by AutoStatic on 2010-06-11
Try Yoshimi instead of ZynAddSubFX, it works way better with JACK.

[https://launchpad.net/%7Efalk-t-j/+archive/lucid/+sourcepub/1162932/+listing-archive-extra](https://launchpad.net/%7Efalk-t-j/+archive/lucid/+sourcepub/1162932/+listing-archive-extra)

---

### Post by Pablo_F on 2010-06-11
Hi!

svenksmand, you should try yoshimi [http://yoshimi.sourceforge.net/](http://yoshimi.sourceforge.net/)
It is a rewrite of zynaddsubfx that makes it much more jack-friendly. The instruments, effects and look are the same.

You can compile it of course but you can also get it from a PPA. Autostatic and Philip5 have it. Just add it/them to your package sources and install through synaptic or apt-get. 

EDIT: Sorry! Nooo, Auto has it for karmic, not for lucid, philip5 and falktx have it for lucid.  

yoshimi uses jack midi so you will need a2jmidid (with the -e option for hardware ports if you have a midi keyboard for example) so you can connect alsa seq ports like those of Rosegarden to yoshimi. 


> 
Timemachine makes w64 wavefiles

This the default but you can change it to standard wav. 
I have a launcher in the panel. Command is:

/usr/bin/timemachine -f wav -t 15

I use it to record the radio streams. After I hear something interesting, Push! Recorded!! Timemachine is great. I choose 15 seconds instead of the default 10 seconds.  I mean, you can also change this. See:

timemachine -h

Cheers! Pablo

---

### Post by svenskmand on 2010-06-12
Thanks for you advice about using Yoshimi, but do you have a link for a ppa? I would like to avoid doing "./configure; make; make install" if I can :)

So what should I but here at the end in the ????? part?
```

sudo add-apt-repository ppa:?????

```

Thanks :)

---

### Post by Pablo_F on 2010-06-12
see:

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

I would do:

sudo add-apt-repository ppa: philip5/extra (no space)
sudo apt-get update
sudo apt-get install yoshimi a2jmidid

Then maybe, disable the new repo (software origins) or maybe  update some other packages from this excellent PPA.

Cheers! Pablo

---

### Post by svenskmand on 2010-06-13
Ok, I get allot of XRUNS with Yoshimi with a buffer size of 128, but using 256 such that I have 11.6 ms of latency completely avoids XRUNS :), and there does also not appear to be skips :)

To do justice to ZynAddSubFX I have also tried that again with a buffer size of 256 so I also have 11.6 ms of latency, here I can also not force XRUNS anymore, but the skips still persist :(

So Yoshimi it is then :), by the way why is there no built in instruments as there is in ZynAddSubFX?

I have attached the two new recordings :) thanks for you help :)

But now I am wondering why does the Zyn-Team not fix these issues? I mean can you use ZynAddSubFX for anything if you do not use JACK?

---

### Post by svenskmand on 2010-06-13
I just realized that Yoshimi only shows up in the Audio and Midi tabs of QJACKCtl, but not the ALSA tab, so I cannot connect Rosegarden to Yoshimi :S It is the same with my MIDI keyboard it shows up in ALSA only, so I also cannot connect it to Yoshimi, what should I do?

---

### Post by Pablo_F on 2010-06-13
> I just realized that Yoshimi only shows up in the Audio and Midi tabs of QJACKCtl, but not the ALSA tab, so I cannot connect Rosegarden to Yoshimi :S It is the same with my MIDI keyboard it shows up in ALSA only, so I also cannot connect it to Yoshimi, what should I do?

ALT+F2, terminal, add a launcher, whatever.
Run
a2jmidid -e


> by the way why is there no built in instruments as there is in ZynAddSubFX?

It is possible that you have to copy or move the instruments in zyn to yoshimi. I am not sure if your yoshimi version have the instruments already.

I suggest:

$ sudo cp -av /usr/share/zynaddsubfx/* /usr/share/yoshimi/

Cheers! Pablo

---

### Post by svenskmand on 2010-06-13
Thank you :) a2jmidid works great :) I also got the instruments by looking in ZynAddSubFx for where its banks where and then I added them to Yoshimi :)

---

### Post by AutoStatic on 2010-06-13
Philip's PPA has an older version of Yoshimi that probably doesn't include any banks yet. Try the one from [FalkTX's PPA]("https://launchpad.net/~falk-t-j/+archive/lucid/"), that PPA has the latest and greatest ( 0.058 ).
And Yoshimi came to existence for the very flaws you ran into:
> Yoshimi is a software synthesizer for Linux based on the 2.4.0 release of ZynAddSubFX, written by Nasca Octavian Paul. Yoshimi delivers the same synth capabilities, along with very good Jack and Alsa midi/audio functionality.

I've been a ZynAddSubFX lover pretty much since it was first offered. Sadly though, Zyn has long been a case of flawed genius. It's audio and midi capabilities have not kept pace with the evolution and infrastructure improvements of Linux audio.

Performance with Jack was poor. Of recent years I've become more demanding in that respect, so I started looking at the code. I tried working with the official project team, but it proved impossible. We have vastly different and somewhat incompatible design, development and performance philosphies.

And so Yoshimi came to be, as a Linux only derivative of ZynAddSubFX. Yoshi attempts to do everything original Zyn does, but to do it well on Linux. A number of people have given time and energy to bring Yoshimi to life (and keep it that way!). My thanks go to you all.

---

### Post by svenskmand on 2010-06-13
Thanks for the info about the creation of Yoshimi. Another question though, is Yoshimi a complete fork of Zyn meaning that if there is some new novel features built into Zyn then they will not necessarily be made in Yoshimi? Or will Yoshimi be equivalent to Zyn but with proper JACK support?

---

### Post by AutoStatic on 2010-06-13
> **svenskmand said:**
> Another question though, is Yoshimi a complete fork of Zyn meaning that if there is some new novel features built into Zyn then they will not necessarily be made in Yoshimi? Or will Yoshimi be equivalent to Zyn but with proper JACK support?Afaik it's a complete fork based on ZASFX 2.4.0. I also think you don't need to worry about new features in ZASFX, it's already so complete, it just lacks solid JACK support. That's also why Yoshimi uses JACK Midi, and not the ALSA Midi backend.

---

### Post by AutoStatic on 2010-06-13
> **svenskmand said:**
> I have attached the two new recordings :)Cool sounds! Some nasty clipping though :(
Here's my latest thingy in which I used Yoshimi: [http://linux.autostatic.com/temp/theinfiniterepeat-unawareofadirection.ogv](http://linux.autostatic.com/temp/theinfiniterepeat-unawareofadirection.ogv) (approx. 25 Mb)

---

### Post by svenskmand on 2010-06-13
> **AutoStatic said:**
> Cool sounds! Some nasty clipping though :(

Thanks, I just move the mouse like crazy over the virtual keyboard in Yoshimi using a build in instrument. There is no [clipping]("http://en.wikipedia.org/wiki/Clipping_%28audio%29") :S, if you talk about the clicks you can hear in the ZyntoArdour.ogg file then they are caused by the skips I have been talking about in this thread.
> **AutoStatic said:**
> 
Here's my latest thingy in which I used Yoshimi: [http://linux.autostatic.com/temp/theinfiniterepeat-unawareofadirection.ogv](http://linux.autostatic.com/temp/theinfiniterepeat-unawareofadirection.ogv) (approx. 25 Mb)
That is a sweet piece :), if you will accept a comment then I think you should sing a bit stronger (more powerfull in volume), but very nice indeed :) Are you a professional musician?

Looks like some sweet programs, would you care to list them here maybe along with a one line description of what they do? I am on the lookout for programs to make music with on Linux :) and I know and use these programs:
JACK (of course :)!)
Ardour
Rosegarden
Yoshimi
Hydrogen
QSynth

Another thing, when you have as many programs open as you have, then do you have a trick for storing the JACK configuration of everything? I mean to play the song again you would have to open op all programs and load configuration files for each of them, and make the correct connections in JACK - hence allot of work :S

Thank you :)

---

### Post by AutoStatic on 2010-06-13
> **svenskmand said:**
> There is no [clipping]("http://en.wikipedia.org/wiki/Clipping_%28audio%29") :S, if you talk about the clicks you can hear in the ZyntoArdour.ogg file then they are caused by the skips I have been talking about in this thread.Ah, yeah, those were still Zyn recordings. My bad :oops:

> **svenskmand said:**
> That is a sweet piece :), if you will accept a comment then I think you should sing a bit stronger (more powerfull in volume), but very nice indeed :)Thanks! And you're right about the vocals, but I recorded them in like a few minutes and I can't sing out loud because our newborn was sleeping ;)

> **svenskmand said:**
> Are you a professional musician?Wish I was. No, semi-professional. But I've been making music for like 20 years, released several albums, played live a lot.

> **svenskmand said:**
> Looks like some sweet programs, would you care to list them here maybe along with a one line description of what they do?Sure!

Hydrogen: used as a sequencer. Every pattern is triggered live in the vid. All vocals, bass and melodica lines are samples I recorded in Qtractor and then imported in Hydrogen. All softsynths are triggered from Hydrogen too.
Qtractor: used as the mixer and JACK transport app. Qtractor's mixer is MIDI operable and Qtractor also accepts MMC messages. And Qtractor allows to create separate buses for each instrument/sample/track.
PHASEX: two instances of PHASEX, one for extra bass (harsh-saw patch) and one for the melody (electro-lead).
Yoshimi: Pizzicato Strings instrument.
Rakarrack: reverb for the Melodica. I could use a LADSPA plugin but since I use the same reverb in Yoshimi it just matches better.
Guitarix: two instances for the bass samples.

> **svenskmand said:**
> Another thing, when you have as many programs open as you have, then do you have a trick for storing the JACK configuration of everything? I mean to play the song again you would have to open op all programs and load configuration files for each of them, and make the correct connections in JACK - hence allot of work :SI use Qtractor for this, it also stores any connection made to it in the project file. So it doesn't store all connections, I make those manually. I could use a session manager like[ Ladish]("http://ladish.org/") but I'm still on Karmic with JACK1 so that's not really an option at the moment.
So when I want to work on songs I do have to start all the apps up first and then load the Qtractor project file to make the connections. Any connections outside of Qtractor have to be made manually. A bit time consuming and error prone (who didn't get that nasty feedback loop yet when working with JACK ;) ) but I've learned to work with it.

---

### Post by svenskmand on 2010-06-14
> **AutoStatic said:**
> Ah, yeah, those were still Zyn recordings. My bad :oops:

Thanks! And you're right about the vocals, but I recorded them in like a few minutes and I can't sing out loud because our newborn was sleeping ;)
[QUOTE=AutoStatic;9456341]
Heh my first thought was that you where recording in an apartment and where afraid that you would wake the neighbors :)

Wish I was. No, semi-professional. But I've been making music for like 20 years, released several albums, played live a lot.
> **AutoStatic said:**
> 
Ok, by the way do you have [perfect pitch]("http://en.wikipedia.org/wiki/Absolute_pitch") or [relative pitch]("http://en.wikipedia.org/wiki/Relative_pitch") and do you know of any program to train it?

Sure!

Hydrogen: used as a sequencer. Every pattern is triggered live in the vid. All vocals, bass and melodica lines are samples I recorded in Qtractor and then imported in Hydrogen. All softsynths are triggered from Hydrogen too.
Qtractor: used as the mixer and JACK transport app. Qtractor's mixer is MIDI operable and Qtractor also accepts MMC messages. And Qtractor allows to create separate buses for each instrument/sample/track.
PHASEX: two instances of PHASEX, one for extra bass (harsh-saw patch) and one for the melody (electro-lead).
Yoshimi: Pizzicato Strings instrument.
Rakarrack: reverb for the Melodica. I could use a LADSPA plugin but since I use the same reverb in Yoshimi it just matches better.
Guitarix: two instances for the bass samples.

> **AutoStatic said:**
> 
I use Qtractor for this, it also stores any connection made to it in the project file. So it doesn't store all connections, I make those manually. I could use a session manager like[ Ladish]("http://ladish.org/") but I'm still on Karmic with JACK1 so that's not really an option at the moment.
So when I want to work on songs I do have to start all the apps up first and then load the Qtractor project file to make the connections. Any connections outside of Qtractor have to be made manually. A bit time consuming and error prone (who didn't get that nasty feedback loop yet when working with JACK ;) ) but I've learned to work with it.
Why can you not use JACK2 and what is the difference? - that is why do the JACK-team have two different versions?

---

### Post by AutoStatic on 2010-06-14
> **svenskmand said:**
> Ok, by the way do you have perfect pitch or relative pitch and do you know of any program to train it?Relative pitch, close to no pitch at all, I'm horrible at musical theory (can't read notes). But I can tell in which key a song is, and what kind of scale. Learned this through experience and if you don't have any relative pitch you can't play in a band. Don't know about any program to train it. The best training imho would be to play with others.

> **svenskmand said:**
> Why can you not use JACK2 and what is the difference? - that is why do the JACK-team have two different versions?I'm happy with JACK1, it's stable as a rock and practically without bugs. Maybe I should try JACK2 but it's under development and I don't like my main tool/libs/sound-daemon to be experimental. My home studio machine has to be rock solid and not some kind of testing ground.
And about the different versions: [http://ubuntuforums.org/showthread.php?t=1483525](http://ubuntuforums.org/showthread.php?t=1483525)

So another reason for me to stick would be the JACK transport issue. I use JACK transport a lot.

---

### Post by cchhrriiss121212 on 2010-06-14
> *Ok, by the way do you have perfect pitch or relative pitch and do you know of any program to train it?*
                                 Relative pitch, close to no pitch at all, I'm horrible at musical theory (can't read notes). But I can tell in which key a song is, and what kind of scale. Learned this through experience and if you don't have any relative pitch you can't play in a band. Don't know about any program to train it. The best training imho would be to play with others.
+1 to this, but you can also learn pitch techniques by yourself by using another instrument. Just play a major scale and try to match each note with your voice, then try it the other way around. Try to pick up on the most powerful intervals first like 3rds and 5ths (ie play a C and sing or hum a E or G respectively) and you will soon develop good pitch awareness.

---

### Post by svenskmand on 2010-06-14
Regarding the relative pitch program then I found a program called [RPitch]("http://rpitch.sourceforge.net/"), but I do not understand the labels of the notes :S, I just wanted a program that could connect through JACK to my MIDI keyboard, such that the program can play a random tone on my keyboard, and then I should press the right one or the corresponding note in another octave.

---

### Post by Pablo_F on 2010-06-14
>  Originally Posted by svenskmand  View Post
Ok, by the way do you have perfect pitch or relative pitch and do you know of any program to train it?

Take a look at [GNU Solfege]("http://www.solfege.org"). You can just apt-get install it. It will install timidity as a dependency but you don't have to use it if you prefer to have the sound through jack - qsynth. See:
[http://www.solfege.org/Solfege/SoundSetup](http://www.solfege.org/Solfege/SoundSetup) (4.3)

> So another reason for me to stick would be the JACK transport issue
I don't want to spread FUD about this! This issue affects the jack2 + ardour combination when you have tempo changes in ardour and you want to drive hydrogen. Then you put ardour as the jack transport master and hydrogen follows the tempo changes. With jack2 you can't move the playhead as you like. You have to disable master, move, and enable again, which is  PITA. 
I haven't tested with qtractor / hydrogen. 

> All softsynths are triggered from Hydrogen too.

Auto, if I understand you correctly, you can use hydrogen as a sequencer and use an external synth or a virtual instrument with a MIDI IN port? How do you achive this? I can only get sounds from drumkits. 


> I just move the mouse like crazy over the virtual keyboard in Yoshimi using a build in instrument.

svenskmand, if you don't have a rmpk (real midi piano keyboard) I suggest you try vmpk. You can load keymaps. I know it is ridiculous but I learned to play Toccata and Fugue in D minor with the keyboard. With the mouse is much more difficult.

The desktop integration is being worked on. Patience is a virtue. 
For the time being, once you find a combination you like, you can do "session scripting". See:
[http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)

Auto: nice song!

Pablo

---

### Post by svenskmand on 2010-06-14
> **Pablo_F said:**
> Take a look at [GNU Solfege]("http://www.solfege.org"). You can just apt-get install it. It will install timidity as a dependency but you don't have to use it if you prefer to have the sound through jack - qsynth. See:
[http://www.solfege.org/Solfege/SoundSetup](http://www.solfege.org/Solfege/SoundSetup) (4.3)
It seems to be able to do what I want, although I cannot seem to find it. So what I want is: Solfege plays a tone, say D4, and then I should press the key on the piano corresponding to D4 or the same not but in another octave, say D5, in either case Solfege would say that the key I pressed is correct. Is this possible?

Thanks :)

Edit: I almost found what I was looking for, under "Misc - Identify Tone" I can do almost what I want, I do not have all piano keys to choose from, but only the 12 keys of one octave, but it is ok for now :)

---

### Post by sgx on 2010-06-14
> **Pablo_F said:**
> 

snip
I don't want to spread FUD about this!
snip

 

Linux FUD =

free
uninhibited
discourse

The windows definition is a little different :)

---

### Post by AutoStatic on 2010-06-15
> **Pablo_F said:**
> I don't want to spread FUD about this! This issue affects the jack2 + ardour combination when you have tempo changes in ardour and you want to drive hydrogen. Then you put ardour as the jack transport master and hydrogen follows the tempo changes. With jack2 you can't move the playhead as you like. You have to disable master, move, and enable again, which is  PITA. 
I haven't tested with qtractor / hydrogen.You're right Pablo. As long as I haven't tried JACK2 myself I can't say anything sensible about it.

> **Pablo_F said:**
> Auto, if I understand you correctly, you can use hydrogen as a sequencer and use an external synth or a virtual instrument with a MIDI IN port? How do you achive this? I can only get sounds from drumkits.[LIST]
[*]Create/Modify an instrument
[*]Import a long empty wave file as a layer
[*]Set a dedicated MIDI channel
[*]Insert your notes in the Pattern Editor
[*]Connect your softsynth to the MIDI out of Hydrogen
[*]Set the MIDI channel to the one of your Hydrogen instrument
[*]Let it roll!
[/LIST]

> **Pablo_F said:**
> The desktop integration is being worked on. Patience is a virtue. 
For the time being, once you find a combination you like, you can do "session scripting". See:
[http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)Did you try the session scripting? He also released it as a Bash script afaik in the meanwhile.

> **Pablo_F said:**
> Auto: nice song!Thanks! It does need a lot of improvement (a chorus, better balanced instruments and the necessary effects) but for a raw demo it's pretty ok I guess.

---

### Post by philip5 on 2010-06-15
FYI
I'll update Yoshimi to 0.058 on my PPA for karmic and Lucid when I get home from work this evening. There should be banks in my packages as they are now to but maybe not as updated. I'll look into this later...

/P

[edit]

Done. :)

---

### Post by AutoStatic on 2010-06-15
For the impatient: [http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/y/yoshimi/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/y/yoshimi/)

Lucid only at the moment.

---

### Post by Pablo_F on 2010-06-16
> Did you try the session scripting? He also released it as a Bash script afaik in the meanwhile.

For the time being, I do very simple session scripting but it allows me to launch several programs with one klick by adding custom launchers in a gnome panel with the command: bash /usr/local/sbin/script.bash.

Generic example:
sudo gedit /usr/local/sbin/script.bash

#!bin/bash
programA &
sleep 3
programB &
sleep 3
programC &
sleep 3
patchage

Examples:

This one one launchs qjacktl, ardour and hydrogen. I have qjackctl with the option "start jack server at qjackctl start" in the "others" tab. After opening the session in ardour, all is ready to go as I left it previously. 

/usr/local/sbin$ cat hydrogen-ardour.bash 
#!bin/bash
qjackctl &
sleep 3
hydrogen &
sleep 3
ardour2

This is another example:

/usr/local/sbin$ cat rakarrack-guitarix.bash 
#!bin/bash
qjackctl &
sleep 3
rakarrack &
sleep 3
guitarix &
sleep 3
patchage 

I have to make some connections manually but a recent version of patchage (like the one you can find in ppa: philip5/extra for karmic and lucid) is much faster and nicer than qjackctl's connection window. 

More complicated scripts are worth in some situations but for me, this is enough for the moment. Once you find a combinations of programs to work with, these scripts come very handy until we have a solid, universal and ready-to-go linux audio session integration app. 

Regards, Pablo




 Linux FUD = FUn Do it yourself :D

---

### Post by nairatinu on 2011-08-07
Hey thanks you guys.  That problem had been driving me crazy!  Had to set the midi driver in Jack to "seq" for it to see my Yamahaha keyboard, but now all seems well.

---

### Post by slavinzing56 on 2011-08-08
Thanks! And you're right about the vocals, but I recorded them in like a  few minutes and I can't sing out loud because our newborn was sleeping :wink:

---

