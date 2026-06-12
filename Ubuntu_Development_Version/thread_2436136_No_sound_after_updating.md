---
title: "No sound after updating?"
date: 2020-01-31
forum: Ubuntu Development Version
---

### Post by fired-spenser on 2020-01-31
Hey guys.  I was running 19.10 on a Lenovo Yoga c940 with no major issues... I pushed the 20.04 update - because I'm not a very smart man. Since then, no more sound.  Been doing some reading, trying to figure things out, but no luck.  Any suggestions?  Output below of lspci -vv | grep -i audio and sudo dmesg | grep -i audio

Thanks for any help!

$ sudo lspci -vv | grep -i audio
00:1f.3 Multimedia audio controller: Intel Corporation Smart Sound Technology Audio Controller (rev 30)
    Subsystem: Lenovo Smart Sound Technology Audio Controller
    Kernel driver in use: sof-audio-pci

```
$ sudo dmesg | grep -i audio
[    0.110266] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    4.636204] sof-audio-pci 0000:00:1f.3: warning: No matching ASoC machine driver found
[    4.636210] sof-audio-pci 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
[    4.636345] sof-audio-pci 0000:00:1f.3: use msi interrupt mode
[    4.689087] sof-audio-pci 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    4.729706] sof-audio-pci 0000:00:1f.3: hda codecs found, mask 5
[    4.729708] sof-audio-pci 0000:00:1f.3: using HDA machine driver skl_hda_dsp_generic now
[    5.859812] sof-audio-pci 0000:00:1f.3: Direct firmware load for intel/sof/sof-icl.ri failed with error -2
[    5.859816] sof-audio-pci 0000:00:1f.3: error: request firmware intel/sof/sof-icl.ri failed err: -2
[    5.859818] sof-audio-pci 0000:00:1f.3: error: failed to load DSP firmware -2
[    5.859819] sof-audio-pci 0000:00:1f.3: error: sof_probe_work failed err: -2
```

---

### Post by wildmanne39 on 2020-01-31
*Thread moved to **Ubuntu Development Version a more appropriate sub-forum**.*

---

### Post by fired-spenser on 2020-01-31
Some additional info...  

Soundcard isn't found if I run sudo aplay -l

Sound modules are installed, verified when I run: find /lib/modules/`uname -r` | grep snd

If I run:
```
lspci -v | grep -A7 -i "audio" then I get: 
00:1f.3 Multimedia audio controller: Intel Corporation Smart Sound Technology Audio Controller (rev 30)
    Subsystem: Lenovo Smart Sound Technology Audio Controller
    Flags: bus master, fast devsel, latency 32, IRQ 178
    Memory at 601d160000 (64-bit, non-prefetchable) [size=16K]
    Memory at 601d000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: sof-audio-pci
    Kernel modules: snd_hda_intel, snd_sof_pci

00:1f.4 SMBus: Intel Corporation Ice Lake-LP SMBus Controller (rev 30)
    Subsystem: Lenovo Ice Lake-LP SMBus Controller
    Flags: medium devsel, IRQ 16
    Memory at 601d16c000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 3040 [size=32]
```

Help?  Thanks everyone!

---

### Post by chili555 on 2020-02-01
> Direct firmware load for intel/sof/sof-icl.ri failed with error -2Let's fix that and see if it helps. From the terminal:

```
sudo apt install zstd
wget http://ftp5.gwdg.de/pub/linux/archlinux/extra/os/x86_64//sof-firmware-1.4.2-1-any.pkg.tar.zst
tar -I zstd -xvf sof-firmware-1.4.2-1-any.pkg.tar.zst
sudo cp ~/usr/lib/firmware/intel/sof/*.ri  /lib/firmware/intel/sof
```Reboot and tell us if there is any improvement.

---

### Post by Smask on 2020-02-03
I've had some boxes here at one point or another during the 20.04 cycle, go mute. Intel, AMD or Realtek, it doesn't matter.

---

