---
title: "dmesg(command) log not exist in /var/log/dmesg"
date: 2010-07-19
forum: Server Platforms
---

### Post by sirkubax on 2010-07-19
Hello, 

I would like to find where logs form dmesg(command) are stored on my hdd drive.
I'm testing broken hdd with badsectors, and i've got some i/o errors, that i can read (just the most recent) using dmesg command (dmesg buffer)
I would like to see whole log, that is interesting for me, but i cannot find where it is stored in /var/log

dmesg command(buffer) (last few lines)
```
[245129.080558] end_request: I/O error, dev sdb, sector 218246624
[245129.080562] Buffer I/O error on device sdb, logical block 27280828
[245132.037921] sd 2:0:0:0: [sdb] Unhandled sense code
[245132.037925] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[245132.037928] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] 
[245132.037932] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[245132.037936] end_request: I/O error, dev sdb, sector 218246624
[245132.037940] Buffer I/O error on device sdb, logical block 27280828
[245163.104010] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[245163.220006] usb 1-7: device descriptor read/64, error -32
[245163.440007] usb 1-7: device descriptor read/64, error -32
[245163.655306] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[245163.768005] usb 1-7: device descriptor read/64, error -32
[245163.988005] usb 1-7: device descriptor read/64, error -32
[245164.204006] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[245164.234407] usb 1-7: device descriptor read/8, error -71
[245164.368164] usb 1-7: device descriptor read/8, error -71
[245164.584006] usb 1-7: reset high speed USB device using ehci_hcd and address 3
[245164.616172] usb 1-7: device descriptor read/8, error -71
[245164.748181] usb 1-7: device descriptor read/8, error -71
[245164.852028] sd 2:0:0:0: Device offlined - not ready after error recovery
[245164.852038] sd 2:0:0:0: [sdb] Unhandled error code
[245164.852040] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[245164.852043] end_request: I/O error, dev sdb, sector 218246632
[245164.852047] Buffer I/O error on device sdb, logical block 27280829
[245164.852049] lost page write due to I/O error on sdb
[245164.852055] Buffer I/O error on device sdb, logical block 27280830
[245164.852057] lost page write due to I/O error on sdb
[245164.852060] Buffer I/O error on device sdb, logical block 27280831
[245164.852061] lost page write due to I/O error on sdb
[245164.852064] Buffer I/O error on device sdb, logical block 27280832
[245164.852066] lost page write due to I/O error on sdb
[245164.852068] Buffer I/O error on device sdb, logical block 27280833
[245164.852070] lost page write due to I/O error on sdb
[245164.852073] Buffer I/O error on device sdb, logical block 27280834
[245164.852074] lost page write due to I/O error on sdb
[245164.852077] Buffer I/O error on device sdb, logical block 27280835
[245164.852078] lost page write due to I/O error on sdb
[245164.852081] Buffer I/O error on device sdb, logical block 27280836
[245164.852082] lost page write due to I/O error on sdb
[245164.852085] Buffer I/O error on device sdb, logical block 27280837
[245164.852087] lost page write due to I/O error on sdb
[245164.852089] Buffer I/O error on device sdb, logical block 27280838
[245164.852091] lost page write due to I/O error on sdb
[245164.852113] sd 2:0:0:0: rejecting I/O to offline device
[245164.852123] sd 2:0:0:0: [sdb] Unhandled error code
[245164.852125] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[245164.852128] end_request: I/O error, dev sdb, sector 218246536
[245164.852513] usb 1-7: USB disconnect, address 3
[245164.852563] sd 2:0:0:0: rejecting I/O to offline device
[245165.080514] usb 1-7: new high speed USB device using ehci_hcd and address 4
[245165.236511] usb 1-7: device descriptor read/64, error -32
[245165.500511] usb 1-7: device descriptor read/64, error -32
[245165.724510] usb 1-7: new high speed USB device using ehci_hcd and address 5
[245165.880510] usb 1-7: device descriptor read/64, error -32
[245166.144511] usb 1-7: device descriptor read/64, error -32
[245166.376510] usb 1-7: new high speed USB device using ehci_hcd and address 6
[245166.456505] usb 1-7: device descriptor read/8, error -71
[245166.620506] usb 1-7: device descriptor read/8, error -71
[245166.844511] usb 1-7: new high speed USB device using ehci_hcd and address 7
[245166.920506] usb 1-7: device descriptor read/8, error -71
[245167.080506] usb 1-7: device descriptor read/8, error -71
[245167.188516] hub 1-0:1.0: unable to enumerate USB device on port 7
[245167.556511] usb 5-1: new full speed USB device using uhci_hcd and address 2
[245167.712509] usb 5-1: device descriptor read/64, error -32
[245167.968510] usb 5-1: device descriptor read/64, error -32
[245168.196511] usb 5-1: new full speed USB device using uhci_hcd and address 3
[245168.352511] usb 5-1: device descriptor read/64, error -32
[245168.612510] usb 5-1: device descriptor read/64, error -32
[245168.840511] usb 5-1: new full speed USB device using uhci_hcd and address 4
[245168.908506] usb 5-1: device descriptor read/8, error -71
[245169.072507] usb 5-1: device descriptor read/8, error -71
[245169.300511] usb 5-1: new full speed USB device using uhci_hcd and address 5
[245169.368506] usb 5-1: device descriptor read/8, error -71
[245169.532506] usb 5-1: device descriptor read/8, error -71
[245169.640518] hub 5-0:1.0: unable to enumerate USB device on port 1

```


