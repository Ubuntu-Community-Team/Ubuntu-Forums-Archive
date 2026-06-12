---
title: "Ubuntu Sever 14.04 LTS system doesn't wake up after suspend (S3 mode)"
date: 2016-04-10
forum: Server Platforms
---

### Post by alexey24 on 2016-04-10
Hello, Guys!

I do want to make work S3 suspending on my server (for quick waking up from StandBy mode), but it doesn't :D
My old motherboard Asus K8N-VM must support this kind of suspending, but I get really strange behavior. 
Sometimes everything goes good and I can suspend and wake up the system even several times, but on next awakening OS becomes freezed. Nevertheless S1 suspending and hibernation work fine.
The display which is connected to motherboard's VGA port doesn't wake up too. Only hard reset of the system can help in this case. 
It is a headless setup (display was connected just for test), without keyboards and else periphery.

Kernel:
```
4.2.0-34-generic
```

[SuspendResumeTesting]("https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting") has the same results.

Below I provide some pm's logs.

/var/log/pm-suspend.log

```

Initial commandline parameters: 
Sun Apr 10 23:11:47 EEST 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux z-storage 4.2.0-34-generic #39~14.04.1-Ubuntu SMP Fri Mar 11 11:38:02 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ppdev                  20480  0 
nouveau              1368064  1 
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
video                  40960  1 nouveau
amd64_edac_mod         32768  0 
ttm                    94208  1 nouveau
edac_core              53248  2 amd64_edac_mod
drm_kms_helper        126976  1 nouveau
serio_raw              16384  0 
edac_mce_amd           24576  1 amd64_edac_mod
dm_multipath           24576  0 
k8temp                 16384  0 
scsi_dh                16384  1 dm_multipath
drm                   360448  4 ttm,drm_kms_helper,nouveau
i2c_nforce2            16384  0 
i2c_algo_bit           16384  1 nouveau
shpchp                 36864  0 
snd_mpu401_uart        16384  0 
snd_rawmidi            32768  1 snd_mpu401_uart
snd_seq_device         16384  1 snd_rawmidi
ns558                  16384  0 
gameport               16384  1 ns558
snd                    81920  3 snd_rawmidi,snd_mpu401_uart,snd_seq_device
soundcore              16384  1 snd
8250_fintek            16384  0 
parport_pc             32768  0 
asus_atk0110           20480  0 
mac_hid                16384  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
dm_snapshot            40960  3 
dm_bufio               28672  1 dm_snapshot
pata_acpi              16384  0 
psmouse               126976  0 
forcedeth              69632  0 
sata_nv                28672  2 
pata_amd               20480  0 
floppy                 73728  0 
dm_mirror              24576  1 
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  3 dm_region_hash,dm_mirror
             total       used       free     shared    buffers     cached
Mem:        951168     126448     824720        568      18136      54408
-/+ buffers/cache:      53904     897264
Swap:       978940          0     978940
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Sun Apr 10 23:11:48 EEST 2016: performing suspend
Sun Apr 10 23:12:30 EEST 2016: Awake.
Sun Apr 10 23:12:30 EEST 2016: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Sun Apr 10 23:12:35 EEST 2016: Finished.
Initial commandline parameters: 
Sun Apr 10 23:12:40 EEST 2016: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux z-storage 4.2.0-34-generic #39~14.04.1-Ubuntu SMP Fri Mar 11 11:38:02 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ppdev                  20480  0 
nouveau              1368064  1 
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
video                  40960  1 nouveau
amd64_edac_mod         32768  0 
ttm                    94208  1 nouveau
edac_core              53248  2 amd64_edac_mod
drm_kms_helper        126976  1 nouveau
serio_raw              16384  0 
edac_mce_amd           24576  1 amd64_edac_mod
dm_multipath           24576  0 
k8temp                 16384  0 
scsi_dh                16384  1 dm_multipath
drm                   360448  4 ttm,drm_kms_helper,nouveau
i2c_nforce2            16384  0 
i2c_algo_bit           16384  1 nouveau
shpchp                 36864  0 
snd_mpu401_uart        16384  0 
snd_rawmidi            32768  1 snd_mpu401_uart
snd_seq_device         16384  1 snd_rawmidi
ns558                  16384  0 
gameport               16384  1 ns558
snd                    81920  3 snd_rawmidi,snd_mpu401_uart,snd_seq_device
soundcore              16384  1 snd
8250_fintek            16384  0 
parport_pc             32768  0 
asus_atk0110           20480  0 
mac_hid                16384  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
dm_snapshot            40960  3 
dm_bufio               28672  1 dm_snapshot
pata_acpi              16384  0 
psmouse               126976  0 
forcedeth              69632  0 
sata_nv                28672  2 
pata_amd               20480  0 
floppy                 73728  0 
dm_mirror              24576  1 
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  3 dm_region_hash,dm_mirror
             total       used       free     shared    buffers     cached
Mem:        951168     129404     821764        576      18164      54576
-/+ buffers/cache:      56664     894504
Swap:       978940          0     978940
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Sun Apr 10 23:12:40 EEST 2016: performing suspend



```

