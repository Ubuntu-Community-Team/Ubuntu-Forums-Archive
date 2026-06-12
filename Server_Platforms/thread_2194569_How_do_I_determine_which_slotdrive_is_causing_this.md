---
title: "How do I determine which slot/drive is causing this reset?"
date: 2013-12-19
forum: Server Platforms
---

### Post by MakOwner on 2013-12-19
I have a 16 tray shelf attached to an LSI 1068e controller, with one empty bay. I am using mdadm raid 6 configuration with 15 drives.
I only see this error when running an array check.
I thought at first this was a result of the controller trying to access a drive in the empty slot, but duing the last checkarray run, it occurred several times and eventually caused segfaults from the timeouts.

Is there anyway to determine whcih drive/slot/controller port that causes this issue so I can replace it rahter than waiting for the inevitable catastrophic failure?


```

[140537.152023] mptbase: ioc1: WARNING - IOC is in FAULT state (7814h)!!!
[140537.152028] mptbase: ioc1: WARNING - Issuing HardReset from mpt_fault_reset_work!!
[140537.152035] mptbase: ioc1: Initiating recovery
[140537.152040] mptbase: ioc1: WARNING - IOC is in FAULT state!!!
[140537.152043] mptbase: ioc1: WARNING -            FAULT code = 7814h
[140540.268033] mptbase: ioc1: Recovered from IOC FAULT
[140550.928069] mptbase: ioc1: WARNING - mpt_fault_reset_work: HardReset: success
[140563.049538] mptbase: ioc1: LogInfo(0x31111000): Originator={PL}, Code={Reset}, SubCode(0x1000) cb_idx mptbase_reply
[140564.792251] mptbase: ioc1: LogInfo(0x31111000): Originator={PL}, Code={Reset}, SubCode(0x1000) cb_idx mptscsih_io_done
[140564.792266] mptbase: ioc1: LogInfo(0x31111000): Originator={PL}, Code={Reset}, SubCode(0x1000) cb_idx mptscsih_io_done
[140564.792317] mptbase: ioc1: LogInfo(0x31111000): Originator={PL}, Code={Reset}, SubCode(0x1000) cb_idx mptscsih_io_done
[140564.792354] mptbase: ioc1: LogInfo(0x31111000): Originator={PL}, Code={Reset}, SubCode(0x1000) cb_idx mptscsih_io_done
[140564.792390] mptbase: ioc1: LogInfo(0x31111000): Originator={PL}, Code={Reset}, SubCode(0x1000) cb_idx mptscsih_io_done

```

---

### Post by SeijiSensei on 2013-12-19
Do you see any errors when running "sudo mdadm --detail /dev/mdX"?

You might also try "--detail-platform" which I don't think I've ever used.

---

### Post by MakOwner on 2013-12-19
No unusual output from the array, and no drives are reporting issues independantly via any SMART information.
I need to figure out how to track down the drive or port causing the error.

```

# mdadm --detail /dev/md8
/dev/md8:
        Version : 1.2
  Creation Time : Sat Jun  1 07:44:56 2013
     Raid Level : raid6
     Array Size : 25393964544 (24217.57 GiB 26003.42 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 15
  Total Devices : 15
    Persistence : Superblock is persistent

    Update Time : Thu Dec 19 11:01:44 2013
          State : clean, checking 
 Active Devices : 15
Working Devices : 15
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Check Status : 87% complete

           Name : PE850-fs05:ES202TB
           UUID : dc8a11e1:de053156:f5bc1550:12e40ec9
         Events : 3056476

    Number   Major   Minor   RaidDevice State
       0       8      177        0      active sync   /dev/sdl1
       1       8      129        1      active sync   /dev/sdi1
       2       8      113        2      active sync   /dev/sdh1
       3      65        1        3      active sync   /dev/sdq1
       4       8      161        4      active sync   /dev/sdk1
       5       8      225        5      active sync   /dev/sdo1
       6       8      145        6      active sync   /dev/sdj1
       7       8      209        7      active sync   /dev/sdn1
       8       8      241        8      active sync   /dev/sdp1
      10       8       97        9      active sync   /dev/sdg1
      14       8       49       10      active sync   /dev/sdd1
      13       8       81       11      active sync   /dev/sdf1
      12       8       33       12      active sync   /dev/sdc1
      11       8      193       13      active sync   /dev/sdm1
      15       8       65       14      active sync   /dev/sde1

```

---

### Post by jfolsom2 on 2013-12-19
You might have some luck with mpt-status, from the repositories, or LSIutil. See: [http://www.dzhang.com/blog/2013/03/22/where-to-get-download-lsiutil](http://www.dzhang.com/blog/2013/03/22/where-to-get-download-lsiutil)

---

### Post by MakOwner on 2013-12-19
I installed mtp-status, but it looks like something is missing:
lsmod shows not mptctl loaded, and I dont find an mptctl program anywhere.

(I rebooted after the array finished the check and the mpt-status install, thinking that might help)

if all I need to do is create the node in the /dev/ directory, how do I confirm that "mknod /dev/mptctl c 10 220" is correct?
```

# mpt-status
open /dev/mptctl: No such file or directory
  Try: mknod /dev/mptctl c 10 220
Make sure mptctl is loaded into the kernel

```

---

### Post by MakOwner on 2013-12-19
I installed mtp-status, but it looks like something is missing:
lsmod shows not mptctl loaded, and I dont find an mptctl program anywhere.

(I rebooted after the array finished the check and the mpt-status install, thinking that might help)

```

# mpt-status
open /dev/mptctl: No such file or directory
  Try: mknod /dev/mptctl c 10 220
Make sure mptctl is loaded into the kernel

```

I tried it blind:

```

# mknod /dev/mptctl c 10 220
# mpt-status
open /dev/mptctl: No such device
  Are you sure your controller is supported by mptlinux?
Make sure mptctl is loaded into the kernel

```

---

### Post by MakOwner on 2013-12-19
This is on a Dell PE850, but the LSI controller is not a Dell controller.  I loaded OMSA and the mpt-status package I installed causes conflicts, or OMSA doesn't like the LSI controller I have.

---

