---
title: "2019 HP Omen 15t: digital microphone not working"
date: 2021-01-18
forum: Ubuntu/Debian BASED
---

### Post by Welly Wu on 2021-01-18
[COLOR=#000000][FONT=&amp]I own a late 2019 Computer Upgrade King Hewlett Packard Omen 15t gaming notebook PC and I have Microsoft Windows 10 64-bit Pro edition version 20H2 installed on my primary ADATA SX8100NP M.2 2 TB PCI-e NVMe x4 solid-state disk. It just works fine.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]I also have Feren OS 2021.1 64-bit GNU/Linux installed on my secondary Kingston A400 SATA-III 6 GB/s 1.92 TB solid-state disk. It mostly works, but my digital microphone array or my built-in laptop microphone is detected as a Cannon Lake PCH cAVS multichannel input and it can not detect any audio. I want to be able to get my built-in digital microphone array to work so I can use Facebook video calling with a few friends of mine. Just to be clear, my built-in 720P web camera works, but other people can not hear me via Facebook video calling or telephone calling features.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]I know that this is the Linux Mint Forums, but I have been doing research over the past few days and it seems that MrEen is a moderator here and he has had some experience in helping other people with the HP Omen 17 gaming notebook PC to fix the microphone issues.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]How can I get you more technical information about my sound cards to be of greater help in troubleshooting this technical issue? It has been a while since I last used any GNU/Linux distribution in terms of troubleshooting this digital microphone array to get it to work especially on an Ubuntu-based distribution. Previously, I was using Red Hat Fedora Workstation 33 64-bit GNU/Linux and almost everything just worked including the digital microphone array, but I prefer using an Ubuntu-based GNU/Linux distribution as I find that it has more available software packages, libraries, and dependencies and some of my third-party, cross-platform, closed-source, commercial, and proprietary software products work better than on Red Hat-based GNU/Linux distributions. If I am correct, then Feren OS 2021.1 64-bit should be based on Ubuntu 20.10 64-bit GNU/Linux.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]All I need to fix is my built-in digital microphone array. My internal laptop speakers do work and plugging in my Logitech laptop speakers into the 3.5 mm headphone jack also works so I can hear audio and play music. My built-in digital microphone array does not work and that is all that I want to fix so I can use Facebook video and telephone calling features with friends. Thank you.
[/FONT][/COLOR]
```
[FONT=monospace][COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$ inxi -Fxz[/COLOR]
[COLOR=#1818B2]**System:    Kernel:**[/COLOR][COLOR=#000000] 5.8.0-38-generic x86_64 [/COLOR][COLOR=#1818B2]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#1818B2]**compiler:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#1818B2]**Desktop:**[/COLOR][COLOR=#000000] KDE Plasma 5.20.4  [/COLOR]
           [COLOR=#1818B2]**Distro:**[/COLOR][COLOR=#000000] Feren OS 20.04 2021.01  [/COLOR]
[COLOR=#1818B2]**Machine:   Type:**[/COLOR][COLOR=#000000] Laptop [/COLOR][COLOR=#1818B2]**System:**[/COLOR][COLOR=#000000] HP [/COLOR][COLOR=#1818B2]**product:**[/COLOR][COLOR=#000000] OMEN by HP Laptop 15-dh0xxx [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#1818B2]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#1818B2]**Mobo:**[/COLOR][COLOR=#000000] HP [/COLOR][COLOR=#1818B2]**model:**[/COLOR][COLOR=#000000] 8600 [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] 44.48 [/COLOR][COLOR=#1818B2]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#1818B2]**UEFI:**[/COLOR][COLOR=#000000] AMI [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] F.35 [/COLOR][COLOR=#1818B2]**date:**[/COLOR][COLOR=#000000] 11/04/2020  [/COLOR]
[COLOR=#1818B2]**Battery:   ID-1:**[/COLOR][COLOR=#000000] BAT1 [/COLOR][COLOR=#1818B2]**charge:**[/COLOR][COLOR=#000000] 64.0 Wh [/COLOR][COLOR=#1818B2]**condition:**[/COLOR][COLOR=#000000] 64.0/69.0 Wh (93%) [/COLOR][COLOR=#1818B2]**model:**[/COLOR][COLOR=#000000] COMPAL PABAS0241231  [/COLOR]
           [COLOR=#1818B2]**status:**[/COLOR][COLOR=#000000] Full  [/COLOR]
[COLOR=#1818B2]**CPU:       Topology:**[/COLOR][COLOR=#000000] 8-Core [/COLOR][COLOR=#1818B2]**model:**[/COLOR][COLOR=#000000] Intel Core i9-9880H [/COLOR][COLOR=#1818B2]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#1818B2]**type:**[/COLOR][COLOR=#000000] MT MCP [/COLOR][COLOR=#1818B2]**arch:**[/COLOR][COLOR=#000000] Kaby Lake [/COLOR][COLOR=#1818B2]**rev:**[/COLOR][COLOR=#000000] D  [/COLOR]
           [COLOR=#1818B2]**L2 cache:**[/COLOR][COLOR=#000000] 16.0 MiB  [/COLOR]
           [COLOR=#1818B2]**flags:**[/COLOR][COLOR=#000000] avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx [/COLOR][COLOR=#1818B2]**bogomips:**[/COLOR][COLOR=#000000] 73598  [/COLOR]
           [COLOR=#1818B2]**Speed:**[/COLOR][COLOR=#000000] 800 MHz [/COLOR][COLOR=#1818B2]**min/max:**[/COLOR][COLOR=#000000] 800/4800 MHz [/COLOR][COLOR=#1818B2]**Core speeds (MHz):**[/COLOR][COLOR=#1818B2]**1:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**2:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**3:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**4:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**5:**[/COLOR][COLOR=#000000] 800  [/COLOR]
           [COLOR=#1818B2]**6:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**7:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**8:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**9:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**10:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**11:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**12:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**13:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**14:**[/COLOR][COLOR=#000000] 800 [/COLOR][COLOR=#1818B2]**15:**[/COLOR][COLOR=#000000] 801 [/COLOR][COLOR=#1818B2]**16:**[/COLOR][COLOR=#000000] 801  [/COLOR]
[COLOR=#1818B2]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] NVIDIA TU104BM [GeForce RTX 2080 Mobile] [/COLOR][COLOR=#1818B2]**vendor:**[/COLOR][COLOR=#000000] Hewlett-Packard [/COLOR][COLOR=#1818B2]**driver:**[/COLOR][COLOR=#000000] nvidia  [/COLOR]
           [COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] 460.32.03 [/COLOR][COLOR=#1818B2]**bus ID:**[/COLOR][COLOR=#000000] 01:00.0  [/COLOR]
           [COLOR=#1818B2]**Display:**[/COLOR][COLOR=#000000] x11 [/COLOR][COLOR=#1818B2]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.9 [/COLOR][COLOR=#1818B2]**driver:**[/COLOR][COLOR=#000000] nvidia [/COLOR][COLOR=#1818B2]**unloaded:**[/COLOR][COLOR=#000000] modesetting  [/COLOR]
           [COLOR=#1818B2]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~240Hz  [/COLOR]
           [COLOR=#1818B2]**OpenGL:**[/COLOR][COLOR=#1818B2]**renderer:**[/COLOR][COLOR=#000000] GeForce RTX 2080 with Max-Q Design/PCIe/SSE2 [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] 4.6.0 NVIDIA 460.32.03  [/COLOR]
           [COLOR=#1818B2]**direct render:**[/COLOR][COLOR=#000000] Yes  [/COLOR]
[COLOR=#1818B2]**Audio:     Device-1:**[/COLOR][COLOR=#000000] Intel Cannon Lake PCH cAVS [/COLOR][COLOR=#1818B2]**vendor:**[/COLOR][COLOR=#000000] Hewlett-Packard [/COLOR][COLOR=#1818B2]**driver:**[/COLOR][COLOR=#000000] sof-audio-pci  [/COLOR]
           [COLOR=#1818B2]**bus ID:**[/COLOR][COLOR=#000000] 00:1f.3  [/COLOR]
           [COLOR=#1818B2]**Device-2:**[/COLOR][COLOR=#000000] NVIDIA TU104 HD Audio [/COLOR][COLOR=#1818B2]**vendor:**[/COLOR][COLOR=#000000] Hewlett-Packard [/COLOR][COLOR=#1818B2]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#1818B2]**bus ID:**[/COLOR][COLOR=#000000] 01:00.1  [/COLOR]
           [COLOR=#1818B2]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] k5.8.0-38-generic  [/COLOR]
[COLOR=#1818B2]**Network:   Device-1:**[/COLOR][COLOR=#000000] Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet [/COLOR][COLOR=#1818B2]**vendor:**[/COLOR][COLOR=#000000] Hewlett-Packard  [/COLOR]
           [COLOR=#1818B2]**driver:**[/COLOR][COLOR=#000000] r8169 [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#1818B2]**port:**[/COLOR][COLOR=#000000] 4000 [/COLOR][COLOR=#1818B2]**bus ID:**[/COLOR][COLOR=#000000] 3c:00.0  [/COLOR]
           [COLOR=#1818B2]**IF:**[/COLOR][COLOR=#000000] enp60s0 [/COLOR][COLOR=#1818B2]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#1818B2]**speed:**[/COLOR][COLOR=#000000] 1000 Mbps [/COLOR][COLOR=#1818B2]**duplex:**[/COLOR][COLOR=#000000] full [/COLOR][COLOR=#1818B2]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#1818B2]**Device-2:**[/COLOR][COLOR=#000000] Realtek RTL8822BE 802.11a/b/g/n/ac WiFi adapter [/COLOR][COLOR=#1818B2]**vendor:**[/COLOR][COLOR=#000000] Hewlett-Packard  [/COLOR]
           [COLOR=#1818B2]**driver:**[/COLOR][COLOR=#000000] rtw_8822be [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#1818B2]**port:**[/COLOR][COLOR=#000000] 3000 [/COLOR][COLOR=#1818B2]**bus ID:**[/COLOR][COLOR=#000000] 3e:00.0  [/COLOR]
           [COLOR=#1818B2]**IF:**[/COLOR][COLOR=#000000] wlo1 [/COLOR][COLOR=#1818B2]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#1818B2]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
[COLOR=#1818B2]**Drives:    Local Storage:**[/COLOR][COLOR=#1818B2]**total:**[/COLOR][COLOR=#000000] 3.90 TiB [/COLOR][COLOR=#1818B2]**used:**[/COLOR][COLOR=#000000] 203.55 GiB (5.1%)  [/COLOR]
           [COLOR=#1818B2]**ID-1:**[/COLOR][COLOR=#000000] /dev/mmcblk0 [/COLOR][COLOR=#1818B2]**model:**[/COLOR][COLOR=#000000] SC200 [/COLOR][COLOR=#1818B2]**size:**[/COLOR][COLOR=#000000] 183.35 GiB  [/COLOR]
           [COLOR=#1818B2]**ID-2:**[/COLOR][COLOR=#000000] /dev/nvme0n1 [/COLOR][COLOR=#1818B2]**vendor:**[/COLOR][COLOR=#000000] A-Data [/COLOR][COLOR=#1818B2]**model:**[/COLOR][COLOR=#000000] SX8100NP [/COLOR][COLOR=#1818B2]**size:**[/COLOR][COLOR=#000000] 1.86 TiB  [/COLOR]
           [COLOR=#1818B2]**ID-3:**[/COLOR][COLOR=#000000] /dev/sda [/COLOR][COLOR=#1818B2]**vendor:**[/COLOR][COLOR=#000000] Kingston [/COLOR][COLOR=#1818B2]**model:**[/COLOR][COLOR=#000000] SA400S371920G [/COLOR][COLOR=#1818B2]**size:**[/COLOR][COLOR=#000000] 1.75 TiB  [/COLOR]
           [COLOR=#1818B2]**ID-4:**[/COLOR][COLOR=#000000] /dev/sdb [/COLOR][COLOR=#1818B2]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#1818B2]**vendor:**[/COLOR][COLOR=#000000] SanDisk [/COLOR][COLOR=#1818B2]**model:**[/COLOR][COLOR=#000000] Ultra USB 3.0 [/COLOR][COLOR=#1818B2]**size:**[/COLOR][COLOR=#000000] 115.69 GiB  [/COLOR]
[COLOR=#1818B2]**RAID:      Hardware-1:**[/COLOR][COLOR=#000000] Intel 82801 Mobile SATA Controller [RAID mode] [/COLOR][COLOR=#1818B2]**driver:**[/COLOR][COLOR=#000000] ahci [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] 3.0 [/COLOR][COLOR=#1818B2]**bus ID:**[/COLOR][COLOR=#000000] 00:17.0  [/COLOR]
[COLOR=#1818B2]**Partition: ID-1:**[/COLOR][COLOR=#000000] / [/COLOR][COLOR=#1818B2]**size:**[/COLOR][COLOR=#000000] 1.65 TiB [/COLOR][COLOR=#1818B2]**used:**[/COLOR][COLOR=#000000] 179.83 GiB (10.6%) [/COLOR][COLOR=#1818B2]**fs:**[/COLOR][COLOR=#000000] ext4 [/COLOR][COLOR=#1818B2]**dev:**[/COLOR][COLOR=#000000] /dev/sda2  [/COLOR]
           [COLOR=#1818B2]**ID-2:**[/COLOR][COLOR=#000000] swap-1 [/COLOR][COLOR=#1818B2]**size:**[/COLOR][COLOR=#000000] 68.96 GiB [/COLOR][COLOR=#1818B2]**used:**[/COLOR][COLOR=#000000] 0 KiB (0.0%) [/COLOR][COLOR=#1818B2]**fs:**[/COLOR][COLOR=#000000] swap [/COLOR][COLOR=#1818B2]**dev:**[/COLOR][COLOR=#000000] /dev/sda3  [/COLOR]
[COLOR=#1818B2]**Sensors:   System Temperatures:**[/COLOR][COLOR=#1818B2]**cpu:**[/COLOR][COLOR=#000000] 54.0 C [/COLOR][COLOR=#1818B2]**mobo:**[/COLOR][COLOR=#000000] 10.0 C [/COLOR][COLOR=#1818B2]**gpu:**[/COLOR][COLOR=#000000] nvidia [/COLOR][COLOR=#1818B2]**temp:**[/COLOR][COLOR=#000000] 47 C  [/COLOR]
           [COLOR=#1818B2]**Fan Speeds (RPM):**[/COLOR][COLOR=#000000] N/A  [/COLOR]
[COLOR=#1818B2]**Info:      Processes:**[/COLOR][COLOR=#000000] 400 [/COLOR][COLOR=#1818B2]**Uptime:**[/COLOR][COLOR=#000000] 1m [/COLOR][COLOR=#1818B2]**Memory:**[/COLOR][COLOR=#000000] 62.69 GiB [/COLOR][COLOR=#1818B2]**used:**[/COLOR][COLOR=#000000] 3.41 GiB (5.4%) [/COLOR][COLOR=#1818B2]**Init:**[/COLOR][COLOR=#000000] systemd [/COLOR][COLOR=#1818B2]**runlevel:**[/COLOR][COLOR=#000000] 5  [/COLOR]
           [COLOR=#1818B2]**Compilers:**[/COLOR][COLOR=#1818B2]**gcc:**[/COLOR][COLOR=#000000] 9.3.0 [/COLOR][COLOR=#1818B2]**Shell:**[/COLOR][COLOR=#000000] bash [/COLOR][COLOR=#1818B2]**v:**[/COLOR][COLOR=#000000] 5.0.17 [/COLOR][COLOR=#1818B2]**inxi:**[/COLOR][COLOR=#000000] 3.0.38  [/COLOR]
[COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$[/COLOR]
[/FONT]
```

```
[FONT=monospace][COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$ aplay -l[/COLOR]
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sofhdadsp [sof-hda-dsp], device 0: HDA Analog (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sofhdadsp [sof-hda-dsp], device 1: HDA Digital (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sofhdadsp [sof-hda-dsp], device 3: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sofhdadsp [sof-hda-dsp], device 4: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sofhdadsp [sof-hda-dsp], device 5: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/FONT]
```[FONT=monospace]
```
[COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$ arecord -l[/COLOR]
**** List of CAPTURE Hardware Devices ****
card 1: sofhdadsp [sof-hda-dsp], device 0: HDA Analog (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sofhdadsp [sof-hda-dsp], device 1: HDA Digital (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sofhdadsp [sof-hda-dsp], device 6: DMIC (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: sofhdadsp [sof-hda-dsp], device 7: DMIC16kHz (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$[/COLOR]

```[/FONT]

[FONT=monospace][COLOR=#18B218]**```
wellywu@FerenOS
```**[/COLOR]```
[COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$ arecord -L[/COLOR]
default
    Playback/recording through the PulseAudio sound server
surround21
    2.1 Surround output to Front and Subwoofer speakers
surround40
    4.0 Surround output to Front and Rear speakers
surround41
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50
    5.0 Surround output to Front, Center and Rear speakers
surround51
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
samplerate
    Rate Converter Plugin Using Samplerate Library
speexrate
    Rate Converter Plugin Using Speex Resampler
jack
    JACK Audio Connection Kit
oss
    Open Sound System
pulse
    PulseAudio Sound Server
upmix
    Plugin for channel upmix (4,6,8)
vdownmix
    Plugin for channel downmix (stereo) with a simple spacialization
usbstream:CARD=NVidia
    HDA NVidia
    USB Stream Output
sysdefault:CARD=sofhdadsp
    sof-hda-dsp,  
    Default Audio Device
dmix:CARD=sofhdadsp,DEV=0
    sof-hda-dsp,  
    Direct sample mixing device
dmix:CARD=sofhdadsp,DEV=1
    sof-hda-dsp,  
    Direct sample mixing device
dmix:CARD=sofhdadsp,DEV=6
    sof-hda-dsp,  
    Direct sample mixing device
dmix:CARD=sofhdadsp,DEV=7
    sof-hda-dsp,  
    Direct sample mixing device
dsnoop:CARD=sofhdadsp,DEV=0
    sof-hda-dsp,  
    Direct sample snooping device
dsnoop:CARD=sofhdadsp,DEV=1
    sof-hda-dsp,  
    Direct sample snooping device
dsnoop:CARD=sofhdadsp,DEV=6
    sof-hda-dsp,  
    Direct sample snooping device
dsnoop:CARD=sofhdadsp,DEV=7
    sof-hda-dsp,  
    Direct sample snooping device
hw:CARD=sofhdadsp,DEV=0
    sof-hda-dsp,  
    Direct hardware device without any conversions
hw:CARD=sofhdadsp,DEV=1
    sof-hda-dsp,  
    Direct hardware device without any conversions
hw:CARD=sofhdadsp,DEV=6
    sof-hda-dsp,  
    Direct hardware device without any conversions
hw:CARD=sofhdadsp,DEV=7
    sof-hda-dsp,  
    Direct hardware device without any conversions
plughw:CARD=sofhdadsp,DEV=0
    sof-hda-dsp,  
    Hardware device with all software conversions
plughw:CARD=sofhdadsp,DEV=1
    sof-hda-dsp,  
    Hardware device with all software conversions
plughw:CARD=sofhdadsp,DEV=6
    sof-hda-dsp,  
    Hardware device with all software conversions
plughw:CARD=sofhdadsp,DEV=7
    sof-hda-dsp,  
    Hardware device with all software conversions
usbstream:CARD=sofhdadsp
    sof-hda-dsp
    USB Stream Output
[COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$[/COLOR]

```[/FONT]

```
[FONT=monospace][COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$ apt-cache policy alsa[/COLOR]
alsa:
  Installed: (none)
  Candidate: (none)
  Version table:
[COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$ apt-cache policy pulseaudio[/COLOR]
pulseaudio:
  Installed: 1:13.99.1-1ubuntu3.8
  Candidate: 1:13.99.1-1ubuntu3.8
  Version table:
 *** 1:13.99.1-1ubuntu3.8 500
        500 http://la-mirrors.evowise.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:13.99.1-1ubuntu3 500
        500 http://la-mirrors.evowise.com/ubuntu focal/main amd64 Packages
[COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$ uname -r[/COLOR]
5.8.0-38-generic
[COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$ apt-cache policy alsa-ucm-conf[/COLOR]
alsa-ucm-conf:
  Installed: (none)
  Candidate: 1.2.2-1ubuntu0.5
  Version table:
     1.2.2-1ubuntu0.5 500
        500 http://la-mirrors.evowise.com/ubuntu focal-updates/main amd64 Packages
        500 http://la-mirrors.evowise.com/ubuntu focal-updates/main i386 Packages
     1.2.2-1 500
        500 http://la-mirrors.evowise.com/ubuntu focal/main amd64 Packages
        500 http://la-mirrors.evowise.com/ubuntu focal/main i386 Packages
[COLOR=#18B218]**wellywu@FerenOS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#1818B2]**~**[/COLOR][COLOR=#000000]$[/COLOR]
[/FONT]
```

So, I install pavucontrol and aslsamixergui. Pavucontrol shows that it is a Cannonlake PCH cAVS Multichannel. In alsamixer, I selected the sof-hda-dsp and I chose input devices. Both Mic Boost and Capture are set at 100%. Dmic0 and Dmic 1 2nd are set at 46%. When I attempt a Facebook video call to a friend, I can see and hear him because he uses Microsoft Windows 10 64-bit Pro edition version 20H2 on his AVA Direct gaming desktop PC system, but he can see me and he can not hear me. My microphone is not working even though it looks like it is not muted or suppressed.

I am using K Desktop Environment Plasma 5.20 64-bit, Linux kernel 5.8.0-38-generic AMD64, pulseaudio version 13.99.1 64-bit, and alsa-ucm-conf 1.2.2-1. Feren OS 2021.1 64-bit should be based on Ubuntu 20.10 64-bit GNU/Linux. So, my internal laptop speakers just work. I can hear audio, but my digital microphone array does not work and it does not pickup audio or my voice. On paper, I should have the required software packages and versions to make both my speakers and digital microphone array just work right out of the box.

Look, I know this is not directly related to Ubuntu because I am talking about Feren OS 2021.1 64-bit. I think and feel like I am pretty close to a technical solution if you would be so kind to read and offer guidance and help in the right direction. I joined the Disqus Feren OS forum, but it is not the same quality as here on Ubuntu Forums. Live chat really doesn't do much for me on Disqus or other platforms for help and technical support. So, if you can help, then please respond. Thank you.

How do I check where the Intel Sound Open Firmware files are located in Ubuntu 20.04.1 64-bit LTS? How do I update my installed version of Intel Sound Open Firmware? Thanks.

My technical research fixed it. Here is the Ubuntu Launcpad bug report with the two specific hacks to solve it: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1840725](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1840725).

Post #63 shows me how to use arecord -l properly:

```
[COLOR=#333333][FONT=monospace]FIRST: do[/FONT][/COLOR][COLOR=#333333][FONT=monospace]arecord -l
maybe gives:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC3254 Analog [ALC3254 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]NOTE: Subdevices: 1/1, remember it![/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]SECOND:
add
    options snd-hda-intel index=X model=laptop-dmic
to /etc/modprobe.d/alsa-base.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]NOTE:
if Subdevices: 1/1, index=1
if Subdevices: 0/1, index=0[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]after update alsa-base.conf, reboot!
```

Post #66 has the solution for /etc/pulse/default.pa:
```
Had a similar problem with Lenovo S740 (Ubuntu 18.04, 19.10 and 20.04). Tried different combinations in alsa-base.conf, hda-jack-retask - nothing worked.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]And then surprisingly this thread helped (see [https://gist.github.com/hamidzr/dd81e429dc86f4327ded7a2030e7d7d9#gistcomment-3315737](https://gist.github.com/hamidzr/dd81e429dc86f4327ded7a2030e7d7d9#gistcomment-3315737) ).[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]What I've done is I appended next two lines to /etc/pulse/default.pa:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# /etc/pulse/default.pa
load-module module-alsa-sink device=hw:0,0 channels=2 # note that I used 2 here
load-module module-alsa-source device=hw:0,6 channels=2
```[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]For those of you having problems in Ubuntu 20.04 with Realtek ALC285 this could be a solution.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]&#10095; uname -a
Linux anton-Lenovo-Yoga-S740-14IIL 5.4.0-33-generic #37-Ubuntu SMP Thu May 21 12:53:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Now internal microphone records audio, please try to see if it helps you
```

I made backup copies of both alsa-base.conf under /etc/modprobe.d/ to include this line of software code:
```
options snd-usb-audio index=2
```

I also made backup copies of /etc/pulse/default.pa and I added these lines of software code:
```
[COLOR=#222222][FONT=Verdana]load-module module-alsa-sink device=hw:0,0 channels=2[/FONT][/COLOR][/FONT][/COLOR]
load-module module-alsa-source device=hw:0,6 channels=2
```

Restarted my late 2019 CUK HP Omen 15t gaming notebook PC, opened up KDE System Settings -> Audio and selected Cannon Lake PCH cAVS. Do not select Multichannel Input (Cannon Lake PCH cAVS).

Solved!

---

### Post by howefield on 2021-01-18
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

