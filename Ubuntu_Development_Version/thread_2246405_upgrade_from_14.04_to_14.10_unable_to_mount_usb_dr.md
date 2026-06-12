---
title: "upgrade from 14.04 to 14.10 unable to mount usb drive and other function not working"
date: 2014-09-30
forum: Ubuntu Development Version
---

### Post by SpUpUz on 2014-09-30
upgrade from 14.04 to 14.10 upgrade was fine, but i'm not able to mount usb drive: "operation not permitted"
all activities that need also an admin password request are not working and passoword box is not prompet and not appearing.
can't see advance settings for users and group, can't star gparted from the gui, but it works if i use terminal with command "sudo gparted".

Thanks in advance

---

### Post by zika on 2014-09-30
> **SpUpUz said:**
> upgrade from 14.04 to 14.10 upgrade was fine, but i'm not able to mount usb drive: "operation not permitted"
all activities that need also an admin password request are not working and passoword box is not prompet and not appearing.
can't see advance settings for users and group, can't star gparted from the gui, but it works if i use terminal with command "sudo gparted".

Thanks in advanceCheck if You have ~/.gksu.lock and try to remove it if it is present.

---

### Post by SpUpUz on 2014-09-30
i did it but the problem remain

---

### Post by kansasnoob on 2014-09-30
What method did you use to upgrade?

---

### Post by SpUpUz on 2014-09-30
sudo do-release-upgrade -d from terminal

---

### Post by cariboo on 2014-09-30
Does dmesg indicate that the usb drive has been detected properly?

---

### Post by SpUpUz on 2014-10-01
> **cariboo907 said:**
> Does dmesg indicate that the usb drive has been detected properly?

yes it is, unfortunately usb mount from gui it is not the only problem as i said all the operation that request a gui box for password doing something administraively are not working, for example administering user and groups advanced settings, or trying to opening gparted.

---

### Post by ventrical on 2014-10-01
> **SpUpUz said:**
> upgrade from 14.04 to 14.10 upgrade was fine, but i'm not able to mount usb drive: "operation not permitted"
all activities that need also an admin password request are not working and passoword box is not prompet and not appearing.
can't see advance settings for users and group, can't star gparted from the gui, but it works if i use terminal with command "sudo gparted".

Thanks in advance

What desktop are you using .. unity? , gnome-shell, gnome-session ??

---

### Post by SpUpUz on 2014-10-01
> **ventrical said:**
> What desktop are you using .. unity? , gnome-shell, gnome-session ??

using unity.

---

### Post by ventrical on 2014-10-01
> **SpUpUz said:**
> using unity.

s' happened  to me a few times. I would try to install gnome-session-fallback(flashback) and use the metacity session to see if USB's are working. If so then you know something got borked in the unity-desktop during the upgrade. This may not help but it has helped many broken unity sessions I have had during development. In fact I always make it a point to have another desktop environment installed just for these cases.

Then uninstall unity-desktop and reinstall it - see what happens..

---

### Post by SpUpUz on 2014-10-01
> **ventrical said:**
> s' happened  to me a few times. I would try to install gnome-session-fallback(flashback) and use the metacity session to see if USB's are working. If so then you know something got borked in the unity-desktop during the upgrade. This may not help but it has helped many broken unity sessions I have had during development. In fact I always make it a point to have another desktop environment installed just for these cases.

Then uninstall unity-desktop and reinstall it - see what happens..


can i do a  dpkg-reconfigure ?
since i'm not at home and i have the problem on my home pc that is not work critical i'll try that this evening.

for example if i want to shutdown i can't do it via gui, it does not happen anything i must do it via cli. :(

---

### Post by ventrical on 2014-10-01
> **SpUpUz said:**
> can i do a  dpkg-reconfigure ?
since i'm not at home and i have the problem on my home pc that is not work critical i'll try that this evening.

for example if i want to shutdown i can't do it via gui, it does not happen anything i must do it via cli. :(


  I just had the same problem ..'broken pipe' ,etc.. That means unity and a few other pkgs did not get fully installed. In my case it was because of bad D-Link and sloppy connections on my part.

Try the below first from cli  and see if that works. If not then try the first I recommended.

```

sudo apt-get --configure -a

```

or

```

sudo apt-get install -f

```


Regards

---

### Post by SpUpUz on 2014-10-01
> **ventrical said:**
> I just had the same problem ..'broken pipe' ,etc.. That means unity and a few other pkgs did not get fully installed. In my case it was because of bad D-Link and sloppy connections on my part.

Try the below first from cli  and see if that works. If not then try the first I recommended.

```

sudo apt-get --configure -a

```

or

```

sudo apt-get install -f

```


Regards

```
spupuz@spupuz-EP35C-DS3R:~$ sudo apt-get --configure -a
[sudo] password for spupuz: 
E: Command line option --configure is not understood
spupuz@spupuz-EP35C-DS3R:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
spupuz@spupuz-EP35C-DS3R:~$
```

---

### Post by SpUpUz on 2014-10-01
```
spupuz@spupuz-EP35C-DS3R:/var/log$ tail -f syslog
Oct  1 20:42:26 spupuz-EP35C-DS3R kernel: [   43.628116] type=1400 audit(1412188946.270:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=5038 comm="apparmor_parser"
Oct  1 20:42:26 spupuz-EP35C-DS3R colord: Profile added: Deskjet_3520-Gray..
Oct  1 20:42:26 spupuz-EP35C-DS3R colord: Profile added: Deskjet_3520-RGB..
Oct  1 20:42:26 spupuz-EP35C-DS3R colord: Device added: cups-Deskjet_3520
Oct  1 20:42:30 spupuz-EP35C-DS3R dbus[874]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Oct  1 20:42:30 spupuz-EP35C-DS3R kernel: [   47.489623] systemd-hostnamed[5127]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Oct  1 20:42:30 spupuz-EP35C-DS3R dbus[874]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct  1 20:42:59 spupuz-EP35C-DS3R gnome-session[3754]: WARNING: Unable to inhibit system: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Operation not permitted
Oct  1 20:45:01 spupuz-EP35C-DS3R CRON[6269]: (spupuz) CMD (env DISPLAY=:0 /usr/bin/luckybackup --silent --skip-critical /home/spupuz/.luckyBackup/profiles/default.profile > /home/spupuz/.luckyBackup/logs/default-LastCronLog.log 2>&1 # JOB_ID_3)
Oct  1 20:45:01 spupuz-EP35C-DS3R CRON[6270]: (spupuz) CMD (/usr/bin/luckybackup -c --no-questions --skip-critical /home/spupuz/.luckyBackup/profiles/default.profile > /home/spupuz/.luckyBackup/logs/default-LastCronLog.log 2>&1 # JOB_ID_2)
Oct  1 20:46:56 spupuz-EP35C-DS3R anacron[1212]: Job `cron.daily' started
Oct  1 20:46:56 spupuz-EP35C-DS3R anacron[6508]: Updated timestamp for job `cron.daily' to 2014-10-01
```

---

