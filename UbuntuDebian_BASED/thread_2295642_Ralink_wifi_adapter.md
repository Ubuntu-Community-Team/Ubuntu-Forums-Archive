---
title: "Ralink wifi adapter"
date: 2015-09-20
forum: Ubuntu/Debian BASED
---

### Post by nura3 on 2015-09-20
root@kali:~/Downloads/RT2870_LinuxSTA_V2.3.0.0# make
make -C tools
make[1]: Entering directory '/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/tools'
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/Makefile
make -C /lib/modules/4.0.0-kali1-686-pae/build SUBDIRS=/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.0.0-kali1-686-pae'
Makefile:10: *** mixed implicit and normal rules: deprecated syntax
  CC [M]  /root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.o
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c:1446:6: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’ [-Wparentheses]
   if(!erq->flags & IW_ENCODE_MODE) 
      ^
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_private_show’:
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c:1743:78: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
             sprintf(extra, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                              ^
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c:1743:88: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
             sprintf(extra, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                        ^
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c:1892:1: warning: the frame size of 1580 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c:600:1: warning: the frame size of 1296 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c:5737:1: warning: the frame size of 1344 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.c:5935:1: warning: the frame size of 1344 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
cc1: some warnings being treated as errors
/usr/src/linux-headers-4.0.0-kali1-common/scripts/Makefile.build:263: recipe for target '/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.o' failed
make[4]: *** [/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../os/linux/sta_ioctl.o] Error 1
/usr/src/linux-headers-4.0.0-kali1-common/Makefile:1407: recipe for target '_module_/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux' failed
make[3]: *** [_module_/root/Downloads/RT2870_LinuxSTA_V2.3.0.0/os/linux] Error 2
Makefile:145: recipe for target 'sub-make' failed
make[2]: *** [sub-make] Error 2
Makefile:8: recipe for target 'all' failed
make[1]: *** [all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.0.0-kali1-686-pae'
Makefile:185: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2

---

### Post by praseodym on 2015-09-20
Driver too old for kernel 4. Please show
```

lsusb
lsmod
```

---

### Post by nura3 on 2015-09-21
hi, thanks for the reply,

root@kali:~# lsusb
Bus 004 Device 004: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 004 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0e8f:00fb GreenAsia Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

root@kali:~# lsmod
Module                  Size  Used by
nls_utf8               16384  1 
isofs                  40960  1 
udf                    86016  0 
crc_itu_t              16384  1 udf
cfg80211              393216  0 
binfmt_misc            20480  1 
tun                    28672  2 
nfnetlink_queue        20480  0 
nfnetlink_log          20480  0 
nfnetlink              16384  2 nfnetlink_log,nfnetlink_queue
bluetooth             380928  0 
rfkill                 20480  3 cfg80211,bluetooth
iTCO_wdt               16384  0 
iTCO_vendor_support    16384  1 iTCO_wdt
snd_hda_codec_via      24576  1 
snd_hda_codec_generic    61440  1 snd_hda_codec_via
ppdev                  20480  0 
snd_hda_intel          28672  6 
evdev                  20480  6 
snd_hda_controller     28672  1 snd_hda_intel
snd_hda_codec          94208  4 snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                81920  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_timer              28672  1 snd_pcm
snd                    57344  19 snd_hwdep,snd_timer,snd_hda_codec_via,snd_pcm,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
serio_raw              16384  0 
soundcore              16384  2 snd,snd_hda_codec
i2c_i801               20480  0 
lpc_ich                20480  0 
mfd_core               16384  1 lpc_ich
coretemp               16384  0 
rng_core               16384  0 
parport_pc             28672  0 
8250_fintek            16384  0 
i915                  925696  3 
parport                36864  2 ppdev,parport_pc
video                  20480  1 i915
shpchp                 32768  0 
drm_kms_helper         90112  1 i915
drm                   233472  5 i915,drm_kms_helper
button                 16384  1 i915
i2c_algo_bit           16384  1 i915
acpi_cpufreq           20480  0 
processor              28672  1 acpi_cpufreq
thermal_sys            28672  2 video,processor
loop                   24576  0 
fuse                   81920  3 
autofs4                36864  2 
ext4                  462848  1 
crc16                  16384  2 ext4,bluetooth
mbcache                20480  1 ext4
jbd2                   77824  1 ext4
dm_mod                 86016  0 
hid_generic            16384  0 
usbhid                 45056  0 
hid                    90112  2 hid_generic,usbhid
sg                     32768  0 
sr_mod                 24576  1 
cdrom                  49152  1 sr_mod
sd_mod                 40960  3 
ata_generic            16384  0 
ata_piix               32768  3 
libata                163840  2 ata_generic,ata_piix
scsi_mod              180224  4 sg,libata,sd_mod,sr_mod
atl1c                  40960  0 
ehci_pci               16384  0 
uhci_hcd               40960  0 
ehci_hcd               65536  1 ehci_pci
usbcore               176128  4 uhci_hcd,ehci_hcd,ehci_pci,usbhid
usb_common             16384  1 usbcore

---

### Post by praseodym on 2015-09-21
See here:

[http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation/554278#554278](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adapter-installation/554278#554278)

---

### Post by nura3 on 2015-09-22
hi that link didnt work,

root@kali:~# apt-get install linux-headers-generic build-essential git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-generic' has no installation candidate


root@kali:/# apt-cache search linux-headers
linux-headers-4.0.0-kali1-586 - Header files for Linux 4.0.0-kali1-586
linux-headers-4.0.0-kali1-686-pae - Header files for Linux 4.0.0-kali1-686-pae
linux-headers-4.0.0-kali1-all - All header files for Linux 4.0 (meta-package)
linux-headers-4.0.0-kali1-all-i386 - All header files for Linux 4.0 (meta-package)
linux-headers-4.0.0-kali1-common - Common header files for Linux 4.0.0-kali1
linux-headers-586 - Header files for Linux 586 configuration (meta-package)
linux-headers-686-pae - Header files for Linux 686-pae configuration (meta-package)

---

### Post by howefield on 2015-09-22
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by nura3 on 2015-09-22
root@kali:/# aptitude install build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

---

