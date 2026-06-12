---
title: "Very slow raid1 with nvme disks"
date: 2023-10-01
forum: Server Platforms
---

### Post by miks.mikelsons on 2023-10-01
I'm experiencing very slow writes with raid1 ext4 (2x Samsung SSD 980 1TB).
The average write speed is something around 80MB/s. 
I detached one NVMe from raid1, reformated it as a single ext4 partition, and mounted it on /mnt. Made tests and write speed is around 1100MB/s.
Any tough on possible reasons for it? 


Other system parameters:
CPU - AMD Ryzen 9 7900X 12-Core Processor
RAM - 64GB


Tested with both simple ```
dd if=/dev/zero of=tempfile bs=1M count=5024 conv=fdatasync
``` and ```
fio --name=randwrite --ioengine=libaio --iodepth=64 --rw=randwrite     --bs=64k --direct=1 --size=2G --numjobs=8 --runtime=240     --group_reporting
```.
Results are more or less the same.

---

### Post by MAFoElffen on 2023-10-03
Without more information, such as if you ran the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info"), I would be guessing. Please run the script ad post the URL of where the report uploads to a pastebin.

For doing i/o bechmarks, I use fio with a 10GB file. I change the directory (navigate to) to where it is on the disk, or in the case of RAID, in the filesystem container of where I want to test, then for testing writes, run
```

sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
I test writes and reads separately...

For the above, I get 
```

mafoelffen@msi-ubuntu:~/Scripts$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
[sudo] password for mafoelffen: 
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][-.-%][w=683MiB/s][w=683 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=107431: Tue Oct  3 11:20:24 2023
  write: IOPS=3154, BW=3155MiB/s (3308MB/s)(10.0GiB/3246msec); 0 zone resets
    slat (usec): min=93, max=1846, avg=199.59, stdev=103.30
    clat (nsec): min=1126, max=1199.1M, avg=9787987.27, stdev=65507240.76
     lat (usec): min=135, max=1199.4k, avg=9987.66, stdev=65511.63
    clat percentiles (msec):
     |  1.00th=[    4],  5.00th=[    4], 10.00th=[    4], 20.00th=[    5],
     | 30.00th=[    5], 40.00th=[    6], 50.00th=[    6], 60.00th=[    7],
     | 70.00th=[    7], 80.00th=[    8], 90.00th=[   10], 95.00th=[   12],
     | 99.00th=[   15], 99.50th=[   18], 99.90th=[ 1200], 99.95th=[ 1200],
     | 99.99th=[ 1200]
   bw (  MiB/s): min=  188, max= 5234, per=100.00%, avg=3987.60, stdev=2167.44, samples=5
   iops        : min=  188, max= 5234, avg=3987.60, stdev=2167.44, samples=5
  lat (usec)   : 2=0.04%, 100=0.01%, 250=0.04%, 500=0.07%, 750=0.08%
  lat (usec)   : 1000=0.08%
  lat (msec)   : 2=0.27%, 4=14.24%, 10=76.47%, 20=8.40%, 2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=591, max=591, avg=591.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  588],  5.00th=[  588], 10.00th=[  588], 20.00th=[  588],
     | 30.00th=[  588], 40.00th=[  588], 50.00th=[  588], 60.00th=[  588],
     | 70.00th=[  588], 80.00th=[  588], 90.00th=[  588], 95.00th=[  588],
     | 99.00th=[  588], 99.50th=[  588], 99.90th=[  588], 99.95th=[  588],
     | 99.99th=[  588]
  cpu          : usr=11.80%, sys=47.30%, ctx=3807, majf=14, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3155MiB/s (3308MB/s), 3155MiB/s-3155MiB/s (3308MB/s-3308MB/s), io=10.0GiB (10.7GB), run=3246-3246msec

