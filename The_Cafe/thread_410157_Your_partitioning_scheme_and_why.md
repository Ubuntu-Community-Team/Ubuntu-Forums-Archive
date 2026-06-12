---
title: "Your partitioning scheme and why?"
date: 2007-03-16
forum: The Cafe
---

### Post by aysiu on 2007-03-16
This could be the dumbest thread, but I'm going to go ahead and make it anyway.

What's your output of this [terminal](http://www.psychocats.net/ubuntu/terminal) command? ```
sudo fdisk -l
```?

For you first-timers, that last letter is a lowercase *L*. It's not the number one or an uppercase *i*

Here's mine: ```
sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS
/dev/hda2            1912       19457   140938245    5  Extended
/dev/hda5            1912       18174   130632516   83  Linux
/dev/hda6           18175       18295      971901   82  Linux swap / Solaris
/dev/hda7           18296       19457     9333733+  83  Linux
``` Even though I don't boot into Windows, I still keep it in my dual boot "just in case." That huge chunk (/dev/hda5) is my separate /documents partition (I prefer to have a separate /documents partition instead of a separate /home partition).

Any other takers?

---

### Post by johnc4510 on 2007-03-16
Disk /dev/hda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1702    13671283+  83  Linux
/dev/hda2            1703        1824      979965   82  Linux swap / Solaris
/dev/hda3            1825        7301    43994002+  83  Linux

---

### Post by maniacmusician on 2007-03-16
```

Disk /dev/sda: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26109   209720511   83  Linux
/dev/sda2           26110       38913   102848130   83  Linux

Disk /dev/sdb: 80.0 GB, 80059342336 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3039    24410736   83  Linux
/dev/sdb2            3040        3440     3221032+   5  Extended
/dev/sdb5            3040        3440     3221001   82  Linux swap / Solaris

```

sda1 is my /home/[user] partition, sda2 is my /media/Music partition. And sdb is where I install my systems. At the moment, I only have a 20GB Ubuntu partition on there, the rest is empty.

---

### Post by Zuuswa on 2007-03-16
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1281    10289601   83  Linux
/dev/hda2            1282        1411     1044225   82  Linux swap / Solaris
/dev/hda3            1412        3961    20482875   83  Linux
/dev/hda4            3962        9729    46331460   83  Linux

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12188    97900078+   b  W95 FAT32
```
my external hd is fat32 so I can plug it into a winbox and grab the files off of it

---

### Post by C-A on 2007-03-16
> Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+  83  Linux
/dev/hda2            1913        2039     1020127+  82  Linux swap / Solaris
/dev/hda3            2040        7476    43672702+  83  Linux

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       30401   244196001   83  Linux

Disk /dev/hdd: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        4982    40017883+  83  Linux


hda1 - / for kubuntu
hda2 - swap
hda3 - /home 

hdc1 - used for media - music and divx

hdd1 - used for downloads

---

### Post by karellen on 2007-03-16
here's mine

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1215     9759456    7  HPFS/NTFS
/dev/hda2            1216        2425     9719325    c  W95 FAT32 (LBA)
/dev/hda3            2426        7165    38074050    f  W95 Ext'd (LBA)
/dev/hda4            7166        7297     1060290   82  Linux swap / Solaris
/dev/hda5            2426        3426     8040501    b  W95 FAT32
/dev/hda6            3427        6059    21149541    b  W95 FAT32
/dev/hda7            6060        7165     8883913+  83  Linux

it's a little messy but I got used to it :D

---

### Post by beercz on 2007-03-16
Mine is pretty straightforward:

> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris
There you go!

---

### Post by Piotr.Sniady on 2007-03-18
```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        4864    38821072+   5  Extended
/dev/hda5              32         121      722893+  82  Linux swap / Solaris
/dev/hda6             122        4864    38098116   8e  Linux LVM
```All jewels are hidden in Linux LVM partition.

---

### Post by ButteBlues on 2007-03-18
```
will@kalmwave:~$ sudo fdisk -l

Disque /dev/hda: 40.0 Go, 40007761920 octets
255 têtes, 63 secteurs/piste, 4864 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1               1        3363    27013266   83  Linux
/dev/hda2            3364        4668    10482412+  83  Linux
/dev/hda4            4669        4864     1574370    5  Extended
/dev/hda5            4669        4864     1574338+  82  Linux swap / Solaris

```

---

