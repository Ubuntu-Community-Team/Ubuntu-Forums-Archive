---
title: "No DVD mounted in Studio 12.04"
date: 2012-12-16
forum: Ubuntu Studio
---

### Post by venusfenix on 2012-12-16
hi everyboy,
recently, I re-install ubuntu to clean the system and re-start from zero.
but this time, I used Ubuntu Studio 12.04 with a Acer Aspire 7520.
This time, everything goes perfect, wifi, usb, installation, hard-drive partition, etc... with the exception of the DVDrom drive, that it isn't recognize.

I pasted the result:
sudo lshw |grep dvd;lshw | grep cd
WARNING: you should run this program as super-user.
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

does someone can help/support me?

Many thanks in advance,

---

### Post by jejeman on 2012-12-16
You should use this command
```
sudo lshw -C disk
```Copy here the cdrom section.

---

### Post by venusfenix on 2012-12-17
nothing appears:
  *-disk:0                
       description: ATA Disk
       product: Hitachi HTS54251
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: BBCO
       serial: 071028BB0C00WGGTD29C
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000368ec
  *-disk:1
       description: ATA Disk
       product: Hitachi HTS54251
       vendor: Hitachi
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: BBCO
       serial: 071028BB0C00WGGT534C
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000d2300

---

### Post by jejeman on 2012-12-17
Does the drive shows up in BIOS?

---

### Post by venusfenix on 2012-12-17
yes, it was working fine for the last years.
it was erase HDD and install ubuntu studio from zero and start this problem.

thanks,

---

### Post by jejeman on 2012-12-17
Can you boot from it?
Give us output from
```
df -h | grep ^/dev
```

---

### Post by venusfenix on 2012-12-17
let me check in few minutes.

now, the output of your code:
/dev/sda1       143G  6,6G   129G   5% /
/dev/sdb1       143G   51G    85G  38% /home

---

### Post by venusfenix on 2012-12-17
I've checked the BIOS, nothing appears.
nevertheless, I try to boot with a WXP SP1 & SP3, and nothing also.

it maybe the drive? something not well connected?

thanks,

---

### Post by jejeman on 2012-12-17
If the DVD drive does not shows up in BIOS, than it can't be expected to show up in OS.
Check the cables, change the drive if necessery.

---

### Post by venusfenix on 2012-12-19
it's a laptop, difficult, due to everything is smaller than in a desktop.
I will try anyway, if I found something in the net.

thousand thanks,

---

