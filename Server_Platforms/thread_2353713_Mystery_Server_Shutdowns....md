---
title: "Mystery Server Shutdowns..."
date: 2017-02-24
forum: Server Platforms
---

### Post by scott.bouch on 2017-02-24
Hi all,

After a good few months of being online with no issues, yesterday we had very high winds which resulted in 2x power outages during the day. My UPS lasts only about 20 minutes, which wasn't long enough for these outages, so my server had a couple of hard shutdowns.

Today It's been back online, but has shut itself down for reasons unknown after an hour or so of being seemingly ok.

It's not overheating, as it's a cold day.

Does Ubuntu keep any logs of shutdowns etc that I may be able to read?

Thanks, Scott.

---

### Post by volkswagner on 2017-02-24
You should check syslog (/var/log/syslog) along with dmesg (/var/log/dmesg).
Feel free to post relevant information for logs just before the shutdown occurred.

---

### Post by scott.bouch on 2017-02-24
thanks for the pointers, this is from syslog from the last shutdown, and subsequent startup:

Most of these messages relate to Zoneminder CCTV software, and my cameras (Cars, Garage front door etc..) alarm states mean they have detected motion.

At 14:07 it died with a load of ^@^@^@

```
Feb 24 13:13:01 6FC zma_m1[4571]: INF [Garage_Front_Door: 4349 - Gone into alarm state]
Feb 24 13:13:01 6FC zma_m1[4571]: INF [Garage_Front_Door: 4349 - Opening new event 138890, alarm start]
Feb 24 13:13:01 6FC zma_m3[4108]: INF [Cars: 5775 - Gone into alarm state]
Feb 24 13:13:01 6FC zma_m3[4108]: INF [Cars: 5775 - Opening new event 138891, alarm start]
Feb 24 13:13:06 6FC zmc_m1[1757]: WAR [Buffer overrun at index 48, image 27998, slow down capture, speed up anal$
Feb 24 13:13:06 6FC zmc_m3[1800]: WAR [Buffer overrun at index 46, image 27996, slow down capture, speed up anal$
Feb 24 13:13:06 6FC zmc_m1[1757]: INF [Garage_Front_Door: 28000 - Capturing at 8.00 fps]
Feb 24 13:13:07 6FC zmc_m3[1800]: INF [Cars: 28000 - Capturing at 8.00 fps]
Feb 24 13:13:08 6FC zmwatch[1860]: INF [Restarting analysis daemon for Garage_Front_Door, time since last analys$
Feb 24 13:13:08 6FC zmdc[1717]: INF ['zma -m 1' stopping at 17/02/24 13:13:08]
Feb 24 13:13:08 6FC zma_m1[4571]: INF [Got signal 15 (Terminated), exiting]
Feb 24 13:13:08 6FC zma_m1[4571]: INF [Garage_Front_Door: 4350 - Closing event 138890, shutting down]
Feb 24 13:13:08 6FC zmdc[1717]: INF ['zma -m 1' exited normally]
Feb 24 13:13:08 6FC zmwatch[1860]: INF [Restarting analysis daemon for Cars, time since last analysis 8 seconds $
Feb 24 13:13:09 6FC zmdc[1717]: INF ['zma -m 3' stopping at 17/02/24 13:13:09]
Feb 24 13:13:09 6FC zma_m3[4108]: INF [Got signal 15 (Terminated), exiting]
Feb 24 13:13:09 6FC zma_m3[4108]: INF [Cars: 5777 - Closing event 138891, shutting down]
Feb 24 13:13:09 6FC zmdc[1717]: INF ['zma -m 3' exited normally]
Feb 24 13:13:09 6FC zmdc[1717]: INF [Starting pending process, zma -m 3]
Feb 24 13:13:09 6FC zmdc[1717]: INF ['zma -m 3' starting at 17/02/24 13:13:09, pid = 5066]
Feb 24 13:13:09 6FC zmdc[5066]: INF ['zma -m 3' started at 17/02/24 13:13:09]
Feb 24 13:13:10 6FC zma_m3[5066]: INF [In mode 3/1, warming up]
Feb 24 13:13:13 6FC zmdc[1717]: INF [Starting pending process, zma -m 1]
Feb 24 13:13:13 6FC zmdc[1717]: INF ['zma -m 1' starting at 17/02/24 13:13:13, pid = 5077]
Feb 24 13:13:13 6FC zmdc[5077]: INF ['zma -m 1' started at 17/02/24 13:13:13]
Feb 24 13:13:13 6FC zma_m1[5077]: INF [In mode 3/1, warming up]
Feb 24 13:13:36 6FC zmc_dvideo0[1785]: INF [Garage_Inside: 53000 - Capturing at 14.93 fps]
Feb 24 13:13:36 6FC zma_m2[1788]: INF [Garage_Inside: 53000 - Processing at 14.93 fps]
Feb 24 13:14:07 6FC nullmailer[5004]: smtp: Failed: Connect failed
Feb 24 13:14:07 6FC nullmailer[1395]: Sending failed:  Connection failed
Feb 24 13:14:07 6FC nullmailer[1395]: Starting delivery: protocol: smtp host: mail.google.com file: 1477459895.5$
Feb 24 13:14:07 6FC nullmailer[1395]: Starting delivery, 676 message(s) in queue.
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@$
Feb 24 17:18:10 6FC rsyslogd: rsyslogd's groupid changed to 104
Feb 24 17:18:10 6FC rsyslogd: rsyslogd's userid changed to 101
Feb 24 17:18:10 6FC kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 24 17:18:10 6FC kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 24 17:18:10 6FC kernel: [    0.000000] Initializing cgroup subsys cpuacct
Feb 24 17:18:10 6FC kernel: [    0.000000] Linux version 4.2.0-42-generic (buildd@lgw01-55) (gcc version 4.8.4 ($
Feb 24 17:18:10 6FC kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.2.0-42-generic root=/dev/mapper/6$
Feb 24 17:18:10 6FC kernel: [    0.000000] KERNEL supported cpus:
Feb 24 17:18:10 6FC kernel: [    0.000000]   Intel GenuineIntel
Feb 24 17:18:10 6FC kernel: [    0.000000]   AMD AuthenticAMD
Feb 24 17:18:10 6FC kernel: [    0.000000]   Centaur CentaurHauls

```