and most recent /var/log/dmesg
```
[   10.212306] lp: driver loaded but no devices found
[   10.213502] parport_pc 00:09: reported by Plug and Play ACPI
[   10.213547] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.219869] ppdev: user-space parallel port driver
[   10.308729] lp0: using parport0 (interrupt-driven).
[   10.449546] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.321809] __ratelimit: 12 callbacks suppressed
[   12.321812] type=1505 audit(1279271254.725:15): operation="profile_replace" pid=1232 name=/usr/share/gdm/guest-session/Xsession
[   12.323548] type=1505 audit(1279271254.725:16): operation="profile_replace" pid=1233 name=/sbin/dhclient3
[   12.324171] type=1505 audit(1279271254.725:17): operation="profile_replace" pid=1233 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.324504] type=1505 audit(1279271254.729:18): operation="profile_replace" pid=1233 name=/usr/lib/connman/scripts/dhclient-script
[   12.328494] type=1505 audit(1279271254.729:19): operation="profile_replace" pid=1234 name=/usr/bin/evince
[   12.338340] type=1505 audit(1279271254.741:20): operation="profile_replace" pid=1234 name=/usr/bin/evince-previewer
[   12.344102] type=1505 audit(1279271254.745:21): operation="profile_replace" pid=1234 name=/usr/bin/evince-thumbnailer
[   12.352187] type=1505 audit(1279271254.753:22): operation="profile_replace" pid=1236 name=/usr/bin/virt-aa-helper
[   12.353753] type=1505 audit(1279271254.757:23): operation="profile_replace" pid=1237 name=/usr/lib/cups/backend/cups-pdf
[   12.354493] type=1505 audit(1279271254.757:24): operation="profile_replace" pid=1237 name=/usr/sbin/cupsd
[   15.988199] md: bind<sda6>

```