### Post by happy-and-lost on 2007-03-18
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1147     9213246    5  Extended
/dev/sda2   *        1148        3123    15872220    7  HPFS/NTFS
/dev/sda3            3124        7230    32989477+  83  Linux
/dev/sda4            7231        7296      530145   82  Linux swap / Solaris
/dev/sda5               1         640     5140737   83  Linux
/dev/sda6             641        1147     4072446   83  Linux

```

---

### Post by reacocard on 2007-03-18
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

/dev/hda1               1          26      208813+  88  Linux plaintext
/dev/hda2              27        9729    77939347+   f  W95 Ext'd (LBA)
/dev/hda5            1952        2104     1228941   82  Linux swap / Solaris
/dev/hda6            2105        9729    61247781   83  Linux
/dev/hda7              27        1951    15462499+  83  Linux
```
hda1 is for HP's QuickPlay (is there any way to mount this? I'd like to see what's actually in there.) The others should be self-explanatory.

---

### Post by Gustav on 2007-03-18
```
Disk /dev/hda: 82,3 GB, 82348277760 byte
255 huvuden, 63 sektorer/spår, 10011 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1               1        1275    10241406   83  Linux
/dev/hda2            1276       10011    70171920    f  W95 Utökad (LBA)
/dev/hda5            1276        1402     1020064+  83  Linux
/dev/hda6            1403       10011    69151761   83  Linux
```

---

### Post by RandomJoe on 2007-03-18
RAID rules! :) 

My desktop (RAID1):
```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9483    76172166   83  Linux
/dev/hda2            9484        9729     1975995   82  Linux swap / Solaris

Personalities : [raid1]
md0 : active raid1 sda1[0] sdb1[1]
      293033536 blocks [2/2] [UU]

unused devices: <none>
```
The system and all data are on the RAID drives.  The roughly 75GB on hda is unused at this point...  Can't remember just why I put the drive in there now! :rolleyes:

The server (RAID5):
```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666   fd  Linux raid autodetect

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   fd  Linux raid autodetect

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36483   293049666   fd  Linux raid autodetect

Disk /dev/sdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36483   293049666   fd  Linux raid autodetect

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14311   114953076   83  Linux
/dev/hda2           14312       14593     2265165    5  Extended
/dev/hda5           14312       14593     2265133+  82  Linux swap / Solaris

Personalities : [raid5]
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      879148800 blocks level 5, 32k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
```
The system is on /dev/hda in this case, I've gone through several distributions while the RAID array remains untouched!  Nice...

(Fdisk gives useless info on the RAID array itself so I replaced it with the contents of /proc/mdstat...)

---

### Post by AtrejuT on 2007-03-18
```

Disk /dev/sda: 92.3 GB, 92399714304 bytes
255 heads, 63 sectors/track, 11233 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         448        2997    20482875    7  HPFS/NTFS
/dev/sda2            2998        5037    16386300   83  Linux
/dev/sda3               1         447     3590496   82  Linux swap / Solaris
/dev/sda4            5038       11233    49769370   83  Linux

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 912 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           3       96264    0  Empty
/dev/sdb2               4         912    29206170    b  W95 FAT32

Disk /dev/sdc: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2431    19526976   83  Linux

```

including all (2) external disks I could find just now... ;-)
and there's a windows partition as well...

---

### Post by Obor on 2007-03-18
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1402    11261533+   7  HPFS/NTFS
/dev/hda2            1403        2804    11261565   83  Linux
/dev/hda3            2805        7138    34812855    b  W95 FAT32
/dev/hda4            7139        7296     1269135   82  Linux swap / Solaris

