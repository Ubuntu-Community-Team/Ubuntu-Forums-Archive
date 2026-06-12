---
title: "Compare our mount points and disk usage..."
date: 2007-10-13
forum: The Cafe
---

### Post by milosz.galazka on 2007-10-13
I am just curious, it will allow to compare and choose better solution next time :)

So my *df -h* output looks like
```
/dev/sda3             9,4G  5,0G  4,4G  54% /
varrun                502M  252K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   92K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   35M  468M   7% /lib/modules/2.6.22-14-386/volatile
/dev/sda2             228M  166M   50M  77% /boot
/dev/sda6             228M   14K  216M   1% /boot/mydata
/dev/sda5              84G   35G   50G  41% /home
/dev/loop0            2,4G  2,4G     0 100% /mnt
```

Swap is 256MB

*/boot/mydata* is for strange experiments :)

---

### Post by Kingsley on 2007-10-13
So... What's your question?

---

### Post by milosz.galazka on 2007-10-13
Sorry, It's 1:40 AM here..

 What is your output of *df -h* command?

---

### Post by -grubby on 2007-10-13
here:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              73G   15G   54G  22% /
varrun                236M  144K  236M   1% /var/run
varlock               236M     0  236M   0% /var/lock
udev                  236M   52K  236M   1% /dev
devshm                236M     0  236M   0% /dev/shm
lrm                   236M   34M  202M  15% /lib/modules/2.6.22-14-generic/volatile

```

---

### Post by RAV TUX on 2007-10-13
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46266&d=1192322127[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=46262&d=1192320329[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=0")

---

### Post by FuturePilot on 2007-10-13
Mine
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              42G  3.7G   37G  10% /
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  128K 1014M   1% /proc/bus/usb
udev                 1014M  128K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   15M  999M   2% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              95G   28G   67G  29% /media/sda1
/dev/sda2             8.4G  6.6G  1.9G  79% /media/sda2

```

---

### Post by blithen on 2007-10-13
Mine

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             124G   35G   84G  30% /
varrun                760M  156K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M  120K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   34M  726M   5% /lib/modules/2.6.22-14-generic/volatile
/dev/hdb1              75G   30G   45G  41% /media/disk

```

---

### Post by Kingsley on 2007-10-13
Mine

```
king@dv6000t:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              17G   11G  5.0G  69% /
varrun               1013M  340K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb           1013M  120K 1013M   1% /proc/bus/usb
udev                 1013M  120K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   33M  980M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/sda2              70G   55G   16G  79% /media/shared
/dev/sda1              26G   16G  9.8G  62% /media/vista

```
/media/shared houses my music and movies.
/media/vista is Windows Vista.

---

### Post by LowSky on 2007-10-13
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              14G  4.1G  9.1G  31% /
varrun               1014M  212K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   88K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hda3              37G  987M   34G   3% /home
/dev/hda1             131G   48G   84G  37% /media/hda1
/dev/sda1              70G   49G   21G  71% /media/sda1

```

---

### Post by Sayers on 2007-10-13
My hard drive is so big compared to y'alls :P 

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             291G   13G  264G   5% /
varrun                474M  104K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
procbususb            474M  116K  474M   1% /proc/bus/usb
udev                  474M  116K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   33M  441M   7% /lib/modules/2.6.20-16-generic/volatile

```

---

### Post by mjwood0 on 2007-10-13
Just got my RAID1 array setup for /home :)

300 GB of mirrored storage...

I really don't have all my drives partitioned fully.  I've got a 120 GB and 80 GB on top of the raid array.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  3.0G   11G  23% /
varrun                943M  104K  943M   1% /var/run
varlock               943M     0  943M   0% /var/lock
procbususb            943M  148K  943M   1% /proc/bus/usb
udev                  943M  148K  943M   1% /dev
devshm                943M     0  943M   0% /dev/shm
lrm                   943M   13M  930M   2% /lib/modules/2.6.20-16-generic/volatile
/dev/md0              292G   12G  266G   5% /home
/dev/hda1              30G  4.4G   25G  15% /media/hda1
/dev/sda5              37G   11G   25G  29% /shared
/dev/sdd1             984M   32M  953M   4% /media/KINGSTON

```

---