/var/log/syslog des not contain any interesting info
/var/log/messages
```
Jul 16 12:40:47 gamma kernel: [ 5568.283349] Initializing USB Mass Storage driver...
Jul 16 12:40:47 gamma kernel: [ 5568.283892] scsi2 : SCSI emulation for USB Mass Storage devices
Jul 16 12:40:47 gamma kernel: [ 5568.284116] usbcore: registered new interface driver usb-storage
Jul 16 12:40:47 gamma kernel: [ 5568.284121] USB Mass Storage support registered.
Jul 16 12:40:52 gamma kernel: [ 5573.280661] scsi 2:0:0:0: Direct-Access     StoreJet Transcend             PQ: 0 ANSI: 2 CCS
Jul 16 12:40:52 gamma kernel: [ 5573.281281] sd 2:0:0:0: Attached scsi generic sg1 type 0
Jul 16 12:40:52 gamma kernel: [ 5573.282870] sd 2:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jul 16 12:40:52 gamma kernel: [ 5573.283629] sd 2:0:0:0: [sdb] Write Protect is off
Jul 16 12:40:52 gamma kernel: [ 5573.288032]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 sdb7 sdb8 >
Jul 16 12:40:52 gamma kernel: [ 5573.383528] sd 2:0:0:0: [sdb] Attached SCSI disk
Jul 17 07:38:53 gamma rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="587" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 18 07:43:59 gamma rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="587" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

```


so, no hint of i/o errors
i went through other log files, but no single line visible in dmesg buffer
do you have any idea where it can be stored?
sirkubax



