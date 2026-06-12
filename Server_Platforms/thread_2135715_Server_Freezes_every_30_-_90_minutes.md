---
title: "Server Freezes every 30 - 90 minutes"
date: 2013-04-15
forum: Server Platforms
---

### Post by gdi2k on 2013-04-15
I've got a Ubuntu Server that is freezing at reasonably regular intervals. 

**Symptoms: **
[LIST]
[*]Completely freezes every 30 - 90 minutes or so.
[*]During a freeze, all systems connected to it get no repsonse (SSH, VNC, LTSP clients). 
[*]It can be easily "unfrozen" by hitting any key on its (local) keyboard. 
[*]It only happens when the machine itself is not being touched (local keyboard and mouse not being used).
[*]There is nothing in any logs when it happens. I ran dstat during the last freeze, which you can see below.
[/LIST]

**dstat during freeze: **
See 18:08:33. Note the time jumps to 18:08:56, which is when someone touched the keyboard to unfreeze it. The CPU cores go strangely idle at freeze time. 
```
------memory-usage----- ---io/sda------io/sdb-- ----system---- -------cpu0-usage--------------cpu1-usage--------------cpu2-usage--------------cpu3-usage------ ---paging-- --net/eth0- ---file-locks-- -----virtual-memory---- --dsk/sda-----dsk/sdb-- --net/eth0- ---paging-- ---system-->
 used  buff  cach  free| read  writ: read  writ|     time     |usr sys idl wai hiq siq:usr sys idl wai hiq siq:usr sys idl wai hiq siq:usr sys idl wai hiq siq|  in   out | recv  send|pos lck rea wri|majpf minpf alloc  free| read  writ: read  writ| recv  send|  in   out | int   csw >
1811M  283M  880M  979M|   0  3.00 :   0     0 |15-04 18:08:29| 31   5  62   0   0   2: 22   2  72   3   0   2: 12   2  86   0   0   0: 32   4  50   0   0  15|   0     0 |9309k 5752k| 28 1.0  22 7.0|   0  1143  6200  5538 |   0    48k:   0     0 |9258k 5787k|   0     0 |  11k   13k>
1810M  283M  880M  980M|   0     0 :   0     0 |15-04 18:08:30| 37   7  56   0   0   1: 25   8  67   0   0   0: 22   3  74   0   0   1: 29   6  47   0   0  18|   0     0 |8831k 4245k| 28 1.0  22 7.0|   0    15k   13k   13k|   0     0 :   0     0 |8846k 4247k|   0     0 |  11k   14k>
1819M  283M  880M  971M|   0     0 :   0     0 |15-04 18:08:31| 36   5  57   0   0   2: 21   4  73   0   0   2: 21   4  74   0   0   1: 30   6  54   0   0  10|   0     0 |9370k 2972k| 28 1.0  22 7.0|   0    14k   10k 8124 |   0     0 :   0     0 |9382k 2961k|   0     0 |  10k   13k>
1812M  283M  880M  978M|   0  9.00 :   0     0 |15-04 18:08:32| 34   5  60   1   0   1: 22   2  75   0   0   2: 12   6  82   0   0   0: 32   3  46   7   0  12|   0     0 |  10M 2996k| 28 1.0  22 7.0|   0   606  4910  6828 |   0   248k:   0     0 |  10M 2992k|   0     0 |  10k   13k>
1812M  283M  880M  978M|   0     0 :   0     0 |15-04 18:08:33| 28   2  69   0   0   1: 17   3  80   0   0   0: 15   5  80   0   0   0: 27   3  57   0   0  13|   0     0 |  11M 2790k| 28 1.0  22 7.0|   0  9604  9580  9556 |   0     0 :   0     0 |  11M 2792k|   0     0 |9227    12k>
1812M  283M  880M  978M|   0     0 :   0     0 |15-04 18:08:56|  1   0  s   0   0   0:  0   0 100   0   0   0:  0   0 100   0   0   0: 18   2  67   0   0  13|   0     0 |5411k 1497k| 28 1.0  22 7.0|   0    50  2311  2084 |   0    32k:   0     0 |5446k 1486k|   0     0 |3776  5025 > missed 22 ticks
1823M  283M  880M  967M|   0  31.0 :   0  1.00 |15-04 18:08:56| 62  14  19   0   0   5: 67  10  14   0   0  10: 71  14   0  14   0   0: 55  18  14   0   0  14|   0     0 |1925k 1550k| 28 1.0  22 7.0|   0    30k   16k   13k|   0   500k:   0  4096B|1838k 1578k|   0     0 |2792  8682 >
1809M  283M  880M  981M|   0  29.0 :   0     0 |15-04 18:08:57| 30   5  57   0   0   8: 22   7  34  32   0   5: 22   6  70   0   0   1: 29   7  53   0   0  11|   0     0 |9732k 4074k| 28 1.0  22 7.0|   0    14k   12k   16k|   0  1844k:   0     0 |9746k 4035k|   0     0 |  11k   16k>
1810M  283M  880M  980M|   0     0 :   0     0 |15-04 18:08:58| 27   8  44   0   0  21: 33   9  54   0   0   4: 38   6  54   0   0   2: 35   7  45   0   0  13|   0     0 |  10M 3162k| 28 1.0  22 7.0|   0   594  4893  4808 |   0     0 :   0     0 |  10M 3183k|   0     0 |  15k   25k>
1810M  283M  880M  980M|   0     0 :   0     0 |15-04 18:08:59| 34   4  50   0   0  13: 34   7  55   0   0   4: 36   7  55   0   0   2: 34   7  44   0   0  14|   0     0 |8940k 3239k| 28 1.0  22 7.0|   0   707  4127  4013 |   0     0 :   0     0 |8939k 3239k|   0     0 |  14k   21k>
1811M  283M  880M  979M|   0     0 :   0     0 |15-04 18:09:00| 33   7  43   0   0  17: 34   6  54   0   0   6: 30   7  60   0   0   3: 40   7  41   0   0  12|   0     0 |  10M 5010k| 28 1.0  22 7.0|   0   815  5170  4908 |   0     0 :   0     0 |  10M 4986k|   0     0 |  15k   23k>
1819M  283M  880M  971M|   0  10.0 :   0     0 |15-04 18:09:01| 28   4  67   0   0   1: 14   3  79   2   0   2:  8   2  90   0   0   0: 23   4  56   0   0  18|   0     0 |9572k 4852k| 28 1.0  22 7.0|   0  6029  7435  5223 |   0   600k:   0     0 |9565k 4852k|   0     0 |  10k   13k>
1811M  283M  880M  979M|   0     0 :   0  25.0 |15-04 18:09:02| 43   8  35   0   0  14: 25  12  54   0   0   9: 34   8  56   0   0   2: 38  10  35   0   0  16|   0     0 |9177k 4045k| 28 1.0  22 7.0|   0    78k   40k   42k|   0     0 :   0   224k|9242k 4047k|   0     0 |  13k   18k>
1812M  283M  880M  978M|   0  4.00 :   0     0 |15-04 18:09:03| 36   9  46   0   0  10: 34   6  53   0   0   6: 38   7  52   2   0   1: 36   7  45   0   0  12|   0     0 |8349k 2900k| 28 1.0  22 7.0|   0   498  4025  3894 |   0   100k:   0     0 |8333k 2911k|   0     0 |  15k   25k>
1813M  283M  880M  977M|   0     0 :   0     0 |15-04 18:09:04| 35   7  41   0   0  17: 36  10  50   0   0   5: 39   7  51   0   0   3: 41   6  40   0   0  12|   0     0 |7780k 3543k| 28 1.0  22 7.0|   0  1096  3916  3653 |   0     0 :   0     0 |7748k 3554k|   0     0 |  14k   21k>
1813M  283M  880M  977M|   0     0 :   0     0 |15-04 18:09:05| 15   2  83   0   0   0:  5   1  94   0   0   0:  3   1  96   0   0   0: 19   2  59   0   1  19|   0     0 |7519k 3252k| 28 1.0  22 7.0|   0    38  3203  3181 |   0     0 :   0     0 |7543k 3230k|   0     0 |6792  8042 >
1813M  283M  880M  977M|   0  4.00 :   0     0 |15-04 18:09:06| 15   2  81   0   0   2:  7   1  92   0   0   0:  4   1  95   0   0   0: 18   2  59   0   0  21|   0     0 |8378k 3258k| 28 1.0  22 7.0|   0    55  3499  3444 |   0   132k:   0     0 |8357k 3257k|   0     0 |7306  8673 >
1833M  283M  880M  957M|   0  3.00 :   0  3.00 |15-04 18:09:07| 29   5  60   0   0   7: 30   5  62   1   0   2: 17   5  74   1   0   2: 21   7  56   0   0  16|   0     0 |8624k 2792k| 28 1.0  22 7.0|   0    39k   23k   18k|   0   200k:   0    76k|8606k 2792k|   0     0 |9405    12k>
1816M  283M  880M  973M|   0     0 :   0     0 |15-04 18:09:08| 14   2  82   0   0   2:  9   1  90   0   0   0:  5   0  95   0   0   0: 18   3  62   0   0  17|   0     0 |8142k 2947k| 28 1.0  22 7.0|   0   517  3740  8116 |   0     0 :   0     0 |8173k 2947k|   0     0 |6901  8564 >
1819M  283M  880M  971M|   0  3.00 :   0     0 |15-04 18:09:09| 11   2  86   0   0   1:  5   2  87   6   0   0:  3   1  96   0   0   0: 16   4  60   0   0  20|   0     0 |8090k 2934k| 28 1.0  22 7.0|   0   964  4319  3731 |   0   300k:   0     0 |8076k 2934k|   0     0 |6950  8019 >
1819M  283M  880M  971M|   0     0 :   0     0 |15-04 18:09:10| 19   2  78   0   0   1:  5   2  93   0   0   0:  4   0  96   0   0   0: 13   4  62   0   0  21|   0     0 |8398k 3165k| 28 1.0  22 7.0|   0    38  3499  3466 |   0     0 :   0     0 |8380k 3164k|   0     0 |6867  8600 >
1819M  283M  880M  970M|   0  6.00 :   0     0 |15-04 18:09:11| 19   3  78   0   0   0: 10   1  77  12   0   0:  7   1  92   0   0   0: 21   2  59   0   1  18|   0     0 |8669k 3333k| 28 1.0  22 7.0|   0    32  3658  3634 |   0   432k:   0     0 |8685k 3333k|   0     0 |7376  8994 >
1828M  283M  880M  961M|   0  3.00 :   0     0 |15-04 18:09:12| 32   5  57   0   0   6: 23   4  67   5   0   1: 28   7  65   0   0   0: 36   6  48   0   0  11|   0     0 |9024k 3930k| 28 1.0  22 7.0|   0    28k   18k   16k|   0    16k:   0     0 |9015k 3933k|   0     0 |  11k   13k>
1820M  283M  880M  969M|   0     0 :   0     0 |15-04 18:09:13| 29   3  66   0   0   2: 19   5  75   0   0   2: 12   4  84   0   0   0: 27   4  54   0   0  15|   0     0 |6956k 3665k| 28 1.0  22 7.0|   0    10k 9171    11k|   0     0 :   0     0 |6965k 3662k|   0     0 |8907    10k>
1823M  283M  880M  967M|   0  5.00 :   0     0 |15-04 18:09:14| 25   3  70   0   0   2: 11   2  80   7   0   0:  7   1  92   0   0   0: 28   3  56   0   0  13|   0     0 |5157k 3863k| 28 1.0  22 7.0|   0   714  3254  2560 |   0    84k:   0     0 |5146k 3863k|   0     0 |6942  7700 >
1823M  283M  880M  967M|   0     0 :   0     0 |15-04 18:09:15| 19   1  79   0   0   1:  5   0  95   0   0   0:  6   2  92   0   0   0: 23   3  56   0   0  19|   0     0 |4816k 3355k| 28 1.0  22 7.0|   0    74  2324  2297 |   0     0 :   0     0 |4813k 3355k|   0     0 |6838  7904 >
1824M  283M  880M  966M|   0     0 :   0     0 |15-04 18:09:16| 18   1  80   0   0   1:  9   1  90   0   0   0:  2   1  97   0   0   0: 30   4  53   0   0  13|   0     0 |4395k 4474k| 28 1.0  22 7.0|   0   169  2488  2259 |   0     0 :   0     0 |4413k 4475k|   0     0 |7118  7352 >
1829M  283M  880M  960M|   0  6.00 :   0     0 |15-04 18:09:17| 26   5  63   0   0   7: 16   3  73   6   0   2: 15   6  79   0   0   0: 30   2  52   0   0  16|   0     0 |7447k 4841k| 28 1.0  22 7.0|   0    18k   12k   11k|   0   108k:   0     0 |7456k 4842k|   0     0 |9505    11k>
1832M  283M  880M  957M|   0     0 :   0     0 |15-04 18:09:18| 27   5  65   0   0   3: 30   4  66   0   0   0: 13   3  82   0   0   2: 23   5  58   0   0  14|   0     0 |6366k 3817k| 28 1.0  22 7.0|   0    21k   14k   13k|   0     0 :   0     0 |6347k 3817k|   0     0 |8592    10k>
1824M  283M  880M  966M|   0  8.00 :   0     0 |15-04 18:09:19| 23   4  73   0   0   0: 14   0  79   6   0   1:  8   1  91   0   0   0: 19   4  57   3   0  18|   0     0 |7368k 4991k| 28 1.0  22 7.0|   0   257  3587  5866 |   0   692k:   0     0 |7360k 4990k|   0     0 |7935  9330 >
1824M  283M  880M  966M|   0  6.00 :   0     0 |15-04 18:09:20| 22   3  74   0   0   1:  9   2  84   5   0   0:  4   1  95   0   0   0: 22   3  60   0   0  15|   0     0 |5163k 4312k| 28 1.0  22 7.0|   0    19  2468  2534 |   0    52k:   0     0 |5201k 4313k|   0     0 |6512  7081 >
1825M  283M  880M  965M|   0     0 :   0     0 |15-04 18:09:21| 29   6  65   0   0   0: 13   1  86   0   0   0:  6   3  91   0   0   0: 28   6  54   0   0  13|   0     0 |6441k 4364k| 28 1.0  22 7.0|   0    19  3601  3501 |   0     0 :   0     0 |6405k 4363k|   0     0 |8127  9546 >
1826M  283M  880M  964M|   0  5.00 :   0     0 |15-04 18:09:22| 35   2  60   0   0   3: 18   3  78   0   0   1: 12   3  78   6   0   0: 37   3  50   0   0  10|   0     0 |4863k 5435k| 28 1.0  22 7.0|   0    10k 8223  7820 |   0   212k:   0     0 |4861k 5435k|   0     0 |8251  8652 >
1810M  283M  880M  980M|   0     0 :   0     0 |15-04 18:09:23| 30   4  64   0   0   2: 31   4  65   0   0   0: 22   5  71   0   0   2: 32   4  50   0   0  14|   0     0 |5882k 4894k| 28 1.0  22 7.0|   0    24k   16k   20k|   0     0 :   0     0 |5935k 4895k|   0     0 |9518    11k>
1814M  283M  880M  976M|   0  3.00 :   0     0 |15-04 18:09:24| 33   2  63   0   0   2: 17   2  75   6   0   0:  6   1  93   0   0   0: 39   6  45   0   0  10|   0     0 |3716k 3726k| 28 1.0  22 7.0|   0  5677  5533  4572 |   0   300k:   0     0 |3686k 3726k|   0     0 |7650  8065 >
1814M  283M  880M  976M|   0  12.0 :   0     0 |15-04 18:09:25| 27   2  66   4   0   1: 15   2  79   5   0   0:  5   2  92   1   0   0: 25   3  60   0   0  12|   0     0 |5577k 4727k| 28 1.0  22 7.0|   0   365  3201  3237 |   0   784k:   0     0 |5553k 4726k|   0     0 |7553  8362 >
```