Not really knowing what I'm looking for in dmesg, these are the last lines from dmesg.0:

```

[   13.050557] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 1, phy 1, sas_addr 0x1221000001000000
[   13.053201] scsi 2:0:1:0: Direct-Access     ATA      ST3500312CS      SC13 PQ: 0 ANSI: 5
[   13.055327] sd 2:0:0:0: [sda] Write Protect is off
[   13.055365] sd 2:0:0:0: [sda] Mode Sense: 73 00 00 08
[   13.056234] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.057866] sd 2:0:1:0: Attached scsi generic sg1 type 0
[   13.059281] sd 2:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[   13.065757]  sda: sda1 sda2 < sda5 >
[   13.072666] sd 2:0:0:0: [sda] Attached SCSI disk
[   13.079785] sd 2:0:1:0: [sdb] Write Protect is off
[   13.079824] sd 2:0:1:0: [sdb] Mode Sense: 73 00 00 08
[   13.093596] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.164748]  sdb: sdb1
[   13.227816] sd 2:0:1:0: [sdb] Attached SCSI disk
[   13.254021] random: lvm urandom read with 65 bits of entropy available
[   18.663623] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[   18.663663] EXT4-fs (dm-0): write access will be enabled during recovery
[   18.775379] random: nonblocking pool is initialized
[   19.328546] EXT4-fs (dm-0): orphan cleanup on readonly fs
[   19.331020] EXT4-fs (dm-0): 6 orphan inodes deleted
[   19.331043] EXT4-fs (dm-0): recovery complete
[   19.341091] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   23.234998] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   23.315192] systemd-udevd[442]: starting version 204
[   23.319360] FS-Cache: Loaded
[   23.330528] FS-Cache: Netfs 'cifs' registered for caching
[   23.330648] Key type cifs.spnego registered
[   23.330652] Key type cifs.idmap registered
[   23.334040] CIFS VFS: Error connecting to socket. Aborting operation.
[   23.334757] CIFS VFS: cifs_mount failed w/return code = -101
[   23.349009] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.359239] lp: driver loaded but no devices found
[   23.377318] ppdev: user-space parallel port driver
[   23.383138] EDAC MC: Ver: 3.0.0
[   23.388714] EDAC MC0: Giving out device to module i5100_edac.c controller i5100: DEV 0000:00:10.1 (POLLED)
[   23.417950] ACPI Warning: SystemIO range 0x0000000000000828-0x000000000000082F conflicts with OpRegion 0x0000$
[   23.417952] ACPI: If an ACPI driver is available for this device, you should use it instead of the native dri$
[   23.417959] ACPI Warning: SystemIO range 0x0000000000000480-0x00000000000004AF conflicts with OpRegion 0x0000$
[   23.417959] ACPI: If an ACPI driver is available for this device, you should use it instead of the native dri$
[   23.418002] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   23.471473] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   23.472578] CIFS VFS: Error connecting to socket. Aborting operation.
[   23.474296] CIFS VFS: cifs_mount failed w/return code = -101
[   23.489347] audit: type=1400 audit(1487938475.780:2): apparmor="STATUS" operation="profile_load" profile="unc$
[   23.489353] audit: type=1400 audit(1487938475.780:3): apparmor="STATUS" operation="profile_load" profile="unc$
[   23.489357] audit: type=1400 audit(1487938475.780:4): apparmor="STATUS" operation="profile_load" profile="unc$
[   23.489588] audit: type=1400 audit(1487938475.780:5): apparmor="STATUS" operation="profile_replace" profile="$
[   23.489598] audit: type=1400 audit(1487938475.780:6): apparmor="STATUS" operation="profile_replace" profile="$
[   23.489603] audit: type=1400 audit(1487938475.780:7): apparmor="STATUS" operation="profile_replace" profile="$
[   23.489836] audit: type=1400 audit(1487938475.780:8): apparmor="STATUS" operation="profile_replace" profile="$
[   23.489843] audit: type=1400 audit(1487938475.780:9): apparmor="STATUS" operation="profile_replace" profile="$
[   23.490087] audit: type=1400 audit(1487938475.780:10): apparmor="STATUS" operation="profile_replace" profile=$
[   23.490092] audit: type=1400 audit(1487938475.780:11): apparmor="STATUS" operation="profile_replace" profile=$
[   23.502809] gpio_ich: GPIO from 451 to 511 on gpio_ich
[   23.623162] media: Linux media interface: v0.10
[   23.628271] Linux video capture interface: v2.00
[   23.638018] uvcvideo: Found UVC 1.00 device Microsoft LifeCam VX-5000 (045e:0728)
[   23.640186] input: Microsoft LifeCam VX-5000 as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input8
[   23.640309] usbcore: registered new interface driver uvcvideo
[   23.640310] USB Video Class driver (1.1.1)
[   23.672753] usbcore: registered new interface driver snd-usb-audio
[   23.972992] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   23.988444] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   24.144489] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.907873] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   26.106946] Bluetooth: Core ver 2.20
[   26.106962] NET: Registered protocol family 31
[   26.106962] Bluetooth: HCI device and connection manager initialized
[   26.106967] Bluetooth: HCI socket layer initialized
[   26.106969] Bluetooth: L2CAP socket layer initialized
[   26.106979] Bluetooth: SCO socket layer initialized
[   26.111842] Bluetooth: RFCOMM TTY layer initialized
[   26.111852] Bluetooth: RFCOMM socket layer initialized
[   26.111857] Bluetooth: RFCOMM ver 1.11
[   26.115333] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.115335] Bluetooth: BNEP filters: protocol multicast
[   26.115340] Bluetooth: BNEP socket layer initialized
[   26.131320] init: cups main process (886) killed by HUP signal
[   26.131330] init: cups main process ended, respawning
[   26.184579] init: samba-ad-dc main process (921) terminated with status 1
[   26.280870] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   26.281018] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.144090] CIFS VFS: Error connecting to socket. Aborting operation.
[   30.144712] CIFS VFS: cifs_mount failed w/return code = -113
[   36.322174] init: failsafe main process (830) killed by TERM signal
[   36.572597] audit_printk_skb: 15 callbacks suppressed
[   36.572599] audit: type=1400 audit(1487938488.864:17): apparmor="STATUS" operation="profile_load" profile="un$
[   36.572643] audit: type=1400 audit(1487938488.864:18): apparmor="STATUS" operation="profile_load" profile="un$
[   36.572832] audit: type=1400 audit(1487938488.864:19): apparmor="STATUS" operation="profile_replace" profile=$
[   36.572841] audit: type=1400 audit(1487938488.864:20): apparmor="STATUS" operation="profile_replace" profile=$
[   36.572846] audit: type=1400 audit(1487938488.864:21): apparmor="STATUS" operation="profile_replace" profile=$
[   36.573326] audit: type=1400 audit(1487938488.864:22): apparmor="STATUS" operation="profile_replace" profile=$
[   36.573331] audit: type=1400 audit(1487938488.864:23): apparmor="STATUS" operation="profile_replace" profile=$
[   36.573576] audit: type=1400 audit(1487938488.864:24): apparmor="STATUS" operation="profile_replace" profile=$
[   36.573828] audit: type=1400 audit(1487938488.864:25): apparmor="STATUS" operation="profile_load" profile="un$
[   36.573845] audit: type=1400 audit(1487938488.864:26): apparmor="STATUS" operation="profile_replace" profile=$
[   36.624577] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
```



