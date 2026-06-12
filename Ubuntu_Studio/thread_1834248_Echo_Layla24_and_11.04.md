---
title: "Echo Layla24 and 11.04"
date: 2011-08-27
forum: Ubuntu Studio
---

### Post by gslug79 on 2011-08-27
Hello all!

Having acquired a rather old Echo Layla24 PCI audio interface, I have spent the last day fighting to get to work. There are a few threads on this already, but they are several years old.

Initially I tried using Medibuntu to install alsa-firmware, but found that this did not contain anything for the Echo interfaces. I then built alsa-driver-1.0.24,  alsa-lib-1.0.24.1, alsa-utils-1.0.24.2 and alsa-firmware-1.0.24.1 from source, with the –with-cards=layla24 option for the latter. Everything compiled and installed without problem, but the interface still failed to work.

Attempting to restart alsa gives this:

```
slune@slune-desktop:~$ sudo /etc/init.d/alsasound start

WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.

Starting sound driver: snd-layla24 WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.

WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.

FATAL: Error inserting snd (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)

WARNING: Error running install command for snd

WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)

WARNING: Error inserting snd_seq_device (/lib/modules/2.6.38-11-generic/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)

WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.38-11-generic/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

FATAL: Error inserting snd_layla24 (/lib/modules/2.6.38-11-generic/kernel/sound/pci/echoaudio/snd-layla24.ko): Unknown symbol in module, or unknown parameter (see dmesg)

done

```

The result of dmesg:

```
[  257.963387] snd: Unknown symbol unregister_sound_special (err 0)

[  257.964040] snd: Unknown symbol register_sound_special_device (err 0)

[  257.967338] snd_timer: Unknown symbol snd_info_register (err 0)

[  257.967566] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)

[  257.967847] snd_timer: Unknown symbol snd_info_free_entry (err 0)

[  257.968384] snd_timer: Unknown symbol __snd_printk (err 0)

[  257.968621] snd_timer: Unknown symbol snd_iprintf (err 0)

[  257.968935] snd_timer: Unknown symbol snd_ecards_limit (err 0)

[  257.969208] snd_timer: Unknown symbol snd_oss_info_register (err 0)

[  257.969433] snd_timer: Unknown symbol snd_unregister_device (err 0)

[  257.969715] snd_timer: Unknown symbol snd_device_new (err 0)

[  257.970235] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)

[  473.501861] snd: Unknown symbol unregister_sound_special (err 0)

[  473.502513] snd: Unknown symbol register_sound_special_device (err 0)

[  473.505830] snd_timer: Unknown symbol snd_info_register (err 0)

[  473.506058] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)

[  473.506340] snd_timer: Unknown symbol snd_info_free_entry (err 0)

[  473.506873] snd_timer: Unknown symbol __snd_printk (err 0)

[  473.507107] snd_timer: Unknown symbol snd_iprintf (err 0)

[  473.507422] snd_timer: Unknown symbol snd_ecards_limit (err 0)

[  473.507695] snd_timer: Unknown symbol snd_oss_info_register (err 0)

[  473.507920] snd_timer: Unknown symbol snd_unregister_device (err 0)

[  473.508200] snd_timer: Unknown symbol snd_device_new (err 0)

[  473.508685] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)

[  489.806858] snd: Unknown symbol unregister_sound_special (err 0)

[  489.807510] snd: Unknown symbol register_sound_special_device (err 0)

[  489.810545] snd_timer: Unknown symbol snd_info_register (err 0)

[  489.810611] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)

[  489.810691] snd_timer: Unknown symbol snd_info_free_entry (err 0)

[  489.810844] snd_timer: Unknown symbol __snd_printk (err 0)

[  489.810911] snd_timer: Unknown symbol snd_iprintf (err 0)

[  489.811001] snd_timer: Unknown symbol snd_ecards_limit (err 0)

[  489.811079] snd_timer: Unknown symbol snd_oss_info_register (err 0)

[  489.811143] snd_timer: Unknown symbol snd_unregister_device (err 0)

[  489.811224] snd_timer: Unknown symbol snd_device_new (err 0)

[  489.811363] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)

[  494.237272] snd: Unknown symbol unregister_sound_special (err 0)

[  494.238017] snd: Unknown symbol register_sound_special_device (err 0)

[  507.406916] snd: Unknown symbol unregister_sound_special (err 0)

[  507.407568] snd: Unknown symbol register_sound_special_device (err 0)

[29193.707443] snd: Unknown symbol unregister_sound_special (err 0)

[29193.707631] snd: Unknown symbol register_sound_special_device (err 0)

[29193.708610] snd_timer: Unknown symbol snd_info_register (err 0)

[29193.708675] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)

[29193.708755] snd_timer: Unknown symbol snd_info_free_entry (err 0)

[29193.708909] snd_timer: Unknown symbol __snd_printk (err 0)

[29193.708977] snd_timer: Unknown symbol snd_iprintf (err 0)

[29193.709067] snd_timer: Unknown symbol snd_ecards_limit (err 0)

[29193.709144] snd_timer: Unknown symbol snd_oss_info_register (err 0)

[29193.709209] snd_timer: Unknown symbol snd_unregister_device (err 0)

[29193.709289] snd_timer: Unknown symbol snd_device_new (err 0)

[29193.709429] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
```

Running alsaconf appears to work and detects the hardware as  layla24 Motorola DSP56361 Digital Signal Processor, but alsamixer (presumably) finds no cards:

```
slune@slune-desktop:~$ alsamixer 

cannot open mixer: No such file or directory

slune@slune-desktop:~$ aplay -l

aplay: device_list:240: no soundcards found...

```

I am totally stuck. Any ideas?

---

