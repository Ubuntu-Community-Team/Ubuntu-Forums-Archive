---
title: "bad hard drive?"
date: 2012-03-28
forum: Server Platforms
---

### Post by berryboy on 2012-03-28
hello i hope someone can help me here, ive been having some probs downloading with deluge, the files dont complete or when re'hashed fail. i whiched client to rule that out and still have issues, so figure it's the hard drive failing :'(

here is some output of smartmontools
many thanks to anyone who can point a noob in the right direction
 ```
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_                                                                                        FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   099   006    Pre-fail  Always       -                                                                                               91572484
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -                                                                                               0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -                                                                                               17
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -                                                                                               0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -                                                                                               306193572
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -                                                                                               6686
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -                                                                                               0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -                                                                                               17
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -                                                                                               0
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -                                                                                               0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -                                                                                               0
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -                                                                                               3
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -                                                                                               0
190 Airflow_Temperature_Cel 0x0022   062   053   045    Old_age   Always       -                                                                                               38 (Lifetime Min/Max 31/41)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -                                                                                               1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -                                                                                               16
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -                                                                                               17
194 Temperature_Celsius     0x0022   038   047   000    Old_age   Always       -                                                                                               38 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   043   028   000    Old_age   Always       -                                                                                               91572484
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -                                                                                               0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -                                                                                               0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -                                                                                               0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -                                                                                               90361816947268
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -                                                                                               955310061
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -                                                                                               1292083936

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA                                                                                        _of_first_error
# 1  Short offline       Completed without error       00%         9         -
# 2  Short offline       Completed without error       00%         7         -
# 3  Short offline       Completed without error       00%         7         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by QIII on 2012-03-28
SMART is one of those things that has a "sort of" standard.  You'll notice "vendor specific" at the top.

But I think "pre fail" is pretty clear.

The right direction is probably your computer parts store for a new drive after shutting down your machine and not restarting it until you have a plan to safeguard your data.

---

### Post by berryboy on 2012-03-28
oh crap its in a data center, i best download everything i can !!
i use it for everything host sites, vent server, alsorts :/

thanks for your advice and so fast! :)

could anyone recommend something to back everything up? or will it likely be damaged, or should i just grab the databases / configs manually, oh wow i have a lot of work a head of me

---

### Post by QIII on 2012-03-28
Yeah.  If it were all just "old age" I'd just say to do regular backups.  Disks can last for years, as you know.

But, you might want to look at your cooling solution.  It looks like that disk has gotten mighty hot in the past.

Someone will probably be by shortly with a good recovery plan for you.

---

### Post by QIII on 2012-03-28
Hold the boat -- maybe.  Pre-fail does not mean failure is immenent.  I just had a look at docs for smartmontools.

Hang tight for a bit.

Edit:  OK.  Don't take anything I just said as in any way worthwhile.  In fact, I'm full of crap.  I'll leave my embarrassment here for all to see...

As one gets older, it sometimes takes one a while to get the uneasy feeling he's not remembering something he once knew.

The disk, as far as SMART is concerned, is perfectly healthy.

You may now throw darts at me.

---

### Post by rubylaser on 2012-03-28
> **QIII said:**
> Hold the boat -- maybe.  Pre-fail does not mean failure is immenent.  I just had a look at docs for smartmontools.

Hang tight for a bit.

Edit:  OK.  Don't take anything I just said as in any way worthwhile.  In fact, I'm full of crap.  I'll leave my embarrassment here for all to see...

As one gets older, it sometimes takes one a while to get the uneasy feeling he's not remembering something he once knew.

The disk, as far as SMART is concerned, is perfectly healthy.

You may now throw darts at me.
QIII that was a very honest dialog, and you arrived at the correct final answer :)  You were trying to be helpful  and were very quick to reply.  

For the OP, you don't want to be thinking about backup only when you think your disk(s) are failing.  If that disk is as important as it sounds, you should have multiple backups and in geographically dispersed locations.

---

### Post by QIII on 2012-03-28
It's particularly embarrassing, however.

On a Fedora forum not long ago my answer was just what it should have been here.  And I have checked my own hardware with similar results.

Momentary senior brain fart.

---

### Post by westie457 on 2012-03-28
@QIII it might not have that much of a brain fart. Did you look at the numbers to the far right of the OP's code output. There is some high numbers there that would get me very worried if this was my hard drive.

---

### Post by QIII on 2012-03-28
The raw values are not necessarily alarming.  They are "normalized" by the disk's firmware.

A large number like some of those may be a raw number of "failures" out of a figure several orders of magnitude larger -- meaning it's not alarming.

---

### Post by rubylaser on 2012-03-28
The drive looks very healthly to me.  It has 0 Current Pending Sectors, and 0 Offline Uncorrectable. No errors in the logs, and has passed all short tests without errors.

---

### Post by berryboy on 2012-03-29
wow thanks for your responses guys!

any idea what the issue is ? RAM maybe?

---

### Post by westie457 on 2012-03-29
@QIII and @rubylaser

I agree with you about the condition of the hard drive after doing a (small) amount of research. Personally when checking a drive I usually look at the reallocated sector count and decide whether or not to get a replacement.

@berryboy It is never too soon to make backups and quite often people leave it too late. In general terms the drive is healthy
however the 'read error rate' could be caused by problems with the read/write heads.

---

### Post by rubylaser on 2012-03-29
> **berryboy said:**
> wow thanks for your responses guys!

any idea what the issue is ? RAM maybe?

I would guess it's a misconfiguration in your torrent client or a permissions problem.  If you want to check the RAM, just grab a copy of [memtest]("http://www.memtest.org/download/4.20/memtest86+-4.20.iso.gz") and test it.

---

