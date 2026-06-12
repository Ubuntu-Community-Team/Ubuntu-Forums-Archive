---
title: "dvd/cd does not mount"
date: 2012-07-02
forum: Ubuntu Studio
---

### Post by andthy on 2012-07-02
I have just installed ubuntu_studio 12.04 and since then it does not see the drive.  When I look at sudo lshw - C disk, i do not see a section dor cdrom.  When I had ubuntu 12.04 it worked.  The computer is aspire 5810T-8929.  Frustrating and thanks for the help.


sudo lshw -C disk

---

### Post by papibe on 2012-07-02
Hi andthy. Welcome to the forums!

Could you post the result of that command?
```
sudo lshw -C disk
```

Also could you post the result of this one:
```
ls -l  /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw /dev/scd0 /dev/sr0
```
Regards.

---

### Post by andthy on 2012-07-06
Thanks for the fast response - here is sudo lshw -C disk

  *-disk                  
       description: ATA Disk
       product: Hitachi HTS72505
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: PC4O
       serial: 101213PCK410GLG3EJRJ
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000abb16
jdillon@jtd-lap01:~$ ^C

---

### Post by andthy on 2012-07-06
jdillon@jtd-lap01:~$ ls -l  /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw /dev/scd0 /dev/sr0

ls: cannot access /dev/cdrom: No such file or directory
ls: cannot access /dev/cdrw: No such file or directory
ls: cannot access /dev/dvd: No such file or directory
ls: cannot access /dev/dvdrw: No such file or directory
ls: cannot access /dev/scd0: No such file or directory
ls: cannot access /dev/sr0: No such file or directory

---

### Post by andthy on 2012-07-06
also I see the following

jdillon@jtd-lap01:~$ dmesg | grep sr0
[    4.021755] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.021894] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  450.590892] sr 4:0:0:0: [sr0] Device not ready
[  450.590900] sr 4:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE

---