btw
my /var/log 
interesting information should be stored in files form 18.07.2010 (so older files are not important - i have not been searching in those files)
```

jacek@gamma:/var/log$ ls -la
total 2416
drwxr-xr-x 20 root              root       4096 2010-07-19 08:03 .
drwxr-xr-x 16 root              root       4096 2009-12-23 22:40 ..
drwxr-x---  2 root              adm        4096 2010-07-19 08:03 apache2
drwxr-xr-x  2 root              root       4096 2009-10-17 06:40 apparmor
drwxr-xr-x  2 root              root       4096 2010-07-01 07:57 apt
-rw-r--r--  1 root              root          0 2010-01-01 07:49 aptitude
-rw-r--r--  1 root              root        210 2009-12-23 19:11 aptitude.1.gz
-rw-r-----  1 syslog            adm      120969 2010-07-19 11:20 auth.log
-rw-r-----  1 syslog            adm      548876 2010-07-18 07:40 auth.log.1
-rw-r-----  1 syslog            adm       41243 2010-07-11 07:40 auth.log.2.gz
-rw-r-----  1 syslog            adm       41904 2010-07-04 08:00 auth.log.3.gz
-rw-r-----  1 syslog            adm        6088 2010-06-27 08:00 auth.log.4.gz
-rw-r-----  1 root              adm          31 2009-12-23 18:42 boot
-rw-rw----  1 root              utmp       1152 2010-07-15 00:54 btmp
-rw-rw----  1 root              utmp         62 2010-06-28 14:46 btmp.1.gz
drwxr-xr-x  2 www-data          www-data   4096 2010-07-18 07:43 cacti
drwxr-xr-x  2 root              root       4096 2010-07-18 07:43 ConsoleKit
drwxr-xr-x  2 root              root       4096 2010-07-16 11:38 cups
-rw-r-----  1 syslog            adm           0 2010-07-18 07:43 daemon.log
-rw-r-----  1 syslog            adm       60089 2010-07-16 14:17 daemon.log.1
-rw-r-----  1 syslog            adm         488 2010-07-08 12:13 daemon.log.2.gz
-rw-r-----  1 syslog            adm         588 2010-07-04 00:57 daemon.log.3.gz
-rw-r-----  1 syslog            adm        3176 2010-06-28 15:00 daemon.log.4.gz
drwxr-xr-x  2 root              root       4096 2009-12-23 22:40 dbconfig-common
-rw-r-----  1 syslog            adm           0 2010-07-18 07:43 debug
-rw-r-----  1 syslog            adm       19429 2010-07-16 12:40 debug.1
-rw-r-----  1 syslog            adm        4265 2010-07-15 14:15 debug.2.gz
-rw-r-----  1 syslog            adm          95 2010-06-30 00:26 debug.3.gz
-rw-r-----  1 syslog            adm        2760 2010-06-28 15:00 debug.4.gz
drwxr-xr-x  2 root              root       4096 2009-10-23 18:21 dist-upgrade
-rw-r-----  1 root              adm       44452 2010-07-16 11:08 dmesg
-rw-r-----  1 root              adm       45196 2010-07-15 14:13 dmesg.0
-rw-r-----  1 root              adm       12548 2010-07-14 20:17 dmesg.1.gz
-rw-r-----  1 root              adm       12593 2010-06-28 15:01 dmesg.2.gz
-rw-r-----  1 root              adm       12127 2010-06-26 01:17 dmesg.3.gz
-rw-r-----  1 root              adm       13234 2010-06-03 23:52 dmesg.4.gz
-rw-r--r--  1 root              root       1610 2010-07-16 13:46 dpkg.log
-rw-r--r--  1 root              root       7902 2010-06-05 01:29 dpkg.log.1
-rw-r--r--  1 root              root       1484 2010-06-03 23:48 dpkg.log.2.gz
-rw-r--r--  1 root              root       8510 2010-02-22 12:49 dpkg.log.3.gz
-rw-r--r--  1 root              root       1948 2010-01-10 14:30 dpkg.log.4.gz
-rw-r--r--  1 root              root      89050 2009-12-28 01:25 dpkg.log.5.gz
-rw-r--r--  1 root              root      24024 2010-03-20 06:15 faillog
-rw-r--r--  1 root              root       2215 2009-12-23 19:21 fontconfig.log
drwxr-xr-x  2 root              root       4096 2009-12-23 18:42 fsck
drwxrwx--T  2 root              gdm        4096 2010-07-16 11:09 gdm
drwxr-xr-x  3 root              root       4096 2009-12-23 19:37 installer
-rw-r--r--  1 root              root          0 2009-12-24 00:29 jockey.log
-rw-r--r--  1 root              root      24795 2009-12-24 00:29 jockey.log.1
-rw-r-----  1 syslog            adm           0 2010-07-18 07:43 kern.log
-rw-r-----  1 syslog            adm      218368 2010-07-16 12:40 kern.log.1
-rw-r-----  1 syslog            adm          89 2010-07-08 12:13 kern.log.2.gz
-rw-r-----  1 syslog            adm       14668 2010-07-04 00:57 kern.log.3.gz
-rw-r-----  1 syslog            adm         194 2010-06-26 20:36 kern.log.4.gz
-rw-rw-r--  1 root              utmp     292292 2010-07-19 08:57 lastlog
drwxr-xr-x  3 root              root       4096 2009-12-23 19:41 libvirt
-rw-r-----  1 syslog            adm           0 2010-07-18 07:43 lpr.log
-rw-r-----  1 syslog            adm        3976 2010-07-16 11:08 lpr.log.1
-rw-r-----  1 syslog            adm         563 2010-07-15 14:13 lpr.log.2.gz
-rw-r-----  1 syslog            adm         368 2010-06-28 15:00 lpr.log.3.gz
-rw-r-----  1 syslog            adm         317 2010-06-26 01:17 lpr.log.4.gz
-rw-r-----  1 syslog            adm         214 2010-07-19 08:03 mail.err
-rw-r-----  1 syslog            adm        1486 2010-07-16 11:08 mail.err.1
-rw-r-----  1 syslog            adm         136 2010-07-05 07:40 mail.err.2.gz
-rw-r-----  1 syslog            adm         146 2010-06-28 15:00 mail.err.3.gz
-rw-r-----  1 syslog            adm         117 2010-06-26 08:05 mail.err.4.gz
-rw-r-----  1 syslog            adm         214 2010-07-19 08:03 mail.info
-rw-r-----  1 syslog            adm        1486 2010-07-16 11:08 mail.info.1
-rw-r-----  1 syslog            adm         136 2010-07-05 07:40 mail.info.2.gz
-rw-r-----  1 syslog            adm         146 2010-06-28 15:00 mail.info.3.gz
-rw-r-----  1 syslog            adm         117 2010-06-26 08:05 mail.info.4.gz
-rw-r-----  1 syslog            adm         214 2010-07-19 08:03 mail.log
-rw-r-----  1 syslog            adm        1486 2010-07-16 11:08 mail.log.1
-rw-r-----  1 syslog            adm         136 2010-07-05 07:40 mail.log.2.gz
-rw-r-----  1 syslog            adm         146 2010-06-28 15:00 mail.log.3.gz
-rw-r-----  1 syslog            adm         117 2010-06-26 08:05 mail.log.4.gz
-rw-r-----  1 syslog            adm         214 2010-07-19 08:03 mail.warn
-rw-r-----  1 syslog            adm        1486 2010-07-16 11:08 mail.warn.1
-rw-r-----  1 syslog            adm         136 2010-07-05 07:40 mail.warn.2.gz
-rw-r-----  1 syslog            adm         146 2010-06-28 15:00 mail.warn.3.gz
-rw-r-----  1 syslog            adm         117 2010-06-26 08:05 mail.warn.4.gz
-rw-r-----  1 syslog            adm         326 2010-07-19 08:03 messages
-rw-r-----  1 syslog            adm      170087 2010-07-18 07:43 messages.1
-rw-r-----  1 syslog            adm         258 2010-07-11 07:40 messages.2.gz
-rw-r-----  1 syslog            adm       12523 2010-07-04 08:04 messages.3.gz
-rw-r-----  1 syslog            adm         168 2010-06-27 08:04 messages.4.gz
drwxr-s---  2 mysql             adm        4096 2009-12-23 22:40 mysql
-rw-r-----  1 mysql             adm           0 2010-02-18 13:11 mysql.err
-rw-r-----  1 mysql             adm           0 2010-07-19 08:03 mysql.log
-rw-r-----  1 mysql             adm          20 2010-07-18 07:43 mysql.log.1.gz
-rw-r-----  1 mysql             adm          20 2010-07-17 07:38 mysql.log.2.gz
-rw-r-----  1 mysql             adm          20 2010-07-16 11:38 mysql.log.3.gz
-rw-r-----  1 mysql             adm          20 2010-07-15 14:28 mysql.log.4.gz
-rw-r-----  1 mysql             adm          20 2010-07-14 07:55 mysql.log.5.gz
-rw-r-----  1 mysql             adm          20 2010-07-13 07:37 mysql.log.6.gz
-rw-r-----  1 mysql             adm          20 2010-07-12 07:39 mysql.log.7.gz
drwxr-xr-x  2 root              root       4096 2009-12-23 19:38 news
-rw-r--r--  1 root              root       1984 2010-07-16 11:09 pm-powersave.log
-rw-r--r--  1 root              root       1370 2010-06-28 15:00 pm-powersave.log.1
-rw-r--r--  1 root              root        197 2010-06-03 23:44 pm-powersave.log.2.gz
-rw-r--r--  1 root              root        246 2010-02-05 14:57 pm-powersave.log.3.gz
-rw-r--r--  1 root              root        218 2010-01-09 16:33 pm-powersave.log.4.gz
-rw-r--r--  1 root              root          0 2009-12-23 18:43 pycentral.log
drwxr-xr-x  3 root              root       4096 2010-07-18 07:43 samba
drwxr-xr-x  2 speech-dispatcher root       4096 2009-10-13 07:27 speech-dispatcher
-rw-r-----  1 syslog            adm        9739 2010-07-19 11:20 syslog
-rw-r-----  1 syslog            adm       67284 2010-07-19 08:00 syslog.1
-rw-r-----  1 syslog            adm        4246 2010-07-18 07:40 syslog.2.gz
-rw-r-----  1 syslog            adm        4553 2010-07-17 07:35 syslog.3.gz
-rw-r-----  1 syslog            adm       20008 2010-07-16 11:35 syslog.4.gz
-rw-r-----  1 syslog            adm       39456 2010-07-15 14:25 syslog.5.gz
-rw-r-----  1 syslog            adm        4225 2010-07-14 07:55 syslog.6.gz
-rw-r-----  1 syslog            adm        4179 2010-07-13 07:35 syslog.7.gz
drwxr-xr-x  2 root              root       4096 2010-07-19 08:03 sysstat
-rw-r--r--  1 root              root     195532 2010-07-16 11:09 udev
drwxr-xr-x  2 root              root       4096 2009-07-20 13:53 unattended-upgrades
-rw-r-----  1 syslog            adm           0 2010-02-04 07:47 user.log
-rw-r-----  1 syslog            adm          73 2010-02-03 21:10 user.log.1
-rw-r-----  1 syslog            adm         569 2010-01-10 14:30 user.log.2.gz
-rw-r-----  1 syslog            adm        1638 2009-12-27 00:06 user.log.3.gz
-rw-rw-r--  1 root              utmp      17280 2010-07-19 08:57 wtmp
-rw-rw-r--  1 root              utmp        668 2010-06-29 19:59 wtmp.1.gz
-rw-r--r--  1 root              root      29206 2010-07-16 11:09 Xorg.0.log
-rw-r--r--  1 root              root      42429 2010-07-15 14:37 Xorg.0.log.old
-rw-r--r--  1 root              root       6465 2010-06-03 23:52 Xorg.1.log
-rw-r--r--  1 root              root       6465 2010-06-03 23:52 Xorg.2.log
-rw-r--r--  1 root              root       6465 2010-06-03 23:52 Xorg.3.log
-rw-r--r--  1 root              root       6465 2010-06-03 23:52 Xorg.4.log
-rw-r--r--  1 root              root       6465 2010-06-03 23:52 Xorg.5.log
-rw-r--r--  1 root              root       4814 2010-06-03 23:52 Xorg.failsafe.log

```

