---
title: "Problem with using wired headset"
date: 2020-08-29
forum: Ubuntu/Debian BASED
---

### Post by Amir_Hossein on 2020-08-29
Hi, I have a TSCO wired headset, But Debian will not recognize it.
I have tried many solutions provided in forums and blogs, But they do not work for my problem.
I appreciate it if someone can help me.

The headset has two 3.5mm jack for speaker and microphone.
The manufacturer is not international, But I tested it via Windows 10 with this PC and it works without any problem.

The information I have seen ask from OP in other forums which may need to debug my problem:

```
amir@debian:~$ lspci -vvvv | grep -A 10 -i audio; amixer; aplay -l; lsmod | grep -i snd
07:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio Controller
    Subsystem: ASUSTeK Computer Inc. Raven/Raven2/Fenghuang HDMI/DP Audio Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 64
    Region 0: Memory at fcc88000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

07:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
--
07:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
    Subsystem: ASUSTeK Computer Inc. Family 17h (Models 10h-1fh) HD Audio Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 65
    Region 0: Memory at fcc80000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

08:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61) (prog-if 01 [AHCI 1.0])
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
snd_usb_audio         311296  0
snd_usbmidi_lib        40960  1 snd_usb_audio
snd_rawmidi            45056  1 snd_usbmidi_lib
snd_seq_device         16384  1 snd_rawmidi
mc                     57344  1 snd_usb_audio
snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    98304  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_codec_hdmi     73728  1
snd_hda_intel          57344  6
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         163840  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core          106496  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
snd_pcm               131072  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
snd_timer              45056  1 snd_pcm
snd                   106496  24 snd_hda_codec_generic,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
usbcore               315392  5 xhci_hcd,snd_usb_audio,usbhid,snd_usbmidi_lib,xhci_pci



```

OS info:
```
amir@debian:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Debian
Description:    Debian GNU/Linux 10 (buster)
Release:    10
Codename:    buster
amir@debian:~$ uname -r
5.7.0-0.bpo.2-amd64

```

---

### Post by yapidumoac on 2020-08-31
Could you provide the specific make and model of this &#8220;wired headset&#8221;?

---

