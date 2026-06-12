---
title: "No Sound On Galaxy Book 12"
date: 2019-01-24
forum: Ubuntu/Debian BASED
---

### Post by yanisdb on 2019-01-24
Good Evening, 
So, this is my second post and I'm still trying to make Linux work on my new Samsung Galaxy Book 12. Making the WiFi work was a pain but I think making the sound work will be even worst because I don't know anything about sound in Linux, I've made some research but everything I tried seems to tell me that everything is fine. I don't have anymore idea on how to troubleshoot the problem. You will find bellow outputs that might help you figure out the problems. In any case, thank you for your help =).

```

root@kali:/home/kali# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC298 Analog [ALC298 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

amixer -c0 scontrols
Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Mic',0
Simple mixer control 'Mic Boost',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958',1
Simple mixer control 'IEC958',2
Simple mixer control 'IEC958',3
Simple mixer control 'IEC958',4
Simple mixer control 'Capture',0
Simple mixer control 'Internal Mic Boost',0
Simple mixer control 'Loopback Mixing',0

```

This gives me no sound at all :
```

speaker-test -c2 -t wav

speaker-test 1.1.7

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 3.037324

```

```

root@kali:/home/kali# lspci -v | grep -B1 -A12 -i audio

00:1f.3 Multimedia audio controller: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: Samsung Electronics Co Ltd Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 131
    Memory at df638000 (64-bit, non-prefetchable) [size=16K]
    Memory at df600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl

00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
    Subsystem: Samsung Electronics Co Ltd Sunrise Point-LP SMBus
    Flags: medium devsel, IRQ 16
    Memory at df642000 (64-bit, non-prefetchable) [size=256]

```

```

sudo lshw | grep -B4 -A10 -i audio
             clock: 33MHz (30.3ns)
             configuration: latency=0
             resources: memory:df63c000-df63ffff
        *-multimedia:2
             description: Multimedia audio controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:131 memory:df638000-df63bfff memory:df600000-df60ffff

```

```

dmesg | grep intel
[    1.421121] intel_idle: MWAIT substates: 0x11142120
[    1.421122] intel_idle: v0.4.1 model 0x8E
[    1.421343] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.425944] intel_pstate: Intel P-state driver initializing
[    1.426174] intel_pstate: HWP enabled
[    1.603338] intel-lpss 0000:00:15.0: enabling device (0000 -> 0002)
[    1.639411] intel-lpss 0000:00:15.1: enabling device (0000 -> 0002)
[    2.708103] intel-lpss 0000:00:15.2: enabling device (0000 -> 0002)
[    2.716481] intel-lpss 0000:00:15.3: enabling device (0000 -> 0002)
[    2.722129] intel-lpss 0000:00:19.0: enabling device (0000 -> 0002)
[    2.722869] intel-lpss 0000:00:1e.0: enabling device (0000 -> 0002)
[    4.847892] fb: switching to inteldrmfb from EFI VGA
[    4.904511] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    5.029174] intel_rapl: Found RAPL domain package
[    5.029175] intel_rapl: Found RAPL domain core
[    5.029176] intel_rapl: Found RAPL domain uncore
[    5.029177] intel_rapl: Found RAPL domain dram
[    5.407689] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    5.409664] fbcon: inteldrmfb (fb0) is primary device
[    6.636465] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device

```

```

lsmod | grep intel
snd_soc_acpi_intel_match    24576  1 snd_soc_skl
snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_soc_skl
intel_rapl             24576  0
intel_powerclamp       16384  0
btintel                24576  1 btusb
snd_hda_intel          45056  7
bluetooth             643072  5 btrtl,btintel,btbcm,btusb
snd_hda_codec         151552  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
kvm_intel             241664  0
snd_hda_core           94208  7 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_soc_skl
kvm                   729088  1 kvm_intel
snd_pcm               114688  8 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_core,snd_soc_skl,snd_hda_core
intel_cstate           16384  0
snd                    94208  23 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm
intel_uncore          135168  0
intel_rapl_perf        16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
intel_pch_thermal      16384  0
intel_vbtn             16384  0
sparse_keymap          16384  1 intel_vbtn
crc32c_intel           24576  2
ghash_clmulni_intel    16384  0
aesni_intel           200704  4
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 28672  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
intel_lpss_pci         20480  0
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi

```

If you've read till here tank you so much and have a nice evening =).

---

### Post by yanisdb on 2019-01-27
Please guys, does nobody have a solution, or didn't I post in the right place ?

---

### Post by coffeecat on 2019-01-27
As a matter of fact you didn't - you are using Kali, which is not Ubuntu, nor based on Ubuntu. I've moved this thread to an appropriate section, although you need to be aware of a couple of things.

Kali is a highly specialised operating system intended for penetration testing and "ethical hacking", not the sort of general use most forum members here expect. It differs in several fundamental ways from more mainstream distros. I doubt you'd find many people on this forum with experience of Kali. You might be better off in Kali's own forum: [https://forums.kali.org/](https://forums.kali.org/) . 

Does Kali really suit your needs? Would you be better off with a more mainstream distro?

---

### Post by yanisdb on 2019-01-27
Thank you very much, and yes indeed, I need it, for school. But I didn't thought it would be that hard to make it work. I knew what I was doing when I chose and I'm ready to do what it takes but I'm lost here, I've got not idea what's the problem. Could you help or just show me the right direction to look ?
Thank you very much for answering me before in any case

---

### Post by yanisdb on 2019-01-30
As I'm not getting any answer at all, probably because  it's not the right forum for this question, I mean, asking about Kali on a Ubuntu forum... Could anyone tell me which forum, or who I could ask for help ?

---

### Post by yaazzz on 2019-05-08
The same problem is present on ubuntu for instance 19.04. I don't think it is related to the distri but more to the alsa driver.

---

### Post by briggs_1978 on 2019-12-07
I'm having the same issue in Ubuntu 19.20.  Does anyone know if there has been any development on this?
Also using a Samsung laptop (2019 notebook 9 pen)

---

### Post by coffeecat on 2019-12-07
Sub-forum strapline:

> Support for Ubuntu or Debian based distributions - **not for Official Ubuntu flavours**

@briggs_1978, this is an old thread. You are very unlikely to attract help here. Please start your own thread in an appropriate sub-forum of the official flavours section of the forum, giving full details of your hardware and operating system. There is no Ubuntu 19.20 - perhaps this is a typo for 19.10?

Old thread closed.

---