**Things I've tried without success: **
[LIST]
[*]I thought this would be a case of DPMS misbehaving, so I stopped X from starting during boot and removed all power saving features from the console. 
[*]My NIC is apparently famous for causing headaches (Realtek RTL8111/8168B) so I installed the drivers from the manufacturer. It eliminated nasty errors in syslog but didn't stop the freezing. 
[*]Disabled many different BIOS features, including ACPI, HPET, all power saving related features, all unused hardware (IDE, extra SATA chip, COM port, audio etc.). 
[*]Replaced RAM.
[*]Googled a lot and found very little (aside from on the DPMS and Realtek NIC issues). 
[/LIST]

Does anyone have any suggestions as to where I might look next to get this sorted out?

---

### Post by gdi2k on 2013-04-15
Quick update: Given that I am accessing the server remotely, I wondered if maybe only the NIC is freezing and the OS / apps are actually continuing to run normally, albeit inaccessible via the network. 

So I ran dstat within screen so it didn't depend on my connectivity. Result: Exactly the same - the whole machine really does seem to freeze, not just the NIC.

---

### Post by gdi2k on 2013-04-15
Second update, hopefully this will help someone. While bumbling around the Server Platform forums, I came accross this: 
[http://ubuntuforums.org/showthread.php?t=1397722](http://ubuntuforums.org/showthread.php?t=1397722)

It's a very old thread but was coincidentally bumped just at the right time for me to spot it. The recommendation of adding: 
```
acpi=off
```
to the boot command in grub seems to have resolved it - no more freezes so far...

I thought initially it may be ACPI-related, which is why I disabled it in the BIOS, but that didn't fix it. Forcing it off from the OS side seems to work differently for some reason, and works for me. :)

---

### Post by ian dobson on 2013-04-15
Hi,

Have a look if there's a BIOS update for your mainboard. It sounds as if there are some really nasty bugs in the BIOS/acpi irq mapping table.

regards
Ian Dobson

---

### Post by gdi2k on 2013-04-16
Thanks for the tip! I actually don't have direct access to the machine at the moment, so I can't check what BIOS version it has, but there is a new BIOS release for it from 2011 which I probably don't have as it's been mothballed for a while. 

I'll check it out when I can get at it in May, although the update process looks like a mission - Windows-only! But now that it's no longer freezing, I'm tempted to just leave it alone - if it ain't broke, don't fix it... we'll see how it goes...

---