and some from dmesg.1:

```
[   19.654182] EXT4-fs (dm-0): orphan cleanup on readonly fs
[   19.656627] EXT4-fs (dm-0): 6 orphan inodes deleted
[   19.656669] EXT4-fs (dm-0): recovery complete
[   19.676029] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   23.511288] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   23.927062] systemd-udevd[449]: starting version 204
[   23.953887] FS-Cache: Loaded
[   23.956646] lp: driver loaded but no devices found
[   23.965485] FS-Cache: Netfs 'cifs' registered for caching
[   23.965619] Key type cifs.spnego registered
[   23.965624] Key type cifs.idmap registered
[   23.969321] ppdev: user-space parallel port driver
[   23.972152] CIFS VFS: Error connecting to socket. Aborting operation.
[   23.972760] CIFS VFS: cifs_mount failed w/return code = -101
[   24.014727] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.027827] CIFS VFS: Error connecting to socket. Aborting operation.
[   24.028023] CIFS VFS: cifs_mount failed w/return code = -101
[   24.043048] EDAC MC: Ver: 3.0.0
[   24.047761] EDAC MC0: Giving out device to module i5100_edac.c controller i5100: DEV 0000:00:10.1 (POLLED)
[   24.068736] ACPI Warning: SystemIO range 0x0000000000000828-0x000000000000082F conflicts with OpRegion 0x0000$
[   24.068737] ACPI: If an ACPI driver is available for this device, you should use it instead of the native dri$
[   24.068752] ACPI Warning: SystemIO range 0x0000000000000480-0x00000000000004AF conflicts with OpRegion 0x0000$
[   24.068753] ACPI: If an ACPI driver is available for this device, you should use it instead of the native dri$
[   24.068817] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   24.071117] audit: type=1400 audit(1487930440.367:2): apparmor="STATUS" operation="profile_load" profile="unc$
[   24.071124] audit: type=1400 audit(1487930440.367:3): apparmor="STATUS" operation="profile_load" profile="unc$
[   24.071128] audit: type=1400 audit(1487930440.367:4): apparmor="STATUS" operation="profile_load" profile="unc$
[   24.071597] audit: type=1400 audit(1487930440.367:5): apparmor="STATUS" operation="profile_replace" profile="$
[   24.071603] audit: type=1400 audit(1487930440.367:6): apparmor="STATUS" operation="profile_replace" profile="$
[   24.071845] audit: type=1400 audit(1487930440.367:7): apparmor="STATUS" operation="profile_replace" profile="$
[   24.074325] media: Linux media interface: v0.10
[   24.079653] Linux video capture interface: v2.00
[   24.098771] uvcvideo: Found UVC 1.00 device Microsoft LifeCam VX-5000 (045e:0728)
[   24.102788] input: Microsoft LifeCam VX-5000 as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input8
[   24.102911] usbcore: registered new interface driver uvcvideo
[   24.102912] USB Video Class driver (1.1.1)
[   24.125786] usbcore: registered new interface driver snd-usb-audio
[   24.159997] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   24.181082] gpio_ich: GPIO from 451 to 511 on gpio_ich
[   24.580505] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.698736] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   24.704965] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   26.536870] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   26.537012] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.827641] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   28.055957] audit: type=1400 audit(1487930444.351:8): apparmor="STATUS" operation="profile_load" profile="unc$
[   28.055970] audit: type=1400 audit(1487930444.351:9): apparmor="STATUS" operation="profile_load" profile="unc$
[   28.056579] audit: type=1400 audit(1487930444.355:10): apparmor="STATUS" operation="profile_replace" profile=$
[   28.073932] Bluetooth: Core ver 2.20
[   28.073952] NET: Registered protocol family 31
[   28.073952] Bluetooth: HCI device and connection manager initialized
[   28.073959] Bluetooth: HCI socket layer initialized
[   28.073962] Bluetooth: L2CAP socket layer initialized
[   28.073969] Bluetooth: SCO socket layer initialized
[   28.077705] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.077706] Bluetooth: BNEP filters: protocol multicast
[   28.077709] Bluetooth: BNEP socket layer initialized
[   28.083007] Bluetooth: RFCOMM TTY layer initialized
[   28.083013] Bluetooth: RFCOMM socket layer initialized
[   28.083017] Bluetooth: RFCOMM ver 1.11
[   28.118995] init: samba-ad-dc main process (910) terminated with status 1
[   28.602204] audit: type=1400 audit(1487930444.899:11): apparmor="STATUS" operation="profile_load" profile="un$
[   30.604091] CIFS VFS: Error connecting to socket. Aborting operation.
[   30.604970] CIFS VFS: cifs_mount failed w/return code = -113
[   36.789515] init: failsafe main process (816) killed by TERM signal
[   37.045582] audit: type=1400 audit(1487930453.343:12): apparmor="STATUS" operation="profile_replace" profile=$
[   37.045879] audit: type=1400 audit(1487930453.343:13): apparmor="STATUS" operation="profile_load" profile="un$
[   37.045960] audit: type=1400 audit(1487930453.343:14): apparmor="STATUS" operation="profile_replace" profile=$
[   37.045971] audit: type=1400 audit(1487930453.343:15): apparmor="STATUS" operation="profile_replace" profile=$
[   37.045976] audit: type=1400 audit(1487930453.343:16): apparmor="STATUS" operation="profile_replace" profile=$
[   37.046440] audit: type=1400 audit(1487930453.343:17): apparmor="STATUS" operation="profile_replace" profile=$
[   37.046445] audit: type=1400 audit(1487930453.343:18): apparmor="STATUS" operation="profile_replace" profile=$
[   37.046687] audit: type=1400 audit(1487930453.343:19): apparmor="STATUS" operation="profile_replace" profile=$
[   37.046886] audit: type=1400 audit(1487930453.343:20): apparmor="STATUS" operation="profile_replace" profile=$
[   37.046897] audit: type=1400 audit(1487930453.343:21): apparmor="STATUS" operation="profile_replace" profile=$
[   37.088572] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
```