### Post by SpUpUz on 2014-10-01
```
[    1.845462] sd 2:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.845493] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.845547] sd 2:0:0:0: [sdc] Write Protect is off
[    1.845556] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.845591] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.845683] scsi 3:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.15 PQ: 0 ANSI: 5
[    1.845832] sd 3:0:0:0: [sdd] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.845868] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.845970] sd 3:0:0:0: [sdd] Write Protect is off
[    1.845974] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.846000] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.848180]  sdd: sdd1 sdd2 sdd3 < sdd5 >
[    1.848645] sd 3:0:0:0: [sdd] Attached SCSI disk
[    1.849672]  sda: sda1
[    1.849912] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.866476]  sdc: sdc1
[    1.866783] sd 2:0:0:0: [sdc] Attached SCSI disk
[    1.868240]  sdb: sdb1
[    1.868530] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.868912] Freeing unused kernel memory: 872K (c19ae000 - c1a88000)
[    1.868971] Write protecting the kernel text: 6512k
[    1.869094] Write protecting the kernel read-only data: 2756k
[    1.869096] NX-protecting the kernel data: 5776k
[    1.888246] systemd-udevd[116]: starting version 208
[    1.889387] random: systemd-udevd urandom read with 32 bits of entropy available
[    1.920746] Floppy drive(s): fd0 is 1.44M
[    1.935452] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    1.941534] scsi4 : pata_jmicron
[    1.943720] FDC 0 is a post-1991 82077
[    1.944294] scsi5 : pata_jmicron
[    1.944368] ata5: PATA max UDMA/100 cmd 0xc000 ctl 0xc100 bmdma 0xc400 irq 16
[    1.944372] ata6: PATA max UDMA/100 cmd 0xc200 ctl 0xc300 bmdma 0xc408 irq 16
[    1.944604] ahci 0000:03:00.0: version 3.0
[    1.944958] usb 3-1: New USB device found, idVendor=046d, idProduct=c51a
[    1.944963] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.944967] usb 3-1: Product: USB Receiver
[    1.944970] usb 3-1: Manufacturer: Logitech
[    1.948701] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.948717] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.948953] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.949214] r8169 0000:04:00.0 eth0: RTL8168b/8111b at 0xf840c000, 00:1a:4d:5f:d3:9d, XID 18000000 IRQ 44
[    1.949219] r8169 0000:04:00.0 eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
[    1.960109] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.960116] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.960666] scsi6 : ahci
[    1.960796] scsi7 : ahci
[    1.960867] ata7: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000100 irq 19
[    1.960872] ata8: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000180 irq 19
[    2.013941] hidraw: raw HID events driver (C) Jiri Kosina
[    2.028577] usbcore: registered new interface driver usbhid
[    2.028581] usbhid: USB HID core driver
[    2.035564] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input5
[    2.035710] hid-generic 0003:046D:C51A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1/input0
[    2.040841] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input6
[    2.041033] hid-generic 0003:046D:C51A.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1/input1
[    2.116521] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    2.116529] ata5.01: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    2.132594] ata5.00: configured for UDMA/33
[    2.148512] ata5.01: configured for UDMA/33
[    2.156626] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    2.162798] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.162802] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.162987] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.163092] sr 4:0:0:0: Attached scsi generic sg4 type 5
[    2.168994] scsi 4:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    2.175157] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.175319] sr 4:0:1:0: Attached scsi CD-ROM sr1
[    2.175428] sr 4:0:1:0: Attached scsi generic sg5 type 5
[    2.280037] ata7: SATA link down (SStatus 0 SControl 300)
[    2.280076] ata8: SATA link down (SStatus 0 SControl 300)
[    2.423584] random: nonblocking pool is initialized
[    2.591600] EXT4-fs (sdd2): INFO: recovery required on readonly filesystem
[    2.591604] EXT4-fs (sdd2): write access will be enabled during recovery
[    2.708031] usb 8-1: new full-speed USB device number 2 using uhci_hcd
[    2.732081] Switched to clocksource tsc
[    2.879088] usb 8-1: New USB device found, idVendor=046d, idProduct=c223
[    2.879094] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.879098] usb 8-1: Product: Logitech G15 Keyboard
[    2.879101] usb 8-1: Manufacturer: Logitech
[    2.882127] hub 8-1:1.0: USB hub found
[    2.884087] hub 8-1:1.0: 4 ports detected
[    2.923062] EXT4-fs (sdd2): recovery complete
[    2.923587] EXT4-fs (sdd2): mounted filesystem with ordered data mode. Opts: (null)
[    3.128041] usb 8-2: new full-speed USB device number 3 using uhci_hcd
[    3.286081] usb 8-2: New USB device found, idVendor=045e, idProduct=00f5
[    3.286087] usb 8-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    3.286091] usb 8-2: Product: USB camera
[    3.504080] usb 1-4.3: new full-speed USB device number 4 using ehci-pci
[    3.592078] usb 1-4.3: device descriptor read/64, error -32
[    3.784071] usb 1-4.3: device descriptor read/64, error -32
[    3.976082] usb 1-4.3: new full-speed USB device number 5 using ehci-pci
[    4.064073] usb 1-4.3: device descriptor read/64, error -32
[    4.256081] usb 1-4.3: device descriptor read/64, error -32
[    4.448331] usb 1-4.3: new full-speed USB device number 6 using ehci-pci
[    4.856017] usb 1-4.3: device not accepting address 6, error -32
[    4.944099] usb 1-4.3: new full-speed USB device number 7 using ehci-pci
[    5.352036] usb 1-4.3: device not accepting address 7, error -32
[    5.352212] hub 1-4:1.0: unable to enumerate USB device on port 3
[    5.681083] usb 8-1.1: new low-speed USB device number 4 using uhci_hcd
[    5.824107] usb 8-1.1: New USB device found, idVendor=046d, idProduct=c221
[    5.824114] usb 8-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.824118] usb 8-1.1: Product: Logitech Gaming Keyboard
[    5.824121] usb 8-1.1: Manufacturer: Logitech
[    5.842239] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.1/8-1.1:1.0/input/input7
[    5.842396] hid-generic 0003:046D:C221.0003: input,hidraw2: USB HID v1.10 Keyboard [Logitech Logitech Gaming Keyboard] on usb-0000:00:1d.2-1.1/input0
[    5.878150] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.1/8-1.1:1.1/input/input8
[    5.878347] hid-generic 0003:046D:C221.0004: input,hiddev0,hidraw3: USB HID v1.10 Device [Logitech Logitech Gaming Keyboard] on usb-0000:00:1d.2-1.1/input1
[    5.953110] usb 8-1.4: new full-speed USB device number 5 using uhci_hcd
[    6.096107] usb 8-1.4: New USB device found, idVendor=046d, idProduct=c222
[    6.096114] usb 8-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.096118] usb 8-1.4: Product: G15 Keyboard
[    6.096121] usb 8-1.4: Manufacturer: G15 Keyboard
[    6.106235] input: G15 Keyboard G15 Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.4/8-1.4:1.0/input/input9
[    6.106403] hid-generic 0003:046D:C222.0005: input,hiddev0,hidraw4: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:1d.2-1.4/input0
[   10.129693] Adding 2146300k swap on /dev/sdd1.  Priority:-1 extents:1 across:2146300k SSFS
[   10.156394] EXT4-fs (sdd2): re-mounted. Opts: errors=remount-ro
[   10.223595] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.308262] systemd-udevd[403]: starting version 208
[   10.367354] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.406887] lp: driver loaded but no devices found
[   10.423808] EXT4-fs (sdd5): mounted filesystem with ordered data mode. Opts: (null)
[   10.457752] ppdev: user-space parallel port driver
[   10.471879] parport_pc 00:08: reported by Plug and Play ACPI
[   10.471930] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.491829] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.526767] [drm] Initialized drm 1.1.0 20060810
[   10.546369] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   10.561194] lp0: using parport0 (interrupt-driven).
[   10.579940] type=1400 audit(1412188913.217:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=525 comm="apparmor_parser"
[   10.579951] type=1400 audit(1412188913.217:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=525 comm="apparmor_parser"
[   10.579959] type=1400 audit(1412188913.217:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=525 comm="apparmor_parser"
[   10.607953] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \GP2C 1 (20131115/utaddress-251)
[   10.607963] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.608019] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.628737] Linux video capture interface: v2.00
[   10.655902] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   10.658359] gspca_main: v2.14.0 registered
[   10.666217] gspca_main: sonixj-2.14.0 probing 045e:00f5
[   10.680448] input: sonixj as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/input/input10
[   10.680736] usbcore: registered new interface driver sonixj
[   10.698182] device-mapper: multipath: version 1.6.0 loaded
[   10.747342] nvidia: module license 'NVIDIA' taints kernel.
[   10.747347] Disabling lock debugging due to kernel taint
[   10.749380] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   10.749548] saa7133[0]: found at 0000:05:01.0, rev: 208, irq: 19, latency: 32, mmio: 0xfa100000
[   10.749555] saa7133[0]: subsystem: 11bd:002f, board: Pinnacle PCTV 310i [card=101,autodetected]
[   10.749570] saa7133[0]: board init: gpio is 600e000
[   10.761141] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   10.771069] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   10.771517] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   10.771531] NVRM: loading NVIDIA UNIX x86 Kernel Module  331.89  Tue Jul  1 12:44:47 PDT 2014
[   10.805618] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   10.840668] SKU: Nid=0x1d sku_cfg=0x4005e601
[   10.840673] SKU: port_connectivity=0x1
[   10.840675] SKU: enable_pcbeep=0x0
[   10.840678] SKU: check_sum=0x00000005
[   10.840680] SKU: customization=0x000000e6
[   10.840682] SKU: external_amp=0x0
[   10.840739] SKU: platform_type=0x0
[   10.840741] SKU: swap=0x0
[   10.840743] SKU: override=0x1
[   10.841493] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   10.841559]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   10.841562]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   10.841564]    mono: mono_out=0x0
[   10.841566]    dig-out=0x1e/0x0
[   10.841568]    inputs:
[   10.841571]      Rear Mic=0x18
[   10.841574]      Front Mic=0x19
[   10.841576]      Line=0x1a
[   10.841578]      CD=0x1c
[   10.841580]    dig-in=0x1f
[   10.841583] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[   10.841586] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0885
[   10.845923] usbcore: registered new interface driver snd-usb-audio
[   10.895213] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   10.895337] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   10.895429] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   10.895520] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   10.895609] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   10.895696] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   10.895785] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.895879] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.900026] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   10.900044] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2c 1b 8d ff ff
[   10.900059] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 31 98 ff 00 a6 ff 21 00 c2
[   10.900073] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff ff 0c 22 17 77 03 1c 8a 1d
[   10.900088] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900102] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900116] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900130] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900144] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900158] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900172] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900187] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900201] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900215] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900229] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.900243] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.043938] tuner 0-004b: Tuner -1 found with type(s) Radio TV.
[   11.066245] coretemp coretemp.0: Using relative temperature scale!
[   11.066273] coretemp coretemp.0: Using relative temperature scale!
[   11.066299] coretemp coretemp.0: Using relative temperature scale!
[   11.066332] coretemp coretemp.0: Using relative temperature scale!
[   11.136049] tda829x 0-004b: setting tuner address to 61
[   11.264893] gpio_ich: GPIO from 195 to 255 on gpio_ich
[   11.288023] tda829x 0-004b: type set to tda8290+75a
[   12.720813] init: Error while reading from descriptor: Broken pipe
[   12.731092] init: failsafe main process (856) killed by TERM signal
[   12.843294] init: samba-ad-dc main process (884) terminated with status 1
[   12.893391] Bluetooth: Core ver 2.17
[   12.893419] NET: Registered protocol family 31
[   12.893422] Bluetooth: HCI device and connection manager initialized
[   12.893431] Bluetooth: HCI socket layer initialized
[   12.893436] Bluetooth: L2CAP socket layer initialized
[   12.893443] Bluetooth: SCO socket layer initialized
[   12.921915] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.921920] Bluetooth: BNEP filters: protocol multicast
[   12.921929] Bluetooth: BNEP socket layer initialized
[   12.932043] Bluetooth: RFCOMM TTY layer initialized
[   12.932057] Bluetooth: RFCOMM socket layer initialized
[   12.932065] Bluetooth: RFCOMM ver 1.11
[   12.946571] type=1400 audit(1412188915.585:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=959 comm="apparmor_parser"
[   12.946583] type=1400 audit(1412188915.585:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=959 comm="apparmor_parser"
[   12.946590] type=1400 audit(1412188915.585:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=959 comm="apparmor_parser"
[   12.985901] init: cups main process (966) killed by HUP signal
[   12.985919] init: cups main process ended, respawning
[   13.014563] type=1400 audit(1412188915.653:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1001 comm="apparmor_parser"
[   13.014575] type=1400 audit(1412188915.653:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1001 comm="apparmor_parser"
[   13.018455] type=1400 audit(1412188915.657:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1001 comm="apparmor_parser"
[   13.018464] type=1400 audit(1412188915.657:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1001 comm="apparmor_parser"
[   13.114425] systemd-logind[1006]: Watching system buttons on /dev/input/event1 (Power Button)
[   13.114551] systemd-logind[1006]: Watching system buttons on /dev/input/event0 (Power Button)
[   13.114602] systemd-logind[1006]: New seat seat0.
[   13.149303] r8169 0000:04:00.0 eth0: link down
[   13.149318] r8169 0000:04:00.0 eth0: link down
[   13.149357] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.542249] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   13.562878] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   13.574202] zram: Created 4 device(s) ...
[   13.586972] zram: Cannot change disksize for initialized device
[   13.607720] Adding 516824k swap on /dev/zram0.  Priority:100 extents:1 across:516824k SSFS
[   13.610372] Adding 516824k swap on /dev/zram1.  Priority:100 extents:1 across:516824k SSFS
[   13.613082] Adding 516824k swap on /dev/zram2.  Priority:100 extents:1 across:516824k SSFS
[   13.615411] Adding 516824k swap on /dev/zram3.  Priority:100 extents:1 across:516824k SSFS
[   13.674920] init: zram-config pre-start process (1182) terminated with status 1
[   13.804573] init: zram-config post-stop process (1347) terminated with status 1
[   13.875172] init: plymouth-upstart-bridge main process ended, respawning
[   13.972845] nvidia 0000:01:00.0: irq 46 for MSI/MSI-X
[   14.092145] usb 1-4.3: new full-speed USB device number 8 using ehci-pci
[   14.180154] usb 1-4.3: device descriptor read/64, error -32
[   14.372145] usb 1-4.3: device descriptor read/64, error -32
[   14.564145] usb 1-4.3: new full-speed USB device number 9 using ehci-pci
[   14.648014] Registered IR keymap rc-pinnacle-color
[   14.648135] input: i2c IR (Pinnacle PCTV) as /devices/virtual/rc/rc0/input19
[   14.648431] rc0: i2c IR (Pinnacle PCTV) as /devices/virtual/rc/rc0
[   14.648433] ir-kbd-i2c: i2c IR (Pinnacle PCTV) detected at i2c-0/0-0047/ir0 [saa7133[0]]
[   14.652332] usb 1-4.3: device descriptor read/64, error -32
[   14.720200] saa7133[0]: registered device video1 [v4l2]
[   14.720334] saa7133[0]: registered device vbi0
[   14.720462] saa7133[0]: registered device radio0
[   14.731160] saa7134 ALSA driver for DMA sound loaded
[   14.731197] saa7133[0]/alsa: saa7133[0] at 0xfa100000 irq 19 registered as card -2
[   14.759666] dvb_init() allocating 1 frontend
[   14.808051] DVB: registering new adapter (saa7133[0])
[   14.808059] saa7134 0000:05:01.0: DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   14.841987] r8169 0000:04:00.0 eth0: link up
[   14.842001] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.844271] usb 1-4.3: device descriptor read/64, error -32
[   15.036524] usb 1-4.3: new full-speed USB device number 10 using ehci-pci
[   15.096178] tda1004x: setting up plls for 48MHz sampling clock
[   15.298595] systemd-logind[1006]: Failed to start unit [EMAIL="user@104.servic"]user@104.servic[/EMAIL]e: Unknown unit: [EMAIL="user@104.servic"]user@104.servic[/EMAIL]e
[   15.298606] systemd-logind[1006]: Failed to start user service: Unknown unit: [EMAIL="user@104.servic"]user@104.servic[/EMAIL]e
[   15.304308] systemd-logind[1006]: New session c1 of user lightdm.
[   15.304336] systemd-logind[1006]: Linked /tmp/.X11-unix/X0 to /run/user/104/X11-display.
[   15.444015] usb 1-4.3: device not accepting address 10, error -32
[   15.536147] usb 1-4.3: new full-speed USB device number 11 using ehci-pci
[   15.944808] usb 1-4.3: device not accepting address 11, error -32
[   15.944911] hub 1-4:1.0: unable to enumerate USB device on port 3
[   16.132340] usb 1-4.3: new full-speed USB device number 12 using ehci-pci
[   16.220089] usb 1-4.3: device descriptor read/64, error -32
[   16.378085] retire_capture_urb: 60 callbacks suppressed
[   16.412094] usb 1-4.3: device descriptor read/64, error -32
[   16.604097] usb 1-4.3: new full-speed USB device number 13 using ehci-pci
[   16.692096] usb 1-4.3: device descriptor read/64, error -32
[   16.884098] usb 1-4.3: device descriptor read/64, error -32
[   17.076095] usb 1-4.3: new full-speed USB device number 14 using ehci-pci
[   17.484017] usb 1-4.3: device not accepting address 14, error -32
[   17.560010] tda1004x: timeout waiting for DSP ready
[   17.572095] usb 1-4.3: new full-speed USB device number 15 using ehci-pci
[   17.600021] tda1004x: found firmware revision 0 -- invalid
[   17.600025] tda1004x: trying to boot from eeprom
[   17.980022] usb 1-4.3: device not accepting address 15, error -32
[   17.980094] hub 1-4:1.0: unable to enumerate USB device on port 3
[   18.504095] usb 1-4.3: new full-speed USB device number 16 using ehci-pci
[   18.592096] usb 1-4.3: device descriptor read/64, error -32
[   18.682395] usb 8-1.4: usbfs: process 2807 (g15daemon) did not claim interface 0 before use
[   18.682433] usb 8-1.4: usbfs: process 2807 (g15daemon) did not claim interface 0 before use
[   18.682441] usb 8-1.4: usbfs: process 2807 (g15daemon) did not claim interface 0 before use
[   18.682447] usb 8-1.4: usbfs: process 2807 (g15daemon) did not claim interface 0 before use
[   18.682667] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.682767] usb 8-1.4: usbfs: process 2807 (g15daemon) did not claim interface 0 before use
[   18.685556] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.685811] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.689196] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.690224] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.690460] input: G15 Extra Keys as /devices/virtual/input/input20
[   18.723413] init: udev-fallback-graphics main process (2818) terminated with status 1
[   18.730309] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.767750] init: plymouth-splash main process (2837) terminated with status 1
[   18.770397] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.784220] usb 1-4.3: device descriptor read/64, error -32
[   18.810482] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.850569] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.890657] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.930742] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.970824] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   18.976098] usb 1-4.3: new full-speed USB device number 17 using ehci-pci
[   19.010906] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   19.050987] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   19.064092] usb 1-4.3: device descriptor read/64, error -32
[   19.091068] usb 8-1.4: usbfs: process 2808 (g15daemon) did not claim interface 0 before use
[   19.152419] /dev/vmmon[2991]: Module vmmon: registered with major=10 minor=165
[   19.152427] /dev/vmmon[2991]: Module vmmon: initialized
[   19.184733] Guest personality initialized and is inactive
[   19.186425] VMCI host device registered (name=vmci, major=10, minor=57)
[   19.186429] Initialized host personality
[   19.236472] NET: Registered protocol family 40
[   19.256134] usb 1-4.3: device descriptor read/64, error -32
[   19.364083] tda1004x: found firmware revision 0 -- invalid
[   19.364089] tda1004x: waiting for firmware upload...
[   19.365461] saa7134 0000:05:01.0: Direct firmware load failed with error -2
[   19.365466] saa7134 0000:05:01.0: Falling back to user helper
[   19.366458] saa7134 0000:05:01.0: Direct firmware load failed with error -2
[   19.366463] saa7134 0000:05:01.0: Falling back to user helper
[   19.367099] tda1004x: no firmware upload (timeout or file not found?)
[   19.367103] tda1004x: firmware upload failed
[   19.442749] /dev/vmnet: open called by PID 3201 (vmnet-bridge)
[   19.442762] /dev/vmnet: hub 0 does not exist, allocating memory.
[   19.442787] /dev/vmnet: port on hub 0 successfully opened
[   19.442801] bridge-eth0: up
[   19.442806] bridge-eth0: attached
[   19.448218] usb 1-4.3: new full-speed USB device number 18 using ehci-pci
[   19.856023] usb 1-4.3: device not accepting address 18, error -32
[   19.944100] usb 1-4.3: new full-speed USB device number 19 using ehci-pci
[   20.352024] usb 1-4.3: device not accepting address 19, error -32
[   20.352099] hub 1-4:1.0: unable to enumerate USB device on port 3
[   20.468207] /dev/vmnet: open called by PID 3238 (vmnet-netifup)
[   20.468219] /dev/vmnet: hub 1 does not exist, allocating memory.
[   20.468243] /dev/vmnet: port on hub 1 successfully opened
[   20.484113] /dev/vmnet: open called by PID 3240 (vmnet-dhcpd)
[   20.484129] /dev/vmnet: port on hub 1 successfully opened
[   20.495605] /dev/vmnet: open called by PID 3244 (vmnet-natd)
[   20.495616] /dev/vmnet: hub 8 does not exist, allocating memory.
[   20.495639] /dev/vmnet: port on hub 8 successfully opened
[   20.497209] userif-3: sent link down event.
[   20.497214] userif-3: sent link up event.
[   20.499902] /dev/vmnet: open called by PID 3245 (vmnet-netifup)
[   20.499916] /dev/vmnet: port on hub 8 successfully opened
[   20.514463] /dev/vmnet: open called by PID 3248 (vmnet-dhcpd)
[   20.514481] /dev/vmnet: port on hub 8 successfully opened
[   21.820696] systemd-logind[1006]: Failed to start unit [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e: Unknown unit: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
[   21.820707] systemd-logind[1006]: Failed to start user service: Unknown unit: [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
[   21.826276] systemd-logind[1006]: New session c2 of user spupuz.
[   21.826303] systemd-logind[1006]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   22.696289] init: plymouth-stop pre-start process (3687) terminated with status 1
[   24.526094] retire_capture_urb: 5 callbacks suppressed
[   36.481156] retire_capture_urb: 5 callbacks suppressed
[   43.618917] audit_printk_skb: 4 callbacks suppressed
[   43.618922] type=1400 audit(1412188946.258:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=5038 comm="apparmor_parser"
[   43.618932] type=1400 audit(1412188946.258:33): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=5038 comm="apparmor_parser"
[   43.628116] type=1400 audit(1412188946.270:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=5038 comm="apparmor_parser"
[   47.489623] systemd-hostnamed[5127]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

---

### Post by SpUpUz on 2014-10-01
```
spupuz@spupuz-EP35C-DS3R:/var/log$ sudo apt-get install --reinstall unity-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package unity-desktop
spupuz@spupuz-EP35C-DS3R:/var/log$
```

---

### Post by zika on 2014-10-01
> **SpUpUz said:**
> ```
sudo apt-get --configure -a
```
There is no option```
--configure
```for```
apt-get
```command, as far as I know. You've probably meant to use```
sudo dpkg --reconfigure -a
```but beware that could last a while.
> **SpUpUz said:**
> ```
sudo apt-get install --reinstall unity-desktop
```There is no package *unity-desktop* as far as I know.
For outputs like these You've gave above do use code-tag as it makes thread much more readable and easier to follow.

---

### Post by QIII on 2014-10-01
SpUpUz --

Please use code tags for terminal output.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.
 
2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by ventrical on 2014-10-01
@SpUpUz

My bad.

See here

[http://ubuntuforums.org/showthread.php?t=1970289&page=6&p=12608357#post12608357](http://ubuntuforums.org/showthread.php?t=1970289&page=6&p=12608357#post12608357)

This apparently will only work for broken packages.

Also it's

```