```
So that tests out at 3308MB/s on an NVMe M.2 Samsung SSD 990 PRO on a PCIe Gen 5.0 bus...

---

### Post by miks.mikelsons on 2023-10-03
System info: [https://paste.ubuntu.com/p/9vb6hrKw4F/](https://paste.ubuntu.com/p/9vb6hrKw4F/)

Test on raid1 (currently in degraded state, with single NVME disk)
```
#fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][24.1%][w=106MiB/s][w=106 IOPS][eta 00m:22s]
Jobs: 1 (f=1): [W(1)][28.3%][w=76.1MiB/s][w=76 IOPS][eta 00m:33s]
Jobs: 1 (f=1): [W(1)][31.7%][w=82.1MiB/s][w=82 IOPS][eta 00m:41s]
Jobs: 1 (f=1): [W(1)][41.7%][w=66.1MiB/s][w=66 IOPS][eta 00m:35s]
Jobs: 1 (f=1): [W(1)][51.7%][w=81.0MiB/s][w=81 IOPS][eta 00m:29s]
Jobs: 1 (f=1): [W(1)][61.7%][w=53.0MiB/s][w=53 IOPS][eta 00m:23s]
Jobs: 1 (f=1): [W(1)][71.7%][w=90.0MiB/s][w=90 IOPS][eta 00m:17s]
Jobs: 1 (f=1): [W(1)][81.7%][w=18.0MiB/s][w=18 IOPS][eta 00m:11s]
Jobs: 1 (f=1): [W(1)][91.7%][w=69.0MiB/s][w=69 IOPS][eta 00m:05s]
Jobs: 1 (f=1): [W(1)][100.0%][w=72.0MiB/s][w=72 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=641479: Tue Oct  3 21:50:00 2023
  write: IOPS=103, BW=103MiB/s (108MB/s)(6213MiB/60258msec); 0 zone resets
    slat (usec): min=28, max=813957, avg=2115.67, stdev=24465.86
    clat (usec): min=1726, max=1537.9k, avg=306914.42, stdev=250961.86
     lat (usec): min=1793, max=1538.0k, avg=309030.23, stdev=251517.18
    clat percentiles (msec):
     |  1.00th=[   22],  5.00th=[   31], 10.00th=[   32], 20.00th=[   35],
     | 30.00th=[   40], 40.00th=[  239], 50.00th=[  334], 60.00th=[  372],
     | 70.00th=[  422], 80.00th=[  502], 90.00th=[  609], 95.00th=[  709],
     | 99.00th=[ 1062], 99.50th=[ 1234], 99.90th=[ 1502], 99.95th=[ 1519],
     | 99.99th=[ 1536]
   bw (  KiB/s): min= 6144, max=972800, per=100.00%, avg=106392.74, stdev=165647.17, samples=119
   iops        : min=    6, max=  950, avg=103.90, stdev=161.76, samples=119
  lat (msec)   : 2=0.06%, 4=0.08%, 10=0.23%, 20=0.50%, 50=32.35%
  lat (msec)   : 100=0.69%, 250=6.84%, 500=39.24%, 750=16.14%, 1000=2.58%
  lat (msec)   : 2000=1.29%
  cpu          : usr=0.29%, sys=0.50%, ctx=5099, majf=2, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=0.3%, 8=0.5%, 16=1.0%, 32=98.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,6213,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=103MiB/s (108MB/s), 103MiB/s-103MiB/s (108MB/s-108MB/s), io=6213MiB (6515MB), run=60258-60258msec


Disk stats (read/write):
    md0: ios=51/22068, merge=0/0, ticks=2692/6016916, in_queue=6019608, util=97.69%, aggrios=46/19841, aggrmerge=5/2277, aggrticks=2690/5461387, aggrin_queue=5472758, aggrutil=98.22%
  nvme0n1: ios=46/19841, merge=5/2277, ticks=2690/5461387, in_queue=5472758, util=98.22%
```

The same test on second NVME (removed from raid1 to test hypothesis that speed problems happen only when raid1 is involved):

```

# fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][100.0%][w=1588MiB/s][w=1587 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=673080: Tue Oct  3 22:01:49 2023
  write: IOPS=1564, BW=1565MiB/s (1641MB/s)(10.0GiB/6545msec); 0 zone resets
    slat (usec): min=27, max=9162, avg=54.61, stdev=91.37
    clat (usec): min=1519, max=52601, avg=20370.86, stdev=3319.78
     lat (usec): min=1640, max=52653, avg=20425.56, stdev=3318.28
    clat percentiles (usec):
     |  1.00th=[10814],  5.00th=[18482], 10.00th=[19006], 20.00th=[19006],
     | 30.00th=[19006], 40.00th=[19006], 50.00th=[19792], 60.00th=[20055],
     | 70.00th=[21103], 80.00th=[21890], 90.00th=[22676], 95.00th=[24249],
     | 99.00th=[35390], 99.50th=[38011], 99.90th=[40109], 99.95th=[46400],
     | 99.99th=[52691]
   bw (  MiB/s): min= 1348, max= 1598, per=100.00%, avg=1565.54, stdev=65.83, samples=13
   iops        : min= 1348, max= 1598, avg=1565.54, stdev=65.83, samples=13
  lat (msec)   : 2=0.15%, 4=0.20%, 10=0.58%, 20=57.69%, 50=41.37%
  lat (msec)   : 100=0.03%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=260, max=260, avg=260.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  262],  5.00th=[  262], 10.00th=[  262], 20.00th=[  262],
     | 30.00th=[  262], 40.00th=[  262], 50.00th=[  262], 60.00th=[  262],
     | 70.00th=[  262], 80.00th=[  262], 90.00th=[  262], 95.00th=[  262],
     | 99.00th=[  262], 99.50th=[  262], 99.90th=[  262], 99.95th=[  262],
     | 99.99th=[  262]
  cpu          : usr=2.95%, sys=5.91%, ctx=9844, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=1565MiB/s (1641MB/s), 1565MiB/s-1565MiB/s (1641MB/s-1641MB/s), io=10.0GiB (10.7GB), run=6545-6545msec