Many thanks, Scott.

Now some from the end of kern.log of the same shutdown:

```

Feb 24 12:14:38 6FC kernel: [   23.489843] audit: type=1400 audit(1487938475.780:9): apparmor="STATUS" operation$
Feb 24 12:14:38 6FC kernel: [   23.490087] audit: type=1400 audit(1487938475.780:10): apparmor="STATUS" operatio$
Feb 24 12:14:38 6FC kernel: [   23.490092] audit: type=1400 audit(1487938475.780:11): apparmor="STATUS" operatio$
Feb 24 12:14:38 6FC kernel: [   23.502809] gpio_ich: GPIO from 451 to 511 on gpio_ich
Feb 24 12:14:38 6FC kernel: [   23.623162] media: Linux media interface: v0.10
Feb 24 12:14:38 6FC kernel: [   23.628271] Linux video capture interface: v2.00
Feb 24 12:14:38 6FC kernel: [   23.638018] uvcvideo: Found UVC 1.00 device Microsoft LifeCam VX-5000 (045e:0728)
Feb 24 12:14:38 6FC kernel: [   23.640186] input: Microsoft LifeCam VX-5000 as /devices/pci0000:00/0000:00:1d.7/$
Feb 24 12:14:38 6FC kernel: [   23.640309] usbcore: registered new interface driver uvcvideo
Feb 24 12:14:38 6FC kernel: [   23.640310] USB Video Class driver (1.1.1)
Feb 24 12:14:38 6FC kernel: [   23.672753] usbcore: registered new interface driver snd-usb-audio
Feb 24 12:14:38 6FC kernel: [   23.972992] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
Feb 24 12:14:38 6FC kernel: [   23.988444] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
Feb 24 12:14:38 6FC kernel: [   24.144489] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 24 12:14:38 6FC kernel: [   25.907873] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (nul$
Feb 24 12:14:38 6FC kernel: [   26.106946] Bluetooth: Core ver 2.20
Feb 24 12:14:38 6FC kernel: [   26.106962] NET: Registered protocol family 31
Feb 24 12:14:38 6FC kernel: [   26.106962] Bluetooth: HCI device and connection manager initialized
Feb 24 12:14:38 6FC kernel: [   26.106967] Bluetooth: HCI socket layer initialized
Feb 24 12:14:38 6FC kernel: [   26.106969] Bluetooth: L2CAP socket layer initialized
Feb 24 12:14:38 6FC kernel: [   26.106979] Bluetooth: SCO socket layer initialized
Feb 24 12:14:38 6FC kernel: [   26.111842] Bluetooth: RFCOMM TTY layer initialized
Feb 24 12:14:38 6FC kernel: [   26.111852] Bluetooth: RFCOMM socket layer initialized
Feb 24 12:14:38 6FC kernel: [   26.111857] Bluetooth: RFCOMM ver 1.11
Feb 24 12:14:38 6FC kernel: [   26.115333] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 24 12:14:38 6FC kernel: [   26.115335] Bluetooth: BNEP filters: protocol multicast
Feb 24 12:14:38 6FC kernel: [   26.115340] Bluetooth: BNEP socket layer initialized
Feb 24 12:14:38 6FC kernel: [   26.280870] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Feb 24 12:14:38 6FC kernel: [   26.281018] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb 24 12:14:42 6FC kernel: [   30.144090] CIFS VFS: Error connecting to socket. Aborting operation.
Feb 24 12:14:42 6FC kernel: [   30.144712] CIFS VFS: cifs_mount failed w/return code = -113
Feb 24 12:14:48 6FC kernel: [   36.572597] audit_printk_skb: 15 callbacks suppressed
Feb 24 12:14:48 6FC kernel: [   36.572599] audit: type=1400 audit(1487938488.864:17): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.572643] audit: type=1400 audit(1487938488.864:18): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.572832] audit: type=1400 audit(1487938488.864:19): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.572841] audit: type=1400 audit(1487938488.864:20): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.572846] audit: type=1400 audit(1487938488.864:21): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.573326] audit: type=1400 audit(1487938488.864:22): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.573331] audit: type=1400 audit(1487938488.864:23): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.573576] audit: type=1400 audit(1487938488.864:24): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.573828] audit: type=1400 audit(1487938488.864:25): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.573845] audit: type=1400 audit(1487938488.864:26): apparmor="STATUS" operatio$
Feb 24 12:14:48 6FC kernel: [   36.624577] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 24 12:14:54 6FC kernel: [   42.376060] CIFS VFS: Error connecting to socket. Aborting operation.
Feb 24 12:14:54 6FC kernel: [   42.377314] CIFS VFS: cifs_mount failed w/return code = -113
Feb 24 12:15:08 6FC kernel: [   56.161733] audit_printk_skb: 120 callbacks suppressed
Feb 24 12:15:08 6FC kernel: [   56.161740] audit: type=1400 audit(1487938508.452:67): apparmor="STATUS" operatio$
Feb 24 12:15:08 6FC kernel: [   56.161753] audit: type=1400 audit(1487938508.452:68): apparmor="STATUS" operatio$
Feb 24 12:15:08 6FC kernel: [   56.162224] audit: type=1400 audit(1487938508.452:69): apparmor="STATUS" operatio$
Feb 24 12:19:19 6FC kernel: [  332.316363] perf interrupt took too long (2519 > 2500), lowering kernel.perf_even$
Feb 24 12:29:41 6FC kernel: [  954.090859] CPU1: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:29:41 6FC kernel: [  954.091245] CPU1: Core temperature/speed normal
Feb 24 12:30:50 6FC kernel: [ 1022.695655] CPU7: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:30:50 6FC kernel: [ 1022.696039] CPU7: Core temperature/speed normal
Feb 24 12:33:47 6FC kernel: [ 1199.636270] perf interrupt took too long (5026 > 5000), lowering kernel.perf_even$
Feb 24 12:33:47 6FC kernel: [ 1199.812020] mce: [Hardware Error]: Machine check events logged
Feb 24 12:34:41 6FC kernel: [ 1254.101367] CPU1: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:35:50 6FC kernel: [ 1322.696831] CPU7: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:35:50 6FC kernel: [ 1322.697218] CPU7: Core temperature/speed normal
Feb 24 12:36:17 6FC kernel: [ 1349.812024] mce: [Hardware Error]: Machine check events logged
Feb 24 12:37:29 6FC kernel: [ 1421.774543] CPU5: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:37:29 6FC kernel: [ 1421.774929] CPU5: Core temperature/speed normal
Feb 24 12:37:32 6FC kernel: [ 1424.812027] mce: [Hardware Error]: Machine check events logged
Feb 24 12:39:41 6FC kernel: [ 1554.100374] CPU1: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:40:50 6FC kernel: [ 1622.697688] CPU7: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:40:50 6FC kernel: [ 1622.698074] CPU7: Core temperature/speed normal
Feb 24 12:41:55 6FC kernel: [ 1687.812015] mce: [Hardware Error]: Machine check events logged
Feb 24 12:45:18 6FC kernel: [ 1891.195485] CPU0: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:45:18 6FC kernel: [ 1891.195870] CPU0: Core temperature/speed normal
Feb 24 12:45:25 6FC kernel: [ 1898.026085] CPU6: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:45:25 6FC kernel: [ 1898.026469] CPU6: Core temperature/speed normal
Feb 24 12:45:40 6FC kernel: [ 1912.812018] mce: [Hardware Error]: Machine check events logged
Feb 24 12:45:50 6FC kernel: [ 1922.696514] CPU7: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:45:50 6FC kernel: [ 1922.696891] CPU7: Core temperature/speed normal
Feb 24 12:46:49 6FC kernel: [ 1981.489536] perf interrupt took too long (10012 > 10000), lowering kernel.perf_ev$
Feb 24 12:46:55 6FC kernel: [ 1987.812019] mce: [Hardware Error]: Machine check events logged
Feb 24 12:47:30 6FC kernel: [ 2023.008036] CPU5: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:47:30 6FC kernel: [ 2023.008406] CPU5: Core temperature/speed normal
Feb 24 12:47:33 6FC kernel: [ 2025.812023] mce: [Hardware Error]: Machine check events logged
Feb 24 12:50:43 6FC kernel: [ 2215.733129] CPU0: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:50:43 6FC kernel: [ 2215.733515] CPU0: Core temperature/speed normal
Feb 24 12:50:50 6FC kernel: [ 2222.722093] CPU7: Core temperature/speed normal
Feb 24 12:51:18 6FC kernel: [ 2251.426433] CPU4: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:51:18 6FC kernel: [ 2251.426819] CPU4: Core temperature/speed normal
Feb 24 12:52:15 6FC kernel: [ 2307.812015] mce: [Hardware Error]: Machine check events logged
Feb 24 12:52:32 6FC kernel: [ 2324.767824] CPU5: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:53:30 6FC kernel: [ 2382.812018] mce: [Hardware Error]: Machine check events logged
Feb 24 12:55:22 6FC kernel: [ 2494.813197] CPU3: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:55:22 6FC kernel: [ 2494.813202] CPU1: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:55:22 6FC kernel: [ 2494.813577] CPU3: Core temperature/speed normal
Feb 24 12:55:23 6FC kernel: [ 2495.812019] mce: [Hardware Error]: Machine check events logged
Feb 24 12:55:43 6FC kernel: [ 2515.888845] CPU0: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:55:43 6FC kernel: [ 2515.889231] CPU0: Core temperature/speed normal
Feb 24 12:56:01 6FC kernel: [ 2533.812015] mce: [Hardware Error]: Machine check events logged
Feb 24 12:56:24 6FC kernel: [ 2556.738890] CPU6: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 12:56:24 6FC kernel: [ 2556.739274] CPU6: Core temperature/speed normal
Feb 24 13:00:24 6FC kernel: [ 2796.655218] CPU1: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 13:00:24 6FC kernel: [ 2796.655222] CPU3: Core temperature/speed normal
Feb 24 13:00:43 6FC kernel: [ 2815.911768] CPU0: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 13:01:24 6FC kernel: [ 2856.759527] CPU4: Core temperature/speed normal
Feb 24 13:05:43 6FC kernel: [ 3116.043219] CPU0: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 13:05:43 6FC kernel: [ 3116.043605] CPU0: Core temperature/speed normal
Feb 24 13:06:24 6FC kernel: [ 3156.757318] CPU4: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 13:06:24 6FC kernel: [ 3156.757705] CPU4: Core temperature/speed normal
Feb 24 13:10:43 6FC kernel: [ 3416.078993] CPU0: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 13:10:43 6FC kernel: [ 3416.079388] CPU0: Core temperature/speed normal
Feb 24 13:11:24 6FC kernel: [ 3456.756035] CPU4: Core temperature above threshold, cpu clock throttled (total ev$
Feb 24 17:18:10 6FC kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 24 17:18:10 6FC kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 24 17:18:10 6FC kernel: [    0.000000] Initializing cgroup subsys cpuacct
```