sudo apt-get install ubuntu-desktop

```

bad day for winging it :)

apologies..

---

### Post by SpUpUz on 2014-10-02
> **QIII said:**
> SpUpUz --

Please use code tags for terminal output.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.
 
2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

ok and sorry :)

---

### Post by SpUpUz on 2014-10-02
> **ventrical said:**
> @SpUpUz

My bad.

See here

[http://ubuntuforums.org/showthread.php?t=1970289&page=6&p=12608357#post12608357](http://ubuntuforums.org/showthread.php?t=1970289&page=6&p=12608357#post12608357)

This apparently will only work for broken packages.

Also it's

```

sudo apt-get install ubuntu-desktop

```

bad day for winging it :)

apologies..

it is not working yet
i think i need to install another grapical interface as gnome?

---

### Post by ventrical on 2014-10-02
> **SpUpUz said:**
> it is not working yet
i think i need to install another grapical interface as gnome?

```


sudo apt-get install gnome-session-flashback


```


When you get to the log-on screen choose (metacity).

Let us know.

Thanks.

---

### Post by ventrical on 2014-10-02
I am curious. Could you try:

```

apt-cache policy policykit-desktop-privileges

```

and post results.

thnxs

---

### Post by SpUpUz on 2014-10-02
> **ventrical said:**
> I am curious. Could you try:

```

apt-cache policy policykit-desktop-privileges

```

and post results.

thnxs

with sudo or without??

---

### Post by ventrical on 2014-10-02
> **SpUpUz said:**
> with sudo or without??

without sudo

---

### Post by SpUpUz on 2014-10-02
> **ventrical said:**
> ```


sudo apt-get install gnome-session-flashback


```


When you get to the log-on screen choose (metacity).

Let us know.

Thanks.

```
policykit-desktop-privileges:
  Installed: 0.19
  Candidate: 0.19
  Version table:
 *** 0.19 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/main i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by ventrical on 2014-10-02
Did you install gnome-session-flashback?

To choose you have to click the icon in lighdm which is next to the password field. By default it is the little ubuntu circle logo. When you click that you will see the gnome desktop options.

---

### Post by SpUpUz on 2014-10-02
> **ventrical said:**
> Did you install gnome-session-flashback?

To choose you have to click the icon in lighdm which is next to the password field. By default it is the little ubuntu circle logo. When you click that you will see the gnome desktop options.

just logged in with gnome fallback session it does not change anything :/ dunno..... is there any log i can collect?

---

### Post by ventrical on 2014-10-02
here is screenshot

edit:

Ok .. I see you posted while I was posting .

Belay my last. :)

---

### Post by SpUpUz on 2014-10-02
> **ventrical said:**
> here is screenshot

yeah i logged in as gnome fall back i'm quite expert linux user but still has the problem

---

### Post by ventrical on 2014-10-02
> **SpUpUz said:**
> just logged in with gnome fallback session it does not change anything :/ dunno..... is there any log i can collect?


Ok... looks like there is a larger problem. I am assuming something happened to the polkit or other depend when you upgraded.

---

### Post by SpUpUz on 2014-10-02
> **ventrical said:**
> Ok... looks like there is a larger problem. I am assuming something happened to the polkit or other depend when you upgraded.

any other suggestion?

---

### Post by ventrical on 2014-10-02
> **SpUpUz said:**
> any other suggestion?

I'll let someone else reply but I would try installing 'synaptic' if you haven't already and see if it can identify any broken packages.

```

sudo apt-get install synaptic

```

In your original message "operation not permitted" it suggests that something has not been -chown(ed) in user permissions. You also mentioned depends problems. Synaptic should be able to recognize missing. Aptitude is another great tools for resolving busted systems but it is usually good to have them installed before the bork happens.

As you mentioned .. you are expert in linux... so I doubt there is anything I have to offer in reference to a concrete solution.

One thing to note.. if you decide to re-install .. that since trusty tahr, ubiquity installer now has ability to transfer all settings and files .. however .. it may also migrate the broken depend no-policy-kit also.

Regards..

---

### Post by ventrical on 2014-10-02
This is the log of the last update. Tt only goes back to the most recent. It is not a consecutive log.

```

gedit /var/log/apt/history.log

```

---

### Post by ventrical on 2014-10-02
In fact all the upgrade/update history logs are saved.

---

### Post by SpUpUz on 2014-10-03
> **ventrical said:**
> I'll let someone else reply but I would try installing 'synaptic' if you haven't already and see if it can identify any broken packages.

```

sudo apt-get install synaptic

```

In your original message "operation not permitted" it suggests that something has not been -chown(ed) in user permissions. You also mentioned depends problems. Synaptic should be able to recognize missing. Aptitude is another great tools for resolving busted systems but it is usually good to have them installed before the bork happens.

As you mentioned .. you are expert in linux... so I doubt there is anything I have to offer in reference to a concrete solution.

One thing to note.. if you decide to re-install .. that since trusty tahr, ubiquity installer now has ability to transfer all settings and files .. however .. it may also migrate the broken depend no-policy-kit also.

Regards..

what about reinstalling but maintaining home partition?

---

### Post by ventrical on 2014-10-03
> **SpUpUz said:**
> what about reinstalling but maintaining home partition?

Someone else may have another idea but from my experience you always have to mark the partition as root '/' during a re-install. Just do not choose format. It should re-install with all your settings/files.. etc.. but , remember .. this cycle is still in testing/development. 

  You could try to install  trusty to the same partiton , automatically saving settings and files but you still have to mark it as root '/' and do not choose format.

  It has worked for me in practice on a few occasions but one time it also migrated policy bug and I could not get into original account but the new account gave me access to files and settings of the former username that had policy-kit issues.

btw... what type of pc are you running

```


lspci


```

no sudo required..

---

### Post by SpUpUz on 2014-10-03
here is the output

```
spupuz@spupuz-EP35C-DS3R:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 8800 GTS 512] (rev a2)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 01)
05:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
spupuz@spupuz-EP35C-DS3R:~$
```

---

### Post by ventrical on 2014-10-03
One of my systems is near identical.

```

ventrical@asus:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
02:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
04:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
ventrical@asus:~$ 

```

I use it for overclocking Core 2s, Quads and Pentium D's. Currently running trusty and utopic(unity-next with ubuntu-desktop) partitions with no problem. Only prob .. unity8. Otherwise very solid.

---

### Post by SpUpUz on 2014-10-03
is there a log where i can find errors tide to policykit or something related?

---

### Post by ventrical on 2014-10-04
> **SpUpUz said:**
> is there a log where i can find errors tide to policykit or something related?

Not that I know  of off hand. Your particular pc problem stemmed from the upgrade and  if something went wrong in the upgrade processes it should be in the history.logs

```

/var/log/apt/history.log


```

Are you able to add a new user from /system settings/user accounts  in the GUI ?

edit:

You could also try to look at your recent dpkg.logs in /var/log/ or your term.logs in /var/log/apt

regards..

---

### Post by SpUpUz on 2014-10-04
> **ventrical said:**
> Not that I know  of off hand. Your particular pc problem stemmed from the upgrade and  if something went wrong in the upgrade processes it should be in the history.logs

```

/var/log/apt/history.log


```

**Are you able to add a new user from /system settings/user accounts  in the GUI ?**

edit:

You could also try to look at your recent dpkg.logs in /var/log/ or your term.logs in /var/log/apt

regards..

no i'm not able to add a new user from the gui.

---

### Post by ventrical on 2014-10-04
Just seen this old thread here.