Disk stats (read/write):
  nvme1n1: ios=0/29944, merge=0/101, ticks=0/602133, in_queue=602144, util=98.38%

```

---

### Post by MAFoElffen on 2023-10-03
I different comparison with RAID... This is from my server. RAIDz2 array with 5 x Samsung 870 EVO SATA SSD's, with L2ARC and SLOG caches on NVMe.
```

mafoelffen@Mikes-B460M:/data$ sudo zpool status -v datapool
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:16:50 with 0 errors on Tue Oct  3 12:07:31 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

mafoelffen@Mikes-B460M:/data$ sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=3117797: Tue Oct  3 12:08:06 2023
  write: IOPS=1065, BW=1065MiB/s (1117MB/s)(10.0GiB/9614msec); 0 zone resets
    slat (usec): min=114, max=2695, avg=484.99, stdev=513.75
    clat (nsec): min=1223, max=4664.4M, avg=28952029.95, stdev=255061274.21
     lat (usec): min=160, max=4665.6k, avg=29437.28, stdev=255133.83
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    6], 10.00th=[    6], 20.00th=[    6],
     | 30.00th=[    6], 40.00th=[    7], 50.00th=[    8], 60.00th=[   10],
     | 70.00th=[   12], 80.00th=[   32], 90.00th=[   35], 95.00th=[   52],
     | 99.00th=[   75], 99.50th=[   80], 99.90th=[ 4665], 99.95th=[ 4665],
     | 99.99th=[ 4665]
   bw (  MiB/s): min=  438, max= 5250, per=100.00%, avg=1993.80, stdev=1639.10, samples=10
   iops        : min=  438, max= 5250, avg=1993.80, stdev=1639.10, samples=10
  lat (usec)   : 2=0.03%, 4=0.01%, 50=0.01%, 250=0.02%, 500=0.04%
  lat (usec)   : 750=0.04%, 1000=0.04%
  lat (msec)   : 2=0.16%, 4=0.31%, 10=61.97%, 20=13.59%, 50=18.24%
  lat (msec)   : 100=5.23%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=460, max=460, avg=460.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  462],  5.00th=[  462], 10.00th=[  462], 20.00th=[  462],
     | 30.00th=[  462], 40.00th=[  462], 50.00th=[  462], 60.00th=[  462],
     | 70.00th=[  462], 80.00th=[  462], 90.00th=[  462], 95.00th=[  462],
     | 99.00th=[  462], 99.50th=[  462], 99.90th=[  462], 99.95th=[  462],
     | 99.99th=[  462]
  cpu          : usr=3.88%, sys=27.72%, ctx=25753, majf=14, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1065MiB/s (1117MB/s), 1065MiB/s-1065MiB/s (1117MB/s-1117MB/s), io=10.0GiB (10.7GB), run=9614-9614msec