Just run Sensors to see the CPU temps:

```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +96.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +94.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +94.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       -20.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       +98.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       -25.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 3:       -24.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)

```

Processor 0001 seems a bit wobbly (-24 and -25 degrees)... hope the power cuts didn't kill it....

Cheers, Scott.

and now a few minutes later....

```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +97.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +95.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +97.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +97.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       -18.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       -26.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 2:       -22.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 3:       -21.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)

```

It's a really cold day, shouldn't be overheating...

---

### Post by QIII on 2017-02-24
Hello!

The power issues could certainly have affected your hardware to bring that condition about.

As a first line of attack, I'd shut down for now, let it cool, and reboot to check your cooling solution for proper operation.  Perhaps the PSU flicker damaged your fans or the motherboard's power distribution.  The PSU itself may have been damaged.

---

### Post by scott.bouch on 2017-02-24
Hmmm...

All fans are working fine..

Just to get it limping along again, in your (the collective "your") experience, can I just remove the faulty processor and hope it boots on the one? Or do I have to fiddle about in BIOS to tell it there is only one processor present? Will the Ubuntu Kernel mind the difference or automatically adjust?

It's a DELL CS24-SC 1U high 19" rack server.

On the hottest day this summer, I did have issues with this processor getting hotter then the other and causing shutdows, ironically, a storm has finished it off!

