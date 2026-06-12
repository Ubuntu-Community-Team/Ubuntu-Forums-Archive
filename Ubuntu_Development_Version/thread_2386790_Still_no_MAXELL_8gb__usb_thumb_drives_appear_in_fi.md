---
title: "Still no MAXELL 8gb  usb thumb drives appear in file manager"
date: 2018-03-10
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2018-03-10
It does appear in terminal.
This I noticed when I installed alpha 2.
I have a live usb for ubuntu and it does appear, also works in windows.

I have kept updating here hoping it would start working.

```
scott@scott-MS-7596:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13fe:4123 **Kingston Technology Company Inc.** 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
scott@scott-MS-7596:~$ 

```

---

### Post by sdowney717 on 2018-03-10
It appears ubuntu has a bug regarding my 8gb Maxell flash drive...
The Maxell has a live usb on it and it will boot that.
But putting in the maxell into an ubuntu install , does not bring up the file manager with a mounted thumb drive.

A different 1gb thumb drive, ubuntu loads as a mounted drive in the file manager.
LSUSB shows it as a kingston thumb drive.

So its a bug and it might never get fixed.

---

### Post by cariboo on 2018-03-10
What does dmesg show you? On my system the output looks like this:
```

[962.095168] usb-storage 1-1:1.0: USB Mass Storage device detected
[  962.095408] scsi host2: usb-storage 1-1:1.0
[  962.095569] usbcore: registered new interface driver usb-storage
[  962.099883] usbcore: registered new interface driver uas
[  963.118892] scsi 2:0:0:0: Direct-Access     Lexar    JD Secure II +   1100 PQ: 0 ANSI: 0 CCS
[  963.120528] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  965.158723] sd 2:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.02 GB/7.47 GiB)
[  965.522684] sd 2:0:0:0: [sdb] Write Protect is off
[  965.522700] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  965.886105] sd 2:0:0:0: [sdb] No Caching mode page found
[  965.886117] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  965.891296]  sdb: sdb1 sdb2
[  965.894748] sd 2:0:0:0: [sdb] Attached SCSI removable disk
```

The usb drive has Xubuntu 18.04 on it.

---

### Post by sdowney717 on 2018-03-11
This thumb drive I had put a win10 image repair on it, win10 then named the drive 'RECOVERY'
Win10 has a program that lets you build a restore disc for itself on a thumbdrive.

Later, I needed  the thumb drive to install ubuntu, so I then used win10 unetbootin to write an alpha 2 liveusb of ubuntu to the thumb drive.
I had used the thumb drive to install ubuntu on a pc.

No ubuntu PC's could load the drive in file manager. No problem installing ubuntu off that thumb drive,  it booted fine.
So thinking more, I went back to a win10 PC and formatted the thumb drive and deleted the name 'RECOVERY' off the thumb drive.

Now the drive works in the ubuntu PC. 
So wonder what ubuntu did not like, the name called 'RECOVERY", some hidden win10 file leftover??
The thumb drive always worked in win10, regardless.


still shows as kingston```

scott@scott-MS-7596:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 13fe:4123 Kingston Technology Company Inc. **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 055f:021c Mustek Systems, Inc. BearPaw 1200 CU Plus
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
scott@scott-MS-7596:~$
```

This weird problem caused me some grief, had to go digging to find another thumb drive.

---