---

### Post by capscrew on 2010-07-19
> **sirkubax said:**
> Hello, 

I would like to find where logs form dmesg(command) are stored on my hdd drive.
...

There are no logs.  From Wikipedia: "... dmesg (for "display message") is a command on some Unix-like operating systems that **[COLOR="Blue"]prints the message buffer of the kernel[/COLOR]**."

See [**_here _**]("http://linuxgazette.net/issue59/nazario.html")for a complete demsg explanation.

The kern logs would be of interest. ```
-rw-r-----  1 syslog            adm           0 2010-07-18 07:43 kern.log
-rw-r-----  1 syslog            adm      218368 2010-07-16 12:40 kern.log.1
-rw-r-----  1 syslog            adm          89 2010-07-08 12:13 kern.log.2.gz
-rw-r-----  1 syslog            adm       14668 2010-07-04 00:57 kern.log.3.gz
-rw-r-----  1 syslog            adm         194 2010-06-26 20:36 kern.log.4.gz

```
You would have to set the appropriate level of logging to see the I/O errors.

---

### Post by sirkubax on 2010-07-20
> **capscrew said:**
> 
The kern logs would be of interest. ```
-rw-r-----  1 syslog            adm           0 2010-07-18 07:43 kern.log
-rw-r-----  1 syslog            adm      218368 2010-07-16 12:40 kern.log.1
-rw-r-----  1 syslog            adm          89 2010-07-08 12:13 kern.log.2.gz
-rw-r-----  1 syslog            adm       14668 2010-07-04 00:57 kern.log.3.gz
-rw-r-----  1 syslog            adm         194 2010-06-26 20:36 kern.log.4.gz

```
You would have to set the appropriate level of logging to see the I/O errors.

Thx for this clue, i thought about loggigng levels, unfortunately to late.
It's interesting, but my kern.log from that day (it's the newest) is empty.
I'm gonna read your link, thx

---