Now it seems to run for an hour or so, until the processor has warmed up fully, then keels over... which is what it was doing in the summer on the hottest day.

Cheers, Scott.

---

### Post by DuckHook on 2017-02-24
All of your readings are crazy. Your second CPU reads -26° which is impossible either, no matter how cold the day.

At any rate, don't know enough about your HW to advise you re: BIOS settings, but I would suspect that your MOBO is toast. When booting, look at the actual temps being reported in BIOS if you can, rather than lm-sensors. Let it run a while and see. Also, physically check (I mean literally place your hand near) the CPUs and RAM for the temperature. Listening to fans tells you nothing. Your system could just be ignoring them.

Unfortunately, things don't look too good on the physical front. Problems are unlikely to have anything to do with the OS.

On a related note: if you are hooked up to a UPS, why didn't your servers shut down elegantly once low power threshold was reached?

---

### Post by scott.bouch on 2017-02-24
Ah, because I hadn't managed to figure out how to get it to shut down nicely....

I had installed NUT, but that was about as far as I got with it. One of those projects that only got so  far as more pressing tasks came up (as they always do).

hmmm.. Hope it's not the Motherboard... I'll have a poke around BIOS to see if it report CPU temps later tonight...

This Server has been fairly reliable over the last 3 years or so, but when it decides to be a pain, it is a royal pain. Mainly because it's one of DELL's Custom Servers, there is little information available on it.