```

hda1=winXP
hda2=ubuntu
hda3=documents

---

### Post by wilberfan on 2007-03-18
Well, I've gone *Penguinsane:*

I've got 2 hd's and FOUR distros (XP, Feisty64, Edgy32, and openSuSE 10.2 64-bit), so I got LOTS o' partitions!!

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       30400   218588422+   f  W95 Ext'd (LBA)
/dev/sda5            8023       30400   179751285    7  HPFS/NTFS
/dev/sda6            6748        8022    10241406   83  Linux
/dev/sda7            5473        6747    10241406   83  Linux
/dev/sda8            4198        5472    10241406   83  Linux
/dev/sda9            3969        4197     1839411   82  Linux swap / Solaris
/dev/sda10           3188        3967     6265287   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5099    40957686   83  Linux
/dev/sdb3            5100       30401   203238315    5  Extended
/dev/sdb5            5100       12841    62187583+  83  Linux
/dev/sdb6           12842       14116    10241406   83  Linux
/dev/sdb7           14117       15423    10490445   83  Linux

:shock:   (And I haven't even mentioned by OTHER box...)

---

### Post by use a name on 2007-03-18
> 
Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         131     1052226   83  Linux
/dev/hda2   *         132        2742    20972857+   7  HPFS/NTFS
/dev/hda3            2743        5353    20972857+  83  Linux
/dev/hda4            5354       14946    77055772+   f  W95 Ext'd (LBA)
/dev/hda5            5354        7312    15735636   83  Linux
/dev/hda6            7313        9271    15735636   83  Linux
/dev/hda7            9272       14493    41945683+   c  W95 FAT32 (LBA)
/dev/hda8           14494       14946     3638691   82  Linux swap / Solaris

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1307    10490445   83  Linux
/dev/hdb2            6529       38913   260132512+   c  W95 FAT32 (LBA)
/dev/hdb3            1307        6528    41945683+  83  Linux


hda: OS disk
hda1: reserved for Win98, maybe once, to play that one game that doesn't run on anything else
hda2: WinXP
hda3: reserved for Vista, need to see that once
hda5: openSuse
hda6: Ubuntu
hda7: backup

hdb: data disk
hdb1: /home
hdb2: downloads, mp3, some old complete hdd backups
hdb3: data for linux only

---

### Post by prizrak on 2007-03-18
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           8       64228+  83  Linux
/dev/hda2               9         506     4000185   83  Linux
/dev/hda3             507        9604    73079685   83  Linux
/dev/hda4            9605        9729     1004062+  82  Linux swap / Solaris

```
hda1 - boot
hda2 - /
hda3 - /home
hda4 - swap

---

### Post by mcduck on 2007-03-18
This is from my laptop:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/hda2   *         244        3430    25599577+   c  W95 FAT32 (LBA)
/dev/hda3            3431        5980    20482875   83  Linux
/dev/hda4            5981        9729    30113842+   5  Extended
/dev/hda5            9539        9729     1534207+  82  Linux swap / Solaris
/dev/hda6            5981        9538    28579572   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9611    77200326   83  Linux
/dev/sda2            9612       12161    20482875    b  W95 FAT32

```

---

### Post by yopnono on 2007-03-18
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         729     5855661   83  Linux
/dev/sda2             730        6009    42411600   83  Linux
/dev/sda3            6010        6210     1614532+  82  Linux swap / Solaris
```

sda1 /
sda2 / home
sda3 / swap


Easy and simple

---