### Post by dfreer on 2007-10-13
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1               34G  1.9G   32G   6% /
tmpfs                 503M     0  503M   0% /lib/init/rw
udev                   10M  132K  9.9M   2% /dev
tmpfs                 503M     0  503M   0% /dev/shm
/dev/md0              942M   40M  855M   5% /boot
/dev/md2              559G  556G  3.5G 100% /data
/dev/hdb1             233G   38G  196G  17% /data2
/dev/sdd1             153G   33M  153G   1% /data3
```

My /dev/mdX drives consist of three 320 GB' hard drives, RAID 5 on /dev/md2.

---

### Post by -grubby on 2007-10-13
> **dfreer said:**
> ```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1               34G  1.9G   32G   6% /
tmpfs                 503M     0  503M   0% /lib/init/rw
udev                   10M  132K  9.9M   2% /dev
tmpfs                 503M     0  503M   0% /dev/shm
/dev/md0              942M   40M  855M   5% /boot
/dev/md2              559G  556G  3.5G 100% /data
/dev/hdb1             233G   38G  196G  17% /data2
/dev/sdd1             153G   33M  153G   1% /data3
```

My /dev/mdX drives consist of three 320 GB' hard drives, RAID 5 on /dev/md2.

almost a terabyte of storage!!!!!!!!!!:shock: holy $%09

---

### Post by RAV TUX on 2007-10-13
> **Sayers said:**
> My hard drive is so big compared to y'alls :P 

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             291G   13G  264G   5% /
varrun                474M  104K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
procbususb            474M  116K  474M   1% /proc/bus/usb
udev                  474M  116K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   33M  441M   7% /lib/modules/2.6.20-16-generic/volatile

```Only slightly bigger then mine, I only posted one of two of my hard drives also. ;)

---

### Post by DjBones on 2007-10-14
well, this is just my ubuntu partition..
my drive is actually 150 gigs lol

---

### Post by derekr44 on 2007-10-14
Mine

---

### Post by andrewpmk on 2007-10-14
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             16437332   3614920  11987436  24% /
varrun                 1037812       100   1037712   1% /var/run
varlock                1037812         0   1037812   0% /var/lock
udev                   1037812       108   1037704   1% /dev
devshm                 1037812        16   1037796   1% /dev/shm
lrm                    1037812     34696   1003116   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             61440556  35795236  25645320  59% /media/sda1
/dev/sda6             15116836   3175692  11173240  23% /media/sda6
/dev/sda7             60768956  43683496  13998572  76% /media/sda7

/ is the testing partition, in which Gutsy (which I am using now) is currently installed. It was carved out of the Windows partition.
/media/sda1 is the Windows XP partition.
/media/sda6 is the / partition for my main Ubuntu (Feisty) installation.
/media/sda7 is /home under Feisty.
Swap is 1GB.

---

### Post by corney91 on 2007-10-14
```
dan@dan-laptop:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.6G  4.0G  3.2G  56% /
varrun                490M  104K  490M   1% /var/run
varlock               490M     0  490M   0% /var/lock
udev                  490M   80K  490M   1% /dev
devshm                490M     0  490M   0% /dev/shm
lrm                   490M   34M  456M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda2              29G   20G  8.2G  71% /home
/dev/sdb1              75G   46G   29G  62% /media/FREECOM HDD
```

---

### Post by bonzodog on 2007-10-14
```

~-> df -h                                                               [13:18]
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              21G  5.0G   16G  25% /
/dev/sda6             133G   11G  123G   8% /home

```

Yeah, this is a zenwalk system, based around slackware 12.

Unlike ubuntu, it doesn't need to mount extra areas of the drive.

---

### Post by Dalmaris on 2007-10-14
:~> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  2.1G  6.7G  24% /
udev                  375M  140K  375M   1% /dev
/dev/sda3             357G  318M  356G   1% /home
/dev/sdc1             298G  236G   63G  79% /home/mike/video
/dev/sdb1             298G  258G   41G  87% /home/mike/music
/dev/sdf1             298G  272G   27G  92% /home/mike/stuff
/dev/mapper/TOP320_VG-storagelv
                      148G  128G   14G  91% /home/mike/storage
/dev/mapper/general_vg-general_lv
                      298G  216G   83G  73% /home/mike/mirror
/dev/mapper/cryptvg   149G  130G   19G  88% /home/mike/crypt