Cheers, Scott.

---

### Post by SeijiSensei on 2017-02-24
If the UPS comes from APC, I recommend installing apcupsd, a nice little utility that monitors the UPS and can even tell other servers on the network to shut themselves down if the power goes out.

---

### Post by scott.bouch on 2017-02-24
Thanks for the tip, it is APC... I will look into this after the main issue is resolved!

Thanks, Scott

After just booting sensors reports healthy temps:

```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +71.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +64.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +63.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +65.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +73.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +70.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +70.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +69.0°C  (high = +84.0°C, crit = +100.0°C)

```

steadily climbing up a few minutes later:

```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +81.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +76.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +78.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +79.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +94.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +88.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +91.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +92.0°C  (high = +84.0°C, crit = +100.0°C)

```

And now 15 mins after booting, we start seeing crazy information....

```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +89.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +82.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +84.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +85.0°C  (high = +84.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       -25.0°C  (high = +84.0°C, crit = +100.0°C)  ALARM (CRIT)
Core 1:       +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +95.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +96.0°C  (high = +84.0°C, crit = +100.0°C)
```

So, I've been and pulled out CPU2 (isa-0001), and BIOS listed just the one, so no config required there.

It booted nicely, I logged in locally, performed sensors, all good on the one processor.

Now SSHing in, all seems good again... so far, as it's warming up.

