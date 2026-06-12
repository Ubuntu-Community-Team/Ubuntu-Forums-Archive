---
title: "USB 3.0 freezes mouse"
date: 2013-07-20
forum: System76 Support
---

### Post by spideryada on 2013-07-20
I have a Meerkat Ion 64-bit. When I plug a USB 3.0 flash drive or a USB 3.0 SD card reader into the USB 3.0 port the mouse freezes. This happens with both the USB mouse and the wireless mouse. The same problem happens in 12.04, 12.10 and 13.04. I have multiple installs. All works well on the USB 2.0 ports.

July 31 10:30
syslog

Jul 31 10:30:04 spider-Meerkat-Ion-NetTop kernel: [18035.140254] usb 7-1: new SuperSpeed USB device number 2 using xhci_hcd
Jul 31 10:30:04 spider-Meerkat-Ion-NetTop mtp-probe: checking bus 7, device 2: "/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb7/7-1"
Jul 31 10:30:04 spider-Meerkat-Ion-NetTop mtp-probe: bus: 7, device: 2 was not an MTP device
Jul 31 10:30:04 spider-Meerkat-Ion-NetTop kernel: [18035.178184] Initializing USB Mass Storage driver...
Jul 31 10:30:04 spider-Meerkat-Ion-NetTop kernel: [18035.178987] scsi4 : usb-storage 7-1:1.0
Jul 31 10:30:04 spider-Meerkat-Ion-NetTop kernel: [18035.179205] usbcore: registered new interface driver usb-storage
Jul 31 10:30:04 spider-Meerkat-Ion-NetTop kernel: [18035.179210] USB Mass Storage support registered.
Jul 31 10:30:05 spider-Meerkat-Ion-NetTop kernel: [18036.177054] scsi 4:0:0:0: Direct-Access     Lexar    JumpDrive        1.00 PQ: 0 ANSI: 6
Jul 31 10:30:05 spider-Meerkat-Ion-NetTop kernel: [18036.179681] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jul 31 10:30:05 spider-Meerkat-Ion-NetTop kernel: [18036.179834] sd 4:0:0:0: [sdb] 62545920 512-byte logical blocks: (32.0 GB/29.8 GiB)
Jul 31 10:30:05 spider-Meerkat-Ion-NetTop kernel: [18036.180061] sd 4:0:0:0: [sdb] Write Protect is off
Jul 31 10:30:05 spider-Meerkat-Ion-NetTop kernel: [18036.180070] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jul 31 10:30:05 spider-Meerkat-Ion-NetTop kernel: [18036.180287] sd 4:0:0:0: [sdb] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
Jul 31 10:30:05 spider-Meerkat-Ion-NetTop kernel: [18036.184395]  sdb: sdb1
Jul 31 10:30:05 spider-Meerkat-Ion-NetTop kernel: [18036.187838] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jul 31 10:30:52 spider-Meerkat-Ion-NetTop kernel: Kernel logging (proc) stopped.
Jul 31 10:30:52 spider-Meerkat-Ion-NetTop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="880" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul 31 10:31:57 spider-Meerkat-Ion-NetTop kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jul 31 10:31:57 spider-Meerkat-Ion-NetTop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="834" x-info="http://www.rsyslog.com"] start
Jul 31 10:31:58 spider-Meerkat-Ion-NetTop rsyslogd: rsyslogd's groupid changed to 103
Jul 31 10:31:58 spider-Meerkat-Ion-NetTop rsyslogd: rsyslogd's userid changed to 101
Jul 31 10:31:57 spider-Meerkat-Ion-NetTop rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jul 31 10:31:58 spider-Meerkat-Ion-NetTop polkitd[862]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jul 31 10:31:58 spider-Meerkat-Ion-NetTop dbus[797]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul 31 10:31:58 spider-Meerkat-Ion-NetTop NetworkManager[837]:    SCPlugin-Ifupdown: init!

With the Adata USB 3.0 in the second USB 3.0 port

Aug  1 07:03:59 spider-Meerkat-Ion-NetTop kernel: [ 9486.116236] usb 7-2: new SuperSpeed USB device number 2 using xhci_hcd
Aug  1 07:03:59 spider-Meerkat-Ion-NetTop kernel: [ 9486.137078] scsi5 : usb-storage 7-2:1.0
Aug  1 07:03:59 spider-Meerkat-Ion-NetTop mtp-probe: checking bus 7, device 2: "/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/usb7/7-2"
Aug  1 07:03:59 spider-Meerkat-Ion-NetTop mtp-probe: bus: 7, device: 2 was not an MTP device
Aug  1 07:04:00 spider-Meerkat-Ion-NetTop kernel: [ 9487.136865] scsi 5:0:0:0: Direct-Access     ADATA    USB Flash Drive  1.00 PQ: 0 ANSI: 6
Aug  1 07:04:00 spider-Meerkat-Ion-NetTop kernel: [ 9487.138454] sd 5:0:0:0: Attached scsi generic sg1 type 0
Aug  1 07:04:00 spider-Meerkat-Ion-NetTop kernel: [ 9487.138909] sd 5:0:0:0: [sdb] 30869504 512-byte logical blocks: (15.8 GB/14.7 GiB)
Aug  1 07:04:00 spider-Meerkat-Ion-NetTop kernel: [ 9487.139186] sd 5:0:0:0: [sdb] Write Protect is off
Aug  1 07:04:00 spider-Meerkat-Ion-NetTop kernel: [ 9487.139198] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
Aug  1 07:04:00 spider-Meerkat-Ion-NetTop kernel: [ 9487.139487] sd 5:0:0:0: [sdb] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
Aug  1 07:04:00 spider-Meerkat-Ion-NetTop kernel: [ 9487.150013]  sdb: sdb1
Aug  1 07:04:00 spider-Meerkat-Ion-NetTop kernel: [ 9487.151624] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Aug  1 07:05:11 spider-Meerkat-Ion-NetTop kernel: [ 9557.316104] usb 7-2: USB disconnect, device number 2

---

### Post by spideryada on 2013-08-01
Fixed the problem. I plugged the mouse in a different 2.0 port and it now works fine.

---