:)

---

### Post by hessiess on 2007-10-14
```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda6              16G  3.2G   12G  22% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  108K  506M   1% /proc/bus/usb
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda2             105G   19G   82G  19% /home
/dev/hda              7.9G  7.9G     0 100% /media/cdrom0
a@a-desktop:~$
```

---

### Post by dfreer on 2007-10-15
> **Dalmaris said:**
> :~> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  2.1G  6.7G  24% /
udev                  375M  140K  375M   1% /dev
/dev/sda3             357G  318M  356G   1% /home
/dev/sdc1             298G  236G   63G  79% /home/mike/video
/dev/sdb1             298G  258G   41G  87% /home/mike/music
/dev/sdf1             298G  272G   27G  92% /home/mike/stuff
/dev/mapper/TOP320_VG-storagelv
                      148G  128G   14G  91% /home/mike/storage
/dev/mapper/general_vg-general_lv
                      298G  216G   83G  73% /home/mike/mirror
/dev/mapper/cryptvg   149G  130G   19G  88% /home/mike/crypt

:)

Nice! If I calculated right, just shy of 2 Terabytes

@nathangrub
Within the next year I'll add another RAID 5 of three 320 GB drives, since my first one is already full. That will be 1.2 terabytes of backed up data.

---

### Post by ticopelp on 2007-10-15
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              72G  2.9G   66G   5% /
varrun                252M  116K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  108K  252M   1% /proc/bus/usb
udev                  252M  108K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm   
```

Just reinstalled Feisty on my laptop. :D

---

### Post by tarpon_bill on 2007-10-19
I use what you have, but I always break out /home as a separate large directory to prevent user files from mixing with and fragging the system files partition. Just a old school type of thing I guess -- Although I see some others do the same.

I am rebuilding my system, switching to Gibbon, so can't do the Df thing right now. I allocate about 200 GB to /home out of a 250 GB disk. I want a fresh install is the only reason I am rebuilding -- Get rid of any cruft..

---

### Post by x0as on 2007-10-19
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             9.2G  2.9G  6.0G  33% /
tmpfs                 221M     0  221M   0% /lib/init/rw
udev                   10M   72K   10M   1% /dev
tmpfs                 221M     0  221M   0% /dev/shm
/dev/hda6              63G   21G   39G  36% /home
```

---

### Post by bobbocanfly on 2007-10-19
bobbo@penguin:~$ df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              31G  3.2G   26G  12% /
varrun                252M  240K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   80K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             190M   23M  158M  13% /boot
/dev/sda4              43G  2.6G   38G   7% /home
/dev/sdb2              20G  173M   19G   1% /media/Backup
/dev/scd0             6.2G  6.2G     0 100% /media/cdrom1
/dev/scd1             696M  696M     0 100% /media/cdrom0
/dev/sdb1             127G   48G   73G  40% /media/Davids

```

My shiny new partition setup

---

### Post by Ptero-4 on 2008-10-20
```

Filesystem      Size     Used      Avail   Use% Mounted on
/dev/wd0a1       6.2G    210M      6.0G    1%   /
/dev/wd0a2     739.5G      5G    734.5G    6%   /mnt/linux
varrun           252M    240K      252M    1%   /var/run
varlock          252M     0        252M    0%   /var/lock
devshm           252M     0        252M    0%   /dev/shm
/dev/cd0         4.3G    4.3G      0     100%   /mnt/dvdrw
/dev/nfs0         40G      8G       32G   19%   /mnt/fileserver
/dev/nfs1       1024G     15G     1009G   12%   /mnt/netdisk1
/dev/nfs2       1024G     0       1024G    0%   /mnt/netdisk2
/dev/nfs3       1024G     0       1024G    0%   /mnt/netdisk3

```
My current setup.
Last four are the internal in my crappy fileserver (an old MacPPC G3 I salvaged) and the 3 1TB external HD's attached to it.

---

### Post by myusername on 2008-10-20
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             100G  7.5G   92G   8% /
none                  315M     0  315M   0% /dev/shm
/dev/sda1             100G  4.8G   95G   5% /media/sda1
/dev/sda5             100G  9.8G   90G  10% /media/sda5

sda1 = Windows
sda5 = Storage (Music Videos Pictures etc)
sda6 = Arch Linux

---

