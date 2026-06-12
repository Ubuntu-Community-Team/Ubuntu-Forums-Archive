---
title: "MegaCli showing duplicate Enclosure/Slot ID's"
date: 2010-11-12
forum: Server Platforms
---

### Post by ToniVR on 2010-11-12
Hi,

I got a server with an Intel SRCSAS18E controller in it.
It is currently configured with 4 disks in a RAID5 w hotspare, working very well. The system runs Ubuntu Server 8.04 64-bit.

We added 5 disks to the server, and they show up under the 'MegaCli -PDList -a0' list.
I like to add the 5 new disks to the existing RAID5 of 4 disks and keep the hotspare.

The problem I encounter is that MegaCli shows up 2 items that aren't disks with the same Enclosure and Slot number as a disk:
```
Enclosure Number: 1
Slot Number: 0
Device Id: 13
Sequence Number: 1
Media Error Count: 0
Other Error Count: 1
Predictive Failure Count: 0
Last Predictive Failure Event Seq Number: 0
Raw Size: 0MB [0x0 Sectors]
Non Coerced Size: 9007199254740480MB [0xfffffffffff00000 Sectors]
Coerced Size: 0MB [0x0 Sectors]
Firmware state: Unconfigured(good)
SAS Address(0): 0x5000e0ca3996800b
Inquiry Data: ESG-SHV.SCA HSBP M1.....2.02ESG-SHV.qa2.02

```
```
Enclosure Number: 1
Slot Number: 0
Device Id: 15
Sequence Number: 1
Media Error Count: 0
Other Error Count: 0
Predictive Failure Count: 0
Last Predictive Failure Event Seq Number: 0
Raw Size: 140272MB [0x111f83a0 Sectors]
Non Coerced Size: 139760MB [0x110f83a0 Sectors]
Coerced Size: 139236MB [0x10ff2000 Sectors]
Firmware state: Unconfigured(good)
SAS Address(0): 0x500000e115e728d2
SAS Address(1): 0x0
Inquiry Data: FUJITSU MBA3147RC       0103BJA0PA90E76T
```
This makes it very difficult to add those disks to the existing RAID because the MegaCli picks the ESG-SHV.SCA HSBP instead of the Fujitsu disk.

I also tried to install the Intel RAID Web Console 2 onto this system, but the mrmonitord doesn't see my RAID controller (although it is listed as supported).

Anybody an idea how to get those 5 new disks into the RAID without a shutdown of the server?

Thanks.

---