[http://askubuntu.com/questions/371427/lost-privileges-since-upgrading-to-13-10](http://askubuntu.com/questions/371427/lost-privileges-since-upgrading-to-13-10)

I assume you are logging on from lightdm?

---

### Post by ventrical on 2014-10-04
I have a couple of extra hdds with 14.04 on them.  I am going to try and see if I can emulate what happened to your install by using the same command that you did.

here goes ..

---

### Post by ventrical on 2014-10-04
here's the first part..

```

ventrical@ventrical-desktop:~$ sudo do-release-upgrade -d
[sudo] password for ventrical: 
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,143 kB]                                                  
Fetched 1,143 kB in 0s (0 B/s)                                                 
authenticate 'utopic.tar.gz' against 'utopic.tar.gz.gpg' 
extracting 'utopic.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Ign http://archive.ubuntu.com trusty-backports InRelease                       
Ign http://archive.ubuntu.com trusty-security InRelease                        
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://archive.ubuntu.com trusty Release.gpg                               
Get:1 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Get:2 http://archive.ubuntu.com trusty-backports Release.gpg [933 B]           
Hit http://extras.ubuntu.com trusty Release.gpg                                
Get:3 http://archive.ubuntu.com trusty-security Release.gpg [933 B]            
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://extras.ubuntu.com trusty Release                                    
Get:4 http://archive.ubuntu.com trusty-updates Release [59.7 kB]               
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:5 http://archive.ubuntu.com trusty-backports Release [59.7 kB]             
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:6 http://archive.ubuntu.com trusty-security Release [59.7 kB]              
Err http://extras.ubuntu.com trusty/main Translation-en_CA                     
                                                                               
Hit http://archive.ubuntu.com trusty/main Sources                              
Err http://extras.ubuntu.com trusty/main Translation-en                        
                                                                               
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.ubuntu.com trusty/universe Sources                          
Err http://extras.ubuntu.com trusty/main Translation-en_CA                     
                                                                               
Hit http://archive.ubuntu.com trusty/multiverse Sources                        
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Err http://extras.ubuntu.com trusty/main Translation-en                        
                                                                               
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Err http://extras.ubuntu.com trusty/main Translation-en_CA                     
                                                                               
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Hit http://archive.ubuntu.com trusty/main Translation-en_CA                    
Err http://extras.ubuntu.com trusty/main Translation-en                        
                                                                               
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Err http://archive.ubuntu.com trusty/multiverse Translation-en_CA              
                                                                               
Err http://extras.ubuntu.com trusty/main Translation-en_CA                     
                                                                               
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Err http://archive.ubuntu.com trusty/restricted Translation-en_CA              
                                                                               
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Err http://extras.ubuntu.com trusty/main Translation-en                        
                                                                               
Hit http://archive.ubuntu.com trusty/universe Translation-en_CA                
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://extras.ubuntu.com trusty/main Translation-en_CA                     
Get:7 http://archive.ubuntu.com trusty-updates/main Sources [125 kB]           
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:8 http://archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]    
Get:9 http://archive.ubuntu.com trusty-updates/universe Sources [86.2 kB]      
Get:10 http://archive.ubuntu.com trusty-updates/multiverse Sources [3,531 B]   
Get:11 http://archive.ubuntu.com trusty-updates/main i386 Packages [331 kB]    
Get:12 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:13 http://archive.ubuntu.com trusty-updates/universe i386 Packages [209 kB]
Get:14 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,532 B]
Get:15 http://archive.ubuntu.com trusty-updates/main Translation-en [150 kB]   
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Get:16 http://archive.ubuntu.com trusty-backports/main Sources [4,760 B]       
Get:17 http://archive.ubuntu.com trusty-backports/restricted Sources [14 B]    
Get:18 http://archive.ubuntu.com trusty-backports/universe Sources [14.1 kB]   
Get:19 http://archive.ubuntu.com trusty-backports/multiverse Sources [1,315 B] 
Get:20 http://archive.ubuntu.com trusty-backports/main i386 Packages [6,379 B] 
Get:21 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:22 http://archive.ubuntu.com trusty-backports/universe i386 Packages [17.4 kB]
Get:23 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [945 B]
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Get:24 http://archive.ubuntu.com trusty-backports/universe Translation-en [14.6 kB]
Get:25 http://archive.ubuntu.com trusty-security/main Sources [46.3 kB]        
Get:26 http://archive.ubuntu.com trusty-security/restricted Sources [14 B]     
Get:27 http://archive.ubuntu.com trusty-security/universe Sources [10.8 kB]    
Get:28 http://archive.ubuntu.com trusty-security/multiverse Sources [700 B]    
Get:29 http://archive.ubuntu.com trusty-security/main i386 Packages [139 kB]   
Get:30 http://archive.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:31 http://archive.ubuntu.com trusty-security/universe i386 Packages [49.0 kB]
Get:32 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Err http://archive.ubuntu.com trusty/multiverse Translation-en_CA              
                                                                               
Err http://archive.ubuntu.com trusty/restricted Translation-en_CA              
                                                                               
Err http://archive.ubuntu.com trusty/multiverse Translation-en_CA              
                                                                               
Err http://archive.ubuntu.com trusty/restricted Translation-en_CA              
                                                                               
Err http://archive.ubuntu.com trusty/multiverse Translation-en_CA              
                                                                               
Err http://archive.ubuntu.com trusty/restricted Translation-en_CA              
                                                                               
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_CA              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_CA              
Fetched 1,410 kB in 6s (15.7 MB/s)                                             
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
Ign http://archive.ubuntu.com utopic InRelease                                 
Ign http://archive.ubuntu.com utopic-updates InRelease                         
Ign http://archive.ubuntu.com utopic-backports InRelease                       
Ign http://extras.ubuntu.com utopic InRelease                                  
Ign http://archive.ubuntu.com utopic-security InRelease                        
Get:1 http://archive.ubuntu.com utopic Release.gpg [933 B]                     
Get:2 http://archive.ubuntu.com utopic-updates Release.gpg [933 B]             
Get:3 http://extras.ubuntu.com utopic Release.gpg [72 B]                       
Get:4 http://archive.ubuntu.com utopic-backports Release.gpg [933 B]           
Get:5 http://archive.ubuntu.com utopic-security Release.gpg [933 B]            
Get:6 http://extras.ubuntu.com utopic Release [14.0 kB]                        
Get:7 http://archive.ubuntu.com utopic Release [112 kB]                        
Get:8 http://extras.ubuntu.com utopic/main Sources [14 B]                      
Get:9 http://extras.ubuntu.com utopic/main i386 Packages [14 B]                
Get:10 http://archive.ubuntu.com utopic-updates Release [58.5 kB]              
Err http://extras.ubuntu.com utopic/main Translation-en_CA                     
                                                                               
Get:11 http://archive.ubuntu.com utopic-backports Release [58.6 kB]            
Err http://extras.ubuntu.com utopic/main Translation-en                        
                                                                               
Get:12 http://archive.ubuntu.com utopic-security Release [58.5 kB]             
Err http://extras.ubuntu.com utopic/main Translation-en_CA                     
                                                                               
Get:13 http://archive.ubuntu.com utopic/main Sources [1,048 kB]                
Err http://extras.ubuntu.com utopic/main Translation-en                        
                                                                               
Err http://extras.ubuntu.com utopic/main Translation-en_CA                     
                                                                               
Err http://extras.ubuntu.com utopic/main Translation-en                        
                                                                               
Err http://extras.ubuntu.com utopic/main Translation-en_CA                     
                                                                               
Err http://extras.ubuntu.com utopic/main Translation-en                        
                                                                               
Ign http://extras.ubuntu.com utopic/main Translation-en_CA                     
Ign http://extras.ubuntu.com utopic/main Translation-en                        
Get:14 http://archive.ubuntu.com utopic/restricted Sources [5,133 B]           
Get:15 http://archive.ubuntu.com utopic/universe Sources [6,744 kB]            
Get:16 http://archive.ubuntu.com utopic/multiverse Sources [171 kB]            
Get:17 http://archive.ubuntu.com utopic/main i386 Packages [1,340 kB]          
Get:18 http://archive.ubuntu.com utopic/restricted i386 Packages [12.5 kB]     
Get:19 http://archive.ubuntu.com utopic/universe i386 Packages [6,190 kB]      
Get:20 http://archive.ubuntu.com utopic/multiverse i386 Packages [133 kB]      
Get:21 http://archive.ubuntu.com utopic/main Translation-en_CA [584 kB]        
Get:22 http://archive.ubuntu.com utopic/main Translation-en [771 kB]           
Get:23 http://archive.ubuntu.com utopic/multiverse Translation-en [100 kB]     
Get:24 http://archive.ubuntu.com utopic/restricted Translation-en [3,315 B]    
Get:25 http://archive.ubuntu.com utopic/universe Translation-en_CA [3,552 kB]  
Get:26 http://archive.ubuntu.com utopic/universe Translation-en [4,264 kB]     
Get:27 http://archive.ubuntu.com utopic-updates/main Sources [14 B]            
Get:28 http://archive.ubuntu.com utopic-updates/restricted Sources [14 B]      
Get:29 http://archive.ubuntu.com utopic-updates/universe Sources [14 B]        
Get:30 http://archive.ubuntu.com utopic-updates/multiverse Sources [14 B]      
Get:31 http://archive.ubuntu.com utopic-updates/main i386 Packages [14 B]      
Get:32 http://archive.ubuntu.com utopic-updates/restricted i386 Packages [14 B]
Get:33 http://archive.ubuntu.com utopic-updates/universe i386 Packages [14 B]  
Get:34 http://archive.ubuntu.com utopic-updates/multiverse i386 Packages [14 B]
Err http://archive.ubuntu.com utopic-updates/main Translation-en_CA            
                                                                               
Get:35 http://archive.ubuntu.com utopic-updates/main Translation-en [14 B]     
Err http://archive.ubuntu.com utopic-updates/multiverse Translation-en_CA      
                                                                               
Get:36 http://archive.ubuntu.com utopic-updates/multiverse Translation-en [14 B]
Err http://archive.ubuntu.com utopic-updates/restricted Translation-en_CA      
                                                                               
Get:37 http://archive.ubuntu.com utopic-updates/restricted Translation-en [14 B]
Err http://archive.ubuntu.com utopic-updates/universe Translation-en_CA        
                                                                               
Get:38 http://archive.ubuntu.com utopic-updates/universe Translation-en [14 B] 
Get:39 http://archive.ubuntu.com utopic-backports/main Sources [14 B]          
Get:40 http://archive.ubuntu.com utopic-backports/restricted Sources [14 B]    
Get:41 http://archive.ubuntu.com utopic-backports/universe Sources [14 B]      
Get:42 http://archive.ubuntu.com utopic-backports/multiverse Sources [14 B]    
Get:43 http://archive.ubuntu.com utopic-backports/main i386 Packages [14 B]    
Get:44 http://archive.ubuntu.com utopic-backports/restricted i386 Packages [14 B]
Get:45 http://archive.ubuntu.com utopic-backports/universe i386 Packages [14 B]
Get:46 http://archive.ubuntu.com utopic-backports/multiverse i386 Packages [14 B]
Err http://archive.ubuntu.com utopic-backports/main Translation-en_CA          
                                                                               
Get:47 http://archive.ubuntu.com utopic-backports/main Translation-en [14 B]   
Err http://archive.ubuntu.com utopic-backports/multiverse Translation-en_CA    
                                                                               
Get:48 http://archive.ubuntu.com utopic-backports/multiverse Translation-en [14 B]
Err http://archive.ubuntu.com utopic-backports/restricted Translation-en_CA    
                                                                               
Get:49 http://archive.ubuntu.com utopic-backports/restricted Translation-en [14 B]
Err http://archive.ubuntu.com utopic-backports/universe Translation-en_CA      
                                                                               
Get:50 http://archive.ubuntu.com utopic-backports/universe Translation-en [14 B]
Get:51 http://archive.ubuntu.com utopic-security/main Sources [14 B]           
Get:52 http://archive.ubuntu.com utopic-security/restricted Sources [14 B]     
Get:53 http://archive.ubuntu.com utopic-security/universe Sources [14 B]       
Get:54 http://archive.ubuntu.com utopic-security/multiverse Sources [14 B]     
Get:55 http://archive.ubuntu.com utopic-security/main i386 Packages [14 B]     
Get:56 http://archive.ubuntu.com utopic-security/restricted i386 Packages [14 B]
Get:57 http://archive.ubuntu.com utopic-security/universe i386 Packages [14 B] 
Get:58 http://archive.ubuntu.com utopic-security/multiverse i386 Packages [14 B]
Err http://archive.ubuntu.com utopic-security/main Translation-en_CA           
                                                                               
Get:59 http://archive.ubuntu.com utopic-security/main Translation-en [14 B]    
Err http://archive.ubuntu.com utopic-security/multiverse Translation-en_CA     
                                                                               
Get:60 http://archive.ubuntu.com utopic-security/multiverse Translation-en [14 B]
Err http://archive.ubuntu.com utopic-security/restricted Translation-en_CA     
                                                                               
Get:61 http://archive.ubuntu.com utopic-security/restricted Translation-en [14 B]
Err http://archive.ubuntu.com utopic-security/universe Translation-en_CA       
                                                                               
Get:62 http://archive.ubuntu.com utopic-security/universe Translation-en [14 B]
Err http://archive.ubuntu.com utopic-updates/main Translation-en_CA            
                                                                               
Err http://archive.ubuntu.com utopic-updates/multiverse Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-updates/restricted Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-updates/universe Translation-en_CA        
                                                                               
Err http://archive.ubuntu.com utopic-backports/main Translation-en_CA          
                                                                               
Err http://archive.ubuntu.com utopic-backports/multiverse Translation-en_CA    
                                                                               
Err http://archive.ubuntu.com utopic-backports/restricted Translation-en_CA    
                                                                               
Err http://archive.ubuntu.com utopic-backports/universe Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-security/main Translation-en_CA           
                                                                               
Err http://archive.ubuntu.com utopic-security/multiverse Translation-en_CA     
                                                                               
Err http://archive.ubuntu.com utopic-security/restricted Translation-en_CA     
                                                                               
Err http://archive.ubuntu.com utopic-security/universe Translation-en_CA       
                                                                               
Err http://archive.ubuntu.com utopic-updates/main Translation-en_CA            
                                                                               
Err http://archive.ubuntu.com utopic-updates/multiverse Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-updates/restricted Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-updates/universe Translation-en_CA        
                                                                               
Err http://archive.ubuntu.com utopic-backports/main Translation-en_CA          
                                                                               
Err http://archive.ubuntu.com utopic-backports/multiverse Translation-en_CA    
                                                                               
Err http://archive.ubuntu.com utopic-backports/restricted Translation-en_CA    
                                                                               
Err http://archive.ubuntu.com utopic-backports/universe Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-security/main Translation-en_CA           
                                                                               
Err http://archive.ubuntu.com utopic-security/multiverse Translation-en_CA     
                                                                               
Err http://archive.ubuntu.com utopic-security/restricted Translation-en_CA     
                                                                               
Err http://archive.ubuntu.com utopic-security/universe Translation-en_CA       
                                                                               
Err http://archive.ubuntu.com utopic-updates/main Translation-en_CA            
                                                                               
Err http://archive.ubuntu.com utopic-updates/multiverse Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-updates/restricted Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-updates/universe Translation-en_CA        
                                                                               
Err http://archive.ubuntu.com utopic-backports/main Translation-en_CA          
                                                                               
Err http://archive.ubuntu.com utopic-backports/multiverse Translation-en_CA    
                                                                               
Err http://archive.ubuntu.com utopic-backports/restricted Translation-en_CA    
                                                                               
Err http://archive.ubuntu.com utopic-backports/universe Translation-en_CA      
                                                                               
Err http://archive.ubuntu.com utopic-security/main Translation-en_CA           
                                                                               
Err http://archive.ubuntu.com utopic-security/multiverse Translation-en_CA     
                                                                               
Err http://archive.ubuntu.com utopic-security/restricted Translation-en_CA     
                                                                               
Err http://archive.ubuntu.com utopic-security/universe Translation-en_CA       
                                                                               
Ign http://archive.ubuntu.com utopic-updates/main Translation-en_CA            
Ign http://archive.ubuntu.com utopic-updates/multiverse Translation-en_CA      
Ign http://archive.ubuntu.com utopic-updates/restricted Translation-en_CA      
Ign http://archive.ubuntu.com utopic-updates/universe Translation-en_CA        
Ign http://archive.ubuntu.com utopic-backports/main Translation-en_CA          
Ign http://archive.ubuntu.com utopic-backports/multiverse Translation-en_CA    
Ign http://archive.ubuntu.com utopic-backports/restricted Translation-en_CA    
Ign http://archive.ubuntu.com utopic-backports/universe Translation-en_CA      
Ign http://archive.ubuntu.com utopic-security/main Translation-en_CA           
Ign http://archive.ubuntu.com utopic-security/multiverse Translation-en_CA     
Ign http://archive.ubuntu.com utopic-security/restricted Translation-en_CA     
Ign http://archive.ubuntu.com utopic-security/universe Translation-en_CA       
Fetched 25.2 MB in 6s (292 kB/s)                                               

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Do you want to start the upgrade? 


21 packages are going to be removed. 208 new packages are going to be 
installed. 1364 packages are going to be upgraded. 

You have to download a total of 723 M. This download will take about 
30 minutes with your connection. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be canceled. 

 Continue [yN]  Details [d]

```


Look at all the errors in the repos..

here goes .. onward and upwards :)

---

### Post by ventrical on 2014-10-04
Upgrade done!

Results .. same as you. Mabey I can find out why now.

---

### Post by ventrical on 2014-10-04
Tried to reload:

---

### Post by ventrical on 2014-10-04
and...