```
1117MB/s on that RAID array on PCIe Gen 3. SATA SSD's.

So it really depends on the generation of PCIe bus in the motherboard.

---

### Post by MAFoElffen on 2023-10-03
If you run the script with a '--details" start option it will display your RAID details in that report...

Please post the output of this within CODE Tags:
```

sudo dmidecode -t 0,1

```
I think that info is also turned on in the report when you use that startup option, but I can't remember.

---

### Post by miks.mikelsons on 2023-10-03
```
# dmidecode -t 0,1
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.5.0 present.


Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1222
    Release Date: 02/24/2023
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 32 MB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 12.22


Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: ASUS
    Product Name: System Product Name
    Version: System Version
    Serial Number: System Serial Number
    UUID: 901ed735-a55b-efc2-c434-c87f5401f422
    Wake-up Type: Power Switch
    SKU Number: SKU
    Family: To be filled by O.E.M.


Invalid entry length (0). DMI table is broken! Stop.




```and raid info:


```
----------  mdadm RAID Information:
mdadm RAID device present.


md0 : active raid1 nvme0n1p2[0]


/dev/md0:
           Version : 1.2
     Creation Time : Thu Sep 21 18:36:20 2023
        Raid Level : raid1
        Array Size : 976626688 (931.38 GiB 1000.07 GB)
     Used Dev Size : 976626688 (931.38 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 1
       Persistence : Superblock is persistent


       Update Time : Tue Oct  3 23:59:26 2023
             State : active, degraded
    Active Devices : 1
   Working Devices : 1
    Failed Devices : 0
     Spare Devices : 0


Consistency Policy : resync


              Name : ubuntu-server:0
              UUID : b1aeecfc:2487ddf6:3dd3daf6:d3f80be2
            Events : 1071343


    Number   Major   Minor   RaidDevice State
       0     259        2        0      active sync   /dev/nvme0n1p2
       -       0        0        1      removed



```

---

### Post by darkod on 2023-10-03
I have mdadm raid1 with NVME disks, but I can't run these same tests until tomorrow and report results. But receiving only 108MB/s write on NVME is extremely poor. Actually any half decent SATA disk could do that speed for sequential writes.

Did you try unplugging and replugging the NVMEs? Just in case.

Are you running it directly on the motherboard or on PCIe adapter? Can that adapter be at fault?

---

### Post by miks.mikelsons on 2023-10-03
"Did you try unplugging and replugging the NVMEs? Just in case."
- No, but I will try in the following days.

"Are you running it directly on the motherboard or on PCIe adapter? Can that adapter be at fault?"
Both of NVMEs are connected directly to motherboard m2 sockets.

---

### Post by MAFoElffen on 2023-10-03
> **miks.mikelsons said:**
> ```
# dmidecode -t 0,1
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.5.0 present.

BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1222
    Release Date: 02/24/2023
    BIOS Revision: 12.22
...
Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: ASUS
    Product Name: System Product Name
    Version: System Version
    Serial Number: System Serial Number
    UUID: 901ed735-a55b-efc2-c434-c87f5401f42
...
[COLOR=#ff0000]***Invalid entry length (0). DMI table is broken! Stop.***
[/COLOR]
```

I would worry about this result. 

Please rerun
```

sudo dmidecode -t 1

```
If it says the same error message, reflash your BIOS and test again. 

That error message usually means that part of your BIOS image is corrupt and unreadable.

---

### Post by miks.mikelsons on 2023-10-04
ok, I will try that

---

### Post by darkod on 2023-10-04
My mdadm raid1 array has two NVME disks and one SATA SSD disk, so it is not a fair comparison to yours because the SATA SSD will be limiting the writes speed. But here is what the fio results are:

```
Run status group 0 (all jobs):
  WRITE: bw=249MiB/s (261MB/s), 249MiB/s-249MiB/s (261MB/s-261MB/s), io=10.0GiB (10.7GB), run=41160-41160msec

Disk stats (read/write):
    md0: ios=0/42084, merge=0/0, ticks=0/971012, in_queue=971012, util=97.35%, aggrios=2/40834, aggrmerge=0/1395, aggrticks=31/337837, aggrin_queue=338628, aggrutil=99.72%
  nvme0n1: ios=0/41475, merge=0/650, ticks=0/245247, in_queue=245264, util=56.34%
  sdf: ios=7/39554, merge=0/2886, ticks=94/519627, in_queue=521969, util=99.72%
  nvme1n1: ios=0/41475, merge=0/650, ticks=0/248638, in_queue=248653, util=56.22%
```

On the other hand, the command executed against a standalone NVME disk that is not in the array, the result is:

```
Run status group 0 (all jobs):
  WRITE: bw=560MiB/s (587MB/s), 560MiB/s-560MiB/s (587MB/s-587MB/s), io=10.0GiB (10.7GB), run=18294-18294msec

Disk stats (read/write):
    dm-2: ios=0/10240, merge=0/0, ticks=0/573772, in_queue=573772, util=99.45%, aggrios=0/40990, aggrmerge=0/48, aggrticks=0/2200108, aggrin_queue=2200127, aggrutil=99.02%
  nvme0n1: ios=0/40990, merge=0/48, ticks=0/2200108, in_queue=2200127, util=99.02%
```

I have to say that my NVMEs are not high profile. They are "only" Kingston NV2 2TB disks. One is in the motherboard slot, the other in PCIe adapter.

---

### Post by MAFoElffen on 2023-10-04
On my server, PCIe Gen 3. 4 x Samsung 970 PCIe NVMe M.2's in RAIDz2 test out at 2358MiB/s. They are all on a PCIe adapter card. Where as a WD Blue NVme M.2 directly on the MB in that same machine test out as 2475MB/s.

So as said, a lot depends on where it is installed and the Generation of the PCIe bus. For example:
> **MAFoElffen said:**
> You are at least PCIe generation 3.0 right?
```

PCI Express: Unidirectional Bandwidth in x1 and x16 Configurations

Generation     Year of Release     Data Transfer Rate     Bandwidth x1     Bandwidth x16
PCIe 1.0       2003                2.5 GT/s               250 MB/s         4.0 GB/s
PCIe 2.0       2007                5.0 GT/s               500 MB/s         8.0 GB/s
PCIe 3.0       2010                8.0 GT/s               1 GB/s           16 GB/s
PCIe 4.0       2017                16 GT/s                2 GB/s           32 GB/s
PCIe 5.0       2019                32 GT/s                4 GB/s           64 GB/s
PCIe 6.0       2021                64 GT/s                8 GB/s           128 GB/s

```
And That's why I need to ask which ASUS Motherboard you have. ASUS, if it has bifurcation onboard, it allocates / does that strangely, depending on what you have plugged in where. For example, if you have so many SATA drives plugged in, it shuts off an M.2 port, or alters the Generation (speed) of the lanes for some lanes, etc.

I'm hoping that when bifurcation has been around for a while, that they sort those kinds of things out.

---

### Post by darkod on 2023-10-04
Well, mine is a Supermicro X11SCL with PCIe gen3. But according to that my NVME speeds are also very poor. I don't have much time for deeper investigation but obviously I will have to find some time and take a look. Doesn't really matter too much for basic home use. But just for interest and to poke things around. :)

---

### Post by MAFoElffen on 2023-10-05
@darkod --

Look at his 'system-info' report... Lines 45-76:
```

computer
    Description: Desktop Computer
    Product: System Product Name (SKU)
    Vendor: ASUS
    Version: System Version
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-3.5.0 dmi-3.5.0 smp vsyscall32
    Configuration:
        boot=normal
        chassis=desktop
        family=To be filled by O.E.M.
        sku=SKU
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/'
Bios Vendor:
Bios Version:
Bios Release:
Board Vendor:
Board Name:
Board Version:
Board Serial:
Board Asset Tag:

Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
   --- SecureBoot Status from 'mokutil':
EFI variables are not supported on this system

```
He is booting as CSM/Legacy so EFIVARS are not populated, but SMIBIOS should still populate /sys/class/dmi/id/* with the BIOS information. That indicated there was a problem with his BIOS. That is why I asked him to dig deeper by running dmidecode to directly try to access the BIOS registers. If he is running an AMD Ryzen 9 7900X 12-Core Processor in an AMD5 slot, the BIOS for that is SMIBIOS complaint. It says it is: smbios-3.5.0 dmi-3.5.0 smp vsyscall32... But the output there for the registers there are blank. 'dmidecode' verified that there is a BIOS corruption problem.

I would think that he has a bigger problem to deal with as a priority first. Right? Those BIOS registers are the foundation for anything attached. Getting that dealt with may very well fix all his other problems. 

I asked for his motherboard info, because that info is not returning in the output of his BIOS. The reason that "that" is important, is that ASUS had a problem with their BIOS for some boards... Especially for frying Ryzen 7000 series CPU's and their motherboards: [https://www.xda-developers.com/asus-ryzen-7000-motherboard-malfunction-warranty/](https://www.xda-developers.com/asus-ryzen-7000-motherboard-malfunction-warranty/)

On one of their BIOS Updates to correct problems: They went as far as saying that one of their own BIOS updates (BIOS update 1410), voids their own warranty on their motherboards. (???) 

That is just the facts. Let's wait and see what the OP responds with and how this goes. He is at risk of bigger problems than just slow reads/writes of his RAID1 Array. (And he has to be careful on how he corrects that.)

---

### Post by darkod on 2023-10-05
You are right, completely. Any possible BIOS corruption needs to be addressed.

I was just thinking out loud that if my board is PCIe gen3 then speed of a standalone Kingston NV2 2TB disk should be better than the 560MiB/s in my test (using your fio command).

---

### Post by MAFoElffen on 2023-10-05
@darkod --

I'm thinking he is lucky he is just running Linux kernel, and probably a 'balanced' power profile... That if he checks his CPU temps during that, he is likely going to see that his CPU is overheating, and it is toggled to "survival mode", throttling down the IOPS, which in turn slowed down his reads/writes. If he hadn't noticed that, I fear he might have fried his CPU/Motherboard. I'm so glad that he did notice that, and had the sense to notice something was wrong and posted about it (in a timely manner).

If he had been running the Windows OS kernel, well... I would not be running that computer much, except to try to correct that first. I feel it is in that much risk.

I'm surprised he wasn't having system freezes. Or maybe he was, so thought is was from slow reads/writes...

If if had continued and it ran through it's course, that would have been a completely different conversation. (And probably not with us.)

---

### Post by miks.mikelsons on 2023-10-08
As this box is at a remote location I hadn't yet the possibility to upgrade bios.
But I have to report that currently looks like RAID had nothing to do with extre slow write speed.


As I noticed same perfomance drop to second nvme detached from RAID1, I started to looked other possible cuplrits.
Strange pattern was that speed somehow got fixed at the start of the week and eventually degraded over the following days.
I changed fstrim from weekly to daily and write speed issue is gone. It's now around 2500MB/s with both NVME added to raid1.

So, if you have write intensive workload, execute "fstrim -v -a" and run speed tests after that.

---

### Post by MAFoElffen on 2023-10-08
Very good point. 'fstrim-all' first checks the filesystems, then calls fstrim for all devices that support it. 

On BTRFS filesystems, after kernel 6.2, then BTRFS enables discard=async by default on modern SSDs that support fstrim. So they do not need to use fstrim.

On all my computers, they are all ZFS-On-Root, so they use cron jobs for zpool trim, which initiates an immediate on-demand TRIM operation for all of the free space in the pools. This operation informs the underlying storage devices of all blocks in the pool which are no longer allocated and allows thinly provisioned devices to reclaim the space.

---

