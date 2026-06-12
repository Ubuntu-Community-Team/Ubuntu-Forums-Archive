---
title: "WINE - Will not auto-recognize DVD Drive (T60)"
date: 2010-12-22
forum: Virtualisation
---

### Post by samjaynes on 2010-12-22
I am using Ubuntu 10.10 and a Lenovo T60.  Wine does not recognize the DVD drive.

```
~$ dmesg | grep "sr0"
[    0.747800] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.747905] sr 1:0:0:0: Attached scsi CD-ROM sr0

```

Strangely - all day yesterday, when I executed wodim it would give an error when media was in the drive
```
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```
, and not locate any devices.  But now it showing after running handbrake and detected dvd drives (only app I recall running between 
```
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'MATSHITA' 'DVD/CDRW UJDA775'
-------------------------------------------------------------------------

```

Please note sr0 and scd0 differences - Any insight on how to get this running in Wine.

---