```

ventrical@ventrical-desktop:~$ sudo -i
[sudo] password for ventrical: 
root@ventrical-desktop:~# sudo apt-get update
Ign http://archive.ubuntu.com utopic InRelease
Ign http://archive.ubuntu.com utopic-updates InRelease
Ign http://archive.ubuntu.com utopic-backports InRelease
Ign http://extras.ubuntu.com utopic InRelease
Ign http://archive.ubuntu.com utopic-security InRelease
Get:1 http://archive.ubuntu.com utopic Release.gpg [933 B]
Hit http://archive.ubuntu.com utopic-updates Release.gpg  
Hit http://extras.ubuntu.com utopic Release.gpg
Hit http://archive.ubuntu.com utopic-backports Release.gpg
Hit http://archive.ubuntu.com utopic-security Release.gpg
Hit http://extras.ubuntu.com utopic Release
Get:2 http://archive.ubuntu.com utopic Release [112 kB]
Hit http://extras.ubuntu.com utopic/main Sources       
Hit http://extras.ubuntu.com utopic/main i386 Packages                  
Hit http://archive.ubuntu.com utopic-updates Release           
Hit http://archive.ubuntu.com utopic-backports Release                 
Hit http://archive.ubuntu.com utopic-security Release                  
Get:3 http://archive.ubuntu.com utopic/main Sources [1,048 kB]         
Ign http://extras.ubuntu.com utopic/main Translation-en_CA
Ign http://extras.ubuntu.com utopic/main Translation-en  
Get:4 http://archive.ubuntu.com utopic/restricted Sources [5,133 B]
Get:5 http://archive.ubuntu.com utopic/universe Sources [6,744 kB]
Get:6 http://archive.ubuntu.com utopic/multiverse Sources [171 kB]             
Get:7 http://archive.ubuntu.com utopic/main i386 Packages [1,340 kB]           
Get:8 http://archive.ubuntu.com utopic/restricted i386 Packages [12.5 kB]      
Get:9 http://archive.ubuntu.com utopic/universe i386 Packages [6,190 kB]       
Get:10 http://archive.ubuntu.com utopic/multiverse i386 Packages [133 kB]      
Hit http://archive.ubuntu.com utopic/main Translation-en_CA                    
Hit http://archive.ubuntu.com utopic/main Translation-en                       
Hit http://archive.ubuntu.com utopic/multiverse Translation-en                 
Hit http://archive.ubuntu.com utopic/restricted Translation-en                
Hit http://archive.ubuntu.com utopic/universe Translation-en_CA                
Hit http://archive.ubuntu.com utopic/universe Translation-en               
Hit http://archive.ubuntu.com utopic-updates/main Sources                      
Hit http://archive.ubuntu.com utopic-updates/restricted Sources                
Hit http://archive.ubuntu.com utopic-updates/universe Sources                  
Hit http://archive.ubuntu.com utopic-updates/multiverse Sources                
Hit http://archive.ubuntu.com utopic-updates/main i386 Packages              
Hit http://archive.ubuntu.com utopic-updates/restricted i386 Packages        
Hit http://archive.ubuntu.com utopic-updates/universe i386 Packages          
Hit http://archive.ubuntu.com utopic-updates/multiverse i386 Packages        
Hit http://archive.ubuntu.com utopic-updates/main Translation-en             
Hit http://archive.ubuntu.com utopic-updates/multiverse Translation-en       
Hit http://archive.ubuntu.com utopic-updates/restricted Translation-en       
Hit http://archive.ubuntu.com utopic-updates/universe Translation-en         
Hit http://archive.ubuntu.com utopic-backports/main Sources                  
Hit http://archive.ubuntu.com utopic-backports/restricted Sources              
Hit http://archive.ubuntu.com utopic-backports/universe Sources           
Hit http://archive.ubuntu.com utopic-backports/multiverse Sources         
Hit http://archive.ubuntu.com utopic-backports/main i386 Packages         
Hit http://archive.ubuntu.com utopic-backports/restricted i386 Packages   
Hit http://archive.ubuntu.com utopic-backports/universe i386 Packages     
Hit http://archive.ubuntu.com utopic-backports/multiverse i386 Packages   
Hit http://archive.ubuntu.com utopic-backports/main Translation-en        
Hit http://archive.ubuntu.com utopic-backports/multiverse Translation-en  
Hit http://archive.ubuntu.com utopic-backports/restricted Translation-en  
Hit http://archive.ubuntu.com utopic-backports/universe Translation-en    
Hit http://archive.ubuntu.com utopic-security/main Sources                
Hit http://archive.ubuntu.com utopic-security/restricted Sources          
Hit http://archive.ubuntu.com utopic-security/universe Sources            
Hit http://archive.ubuntu.com utopic-security/multiverse Sources               
Hit http://archive.ubuntu.com utopic-security/main i386 Packages               
Hit http://archive.ubuntu.com utopic-security/restricted i386 Packages         
Hit http://archive.ubuntu.com utopic-security/universe i386 Packages           
Hit http://archive.ubuntu.com utopic-security/multiverse i386 Packages         
Hit http://archive.ubuntu.com utopic-security/main Translation-en              
Hit http://archive.ubuntu.com utopic-security/multiverse Translation-en        
Hit http://archive.ubuntu.com utopic-security/restricted Translation-en        
Hit http://archive.ubuntu.com utopic-security/universe Translation-en          
Ign http://archive.ubuntu.com utopic-updates/main Translation-en_CA            
Ign http://archive.ubuntu.com utopic-updates/multiverse Translation-en_CA      
Ign http://archive.ubuntu.com utopic-updates/restricted Translation-en_CA      
Ign http://archive.ubuntu.com utopic-updates/universe Translation-en_CA        
Ign http://archive.ubuntu.com utopic-backports/main Translation-en_CA          
Ign http://archive.ubuntu.com utopic-backports/multiverse Translation-en_CA    
Ign http://archive.ubuntu.com utopic-backports/restricted Translation-en_CA    
Ign http://archive.ubuntu.com utopic-backports/universe Translation-en_CA      
Ign http://archive.ubuntu.com utopic-security/main Translation-en_CA           
Ign http://archive.ubuntu.com utopic-security/multiverse Translation-en_CA     
Ign http://archive.ubuntu.com utopic-security/restricted Translation-en_CA     
Ign http://archive.ubuntu.com utopic-security/universe Translation-en_CA       
Fetched 15.8 MB in 46s (340 kB/s)                                              
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ventrical-desktop:~# 

```

---

### Post by ventrical on 2014-10-04
..so it is updating now ..

```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ventrical-desktop:~# sudo dpkg --configure -a
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-20-generic
Setting up python3-aptdaemon (1.1.1+bzr980-0ubuntu1) ...
Setting up python3-pyparsing (2.0.2+dfsg1-1) ...
Setting up lsb-release (4.1+Debian11ubuntu8) ...
Processing triggers for libgdk-pixbuf2.0-0:i386 (2.30.8-1) ...
Setting up gedit (3.10.4-0ubuntu5) ...
update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode
Setting up python3-speechd (0.8-6ubuntu2) ...
Processing triggers for dbus (1.8.8-1ubuntu2) ...
Setting up ibus-pinyin (1.5.0-3ubuntu1) ...
Setting up gnome-sudoku (1:3.12.3-0ubuntu1) ...
Setting up python3-crypto (2.6.1-5) ...
Setting up python3-louis (2.5.3-3) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu3) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up python3-pyatspi (2.12.0+dfsg-3) ...
Processing triggers for dictionaries-common (1.23.11) ...
Setting up transmission-gtk (2.82-1.1ubuntu4) ...
Setting up python3-lxml (3.3.6-0ubuntu1) ...
Setting up python3-gdbm:i386 (3.4.2~rc1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up python3-brlapi (5.0-2ubuntu3) ...
Setting up overlay-scrollbar-gtk2:i386 (0.2.16+r359+14.10.20140625-0ubuntu1) ...
Setting up aptdaemon (1.1.1+bzr980-0ubuntu1) ...
Setting up perl (5.20.0-6) ...
Setting up python3-problem-report (2.14.7-0ubuntu3) ...
Setting up python3-httplib2 (0.9+dfsg-1) ...
Setting up libcairo-perl (1.104-1build1) ...
Setting up libtext-template-perl (1.46-1) ...
Setting up libio-pty-perl (1:1.08-1build5) ...
Setting up libsub-name-perl (0.07-1build1) ...
Setting up xul-ext-ubufox (2.9-0ubuntu1) ...
Setting up liblog-message-perl (0.8-1) ...
Setting up ubuntu-drivers-common (1:0.2.98.3) ...
Installing new version of config file /etc/init/gpu-manager.conf ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...
Setting up libnss3:i386 (2:3.17.1-0ubuntu1) ...
Setting up firefox (32.0.3+build1-0ubuntu1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up libnet-libidn-perl (0.12.ds-2build1) ...
Setting up python-commandnotfound (0.3ubuntu14) ...
Setting up libclone-perl (0.37-1build1) ...
Setting up libtext-levenshtein-perl (0.09-1) ...
Setting up patchutils (0.3.3-1) ...
Setting up liblist-moreutils-perl (0.33-2build1) ...
Setting up apparmor (2.8.96~2652-0ubuntu7) ...
update-rc.d: warning: start ...etc..


```

and that finished successfully..

```

...
Setting up account-plugin-ubuntuone (14.04+14.10.20140910) ...
Setting up python3-update-manager (1:14.10.6) ...
Setting up liblwp-protocol-https-perl (6.06-2) ...
Setting up python3-distupgrade (1:14.10.7) ...
Setting up libwww-perl (6.08-1) ...
Setting up libxml-parser-perl (2.41-3) ...
Setting up ubuntu-release-upgrader-core (1:14.10.7) ...
Installing new version of config file /etc/update-manager/release-upgrades ...
Setting up libsoap-lite-perl (1.11-1) ...
Setting up ubuntu-release-upgrader-gtk (1:14.10.7) ...
Setting up update-manager-core (1:14.10.6) ...
Setting up update-notifier (3.157) ...
Setting up update-manager (1:14.10.6) ...
Setting up ubuntu-desktop (1.327) ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-20-generic
root@ventrical-desktop:~# 

```

..now to reboot and try USB..

---

### Post by ventrical on 2014-10-04
problem now fixed .. usb working .. policy kit also

..I got to get some sleep..

the same process should work for you

```


sudo - i

```

that will put you in root.. then

```

sudo dpkg --configure -a


```

Regards..

---

### Post by SpUpUz on 2014-10-05
> **ventrical said:**
> problem now fixed .. usb working .. policy kit also

..I got to get some sleep..

the same process should work for you

```


sudo - i

```

that will put you in root.. then

```

sudo dpkg --configure -a


```

Regards..

i have no broken processes and s```
udo dpkg-reconfigure -a
``` is not working also i have no luck doing ```
sudo dpkg-reconfigure lightdm
```

looking at the dmes i got some error like that one:

```
[   23.046801] systemd-logind[720]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   23.046812] systemd-logind[720]: Failed to start user service: Unknown unit: user@1000.service

```

take a look to the whole dmesg output:

```
[    0.858984] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.858987] EDD information not available.
[    0.859032] PM: Hibernation image not present or could not be loaded.
[    1.128155] isapnp: No Plug & Play device found
[    1.280056] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.280161] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.288577] ata4.00: ATA-8: OCZ-AGILITY3, 2.15, max UDMA/133
[    1.288582] ata4.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.315653] ata3.00: ATA-8: ST31500341AS, CC1H, max UDMA/133
[    1.315657] ata3.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.320492] ata4.00: configured for UDMA/133
[    1.371582] ata3.00: configured for UDMA/133
[    1.392031] usb 1-4: new high-speed USB device number 3 using ehci-pci
[    1.524320] usb 1-4: New USB device found, idVendor=0409, idProduct=0059
[    1.524324] usb 1-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.524610] hub 1-4:1.0: USB hub found
[    1.524689] hub 1-4:1.0: 4 ports detected
[    1.600068] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.600080] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.609083] ata2.00: ATA-7: Maxtor 6L200M0, BACE1G20, max UDMA/133
[    1.609087] ata2.00: 398297088 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    1.625115] ata2.00: configured for UDMA/133
[    1.732018] tsc: Refined TSC clocksource calibration: 2399.999 MHz
[    1.824061] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.824073] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.832294] ata1.00: HPA detected: current 240119615, native 240121728
[    1.832299] ata1.00: ATA-7: Maxtor 6Y120M0, YAR51EW0, max UDMA/133
[    1.832303] ata1.00: 240119615 sectors, multi 0: LBA 
[    1.848309] ata1.00: configured for UDMA/133
[    1.848471] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y120M0   YAR5 PQ: 0 ANSI: 5
[    1.848655] sd 0:0:0:0: [sda] 240119615 512-byte logical blocks: (122 GB/114 GiB)
[    1.848674] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.848719] sd 0:0:0:0: [sda] Write Protect is off
[    1.848723] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.848753] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.848860] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6L200M0   BACE PQ: 0 ANSI: 5
[    1.849082] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.849124] sd 1:0:0:0: [sdb] 398297088 512-byte logical blocks: (203 GB/189 GiB)
[    1.849201] sd 1:0:0:0: [sdb] Write Protect is off
[    1.849205] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.849240] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.849251] scsi 2:0:0:0: Direct-Access     ATA      ST31500341AS     CC1H PQ: 0 ANSI: 5
[    1.849400] sd 2:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    1.849428] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.849474] sd 2:0:0:0: [sdc] Write Protect is off
[    1.849478] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.849513] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.849594] scsi 3:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.15 PQ: 0 ANSI: 5
[    1.849770] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.849867] sd 3:0:0:0: [sdd] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.850017] sd 3:0:0:0: [sdd] Write Protect is off
[    1.850022] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.850055] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.852507]  sdd: sdd1 sdd2 sdd3 < sdd5 >
[    1.853010] sd 3:0:0:0: [sdd] Attached SCSI disk
[    1.856564]  sda: sda1
[    1.856792] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.866660]  sdc: sdc1
[    1.866964] sd 2:0:0:0: [sdc] Attached SCSI disk
[    1.871441]  sdb: sdb1
[    1.871732] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.872121] Freeing unused kernel memory: 872K (c19ae000 - c1a88000)
[    1.872181] Write protecting the kernel text: 6512k
[    1.872305] Write protecting the kernel read-only data: 2756k
[    1.872307] NX-protecting the kernel data: 5776k
[    1.891411] systemd-udevd[115]: starting version 208
[    1.892576] random: systemd-udevd urandom read with 32 bits of entropy available
[    1.924813] Floppy drive(s): fd0 is 1.44M
[    1.934332] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
[    1.935464] scsi4 : pata_jmicron
[    1.935560] scsi5 : pata_jmicron
[    1.935620] ata5: PATA max UDMA/100 cmd 0xc000 ctl 0xc100 bmdma 0xc400 irq 16
[    1.935624] ata6: PATA max UDMA/100 cmd 0xc200 ctl 0xc300 bmdma 0xc408 irq 16
[    1.942234] ahci 0000:03:00.0: version 3.0
[    1.945725] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.945741] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.945998] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.946259] r8169 0000:04:00.0 eth0: RTL8168b/8111b at 0xf840c000, 00:1a:4d:5f:d3:9d, XID 18000000 IRQ 44
[    1.946264] r8169 0000:04:00.0 eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
[    1.946349] FDC 0 is a post-1991 82077
[    1.956056] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.956063] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.956524] scsi6 : ahci
[    1.956640] scsi7 : ahci
[    1.956711] ata7: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000100 irq 19
[    1.956716] ata8: SATA max UDMA/133 abar m8192@0xfa000000 port 0xfa000180 irq 19
[    2.104522] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    2.104531] ata5.01: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    2.120584] ata5.00: configured for UDMA/33
[    2.136514] ata5.01: configured for UDMA/33
[    2.144622] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    2.150795] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.150800] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.150988] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.151139] sr 4:0:0:0: Attached scsi generic sg4 type 5
[    2.156969] scsi 4:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    2.163129] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.163284] sr 4:0:1:0: Attached scsi CD-ROM sr1
[    2.163424] sr 4:0:1:0: Attached scsi generic sg5 type 5
[    2.276033] ata8: SATA link down (SStatus 0 SControl 300)
[    2.276068] ata7: SATA link down (SStatus 0 SControl 300)
[    2.284029] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    2.411840] random: nonblocking pool is initialized
[    2.466696] usb 3-1: New USB device found, idVendor=046d, idProduct=c51a
[    2.466702] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.466706] usb 3-1: Product: USB Receiver
[    2.466709] usb 3-1: Manufacturer: Logitech
[    2.484377] hidraw: raw HID events driver (C) Jiri Kosina
[    2.499512] usbcore: registered new interface driver usbhid
[    2.499516] usbhid: USB HID core driver
[    2.506495] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input5
[    2.507057] hid-generic 0003:046D:C51A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1/input0
[    2.510822] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input6
[    2.510975] hid-generic 0003:046D:C51A.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1/input1
[    2.567728] EXT4-fs (sdd2): mounted filesystem with ordered data mode. Opts: (null)
[    2.712035] usb 8-1: new full-speed USB device number 2 using uhci_hcd
[    2.732096] Switched to clocksource tsc
[    2.882208] usb 8-1: New USB device found, idVendor=046d, idProduct=c223
[    2.882214] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.882219] usb 8-1: Product: Logitech G15 Keyboard
[    2.882299] usb 8-1: Manufacturer: Logitech
[    2.886293] hub 8-1:1.0: USB hub found
[    2.888127] hub 8-1:1.0: 4 ports detected
[    2.967631] Adding 2146300k swap on /dev/sdd1.  Priority:-1 extents:1 across:2146300k SSFS
[    2.980050] EXT4-fs (sdd2): re-mounted. Opts: errors=remount-ro
[    3.042295] EXT4-fs (sdd5): mounted filesystem with ordered data mode. Opts: (null)
[    3.064273] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.124871] systemd-udevd[408]: starting version 208
[    3.132119] usb 8-2: new full-speed USB device number 3 using uhci_hcd
[    3.140582] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.175999] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    3.231444] lp: driver loaded but no devices found
[    3.248207] ppdev: user-space parallel port driver
[    3.259955] parport_pc 00:08: reported by Plug and Play ACPI
[    3.260003] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    3.270440] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    3.294214] usb 8-2: New USB device found, idVendor=045e, idProduct=00f5
[    3.294221] usb 8-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    3.294225] usb 8-2: Product: USB camera
[    3.356258] lp0: using parport0 (interrupt-driven).
[    3.476460] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.616511] [drm] Initialized drm 1.1.0 20060810
[    3.652626] Bluetooth: Core ver 2.17
[    3.652678] NET: Registered protocol family 31
[    3.652681] Bluetooth: HCI device and connection manager initialized
[    3.652690] Bluetooth: HCI socket layer initialized
[    3.652694] Bluetooth: L2CAP socket layer initialized
[    3.652702] Bluetooth: SCO socket layer initialized
[    3.682040] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.682044] Bluetooth: BNEP filters: protocol multicast
[    3.682055] Bluetooth: BNEP socket layer initialized
[    3.684115] type=1400 audit(1412494715.321:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=663 comm="apparmor_parser"
[    3.684126] type=1400 audit(1412494715.321:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=663 comm="apparmor_parser"
[    3.684133] type=1400 audit(1412494715.321:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=663 comm="apparmor_parser"
[    3.689597] Bluetooth: RFCOMM TTY layer initialized
[    3.689608] Bluetooth: RFCOMM socket layer initialized
[    3.689616] Bluetooth: RFCOMM ver 1.11
[    3.736175] type=1400 audit(1412494715.373:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=696 comm="apparmor_parser"
[    3.736166] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \GP2C 1 (20131115/utaddress-251)
[    3.736179] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.736267] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.736305] type=1400 audit(1412494715.373:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=696 comm="apparmor_parser"
[    3.736314] type=1400 audit(1412494715.373:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=696 comm="apparmor_parser"
[    3.761548] type=1400 audit(1412494715.397:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=698 comm="apparmor_parser"
[    3.763001] Linux video capture interface: v2.00
[    3.764897] rfkill: input handler disabled
[    3.767770] init: cups main process (687) killed by HUP signal
[    3.767789] init: cups main process ended, respawning
[    3.768077] usb 1-4.3: new full-speed USB device number 4 using ehci-pci
[    3.856080] usb 1-4.3: device descriptor read/64, error -32
[    3.906939] device-mapper: multipath: version 1.6.0 loaded
[    3.995431] systemd-logind[720]: Watching system buttons on /dev/input/event1 (Power Button)
[    3.995559] systemd-logind[720]: Watching system buttons on /dev/input/event0 (Power Button)
[    3.995742] systemd-logind[720]: New seat seat0.
[    4.006189] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    4.021064] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[    4.021235] saa7133[0]: found at 0000:05:01.0, rev: 208, irq: 19, latency: 32, mmio: 0xfa100000
[    4.021243] saa7133[0]: subsystem: 11bd:002f, board: Pinnacle PCTV 310i [card=101,autodetected]
[    4.021260] saa7133[0]: board init: gpio is 600e000
[    4.028142] nvidia: module license 'NVIDIA' taints kernel.
[    4.028147] Disabling lock debugging due to kernel taint
[    4.037372] coretemp coretemp.0: Using relative temperature scale!
[    4.037398] coretemp coretemp.0: Using relative temperature scale!
[    4.037420] coretemp coretemp.0: Using relative temperature scale!
[    4.037446] coretemp coretemp.0: Using relative temperature scale!
[    4.041237] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    4.048213] usb 1-4.3: device descriptor read/64, error -32
[    4.052761] SKU: Nid=0x1d sku_cfg=0x4005e601
[    4.052766] SKU: port_connectivity=0x1
[    4.052768] SKU: enable_pcbeep=0x0
[    4.052770] SKU: check_sum=0x00000005
[    4.052772] SKU: customization=0x000000e6
[    4.052774] SKU: external_amp=0x0
[    4.052776] SKU: platform_type=0x0
[    4.052778] SKU: swap=0x0
[    4.052780] SKU: override=0x1
[    4.053257] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    4.053260]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.053263]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    4.053265]    mono: mono_out=0x0
[    4.053267]    dig-out=0x1e/0x0
[    4.053269]    inputs:
[    4.053272]      Rear Mic=0x18
[    4.053275]      Front Mic=0x19
[    4.053277]      Line=0x1a
[    4.053280]      CD=0x1c
[    4.053282]    dig-in=0x1f
[    4.053284] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[    4.053287] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0885
[    4.053934] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    4.056098] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[    4.056118] NVRM: loading NVIDIA UNIX x86 Kernel Module  331.89  Tue Jul  1 12:44:47 PDT 2014
[    4.135441] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    4.136934] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    4.153046] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    4.153159] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.153253] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.153345] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    4.153436] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    4.153524] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    4.186302] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    4.186310] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2c 1b 8d ff ff
[    4.186317] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 31 98 ff 00 a6 ff 21 00 c2
[    4.186325] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff ff 0c 22 17 77 03 1c 8a 1d
[    4.186332] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186340] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186347] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186355] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186362] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186370] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186377] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186385] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186392] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186400] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186407] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186415] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.194825] gspca_main: v2.14.0 registered
[    4.203450] gspca_main: sonixj-2.14.0 probing 045e:00f5
[    4.213980] input: sonixj as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/input/input15
[    4.214298] usbcore: registered new interface driver sonixj
[    4.248299] usb 1-4.3: new full-speed USB device number 5 using ehci-pci
[    4.264077] tuner 0-004b: Tuner -1 found with type(s) Radio TV.
[    4.289786] gpio_ich: GPIO from 195 to 255 on gpio_ich
[    4.318374] usbcore: registered new interface driver snd-usb-audio
[    4.336236] usb 1-4.3: device descriptor read/64, error -32
[    4.353434] tda829x 0-004b: setting tuner address to 61
[    4.371561] init: failsafe main process (844) killed by TERM signal
[    4.444073] tda829x 0-004b: type set to tda8290+75a
[    4.528081] usb 1-4.3: device descriptor read/64, error -32
[    4.638794] type=1400 audit(1412494716.273:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1050 comm="apparmor_parser"
[    4.638809] type=1400 audit(1412494716.273:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1050 comm="apparmor_parser"
[    4.717315] init: samba-ad-dc main process (1026) terminated with status 1
[    4.724079] usb 1-4.3: new full-speed USB device number 6 using ehci-pci
[    4.737291] r8169 0000:04:00.0 eth0: link down
[    4.737501] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.737614] r8169 0000:04:00.0 eth0: link down
[    5.121251] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    5.132039] usb 1-4.3: device not accepting address 6, error -32
[    5.135335] zram: Created 4 device(s) ...
[    5.140831] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    5.152193] zram: Cannot change disksize for initialized device
[    5.158176] init: zram-config pre-start process (1218) terminated with status 1
[    5.187558] Adding 516824k swap on /dev/zram0.  Priority:100 extents:1 across:516824k SSFS
[    5.190696] Adding 516824k swap on /dev/zram1.  Priority:100 extents:1 across:516824k SSFS
[    5.193716] Adding 516824k swap on /dev/zram2.  Priority:100 extents:1 across:516824k SSFS
[    5.195727] Adding 516824k swap on /dev/zram3.  Priority:100 extents:1 across:516824k SSFS
[    5.208077] usb 1-4.3: new full-speed USB device number 7 using ehci-pci
[    5.290105] init: zram-config post-stop process (1338) terminated with status 1
[    5.616026] usb 1-4.3: device not accepting address 7, error -32
[    5.616206] hub 1-4:1.0: unable to enumerate USB device on port 3
[    5.689135] usb 8-1.1: new low-speed USB device number 4 using uhci_hcd
[    5.832127] usb 8-1.1: New USB device found, idVendor=046d, idProduct=c221
[    5.832133] usb 8-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.832137] usb 8-1.1: Product: Logitech Gaming Keyboard
[    5.832141] usb 8-1.1: Manufacturer: Logitech
[    5.850344] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.1/8-1.1:1.0/input/input16
[    5.850565] hid-generic 0003:046D:C221.0003: input,hidraw2: USB HID v1.10 Keyboard [Logitech Logitech Gaming Keyboard] on usb-0000:00:1d.2-1.1/input0
[    5.886191] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.1/8-1.1:1.1/input/input17
[    5.886383] hid-generic 0003:046D:C221.0004: input,hiddev0,hidraw3: USB HID v1.10 Device [Logitech Logitech Gaming Keyboard] on usb-0000:00:1d.2-1.1/input1
[    5.961129] usb 8-1.4: new full-speed USB device number 5 using uhci_hcd
[    6.103128] usb 8-1.4: New USB device found, idVendor=046d, idProduct=c222
[    6.103134] usb 8-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.103138] usb 8-1.4: Product: G15 Keyboard
[    6.103142] usb 8-1.4: Manufacturer: G15 Keyboard
[    6.113260] input: G15 Keyboard G15 Keyboard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.4/8-1.4:1.0/input/input18
[    6.113502] hid-generic 0003:046D:C222.0005: input,hiddev0,hidraw4: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:1d.2-1.4/input0
[    6.418325] r8169 0000:04:00.0 eth0: link up
[    6.418339] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    9.276015] Registered IR keymap rc-pinnacle-color
[    9.276140] input: i2c IR (Pinnacle PCTV) as /devices/virtual/rc/rc0/input19
[    9.276220] rc0: i2c IR (Pinnacle PCTV) as /devices/virtual/rc/rc0
[    9.276225] ir-kbd-i2c: i2c IR (Pinnacle PCTV) detected at i2c-0/0-0047/ir0 [saa7133[0]]
[    9.348101] saa7133[0]: registered device video1 [v4l2]
[    9.348182] saa7133[0]: registered device vbi0
[    9.348237] saa7133[0]: registered device radio0
[    9.358909] saa7134 ALSA driver for DMA sound loaded
[    9.358950] saa7133[0]/alsa: saa7133[0] at 0xfa100000 irq 19 registered as card -2
[    9.382347] dvb_init() allocating 1 frontend
[    9.432037] DVB: registering new adapter (saa7133[0])
[    9.432045] saa7134 0000:05:01.0: DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[    9.660068] usb 1-4.3: new full-speed USB device number 8 using ehci-pci
[    9.672017] tda1004x: setting up plls for 48MHz sampling clock
[    9.748070] usb 1-4.3: device descriptor read/64, error -32
[    9.940066] usb 1-4.3: device descriptor read/64, error -32
[   10.132066] usb 1-4.3: new full-speed USB device number 9 using ehci-pci
[   10.220065] usb 1-4.3: device descriptor read/64, error -32
[   10.412072] usb 1-4.3: device descriptor read/64, error -32
[   10.604074] usb 1-4.3: new full-speed USB device number 10 using ehci-pci
[   11.012019] usb 1-4.3: device not accepting address 10, error -32
[   11.100074] usb 1-4.3: new full-speed USB device number 11 using ehci-pci
[   11.508014] usb 1-4.3: device not accepting address 11, error -32
[   11.508199] hub 1-4:1.0: unable to enumerate USB device on port 3
[   11.696093] usb 1-4.3: new full-speed USB device number 12 using ehci-pci
[   11.784081] usb 1-4.3: device descriptor read/64, error -32
[   11.976073] usb 1-4.3: device descriptor read/64, error -32
[   12.096015] tda1004x: timeout waiting for DSP ready
[   12.144021] tda1004x: found firmware revision 0 -- invalid
[   12.144025] tda1004x: trying to boot from eeprom
[   12.168080] usb 1-4.3: new full-speed USB device number 13 using ehci-pci
[   12.256082] usb 1-4.3: device descriptor read/64, error -32
[   12.307947] input: G15 Extra Keys as /devices/virtual/input/input20
[   12.448086] usb 1-4.3: device descriptor read/64, error -32
[   12.502618] /dev/vmmon[3188]: Module vmmon: registered with major=10 minor=165
[   12.502625] /dev/vmmon[3188]: Module vmmon: initialized
[   12.541836] Guest personality initialized and is inactive
[   12.541927] VMCI host device registered (name=vmci, major=10, minor=57)
[   12.541930] Initialized host personality
[   12.594635] NET: Registered protocol family 40
[   12.640086] usb 1-4.3: new full-speed USB device number 14 using ehci-pci
[   12.760601] /dev/vmnet: open called by PID 3290 (vmnet-bridge)
[   12.760614] /dev/vmnet: hub 0 does not exist, allocating memory.
[   12.760638] /dev/vmnet: port on hub 0 successfully opened
[   12.760654] bridge-eth0: up
[   12.760658] bridge-eth0: attached
[   13.048022] usb 1-4.3: device not accepting address 14, error -32
[   13.103902] nvidia 0000:01:00.0: irq 46 for MSI/MSI-X
[   13.136085] usb 1-4.3: new full-speed USB device number 15 using ehci-pci
[   13.544015] usb 1-4.3: device not accepting address 15, error -32
[   13.544081] hub 1-4:1.0: unable to enumerate USB device on port 3
[   13.792805] /dev/vmnet: open called by PID 3331 (vmnet-netifup)
[   13.792813] /dev/vmnet: hub 1 does not exist, allocating memory.
[   13.792836] /dev/vmnet: port on hub 1 successfully opened
[   13.820097] /dev/vmnet: open called by PID 3334 (vmnet-dhcpd)
[   13.820110] /dev/vmnet: port on hub 1 successfully opened
[   13.834552] /dev/vmnet: open called by PID 3340 (vmnet-natd)
[   13.834560] /dev/vmnet: hub 8 does not exist, allocating memory.
[   13.834582] /dev/vmnet: port on hub 8 successfully opened
[   13.836406] userif-3: sent link down event.
[   13.836408] userif-3: sent link up event.
[   13.839119] /dev/vmnet: open called by PID 3344 (vmnet-netifup)
[   13.839133] /dev/vmnet: port on hub 8 successfully opened
[   13.852598] /dev/vmnet: open called by PID 3346 (vmnet-dhcpd)
[   13.852612] /dev/vmnet: port on hub 8 successfully opened
[   14.471866] systemd-logind[720]: Failed to start unit user@104.service: Unknown unit: user@104.service
[   14.471876] systemd-logind[720]: Failed to start user service: Unknown unit: user@104.service
[   14.476049] tda1004x: timeout waiting for DSP ready
[   14.480192] systemd-logind[720]: New session c1 of user lightdm.
[   14.480224] systemd-logind[720]: Linked /tmp/.X11-unix/X0 to /run/user/104/X11-display.
[   14.516028] tda1004x: found firmware revision 0 -- invalid
[   14.516033] tda1004x: waiting for firmware upload...
[   14.518286] saa7134 0000:05:01.0: Direct firmware load failed with error -2
[   14.518291] saa7134 0000:05:01.0: Falling back to user helper
[   14.519284] saa7134 0000:05:01.0: Direct firmware load failed with error -2
[   14.519288] saa7134 0000:05:01.0: Falling back to user helper
[   14.520143] tda1004x: no firmware upload (timeout or file not found?)
[   14.520147] tda1004x: firmware upload failed
[   15.972147] retire_capture_urb: 69 callbacks suppressed
[   16.722794] init: plymouth-stop pre-start process (3984) terminated with status 1
[   23.046801] systemd-logind[720]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   23.046812] systemd-logind[720]: Failed to start user service: Unknown unit: user@1000.service
[   23.051940] systemd-logind[720]: New session c2 of user spupuz.
[   23.051969] systemd-logind[720]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   25.963177] retire_capture_urb: 5 callbacks suppressed
[   33.924989] audit_printk_skb: 5 callbacks suppressed
[   33.924995] type=1400 audit(1412494745.561:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=5817 comm="apparmor_parser"
[   33.925005] type=1400 audit(1412494745.561:35): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=5817 comm="apparmor_parser"
[   33.938897] type=1400 audit(1412494745.573:36): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=5817 comm="apparmor_parser"
[   48.322657] systemd-hostnamed[6081]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
spupuz@spupuz-EP35C-DS3R:~$ 

```

