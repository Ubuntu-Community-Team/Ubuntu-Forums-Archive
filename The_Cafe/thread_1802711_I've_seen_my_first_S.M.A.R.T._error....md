---
title: "I've seen my first S.M.A.R.T. error..."
date: 2011-07-12
forum: The Cafe
---

### Post by Lucradia on 2011-07-12
I have an ST31000528AS, stock, from ASUS' CG1330 pre-built computer in my new custom computer. However, as of yesterday, the drive started reporting a S.M.A.R.T Failure as follows:

```
smartctl 5.41 2011-06-09 r3365 [i686-w64-mingw32-win7(64)-sp1] (sf-win32-5.41-1)

Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Warning: Limited functionality due to missing admin rights
Error SMART Thresholds Read failed: Function not implemented
Smartctl: SMART Read Thresholds failed.

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_
FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   ---    Pre-fail  Always       -
       229078016
  3 Spin_Up_Time            0x0003   096   095   ---    Pre-fail  Always       -
       0
  4 Start_Stop_Count        0x0032   100   100   ---    Old_age   Always       -
       653
  5 Reallocated_Sector_Ct   0x0033   025   025   ---    Pre-fail  Always       -
       3101
  7 Seek_Error_Rate         0x000f   078   060   ---    Pre-fail  Always       -
       79493153
  9 Power_On_Hours          0x0032   095   095   ---    Old_age   Always       -
       5139
 10 Spin_Retry_Count        0x0013   100   100   ---    Pre-fail  Always       -
       0
 12 Power_Cycle_Count       0x0032   100   100   ---    Old_age   Always       -
       653
183 Runtime_Bad_Block       0x0000   100   100   ---    Old_age   Offline      -
       0
184 End-to-End_Error        0x0032   100   100   ---    Old_age   Always       -
       0
187 Reported_Uncorrect      0x0032   100   100   ---    Old_age   Always       -
       0
188 Command_Timeout         0x0032   100   098   ---    Old_age   Always       -
       168
189 High_Fly_Writes         0x003a   100   100   ---    Old_age   Always       -
       0
190 Airflow_Temperature_Cel 0x0022   072   051   ---    Old_age   Always       -
       28 (Min/Max 25/28)
194 Temperature_Celsius     0x0022   028   049   ---    Old_age   Always       -
       28 (0 14 0 0)
195 Hardware_ECC_Recovered  0x001a   036   024   ---    Old_age   Always       -
       229078016
197 Current_Pending_Sector  0x0012   100   100   ---    Old_age   Always       -
       0
198 Offline_Uncorrectable   0x0010   100   100   ---    Old_age   Offline      -
       0
199 UDMA_CRC_Error_Count    0x003e   200   200   ---    Old_age   Always       -
       1
240 Head_Flying_Hours       0x0000   100   253   ---    Old_age   Offline      -
       222724119075552
241 Total_LBAs_Written      0x0000   100   253   ---    Old_age   Offline      -
       963034717
242 Total_LBAs_Read         0x0000   100   253   ---    Old_age   Offline      -
       2964695567
```

I hope to get it replaced next month, I guess. Not sure why it's failing now though. If anyone has any recommendations, I'm up for it, but... I don't really care for anything larger than 250 GB. I don't really use more than that ever in years of use. I'm not really looking for an SSD yet, they're way to expensive for my monthly budget as of now.

Something that can also consume less power / use less speed when it thinks it doesn't need as much is also a plus, because I don't think I really need 7200 RPM most of the time. (I definitely don't need 10000 RPM even though I'm a gamer. See processor below in my signature.)

---

### Post by del_diablo on 2011-07-12
Check if you still have warranty on the disk.
In some countries, it is as long as 5 years.

---

