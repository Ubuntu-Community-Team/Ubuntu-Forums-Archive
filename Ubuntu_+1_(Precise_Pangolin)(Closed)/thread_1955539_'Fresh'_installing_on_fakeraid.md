---
title: "'Fresh' installing on fakeraid"
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-04-09
Has anyone been successfully installing from the daily-live iso onto a machine that has fakeraid?
Updating doesn't count -- I mean from USB or CD, preferably amd64.

Since ubu devs were basically giving up on a ubiquity crashing bug ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/973450](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/973450)), I decided to go spelunking in the code myself.

I did find the source of the crash but I'm more concerned with what else I found:  partman seems to confuse 
all the partitions on fakeraid with actual devices.  For example, here's the output on my machine from a utility that ubiquity uses in shell scripts to build a list of devices:

```
peter@thor:~/src/packages/ubiquity/ubiquity-2.10.8/d-i/source/partman-base$ sudo ./parted_devices
/dev/sda    1000204886016    ATA WDC WD1001FALS-0
/dev/sdb    1000204886016    ATA WDC WD1001FALS-0
/dev/sdc    250000000000    ATA ST3250310AS
/dev/sdd    160041885696    Seagate FreeAgent Go
/dev/mapper/isw_cbdbfhdjad_Raid0p6    940568928768    Linux device-mapper (linear)
/dev/mapper/isw_cbdbfhdjad_Raid0p1    1048575112704    Linux device-mapper (linear)
/dev/mapper/isw_cbdbfhdjad_Raid0p5    11260376064    Linux device-mapper (linear)
/dev/mapper/isw_cbdbfhdjad_Raid0p2    951829338112    Linux device-mapper (linear)
/dev/mapper/isw_cbdbfhdjad_Raid0    2000405397504    Linux device-mapper (striped)

```

In this case /dev/sda & /dev/sdb form the raid array so are properly removed by said shell scripts as devices to probe. But everything else is treated as a separate device. Clearly, way wrong -- only ..._Raid0 should be treated as a device.

So my question to those out there with fakeraid, have you tried the daily-live iso?
If so, did it crash?
If it didn't crash, can you take a screenshot of the partitioning screen?

BTW, this crash occurs before selecting how to install (full-disk/side-by-side/something else screen never comes up).

---