maybe you can find some error related to my problem

---

### Post by SpUpUz on 2014-10-05
look there:

[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439)

---

### Post by ventrical on 2014-10-05
```

 4.028142] nvidia: module license 'NVIDIA' taints kernel.
[    4.028147] Disabling lock debugging due to kernel taint
[    4.037372] coretemp coretemp.0: Using relative temperature scale!
[    4.037398] coretemp coretemp.0: Using relative temperature scale!
[    4.037420] coretemp coretemp.0: Using relative temperature scale!
[    4.037446] coretemp coretemp.0: Using relative temperature scale!
[    4.041237] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    4.048213] usb 1-4.3: device descriptor read/64, error -32
[    4.052761] SKU: Nid=0x1d sku_cfg=0x4005e601
[    4.052766] SKU: port_connectivity=0x1
[    4.052768] SKU: enable_pcbeep=0x0
[    4.052770] SKU: check_sum=0x00000005
[    4.052772] SKU: customization=0x000000e6
[    4.052774] SKU: external_amp=0x0
[    4.052776] SKU: platform_type=0x0
[    4.052778] SKU: swap=0x0
[    4.052780] SKU: override=0x1
[    4.053257] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    4.053260]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.053263]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    4.053265]    mono: mono_out=0x0
[    4.053267]    dig-out=0x1e/0x0
[    4.053269]    inputs:
[    4.053272]      Rear Mic=0x18
[    4.053275]      Front Mic=0x19
[    4.053277]      Line=0x1a
[    4.053280]      CD=0x1c
[    4.053282]    dig-in=0x1f
[    4.053284] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[    4.053287] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0885
[    4.053934] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    4.056098] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[    4.056118] NVRM: loading NVIDIA UNIX x86 Kernel Module  331.89  Tue Jul  1 12:44:47 PDT 2014
[    4.135441] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    4.136934] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    4.153046] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    4.153159] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.153253] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.153345] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    4.153436] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    4.153524] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    4.186302] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    4.186310] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2c 1b 8d ff ff
[    4.186317] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 31 98 ff 00 a6 ff 21 00 c2
[    4.186325] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff ff 0c 22 17 77 03 1c 8a 1d
[    4.186332] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186340] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186347] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186355] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186362] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186370] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186377] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186385] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186392] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186400] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186407] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186415] saa7133[0]: i2c eeprom f0: ff f


```

I  have seen the bug report but I am not sure it applies. I will have to get back on this later.

My first assumption is that there is problem with nVidia graphical adapter card or (did you have any ppas running when you upgraded originally)?

What I have done in the past when i see such problems is "remove" the nVidia card from the computer and then re-install it. Make sure it is seated correctly.  Sometimes the memory and BIOS lock up because they do not totally shut down. It appears that something is locked up. I am not telling you  to do this .. just my assumption.

Next , at this point , use sources.list and downgrade to trusty, then try a do-release-upgrade -d once again.

Have you tried booting from another kernel?

---

### Post by ventrical on 2014-10-05
If you are willing to experiement  you can try to change sources list back to trusty, update/upgrade and see what happens.

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

Just switch trusty/utopic to utopic/trusty.

or install aptitude and try the command suggested at the same link and see what happens.

---

### Post by SpUpUz on 2014-10-06
> **ventrical said:**
> ```

 4.028142] nvidia: module license 'NVIDIA' taints kernel.
[    4.028147] Disabling lock debugging due to kernel taint
[    4.037372] coretemp coretemp.0: Using relative temperature scale!
[    4.037398] coretemp coretemp.0: Using relative temperature scale!
[    4.037420] coretemp coretemp.0: Using relative temperature scale!
[    4.037446] coretemp coretemp.0: Using relative temperature scale!
[    4.041237] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    4.048213] usb 1-4.3: device descriptor read/64, error -32
[    4.052761] SKU: Nid=0x1d sku_cfg=0x4005e601
[    4.052766] SKU: port_connectivity=0x1
[    4.052768] SKU: enable_pcbeep=0x0
[    4.052770] SKU: check_sum=0x00000005
[    4.052772] SKU: customization=0x000000e6
[    4.052774] SKU: external_amp=0x0
[    4.052776] SKU: platform_type=0x0
[    4.052778] SKU: swap=0x0
[    4.052780] SKU: override=0x1
[    4.053257] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    4.053260]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.053263]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    4.053265]    mono: mono_out=0x0
[    4.053267]    dig-out=0x1e/0x0
[    4.053269]    inputs:
[    4.053272]      Rear Mic=0x18
[    4.053275]      Front Mic=0x19
[    4.053277]      Line=0x1a
[    4.053280]      CD=0x1c
[    4.053282]    dig-in=0x1f
[    4.053284] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[    4.053287] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0885
[    4.053934] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    4.056098] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[    4.056118] NVRM: loading NVIDIA UNIX x86 Kernel Module  331.89  Tue Jul  1 12:44:47 PDT 2014
[    4.135441] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    4.136934] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    4.153046] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    4.153159] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.153253] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.153345] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    4.153436] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    4.153524] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    4.186302] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    4.186310] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2c 1b 8d ff ff
[    4.186317] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 31 98 ff 00 a6 ff 21 00 c2
[    4.186325] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff ff 0c 22 17 77 03 1c 8a 1d
[    4.186332] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186340] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186347] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186355] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186362] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186370] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186377] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186385] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186392] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186400] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186407] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    4.186415] saa7133[0]: i2c eeprom f0: ff f


```

I  have seen the bug report but I am not sure it applies. I will have to get back on this later.

My first assumption is that there is problem with nVidia graphical adapter card or (did you have any ppas running when you upgraded originally)?

What I have done in the past when i see such problems is "remove" the nVidia card from the computer and then re-install it. Make sure it is seated correctly.  Sometimes the memory and BIOS lock up because they do not totally shut down. It appears that something is locked up. I am not telling you  to do this .. just my assumption.

Next , at this point , use sources.list and downgrade to trusty, then try a do-release-upgrade -d once again.

Have you tried booting from another kernel?

i had a lot of ppa while i upgraded but where disabled before upgrading by the upgrade procedure and now are still disabled.
i'll try what you suggested eventually this evening.

---

### Post by ventrical on 2014-10-06
Method to check if ppas are gone is :

```

if  [[ -d /etc/apt/sources.list.d && $(ls -l   /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir   exists and is not empty\n\n"; for PPA_FILE in $(ls   /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed   -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e   's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e   's|oneiric||' | sed -e 's|trusty||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list;  done;  echo "PPA list saved at $HOME/ppa-sources.list"; else echo -e "\n\nEmpty or inexistent PPA directory\n\n"; fi

```

should give this result.. (unless that code proceedure has changed also)

```

ls: cannot access /etc/apt/sources.list.d/*: No such file or directory


Empty or inexistent PPA directory


```

---

### Post by SpUpUz on 2014-10-06
> **ventrical said:**
> If you are willing to experiement  you can try to change sources list back to trusty, update/upgrade and see what happens.

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

Just switch trusty/utopic to utopic/trusty.

or install aptitude and try the command suggested at the same link and see what happens.

i'm quite scared about that :/ i would like to try to solve without reinstalling a the end all the system.
still hoping some upgrade package will do the trick and solve the situation?

isn't there any log to look at?

---

### Post by SpUpUz on 2014-10-06
what about that?

spupuz@spupuz-EP35C-DS3R:~$ sudo systemctl
Failed to get D-Bus connection: No connection to service manager.

---

### Post by SpUpUz on 2014-10-07
> **ventrical said:**
> Method to check if ppas are gone is :

```

if  [[ -d /etc/apt/sources.list.d && $(ls -l   /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir   exists and is not empty\n\n"; for PPA_FILE in $(ls   /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed   -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e   's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e   's|oneiric||' | sed -e 's|trusty||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list;  done;  echo "PPA list saved at $HOME/ppa-sources.list"; else echo -e "\n\nEmpty or inexistent PPA directory\n\n"; fi

```

should give this result.. (unless that code proceedure has changed also)

```

ls: cannot access /etc/apt/sources.list.d/*: No such file or directory


Empty or inexistent PPA directory


```

EUREKA!!!! reinstalling libpam-systemd and systemd-sysv made the trick it removed upstart and some other package and now it is working!!!

---

### Post by ventrical on 2014-10-08
Bravo !  :)

---

### Post by SpUpUz on 2014-10-08
> **ventrical said:**
> Bravo !  :)

probably for some reason (performance tweak) i installed upstart before the upgrade and that make a hell... :/ now back to systemd and removed upstart i can do everything in unity.

i have some problem there is some trace of upstart :/ maybe you can help me:

