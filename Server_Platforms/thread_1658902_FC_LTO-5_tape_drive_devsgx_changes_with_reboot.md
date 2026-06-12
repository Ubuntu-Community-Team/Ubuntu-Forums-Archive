---
title: "FC LTO-5 tape drive: /dev/sgx changes with reboot"
date: 2011-01-03
forum: Server Platforms
---

### Post by dibun on 2011-01-03
I have a Tandberg T40+ Tapeloader with HP LTO-5 tape drive connected to "QLogic Corp. ISP2532-based 8Gb Fibre Channel to PCI Express HBA" on a Dell 2950 running Ubuntu Server 10.10. The kernel version is 2.6.35-24-server. The autoloader device number changes sometimes with reboot. When I installed the server it was /dev/sg4 and now it is /dev/sg2. The tape drive is at /dev/st0 and /dev/nst0. The tape drive will be used for Bacula.

My question is how can I fix the problem of device number changing with reboots?

It also seems the tape is not using the st driver but is using generic scsi driver, How can I force the tape drive to use the st driver? I already have the stinit.def file under /etc.

lsmod
-------
Module                  Size  Used by
radeon                908842  1 
i5000_edac              9278  0 
ttm                    68180  1 radeon
dell_wmi_aio            2097  0 
dcdbas                  6910  0 
edac_core              46822  3 i5000_edac
drm_kms_helper         32836  1 radeon
i5k_amb                 5536  0 
drm                   205270  3 radeon,ttm,drm_kms_helper
psmouse                62080  0 
joydev                 11171  0 
i2c_algo_bit            6208  1 radeon
serio_raw               4942  0 
hed                     2362  0 
bnx2                   78788  0 
shpchp                 34910  0 
lp                     10169  0 
parport                36936  1 lp
osst                   55779  0 
usbhid                 41966  0 
hid                    84486  1 usbhid
ses                     7065  0 
st                     39928  2 
enclosure               8553  1 ses
ch                     13456  0 
qla2xxx               357996  1 
scsi_transport_fc      52449  1 qla2xxx
scsi_tgt               12469  1 scsi_transport_fc
megaraid_sas           45497  2 

dmesg

[    1.889141] qla2xxx 0000:0c:00.1: Allocated (64 KB) for FCE...
[    1.889220] qla2xxx 0000:0c:00.1: Allocated (64 KB) for EFT...
[    1.889308] qla2xxx 0000:0c:00.1: Allocated (1350 KB) for firmware dump...
[    1.893218] qla2xxx 0000:0c:00.1: Unable to read FCP priority data.
[    1.893278] scsi4 : qla2xxx
[    1.893623] qla2xxx 0000:0c:00.1:
[    1.893625]  QLogic Fibre Channel HBA Driver: 8.03.02-k2
[    1.893626]   QLogic QLE2562 - PCI-Express Dual Channel 8Gb Fibre Channel HBA
[    1.893627]   ISP2532: PCIe (2.5GT/s x8) @ 0000:0c:00.1 hdma+, host#=4, fw=4.04.04 (80)
[    1.969431] scsi 2:0:32:0: Enclosure         DP       BACKPLANE        1.05 PQ: 0 ANSI: 5
[    1.982961] scsi 2:2:0:0: Direct-Access     DELL     PERC 6/i         1.11 PQ: 0 ANSI: 5
[    2.004899] hub 1-1:1.0: USB hub found
[    2.004962] hub 1-1:1.0: 2 ports detected
[    2.180013] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    2.223487] qla2xxx 0000:0c:00.0: LIP reset occurred (f801).
[    2.277452] qla2xxx 0000:0c:00.0: LIP occurred (f801).
[    2.280910] qla2xxx 0000:0c:00.0: LOOP UP detected (8 Gbps).
[    2.330499] hub 1-5:1.0: USB hub found
[    2.330582] hub 1-5:1.0: 4 ports detected
[    2.610010] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.785587] qla2xxx 0000:0c:00.0: MRK-IOCB: Invalid completion handle (0) -- timed-out.
[    2.789058] scsi 3:0:0:0: Sequential-Access HP       Ultrium 5-SCSI   Y23U PQ: 0 ANSI: 6
[    2.792979] scsi 3:0:0:1: Medium Changer    TANDBERG StorageLoader    0415 PQ: 0 ANSI: 3
[    2.803894] scsi 3:0:0:0: Attached scsi generic sg1 type 1
[    2.803982] scsi 3:0:0:1: Attached scsi generic sg2 type 8
[    2.804116] scsi 2:0:32:0: Attached scsi generic sg3 type 13


Any help is greatly appreciated.

---