### Post by X-626 on 2007-03-18
```
Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7644    61400398+  83  Linux
/dev/hda2            7645        9603    15735667+  83  Linux
/dev/hda3            9604        9733     1044225   82  Linux swap / Solaris
```hda1: /
hda2: /home
hda3: swap (don't really think I need to mention that, though)

Not really much to my partition table.

---

### Post by ramasdf123 on 2007-03-18
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=27802&stc=1&d=1174271392[/IMG]

---

### Post by Kujen on 2007-03-18
```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11784    94654948+  83  Linux
/dev/hda2           11785       12161     3028252+   5  Extended
/dev/hda5           11785       12161     3028221   82  Linux swap / Solaris

```

---

### Post by Rotarychainsaw on 2007-03-18
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        9728    37182442+   f  W95 Ext'd (LBA)
/dev/hda5            5100        9728    37182411    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3308    26571478+   7  HPFS/NTFS
/dev/hdb2            3309        9729    51576682+   5  Extended
/dev/hdb5            3309        9729    51576651   83  Linux

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3497    28089621   83  Linux
/dev/sda2            3498        3649     1220940    5  Extended
/dev/sda5            3498        3649     1220908
```

Man, when I built this computer, this was like the most disk space anyone had ever seen lol.

---

### Post by LookTJ on 2007-03-19
Here's mine

```
[B]Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4676    37559938+  83  Linux
/dev/hda2            4677        4864     1510110    5  Extended
/dev/hda5            4677        4864     1510078+  82  Linux swap / Solaris
[/B]
```

---

### Post by public_void on 2007-03-19
```
Disk /dev/hda: 50.0 GB, 50018393088 bytes
255 heads, 63 sectors/track, 6081 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *           1        4418    35487553+   7  HPFS/NTFS
/dev/hda3            4419        6016    12835935   83  Linux
/dev/hda4            6017        6081      522112+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 514 MB, 514850816 bytes
16 heads, 32 sectors/track, 1964 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1964      502768    e  W95 FAT16 (LBA)

```1. My hard drive, numbering starts at 2 because I removed a hidden partition of 6GB put in by the OEM.
2. My external harddrive
3. My USB stick

---

### Post by matthew on 2007-03-19
> **aysiu said:**
> This could be the dumbest thread, but I'm going to go ahead and make it anyway.Mine has changed since I posted a thread on this issue ( [July 13, 2005 ]("http://ubuntuforums.org/showthread.php?t=48561")). :) I hope it's not a dumb thread topic. Since my thread is so old I'll link to it, but I'll also close it so it doesn't get resurrected.

Here's my current data:
```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         170     1365493+  82  Linux swap / Solaris
/dev/hda2   *         171        2089    15414367+  83  Linux
/dev/hda3            2090       12161    80903340   83  Linux

```

---

### Post by xyz on 2007-03-19
Well here is mine. Not much use of Windows any more but I keep it anyways.
> sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        3187    10241437+  83  Linux
/dev/hda3            3188        9548    51094732+   c  W95 FAT32 (LBA)
/dev/hda4            9549        9729     1453882+   f  W95 Ext'd (LBA)
/dev/hda5            9549        9729     1453851   82  Linux swap / Solaris

Just a thought here:

I remember the days when the **-l** of *sudo fdisk -l* looked (was in my head) a 1 as in one.
Wouln't it make more sense, once and for all, to say that the **-l** stands for *list*; and therefore the command line *sudo fdisk -l* will **list** partitions?

I think if someone had explained to me that way, I'd have understood quicker what the command line does and what it stands for exactly.
Just a thought...

---

### Post by SishGupta on 2007-03-19
On my pc (hdb1 system type is incorrect...but only in fdisk)
hda1 is /
hda5 is /home
hdb1 is long term storage, it is only ntfs because I cant convert right now
```

Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4231    33985476   83  Linux
/dev/hda2            4232        4982     6032407+   5  Extended
/dev/hda5            4232        4884     5245191   83  Linux
/dev/hda6            4885        4982      787153+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14593   117218241    6  FAT16

```

On the laptop
sda1 is the windows i am forced to use
sda5 is /
sda6 is /home
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        7296    27888840    5  Extended
/dev/sda5            3825        6501    21502971   83  Linux
/dev/sda6            6502        7139     5124703+  83  Linux
/dev/sda7            7140        7296     1261071   82  Linux swap / Solaris

```

---

### Post by blueturtl on 2007-03-19
Two HDDs, the first contains /boot and /, second /home and swap.
Notice the absolute lack of FAT or NTFS partitions.  ;)

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          15      120456   83  Linux
/dev/hda2              16        4865    38957625    5  Extended
/dev/hda5              16        4865    38957593+  83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241    5  Extended
/dev/hdb5               1          61      489919+  82  Linux swap / Solaris
/dev/hdb6              62       14593   116728258+  83  Linux
```

---

### Post by atdi4ever on 2007-03-20
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2081    15732328+   7  HPFS/NTFS
/dev/hda2            3470       20673   130062209    f  W95 Ext'd (LBA)
/dev/hda3            2082        2775     5246636+  83  Linux
/dev/hda4            2776        3469     5246640   83  Linux
/dev/hda5            3470        3746     2094088+  82  Linux swap / Solaris
/dev/hda6            3747       20673   127968088+   b  W95 FAT32
```

---

### Post by Rizado on 2007-03-20
```
Disk /dev/mapper/isw_bbdjfefhjf_HDS72161_RAID: 329,3 GB, 329392586752 byte
255 huvuden, 63 sektorer/spår, 40046 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

                                    Enhet Start     Början        Slut     Block    Id  System
/dev/mapper/isw_bbdjfefhjf_HDS72161_RAID1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/mapper/isw_bbdjfefhjf_HDS72161_RAID2            2551        5100    20482875   83  Linux
/dev/mapper/isw_bbdjfefhjf_HDS72161_RAID3            5101        5291     1534207+  82  Linux växling / Solaris
/dev/mapper/isw_bbdjfefhjf_HDS72161_RAID4            5292       40046   279169537+   6  FAT16
```

FAT16? FAT16 can't even be that large. It's a ext3 partition. Very strange...

---

### Post by nyinge on 2007-03-20
```
 sudo fdisk -l /dev/mapper/isw_bghfabfaea_Volume0 
``````

Disk /dev/mapper/isw_bghfabfaea_Volume0: 320.0 GB, 320079134720 bytes
255 heads, 63 sectors/track, 38914 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bghfabfaea_Volume0p1   *           1        6080    48837568+  83  Linux
/dev/mapper/isw_bghfabfaea_Volume0p2            6081       18482    99619065    5  Extended
/dev/mapper/isw_bghfabfaea_Volume0p5            6081        6324     1959898+  82  Linux swap / Solaris
/dev/mapper/isw_bghfabfaea_Volume0p6            6325       18482    97659103+  83  Linux

```