```
spupuz@spupuz-EP35C-DS3R:/media/Archive/Downloads$ sudo dpkg -i plexmediaserver_0.9.9.14.531-7eef8c6_i386.deb 
[sudo] password for spupuz: 
(Reading database ... 375223 files and directories currently installed.)
Preparing to unpack plexmediaserver_0.9.9.14.531-7eef8c6_i386.deb ...
**stop: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused**
Unpacking plexmediaserver (0.9.9.14.531-7eef8c6) over (0.9.9.14.531-7eef8c6) ...
Setting up plexmediaserver (0.9.9.14.531-7eef8c6) ...
**start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused**
Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1) ...

```

---

### Post by ventrical on 2014-10-08
I'm not familiar with the plexmediaserver. Never used it.

---

### Post by SpUpUz on 2014-10-08
it is not related to plex is relate to upstart still in some place.

---

### Post by ventrical on 2014-10-08
> **SpUpUz said:**
> it is not related to plex is relate to upstart still in some place.

Yes.. I see .. here is a bit of a read on it:

[http://askubuntu.com/questions/19320/how-to-enable-or-disable-services](http://askubuntu.com/questions/19320/how-to-enable-or-disable-services)

but we cant remove upstart as it has depends.

---

### Post by ventrical on 2014-10-08
you got plexmediaserver from ppa??

because auto-script may be calling upstart .. seems..

---

### Post by ventrical on 2014-10-18
I got somthing similar to what you got a while back. I decided to use systemd.  I then set it in /etc/default.grub, updated grub, rebooted and it worked just great. Then I,

```

sudo apt-get update
sudo apt-get dist-upgrade

```

and this happened ... Just as it happend my screen went blank. I got terminal errors and systemd friendly boot thingy. I then had to Ctrl+Alt _F7 and there was unity-desktop still unpacking files in terminal.

I will --configure -a and see what happens and then reboot.

```

Loading new nvidia-304-304.123 DKMS files...
Building for 3.16.0-12-generic and 3.16.0-23-generic
Building for architecture i686
Building initial module for 3.16.0-12-generic
Done.

nvidia_304:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-12-generic/updates/dkms/

depmod.......

DKMS: install completed.
Building initial module for 3.16.0-23-generic
Done.

nvidia_304:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-23-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up xserver-xorg-video-fbdev (1:0.4.4-1build2) ...
Setting up xserver-xorg-video-savage (1:2.3.7-2ubuntu3) ...
Setting up xserver-xorg-video-qxl (0.1.1-0ubuntu4) ...
Setting up xserver-xorg-video-vmware (1:13.0.2-3ubuntu1) ...
Setting up xserver-xorg-video-openchrome (1:0.3.3-1build2) ...
Setting up xserver-xorg-video-all (1:7.7+7ubuntu2) ...
Setting up xserver-xorg-input-mouse (1:1.9.0-1build2) ...
Setting up xserver-xorg-input-evdev (1:2.9.0-1ubuntu2) ...
Setting up xserver-xorg-input-wacom (1:0.25.0-0ubuntu1) ...
Setting up xserver-xorg-input-vmmouse (1:13.0.0-1build2) ...
Setting up xserver-xorg-input-synaptics (1.8.1-1ubuntu1) ...
Setting up lightdm (1.12.1-0ubuntu1) ...
Installing new version of config file /etc/apparmor.d/abstractions/lightdm_chromium-browser ...
Installing new version of config file /etc/apparmor.d/abstractions/lightdm ...
Setting up ubuntu-drivers-common (1:0.2.98.4) ...
Setting up ubuntu-minimal (1.327) ...
Setting up plymouth-theme-ubuntu-text (0.9.0-0ubuntu6) ...
update-initramfs: deferring update (trigger activated)
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of bluez-alsa:i386:
 bluez-alsa:i386 depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluez-alsa:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gstreamer:
 bluez-gstreamer depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluez-gstreamer (--configure):
 dependency problems - leaving unconfigured
Setting up indicator-session (12.10.5+14.10.20141009-0ubuntu1) ...
Setting up media-player-info (22-2) ...
Setting up nvidia-current (304.123-0ubuntu5) ...
Setting up plymouth-theme-ubuntu-logo (0.9.0-0ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Setting up software-properties-gtk (0.94) ...
Setting up xserver-xorg-input-all (1:7.7+7ubuntu2) ...
Setting up xserver-xorg (1:7.7+7ubuntu2) ...
Setting up xorg (1:7.7+7ubuntu2) ...
dpkg: dependency problems prevent configuration of unity-control-center:
 unity-control-center depends on indicator-bluetooth; however:
  Package indicator-bluetooth is not configured yet.

dpkg: error processing package unity-control-center (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on unity-control-center; however:
  Package unity-control-center is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for dbus (1.8.8-1ubuntu2) ...
Setting up libpam-systemd:i386 (208-8ubuntu8) ...
Setting up pulseaudio (1:4.0-0ubuntu22) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: stop runlevel arguments (1) do not match pulseaudio Default-Stop values (0 1 6)
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
invoke-rc.d: initscript pulseaudio, action "start" failed.
dpkg: error processing package pulseaudio (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of indicator-sound:
 indicator-sound depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package indicator-sound (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up libnss3-nssdb (2:3.17.1-0ubuntu1) ...
Setting up language-pack-en (1:14.10+20141014) ...
Setting up language-pack-en-base (1:14.10+20140909) ...
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZM.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Setting up language-pack-gnome-en (1:14.10+20141014) ...
Setting up language-pack-gnome-en-base (1:14.10+20140909) ...
Setting up perl-modules (5.20.1-1) ...
Setting up libnss3:i386 (2:3.17.1-0ubuntu1) ...
Setting up libnss3-1d:i386 (2:3.17.1-0ubuntu1) ...
Setting up libnm-util2 (0.9.8.8-0ubuntu28) ...
Setting up libnm-glib4 (0.9.8.8-0ubuntu28) ...
Setting up libnm-glib-vpn1 (0.9.8.8-0ubuntu28) ...
Setting up gnome-settings-daemon (3.12.2-1ubuntu2) ...
Setting up gnome-control-center (1:3.12.1-5ubuntu2) ...
Setting up libcamel-1.2-49 (3.12.7.1-0ubuntu1) ...
Setting up libedataserver-1.2-18 (3.12.7.1-0ubuntu1) ...
Setting up libecal-1.2-16 (3.12.7.1-0ubuntu1) ...
Setting up indicator-datetime (13.10.0+14.10.20141009-0ubuntu1) ...
Setting up libebackend-1.2-7 (3.12.7.1-0ubuntu1) ...
Setting up evolution-data-server-online-accounts (3.12.7.1-0ubuntu1) ...
Setting up libebook-contacts-1.2-0 (3.12.7.1-0ubuntu1) ...
Setting up libedata-book-1.2-20 (3.12.7.1-0ubuntu1) ...
Setting up libebook-1.2-14 (3.12.7.1-0ubuntu1) ...
Setting up libedata-cal-1.2-23 (3.12.7.1-0ubuntu1) ...
Setting up evolution-data-server (3.12.7.1-0ubuntu1) ...
Setting up libfolks-eds25:i386 (0.10.0-1) ...
Setting up libreoffice-core (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-base-core (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-calc (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-gtk (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-gnome (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-draw (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-impress (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-writer (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-pdfimport (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-ogltrans (1:4.3.2-0ubuntu1) ...
Setting up libreoffice-math (1:4.3.2-0ubuntu1) ...
Setting up python3-uno (1:4.3.2-0ubuntu1) ...
Setting up network-manager (0.9.8.8-0ubuntu28) ...
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
Setting up liboxideqtcore0:i386 (1.2.5-0ubuntu1) ...
Setting up liboxideqt-qmlplugin:i386 (1.2.5-0ubuntu1) ...
Setting up qtdeclarative5-ubuntu-web-plugin:i386 (0.23+14.10.20141008-0ubuntu1) ...
Setting up qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 (0.23+14.10.20141008-0ubuntu1) ...
Setting up unity-webapps-qml (0.1+14.10.20140813-0ubuntu2) ...
Setting up webbrowser-app (0.23+14.10.20141008-0ubuntu1) ...
Setting up webapp-container (0.23+14.10.20141008-0ubuntu1) ...
Setting up telepathy-mission-control-5 (1:5.16.2-1ubuntu3) ...
Installing new version of config file /etc/apparmor.d/usr.lib.telepathy ...
Setting up empathy (3.8.6-0ubuntu13) ...
Setting up mcp-account-manager-uoa (3.8.6-0ubuntu13) ...
Setting up account-plugin-salut (3.8.6-0ubuntu13) ...
Setting up account-plugin-jabber (3.8.6-0ubuntu13) ...
Setting up account-plugin-yahoo (3.8.6-0ubuntu13) ...
Setting up account-plugin-aim (3.8.6-0ubuntu13) ...
Setting up flashplugin-installer (11.2.202.411ubuntu1) ...
Setting up gir1.2-edataserver-1.2 (3.12.7.1-0ubuntu1) ...
Setting up gir1.2-ebookcontacts-1.2 (3.12.7.1-0ubuntu1) ...
Setting up gir1.2-ebook-1.2 (3.12.7.1-0ubuntu1) ...
Setting up gir1.2-networkmanager-1.0 (0.9.8.8-0ubuntu28) ...
Setting up gnome-contacts (3.8.3-1ubuntu2) ...
Setting up gnome-session (3.9.90-0ubuntu16) ...
Setting up libpurple0 (1:2.10.9-0ubuntu7) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:4.3.2-0ubuntu1) ...
Setting up mythes-en-us (1:4.2.1-0ubuntu3) ...
Setting up perl (5.20.1-1) ...
Setting up libcpan-meta-perl (2.142060-1) ...
Setting up libmodule-build-perl (0.421000-2) ...
Setting up gstreamer0.10-plugins-base-apps (0.10.36-2) ...
Setting up libmailtools-perl (2.13-1) ...
Setting up libparse-debianchangelog-perl (1.2.0-1.1) ...
Setting up hardening-includes (2.5+nmu1ubuntu2) ...
Setting up lintian (2.5.27ubuntu1) ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-23-generic
Processing triggers for libgdk-pixbuf2.0-0:i386 (2.30.8-1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for dictionaries-common (1.23.11) ...
Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Errors were encountered while processing:
 whoopsie
 thermald
 linux-image-generic
 linux-generic
 bluez
 indicator-bluetooth
 bluez-alsa:i386
 bluez-gstreamer
 unity-control-center
 ubuntu-desktop
 pulseaudio
 indicator-sound
 pulseaudio-module-x11
 pulseaudio-module-bluetooth
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-desktop:~$ 

```

*note* I'll put this in appropiate echo when I get a handle on it . 
thnx

---

### Post by ventrical on 2014-10-18
addum

```

ventrical@ventrical-desktop:~$ sudo -i dpkg --configure -a
Setting up bluez (4.101-0ubuntu20) ...
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
invoke-rc.d: initscript dbus, action "force-reload" failed.
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
invoke-rc.d: initscript bluetooth, action "start" failed.
dpkg: error processing package bluez (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of indicator-bluetooth:
 indicator-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.

dpkg: error processing package indicator-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gstreamer:
 bluez-gstreamer depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluez-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-alsa:i386:
 bluez-alsa:i386 depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluez-alsa:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up whoopsie (0.2.39) ...
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
invoke-rc.d: initscript whoopsie, action "start" failed.
dpkg: error processing package whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of unity-control-center:
 unity-control-center depends on indicator-bluetooth; however:
  Package indicator-bluetooth is not configured yet.

dpkg: error processing package unity-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on unity-control-center; however:
  Package unity-control-center is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up pulseaudio (1:4.0-0ubuntu22) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: stop runlevel arguments (1) do not match pulseaudio Default-Stop values (0 1 6)
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
invoke-rc.d: initscript pulseaudio, action "start" failed.
dpkg: error processing package pulseaudio (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up thermald (1.3-6) ...
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
Failed to get D-Bus connection: Failed to connect to socket /run/systemd/private: Connection refused
invoke-rc.d: initscript thermald, action "start" failed.
dpkg: error processing package thermald (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-sound:
 indicator-sound depends on pulseaudio; however:
  Package pulseaudio is not configured yet.

dpkg: error processing package indicator-sound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on thermald; however:
  Package thermald is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.16.0.23.24); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bluez
 indicator-bluetooth
 bluez-gstreamer
 bluez-alsa:i386
 whoopsie
 unity-control-center
 ubuntu-desktop
 pulseaudio
 thermald
 pulseaudio-module-bluetooth
 pulseaudio-module-x11
 indicator-sound
 linux-image-generic
 linux-generic
ventrical@ventr

```

---

### Post by ventrical on 2014-10-18
...ok . this somehow fixed after a hard reboot.

```

Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up bluez (4.101-0ubuntu20) ...
Setting up bluez-alsa:i386 (4.101-0ubuntu20) ...
Setting up bluez-gstreamer (4.101-0ubuntu20) ...
Setting up thermald (1.3-6) ...
Setting up linux-image-generic (3.16.0.23.24) ...
Setting up linux-generic (3.16.0.23.24) ...
Setting up pulseaudio (1:4.0-0ubuntu22) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: stop runlevel arguments (1) do not match pulseaudio Default-Stop values (0 1 6)
Setting up pulseaudio-module-x11 (1:4.0-0ubuntu22) ...
Setting up indicator-sound (12.10.2+14.10.20141010-0ubuntu1) ...
Setting up indicator-bluetooth (0.0.6+14.10.20141006-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/indicator-bluetooth.desktop ...
Setting up unity-control-center (14.10.0+14.10.20140922-0ubuntu2) ...
Setting up ubuntu-desktop (1.327) ...
Setting up whoopsie (0.2.39) ...
Setting up pulseaudio-module-bluetooth (1:4.0-0ubuntu22) ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...
ventrical@ventrical-desktop:~$ systemd-analyze
Startup finished in 11.585s (kernel) + 43.238s (userspace) = 54.824s
ventrical@ventrical-deskt

```

---

### Post by jpanasuik on 2014-11-19
> **SpUpUz said:**
> EUREKA!!!! reinstalling libpam-systemd and systemd-sysv made the trick it removed upstart and some other package and now it is working!!!


KUDO!!!!  Now my server runs smoothly and sleeky.

---

