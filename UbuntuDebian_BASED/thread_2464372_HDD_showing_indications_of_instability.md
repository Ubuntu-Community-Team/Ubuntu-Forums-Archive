---
title: "HDD showing indications of instability"
date: 2021-06-30
forum: Ubuntu/Debian BASED
---

### Post by allienux on 2021-06-30
Hello community!

I'm on KDE Neon, which is based on Ubuntu. after my installation, I'm getting warning from info center, SMART status after startup saying,

```
The storage device *Hitachi modelnumber *(&#8216;/dev/sda&#8217;) is showing indications of instability.
```

It once even showed me warning saying, it's showing early signs of failure..... I wont buy a new harddrive now. My essential data is backed up. How do I fix this error so that I can use this drive till my drive completely fails....And can keep some ammount of regular files without constant worry of losing them.

---

### Post by deadflowr on 2021-06-30
*Thread moved to **Ubuntu/Debian BASED***

Won't buy a new hard drive or can't buy a new hard drive?
But based solely on the posted outputs it doesn't look like you have much choice in the matter.

Edit: you might look at more verbose outputs from smartmontools: [https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")
Post any outputs you don't understand or need help clarifying.

---

### Post by TheFu on 2021-06-30
The HDD doesn't care about your situation.

If you don't want it to fail, then  stop using it.

Move to a flash drive with persistent storage and hobble along until you can replace the HDD.

If it were me, I'd buy a used US$10 HDD and retire the old one already. About 3 yrs ago, I picked up a used 250GB WD-Blue for $9 from a reputable, nationwide, computer store.  It is still going.  I don't keep anything important on it, but for the purpose it was bought (needed an NTFS data drive for security videos), it was a bargain.

---

### Post by CharlesA on 2021-06-30
> **allienux said:**
> Hello community!

I'm on KDE Neon, which is based on Ubuntu. after my installation, I'm getting warning from info center, SMART status after startup saying,

```
The storage device *Hitachi modelnumber *(&#8216;/dev/sda&#8217;) is showing indications of instability.
```

It once even showed me warning saying, it's showing early signs of failure..... I wont buy a new harddrive now. My essential data is backed up. How do I fix this error so that I can use this drive till my drive completely fails....And can keep some ammount of regular files without constant worry of losing them.

You don't fix it. You can either replace the drive with a known good one and restore your files from backups or you can keep using it until it fails and you lose data.

It all depends on what your level of risk tolerance is.

Now with all that said.. you can check to see which specific SMART value it is complaining about by running this command in a terminal:

```
sudo smartctl -a /dev/sda
```

It will have quite a bit of output to the terminal.

Here's what one of my drives returns. Note: The values I have highlighted in red are critical issues and should show zeros, but if they do not, it may signal a drive is near the end of it's life.

```

Model Family:     Western Digital Ultrastar He10/12
Device Model:     WDC WD120EMAZ-11BLFA0
Serial Number:    12345678
Firmware Version: 81.00A81
User Capacity:    12,000,138,625,024 bytes [12.0 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   127   127   054    Old_age   Offline      -       111
  3 Spin_Up_Time            0x0007   164   164   024    Pre-fail  Always       -       413 (Average 387)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       74
[COLOR="#FF0000"]**  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0**[/COLOR]
  7 Seek_Error_Rate         0x000a   100   100   067    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   140   140   020    Old_age   Offline      -       15
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       10671
 10 Spin_Retry_Count        0x0012   100   100   060    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       50
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       488
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       488
194 Temperature_Celsius     0x0002   171   171   000    Old_age   Always       -       38 (Min/Max 21/63)
[COLOR="#FF0000"]**196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0**[/COLOR]
[COLOR="#FF0000"]**197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0**[/COLOR]
[COLOR="#FF0000"]**198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0**[/COLOR]
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
```

---

### Post by TheFu on 2021-07-01
IME, SMART doesn't usually warn at all until after some data loss has already happened on a disk.

If SMART is saying anything, it is time to replace that storage device, unless you like data loss.  Often, it starts with just a few sectors. They could be unimportant or they could be extremely critical.

The skills to "fix" a failing disk aren't something anyone here has. Those people work full time in data recovery businesses and swap out HDD controllers connected to HDDs once a disk appears to have died to the rest of us.  The used controller is a temporary fix, then they get as much data off those platters and put them onto a new HDD - which you are required to purchase. They aren't free and around here, depending on the drive involved, they charge $500-$3000 per drive.  Clearly, having excellent, current, versioned, backups is much cheaper and will let you sleep better at night.

---

### Post by allienux on 2021-07-05
Thanks everyone! I was also wondering if fixing failing HDD was a magic that only advanced Linux user could summon, and why I couldn't find anyth related to that in forums. As I have my all data already backed up, and use that device for browsing and stuffs, Imma let that drive die. Reason I didn't wanna buy a HDD is - that isn't the only problem. As you can guess, the device is pretty worn out. So, planning to get a new one.

Thanks again.

---