---

### Post by xyz on 2007-03-20
Could this "sudo fdisk -l /dev/mapper/isw_bghfabfaea_Volume0" be explained?

---

### Post by Toontwnca on 2007-03-20
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris

---

### Post by erwinquita on 2007-03-20
Here's mine :)

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       14084    92156872+   7  HPFS/NTFS
/dev/sda3           14085       19457    43158622+   5  Extended
/dev/sda5           14085       14148      514048+  83  Linux
/dev/sda6           14149       14670     4192933+  82  Linux swap / Solaris
/dev/sda7           14671       18494    30716248+  83  Linux
/dev/sda8           18495       18518      192748+  83  Linux
/dev/sda9           18519       18767     2000061   82  Linux swap / Solaris
/dev/sda10          18768       19457     5542393+  83  Linux


```

---

### Post by nyinge on 2007-03-20
> **xyz said:**
> Could this "sudo fdisk -l /dev/mapper/isw_bghfabfaea_Volume0" be explained?

I have 2 drives on software raid 0.  Those drives and partitions in them are shown in /dev/mapper/ instead of /dev.
```

# ll /dev/mapper/
total 0
crw-rw---- 1 root root  10, 63 Mar 20 00:21 control
brw-rw---- 1 root disk 239,  0 Mar 20 00:21 isw_bghfabfaea_Volume0
brw-rw---- 1 root disk 239,  1 Mar 20 00:21 isw_bghfabfaea_Volume01
brw-rw---- 1 root disk 239,  2 Mar 20 00:21 isw_bghfabfaea_Volume05
brw-rw---- 1 root disk 239,  3 Mar 20 00:21 isw_bghfabfaea_Volume06

```So, isw_bghfabfaea_Volume0 is considered a virtual drive, and the subsequent numbers are its partitions.  In this case, "...Volume01" is the first partition.   The numbers are not in order, because some are primary and some extended partitions.  I don't really know the technicalities behind it though.

That's why I had to use
```
 # fdisk -l /dev/mapper/isw_bghfabfaea_Volume0 
```If I just do ```
 # fdisk -l 
```I get some garbage :( ... like
```

Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Unable to seek on /dev/sda

```

---

### Post by Kingsley on 2007-03-20
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26500   212861218+   7  HPFS/NTFS
/dev/sda2           26501       30238    30025485   83  Linux
/dev/sda3           30239       30401     1309297+   5  Extended
/dev/sda5           30239       30401     1309266   82  Linux swap / Solaris

```

sda1 = Windows Vista and the majority of my media storage
sda2 = Kubuntu

---

### Post by Motoxrdude on 2007-03-20
```
sudo fdisk -l
Password:

Disk /dev/sda: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2805    22531131    7  HPFS/NTFS
/dev/sda2            2806        7267    35841015   83  Linux
/dev/sda4            7268       30087   183301650    f  W95 Ext'd (LBA)
/dev/sda5           17868       30025    97659103+  83  Linux
/dev/sda6           30026       30087      497983+  82  Linux swap / Solaris
/dev/sda7            7268       11522    34178224+  83  Linux

```

---

### Post by hanzomon4 on 2007-03-20
I'll play....```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+  83  Linux
/dev/hda2           30217       30401     1486012+   5  Extended
/dev/hda3            1913       30216   227351880   83  Linux
/dev/hda5           30217       30401     1485981   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1944    15615148+  83  Linux
/dev/sda2            6002       12003    48211065   83  Linux
/dev/sda3           12004       12188     1486012+   5  Extended
/dev/sda4            1945        6001    32587852+  83  Linux
/dev/sda5           12004       12188     1485981   82  Linux swap / Solaris


```

I have 3 distros : [list][*]Edgy on the internal hard drive[*]Feisty and MintLinux on the usb drives[/list]
hda=/
hda2+4=/swap
hda3=/home
sda=/
sda2=/home
sda3+5=/swap
sda4=/mintlinux/

OT Question can I have mintlinux and edgy share my hda3=/home partition?

---

### Post by tbodine on 2007-03-20
```
tbodine@eisenstein:~$ sudo fdisk -l
Password:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          15      120456   83  Linux
/dev/hda2              16         145     1044225   82  Linux swap / Solaris
/dev/hda3             146        7476    58886257+   5  Extended
/dev/hda5             146        2950    22531131   83  Linux
/dev/hda6            2951        6774    30716248+  83  Linux
/dev/hda7            6775        7476     5638783+  83  Linux

