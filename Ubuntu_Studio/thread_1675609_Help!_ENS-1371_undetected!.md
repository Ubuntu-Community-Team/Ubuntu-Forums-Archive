---
title: "Help! ENS-1371 undetected!"
date: 2011-01-25
forum: Ubuntu Studio
---

### Post by marcoharder on 2011-01-25
For some reason, I installed Alsa 1.0.23 on my PC to make sure that my ENS 1371 card will work. Now, the funny thing was, it was detected by the Ubuntu generic kernel [alongside the internal soundcard] before I installed Alsa. I tried booting into 2.6.33.7-rt and was surprised to see that Ubuntu has not detected it! I did lspci, and it was showing, but the speaker icon just showed 3 lines next to it.

When I tried doing 'modprobe snd-ens1371', I got this set of messages:

```
marcoharder@MTheory-Atom:~/Desktop/alsa-driver-1.0.23$ sudo modprobe snd-ens1371 
FATAL: Error inserting snd (/lib/modules/2.6.33-7-rt/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.33-7-rt/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ac97_bus (/lib/modules/2.6.33-7-rt/kernel/sound/misc/ac97_bus.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.33-7-rt/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.33-7-rt/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.33-7-rt/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting gameport (/lib/modules/2.6.33-7-rt/kernel/drivers/input/gameport/gameport.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ens1371 (/lib/modules/2.6.33-7-rt/kernel/sound/pci/snd-ens1371.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

HELP!

---