CPU1 (isa-0000) has settled and stopped climbing in temperature, the fans seem to be doing their work.

```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +96.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +93.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +94.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +94.0°C  (high = +84.0°C, crit = +100.0°C)



```

Who needs 8 cores anyway?

Cheers, Scott.

---

### Post by DuckHook on 2017-02-24
I hate to be the pessimist here, but even if your CPU is running for now, it is hot enough to boil water at my elevation. This cannot be good. They are not meant to run at that temp and there is still something wrong with your box.

They should be running at 50° to 70° at most. As per my previous suggestion, did you actually try feeling them??? ***This is important***. lm-sensors could be reporting wrong readings because your thermistors are borked.

Your machine is still broken. You can not depend on it for anything important and at those temps, it is frankly a fire hazard.

---

### Post by cariboo on 2017-02-24
Just for comparison, this is the temps my dual core server is running at:

```
sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +39.0°C  (high = +76.0°C, crit = +100.0°C)
Core 1:       +37.0°C  (high = +76.0°C, crit = +100.0°C)
```

---

### Post by scott.bouch on 2017-03-03
Hi Cariboo,

Thank you for those examples, it's good to have a comparison.

These DELL CS24-SC servers (when you search online) are renowned for being too hot, fans running flat out to compensate. 

I feel that now is a good opportunity for me to change hardware. 

I plan to split up what I use my domain for, by:

Moving my website onto a Raspberry Pi: [https://www.scottbouch.com/raspberry-pi-webserver.html](https://www.scottbouch.com/raspberry-pi-webserver.html)
Moving my Mumble Server onto a second Raspberry Pi
Moving my Zoneminder CCTV software, and Plex Media Server onto a more basic computer.

To Achieve this I now face the challenge of trying to set up these independent servers with SSL security (maybe with subdomains and wildcard SSL from what I've read so far) and get organised with router port forwarding.

Clearly this project falls outside the scope of the Ubuntu forum, as it's more about networking and Linux web servers. Can anyone point me to a good forum where I may pose these questions, and get help to design the system architecture?

Many thanks, Scott.

---

### Post by scott.bouch on 2017-06-28
I have an update to this thread to record the changes, but also to help others with this issue.... 

I now have my Dell CS24-SC Intel XEON E5410 SLANW CPU core temperatures under control...

I've:
[LIST]
[*]Upgraded the heatsinks to a type suitable for a 2U high enclosure, so I've got to cut a hole in the lid of the server case so they can poke out. see: [https://www.amazon.co.uk/gp/product/B000H742D2/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B000H742D2/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1)
[*]Replaced the CPU's with like-for-like second hand off Ebay as one of my previous ones got burnt out with temperatures in excess of 100 degrees C.
[*]Installed CentOS as the operating system, just to try something new.
[/LIST]

I haven't yet got any software installed / running, but to baseline the machine before installation, here are my core temperatures as of running for an hour or so indoors in a roughly 23 degree C room:

```

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +65.0°C  (high = +88.0°C, crit = +100.0°C)
Core 1:       +53.0°C  (high = +88.0°C, crit = +100.0°C)
Core 2:       +50.0°C  (high = +88.0°C, crit = +100.0°C)
Core 3:       +55.0°C  (high = +88.0°C, crit = +100.0°C)


coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +59.0°C  (high = +88.0°C, crit = +100.0°C)
Core 1:       +51.0°C  (high = +88.0°C, crit = +100.0°C)
Core 2:       +52.0°C  (high = +88.0°C, crit = +100.0°C)
Core 3:       +67.0°C  (high = +88.0°C, crit = +100.0°C)

```

Cheers, Scott.

---