```

hda1: /boot
hda2: swap
hda3: extended
hda5: /
hda6: /home
hda7: /tmp

---

### Post by plb on 2007-04-15
Personally, since mine is merely a home system with no critical services running I have a separate / and /home which allows me to keep all my settings, docs, music, films etc in case my system should run a muck and I have to reinstall.

---

### Post by trivialpackets on 2007-04-15
I have half of my 60 gig to Windows XP Pro (ntfs), as I use it for a few choice games that I play and such.  Then I divide the remaining 30 into 3 partitions, a 4gb (fat32), appropriately labeled /shared, as I use it to share information between the two OS' that are installed on the system, then 10 for / and 16ish for /home.

---

### Post by 9a3eedi on 2007-04-15
I got 2 hard disks:

1 SATA 150GB 10k rpm hard disk for Windows XP (now unused at all and riddled with viruses) NTFS
1 PATA 40 GB reiserfs for Edgey amd64

I want to switch around the hard disks >__<

---

### Post by trivialpackets on 2007-04-15
Mine's not riddled with virus'.....yet, I reinstalled this morning.  :)

---

### Post by aysiu on 2007-04-15
I've merged your thread with the other, similar one.

---

### Post by Rhapsody on 2007-04-15
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648        9483    46877670   83  Linux
/dev/sda3            9484        9729     1975995   82  Linux swap / Solaris
```

sda1: /
sda2: /home
sda3: swap

I plan to keep sda1 and sda2, and move them over to a new PC later this year. sda1 is more than big enough to do everything I want (e.g. hold the operating system and applications) and I can make sda2 as big as I like since it'll be going on a really big drive with nothing but empty space after it.

I'll also be having an equally large sdb1 on another drive, and sdb2 as a new swap partition.

---

### Post by Fascination on 2007-04-15
Is it just me that likes to give /var/ its on partition? :-P It was drummed into my head by a sysadmin at work that no matter how I choose to do my partitioning (though he still gave me strict instructions on what he considered the most secure method), I should always give var a set partition; that way if something goes wrong and you have a rapidly increasing logfile in it, it can only get so big instead of using up all the space on your hard drive.

---

### Post by rai4shu2 on 2007-04-15
No /var partition for me. I like to live dangerously:

```
$ sudo fdisk -l

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.
```

Oops, still using Debian:

```
$ su -
Password: 
debian:~# fdisk -l

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       11473    92156841    7  HPFS/NTFS
/dev/hdb2           11474       16572    40957717+  83  Linux
/dev/hdb3           16573       22947    51207187+   5  Extended
/dev/hdb4           22948       36483   108727920   83  Linux
/dev/hdb5           16573       21671    40957686   83  Linux
/dev/hdb6           21672       21932     2096451   82  Linux swap / Solaris
/dev/hdb7           21933       22947     8152956    b  W95 FAT32
```

hdb4 = /home, hdb2 and hdb5 = /, hdb1 and hdb7 = Windows

---

### Post by Happy_Man on 2007-04-15
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        6093    48901860    7  HPFS/NTFS
/dev/hda3            6094       14500    67529227+  83  Linux
/dev/hda4           14501       14593      747022+   5  Extended
/dev/hda5           14501       14593      746991   82  Linux swap / Solaris

Disk /dev/sda: 1014 MB, 1014497280 bytes
250 heads, 32 sectors/track, 247 cylinders
Units = cylinders of 8000 * 512 = 4096000 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         248      990704    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 249, 32) logical=(247, 169, 32)

```

That bit at the bottom is my flash drive, for quick info access....or maybe b/c I was too lazy to unplug it. Either one.

---

### Post by click4851 on 2007-04-15
here is mine, 2 hardrives:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        6387    51303546   83  Linux                                      /
/dev/hda2           16924       17565     5156865    5  Extended              
/dev/hda3            6388       16923    84630420   83  Linux                                  /home
/dev/hda4           17566       30401   103105170   83  Linux
/dev/hda5           16924       17565     5156833+  82  Linux swap / Solaris         /swap

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2568    20627428+   7  HPFS/NTFS                          /winxp
/dev/hdb2            2569        8006    43680735   83  Linux
/dev/hdb3            8007       19457    91980157+  83  Linux

Just added the 250Gig and created my seperate /home from aysiu's guide (thank you), and made some additional partions for future use.

---

### Post by Mateo on 2007-04-15
why is it that some people's partitions are named hda and some sda?

---

### Post by bashologist on 2007-04-15
Using the stable debian etch. Not a byte of windows on the hdd's.
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       26108   209712478+   5  Extended
/dev/sdb2           26109       26485     3028252+  82  Linux swap / Solaris
/dev/sdb3           26486       27790    10482412+  83  Linux
/dev/sdb4           27791       30401    20972857+  83  Linux
/dev/sdb5               1       26108   209712447   83  Linux
```