The second suspending led to freezing (there are no any tries to wake up the system).


/var/log/pm-powersave.log

```

Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:
/usr/lib/pm-utils/power.d/95hdparm-apm false: success.


Running hook /usr/lib/pm-utils/power.d/disable_wol false:
Setting Wake On Lan for eth0 to enable...Done.
/usr/lib/pm-utils/power.d/disable_wol false: success.


Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.


Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.
/usr/lib/pm-utils/power.d/laptop-mode false: success.


Running hook /usr/lib/pm-utils/power.d/pci_devices false:
Setting Host Bridge 0000:00:18.0 to on
Setting Host Bridge 0000:00:18.1 to on
Setting Host Bridge 0000:00:18.2 to on
Setting Host Bridge 0000:00:18.3 to on
/usr/lib/pm-utils/power.d/pci_devices false: success.


Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
sh: echo: I/O error
/usr/lib/pm-utils/power.d/pcie_aspm false: success.


Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
/usr/lib/pm-utils/power.d/sata_alpm false: success.


Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF
/usr/lib/pm-utils/power.d/sched-powersave false: success.


Running hook /usr/lib/pm-utils/power.d/usb_bluetooth false:
/usr/lib/pm-utils/power.d/usb_bluetooth false: success.


Running hook /usr/lib/pm-utils/power.d/wireless false:
/usr/lib/pm-utils/power.d/wireless false: success.


Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:
/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.


Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:
/usr/lib/pm-utils/power.d/95hdparm-apm false: success.


Running hook /usr/lib/pm-utils/power.d/disable_wol false:
Setting Wake On Lan for eth0 to enable...Done.
/usr/lib/pm-utils/power.d/disable_wol false: success.


Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.


Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.
/usr/lib/pm-utils/power.d/laptop-mode false: success.


Running hook /usr/lib/pm-utils/power.d/pci_devices false:
Setting Host Bridge 0000:00:18.0 to on
Setting Host Bridge 0000:00:18.1 to on
Setting Host Bridge 0000:00:18.2 to on
Setting Host Bridge 0000:00:18.3 to on
/usr/lib/pm-utils/power.d/pci_devices false: success.


Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
sh: echo: I/O error
/usr/lib/pm-utils/power.d/pcie_aspm false: success.


Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
/usr/lib/pm-utils/power.d/sata_alpm false: success.


Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF
/usr/lib/pm-utils/power.d/sched-powersave false: success.


Running hook /usr/lib/pm-utils/power.d/usb_bluetooth false:
/usr/lib/pm-utils/power.d/usb_bluetooth false: success.


Running hook /usr/lib/pm-utils/power.d/wireless false:
/usr/lib/pm-utils/power.d/wireless false: success.


Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:
/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.


Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:
/usr/lib/pm-utils/power.d/95hdparm-apm false: success.


Running hook /usr/lib/pm-utils/power.d/disable_wol false:
Setting Wake On Lan for eth0 to enable...Done.
/usr/lib/pm-utils/power.d/disable_wol false: success.


Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.


Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.
/usr/lib/pm-utils/power.d/laptop-mode false: success.


Running hook /usr/lib/pm-utils/power.d/pci_devices false:
Setting Host Bridge 0000:00:18.0 to on
Setting Host Bridge 0000:00:18.1 to on
Setting Host Bridge 0000:00:18.2 to on
Setting Host Bridge 0000:00:18.3 to on
/usr/lib/pm-utils/power.d/pci_devices false: success.


Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:
sh: echo: I/O error
/usr/lib/pm-utils/power.d/pcie_aspm false: success.


Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
/usr/lib/pm-utils/power.d/sata_alpm false: success.


Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF
/usr/lib/pm-utils/power.d/sched-powersave false: success.


Running hook /usr/lib/pm-utils/power.d/usb_bluetooth false:
/usr/lib/pm-utils/power.d/usb_bluetooth false: success.


Running hook /usr/lib/pm-utils/power.d/wireless false:
/usr/lib/pm-utils/power.d/wireless false: success.


Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:
/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.


```

Of course it can be a hardware problem, but I can miss something too. Maybe someone had the same issues? What kind of problem can provide to this result?
Thanks in advance for any feedback!

---

