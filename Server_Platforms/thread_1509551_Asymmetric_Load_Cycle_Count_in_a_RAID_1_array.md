---
title: "Asymmetric Load_Cycle_Count in a RAID 1 array"
date: 2010-06-14
forum: Server Platforms
---

### Post by AMMOnium on 2010-06-14
Hi all,

I have set up a small headless home server (file/print server, P2P seedbox(rtorrent, dc++), etc.):

Ubuntu 9.10 server x86, now 10.04 server x86
CPU: Atom 330 (integrated, ION chipset)
MB:  Zotac ION ITX D-E
OS HDD: WDC WD1200BEVS-2
storage HDD: 2 x WDC WD15EADS-00P mirrored in RAID 1 using NVidia RAID on board.

The system was running for about half a year with an average uptime of several days (sometimes just powered off at night to reduce noise).

Regretfully, I payed no attention to monitoring some SMART counters, including Load Cycle Count. Here are the most interesting parameters:

```
First drive:
  3 Spin_Up_Time            0x0027   178   178   021    Pre-fail  Always       -       6083
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       70
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3439
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       68
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       12
**193 Load_Cycle_Count        0x0032   190   190   000    Old_age   Always       -       [COLOR="SeaGreen"]32621[/COLOR]**

Second drive:
  3 Spin_Up_Time            0x0027   183   183   021    Pre-fail  Always       -       5816
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       68
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3325
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       66
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       17
**193 Load_Cycle_Count        0x0032   139   139   000    Old_age   Always       -       [COLOR="Red"]183851[/COLOR]**

```

One drive was really powered up two times more (I have mixed the drives up when I was testing them one by one :) ).

But I cannot explain why the second drive in the raid array got nearly **6 times more **load cycles than the first! Considering the power-on time, it is nearly one load cycle per minute, which is totally unbearable for a desktop HDD.

The two drives are functioning in a RAID 1 mirrored array, why should one drive be accessed 6 times more frequently than another (I can't believe that the raid controller is desgned to route data reads to the same drive every time) ?

After I had noticed the values, I remembered the old head parking issue and tried "hdparm -B ", but it says that APM is not supported on the drives in the raid array (but supported on the OS one, maybe because this one is a laptop drive). Then I set an idle time of 64 for all drives(5:20 min), but I am not sure if either of the two settings influences the head parking policy on the desktop drives. Of course, now I added Load_Cycle_Count values to collectd.

This issue should be rather interesting as Atom+ION solutions are popular in custom NAS'es running under Linux.

---

### Post by AMMOnium on 2010-06-15
After 18 hrs of monitoring the operation (P2P seeding =< 50 KB/s and moderate SMB fileshare access at local eth network speed (100Mbit) ) I have the following stats:

```

First drive:
  3 Spin_Up_Time            0x0027   178   178   021    Pre-fail  Always       -       6083
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       70
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3466
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       68
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       12
**193 Load_Cycle_Count        0x0032   189   189   000    Old_age   Always       -       [COLOR="Red"]35476[/COLOR]**
194 Temperature_Celsius     0x0022   116   110   000    Old_age   Always       -       34

Second drive:
  3 Spin_Up_Time            0x0027   183   183   021    Pre-fail  Always       -       5816
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       68
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3353
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       66
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       17
**193 Load_Cycle_Count        0x0032   139   139   000    Old_age   Always       -       184145**
194 Temperature_Celsius     0x0022   114   111   000    Old_age   Always       -       36

```

This means +2000 load cycles for the first drive and +100 for the second.
Compared to previous results, it yields +3000 cycles for the first drive and +300 for the second.

The graph confirms that the load cycles increased linearly, so the issue does not seem to be influenced with the system load or even frequency of disk accesses.

[[IMG]http://img291.imageshack.us/img291/8611/graphq.png[/IMG]](http://img291.imageshack.us/i/graphq.png/)

**If anyone has a similar setup (ION motherboard + Ubuntu + two HDDs mirrored in RAID1), could you please confirm if you have the same asymmetry of HDD usage.**

---