df -h
```
Filesystem      Size  Used Avail Use% Mounted on Comment
/dev/sdb5       197G  147G   41G  79% /data      #For all my media, pictures, documents.
/dev/sdb3       9.9G  4.0G  5.4G  43% /ubuntu    #For root ubuntu, soon to be feisty from edgy.
/dev/sdb4        20G  8.0G   11G  43% /          #For root debian.
/dev/sda1       230G  356M  218G   1% /backup    #A full hdd for backups.
```

---

### Post by Lucifiel on 2007-04-15
Here we go! :D

> lucifiel@lucifiel:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        3187    25591545    f  W95 Ext'd (LBA)
/dev/sda2            3188        9725    52516485    7  HPFS/NTFS
/dev/sda5               2         893     7164958+   7  HPFS/NTFS
/dev/sda6             894        1622     5855661   83  Linux
/dev/sda7            1866        3187    10618933+   b  W95 FAT32
/dev/sda8            1623        1865     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdc2            2551       10199    61440592+   7  HPFS/NTFS
/dev/hdc3           10200       19457    74364885    7  HPFS/NTFS
lucifiel@lucifiel:~$ 


---

### Post by koenn on 2007-04-15
> **Mateo said:**
> why is it that some people's partitions are named hda and some sda?
hd_ is for IDE disks, aka ATA or , recently PATA or Parallel ATA. Is a specification.  Recently, SATA disks (serial ATA) became more mainstream. Linux approaches them through its scsi driver, so sd_ sisks are SCSI, or, more likely in desktop computers, SATA disks.

---

### Post by Compucore on 2007-04-15
On my old aptiva here that I had running with ubuntu. I had it with two drives a 20 gig for ubuntu and software itself and the 30 gig drive I had the /user accounts on this drive. Both drivers I had put a 768 meg swap drive on both to make sure that there was enough swap space and enough space in general for the OS and the users account. It will change when I bring it to the two servers that I have that are running raid 5 on it. 

Compucore

---

### Post by jsonder on 2007-04-15
Dell notebook:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks            Id  System
/dev/sda1   *           1           2089    16779861       7  HPFS/NTFS
/dev/sda2            2090        4167    16691535     83  Linux
/dev/sda3            4168        4422     2048287+   82  Linux swap / Solaris
/dev/sda4            4423        9546    41158530       5  Extended
/dev/sda5            4423        9546    41158498+  83  Linux

sda1 = XP
sda2 = Feisty
sda5 = /home

******************************************************************

Old HP Pavilion 724c

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks             Id  System
/dev/hda1               1            2590    20804143+  83  Linux
/dev/hda2            2591        4247    13309852+  83  Linux
/dev/hda3            4248        5934    13550827+  83  Linux
/dev/hda4            5935        9729    30483337+    5  Extended
/dev/hda5            5935        6195     2096451      82  Linux swap / Solaris
/dev/hda6            6196        9729    28386823+  83  Linux 

hda6 = /home

hda1, hda2, and hda3 are ubuntu and mepis versions

Disk /dev/hdb: 10.1 GB, 10110320640 bytes
16 heads, 63 sectors/track, 19590 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19590     9873328+  83  Linux

hdb1 = /backuup   an old hd for file backup

******************************************************************

G4 mac mini

/dev/hda
        #      type name                  length   base      ( size )  system
/dev/hda1   Apple_partition_map Apple      63 @ 1         ( 31.5k)  Partition map
/dev/hda2   Apple_Bootstrap NWboot    1953126 @ 19001424  (953.7M)  NewWorld bootblock
/dev/hda3   Apple_HFS Apple_HFS_Untitled_2  18739216 @ 262208    (  8.9G)  HFS
/dev/hda4   Apple_UNIX_SVR2 swap      2929688 @ 20954550  (  1.4G)  Linux swap
/dev/hda5   Apple_UNIX_SVR2 Ubuntu   28906251 @ 23884238  ( 13.8G)  Linux native
/dev/hda6   Apple_UNIX_SVR2 home    103510999 @ 52790489  ( 49.4G)  Linux native
/dev/hda7   Apple_Free Extra           262144 @ 64        (128.0M)  Free space

