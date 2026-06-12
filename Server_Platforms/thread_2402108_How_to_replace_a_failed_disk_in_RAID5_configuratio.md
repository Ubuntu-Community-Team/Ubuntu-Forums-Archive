---
title: "How to replace a failed disk in RAID5 configuration"
date: 2018-09-26
forum: Server Platforms
---

### Post by jonwarner1 on 2018-09-26
Description:    Ubuntu 16.04.5 LTS
Smart Array P400

I have a failed disk which can be seen by using the **"cciss_vol_status -V"** command, however what's the procedure for replacing the disk or is it full automatic?

sudo cciss_vol_status -V  /dev/cciss/c0d1p1
Controller: Smart Array P400
  Board ID: 0x3234103c
  Logical drives: 3
  Running firmware: 7.22
  ROM firmware: 7.22
/dev/cciss/c0d1p1: (Smart Array P400) RAID 1 Volume 0 status: OK.
/dev/cciss/c0d1p1: (Smart Array P400) RAID 5 Volume 1 status: Using interim recovery mode.
  Failed drives:
         connector 1I box 1 bay 5                 HP      EG0300FBDBR                                      PMVRPG5B     HPD7
 
    Total of 1 failed physical drives detected on this logical drive.
/dev/cciss/c0d1p1: (Smart Array P400) RAID 1 Volume 2 status: OK.
  Physical drives: 7
         connector 1I box 1 bay 8                 ATA     ST3000LM024-2AN1                                 WCK2AK71 0001     OK
         connector 1I box 1 bay 7                 ATA     ST3000LM024-2AN1                                 WCK29ZGA 0001     OK
         connector 1I box 1 bay 6                 ATA     ST3000LM024-2AN1                                 WCK29ZAX 0001     OK
         connector 2I box 1 bay 4                 ATA     ST2000LM015-2E81                                 WDZAVHAY SDM1     OK
         connector 2I box 1 bay 3                 ATA     ST2000LM015-2E81                                 WDZAW63Q SDM1     OK
         connector 2I box 1 bay 2                 HP      EG0600FBDBU                                      PVH69SYB     HPD6 OK
         connector 2I box 1 bay 1                 HP      EG0600FBDBU                                      PVHDUKVB     HPD6 OK
/dev/cciss/c0d1p1(Smart Array P400:0): Non-Volatile Cache status:
                   Cache configured: Yes
                  Read cache memory: 208 MiB
                 Write cache memory: 0 MiB
                Write cache enabled: Yes

Thanks very much. Regards, Jon.

---

### Post by darkod on 2018-09-26
If I'm not mistaken, you are using the HW RAID controller of your server, not mdadm SW raid. If that is the case, the OS (ubuntu) has nothing to do with the raid. It sees the logical volumes as any other disk.

You should refer to the server manual for failed drive replacement info. In most cases it is simply removing the failed disk and replacing it with a new one (if they are hotplug). The array will start rebuilding itself.

---