hda3 = OSX 10.4
hda6 = /home (Edgy)

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0

******************************************************************

Old Toshiba Notebook

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         892     7164958+  83  Linux
/dev/hda2             893         990      787185   82  Linux swap / Solaris
/dev/hda3             991        2432    11582865   83  Linux

Mephis 6.5  hda3 = /home

---

### Post by Skidpad on 2007-04-15
Here's mine (3 yr old laptop):

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          11        2297    18370327+   7  HPFS/NTFS
/dev/hda2            2298        4761    19792080   83  Linux
/dev/hda3            4762        4870      875542+   5  Extended
/dev/hda5            4762        4870      875511   82  Linux swap / Solaris


This was an "as-advertised" default installation for me three months ago.  Now I wish my XP partition was smaller.  :D

---

### Post by akelsall on 2009-11-03
Here's a snapshot of my partitions. I had a new 500Gb drive and wanted to minimize the impact of one partition getting corrupted (and destroying all my data). So, I chose to put "major categories" (e.g. music, photos, work, etc), into different partitions to minimize the risk. Makes things easy to remember that way too (if I need to get to my work info, I just enter cd /work). 


[INDENT]> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda2 on /home type ext3 (rw,relatime)
/dev/sda6 on /windows type ext3 (rw,relatime)
/dev/sda8 on /dynamips type ext3 (rw,relatime)
/dev/sda5 on /email type ext3 (rw,relatime)
/dev/sda7 on /music type ext3 (rw,relatime)
/dev/sda12 on /networking type ext3 (rw,relatime)
/dev/sda10 on /personal type ext3 (rw,relatime)
/dev/sda9 on /work type ext3 (rw,relatime)
/dev/sdb1 on /BACKUP1 type ext3 (rw)
/dev/sdb5 on /BACKUP1 type ext3 (rw)
/dev/sdb6 on /BACKUP1 type ext3 (rw)
[/INDENT]

---

### Post by Ocxic on 2009-11-03
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c8f99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25         328     2441880   fd  Linux raid autodetect
/dev/sda3             329       60801   485749372+  fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001fd3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         304     2441848+  fd  Linux raid autodetect
/dev/sdb2             305       60801   485942152+  fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008161e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         304     2441848+  fd  Linux raid autodetect
/dev/sdc2             305       60801   485942152+  fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bd867

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         304     2441848+  fd  Linux raid autodetect
/dev/sdd2             305       60801   485942152+  fd  Linux raid autodetect

Disk /dev/md1: 1990.2 GB, 1990221299712 bytes
2 heads, 4 sectors/track, 485893872 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 10.0 GB, 10001383424 bytes
2 heads, 4 sectors/track, 2441744 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              9.4G  4.9G  4.5G  52% /
udev                  4.0G  300K  4.0G   1% /dev
none                  4.0G  316K  4.0G   1% /dev/shm
none                  4.0G  588K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
/dev/sda1             183M   48M  126M  28% /boot
/dev/md1              1.9T  1.3T  580G  69% /home

```

---

### Post by YeOK on 2009-11-03
```

fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003da16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          66      524288   83  Linux
/dev/sda2              67        1370    10474380   82  Linux swap / Solaris
/dev/sda3            1371       30401   233185953   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00074ca2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdd: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f5d1d8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3892    31262458+  83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095c7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001598d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001   83  Linux

```

```

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdd1              30G  3.9G   26G  14% /
tmpfs                 2.0G  2.0M  2.0G   1% /dev/shm
/dev/sdc1             459G  313G  123G  72% /archive
/dev/sda1             504M   75M  405M  16% /boot
/dev/sda3             219G  112G   97G  54% /downloads
/dev/sde1             459G   91G  345G  21% /home
/dev/sdb1             233G   25G  209G  11% /mnt/Win7

```

---

### Post by winotree on 2009-11-03
winotree@h1n1:~$ sudo fdisk -l
[sudo] password for winotree: 

Disk /dev/sda: 4001 MB, 4001292288 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d087d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         486     3903763+  83  Linux

Disk /dev/sdb: 8095 MB, 8095006720 bytes
255 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097c25

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         984     7903948+  83  Linux

I've got a small device and this is a simple, effective setup for me.  The 8GB SDHC doesn't do as much work as it used to -- maybe I'll change it to ext4 and put a second distribution on it.  BTW interesting thread!

---

