---
title: "Extremely slow harddrive read/write"
date: 2009-10-21
forum: Server Platforms
---

### Post by knutz on 2009-10-21
Hey everybody!

I have a huge problem with my server!
I have installed Ubuntu Minimal 8.04.3 LTS on my small server.

My hardware specs are:

Mainboard: INTEL D945GCLF ATOM230 MINI-ITX
Harddrives: 
 - DELOCK INTERNAL SATA CF CARDREADER with Kingston ELITE PRO 133x 8GB CF car. (/dev/sdb)
 - 1.5 TB WESTERN DIGITAL CAVIAR GREEN 32MB SATA2 (/dev/sda)
RAM: 2gb Kingston VALUE RAM

I have installed ubuntu on the CF card and my problem is the western digital harddrive, which was a surprise to me. 
I run hellanzb as a daemon and after a few minutes a little writing and reading, my harddrive becomes inaccessible. I can see in htop/top, that the programs trying to access the harddrive is in status "D" (drive sleep), and i have tried running running 'hdparm -Tt' for both drives when it "freezes".

The hdparm result for both drives: 
(/dev/sda is the Western Digital drive)
(/dev/sdb is the CF card mounted as /)

```

/dev/sda:
 Timing cached reads:     2 MB in  3.41 seconds = **599.72 kB/sec**
 Timing buffered disk reads:    6 MB in  3.34 seconds =   **1.80 MB/sec**

/dev/sdb:
 Timing cached reads:   996 MB in  2.00 seconds = 498.04 MB/sec
 Timing buffered disk reads:  118 MB in  3.03 seconds =  38.93 MB/sec

```

I have also tried running the command hdparm -I for each drive and the ouput is:

```

**/dev/sda (the slow drive)**
ATA device, with non-removable media
        Model Number:       WDC WD15EADS-00P8B0
        Serial Number:      WD-WMAVU0121769
        Firmware Revision:  01.00A01
        Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
        Supported: 8 7 6 5
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors: 2930277168
        device size with M = 1024*1024:     1430799 MBytes
        device size with M = 1000*1000:     1500301 MBytes (1500 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
                Power-Up In Standby feature set
           *    SET_FEATURES required to spinup after power up
                SET_MAX security extension
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    64-bit World wide name
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
           *    unknown 76[12]
                DMA Setup Auto-Activate optimization
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[12] (vendor specific)
                unknown 206[13] (vendor specific)
Checksum: correct



**/dev/sdb (the CF card mounted as /)**

ATA device, with non-removable media
        Model Number:       ELITE PRO CF CARD 8GB
        Serial Number:      20081205    000066B3
        Firmware Revision:  20090216
Standards:
        Likely used: 6
Configuration:
        Logical         max     current
        cylinders       15538   15538
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   15662304
        LBA    user addressable sectors:   15662304
        device size with M = 1024*1024:        7647 MBytes
        device size with M = 1000*1000:        8019 MBytes (8 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 4
        Standby timer values: spec'd by Vendor
        R/W multiple sector transfer: Max = 1   Current = 0
        Advanced power management level: disabled
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
                Power Management feature set
                Write cache
                WRITE_BUFFER command
                READ_BUFFER command
                NOP cmd
                CFA feature set
                Advanced Power Management feature set
                Mandatory FLUSH_CACHE
HW reset results:
        CBLID- above Vih
        Device num = 0
Integrity word not set (found 0x0000, expected 0x43a5)

```

The Western Digital drive is mounted as ext3 with default options.
The CF card i mounted as reiserfs with the options sync and noatime.
I have also tried installing Ubuntu Server 9.04. SAME PROBLEM!?!

I have no idea what is wrong and what causes the Western Digital drive to be so slow when there is r/w activity on it.
Please help?! :confused:

/knutz

---

### Post by zmagnet on 2009-10-25
Same problem here.  Tried everything I could think of including a new motherboard.  It has to be something with the drive itself.  I also know another person with the exact same drive and the same problem.

---

### Post by knutz on 2009-10-25
Thats weird! I shure hope not, that the drive is the problem. Have you tried other OS's than ubuntu?

---

### Post by zmagnet on 2009-10-25
I'm using it for mythtv, so no.  But I have tried several Ubuntu versions.  I have an older Western Digital SATA drive in the same system that has always worked perfectly.  It really seems like something with this specific drive and revision (WD15EADS-00P8B0).

---

### Post by ian dobson on 2009-10-26
Hi,

Try disabling NCQ for the drive:-

echo 1 > /sys/block/sdb/device/queue_depth

Some WD drives don't work correctly with NCQ. It worked for me on a 500Gb WD drive.

Regards
Ian Dobson

---

### Post by knutz on 2009-10-26
I have tried running the command, but I don't have the permission to do it, not even as root. 
But if I read the /sys/block/sda/device/queue_depth in 'nano' the contents of that file is "1".

Does that mean that NCQ is already disabled?

---

### Post by zmagnet on 2009-10-27
I talked to a 2nd level support tech at Western Digital and they won't acknowledge a problem with the drive under Linux.  I was advised by the tech to install Windows XP or Vista.  They did offer to RMA the drive, but they will return the exact same model, likely with the same issue.

---

### Post by kbrunsting on 2009-10-28
to try running that command to disable ncq, I googled and found you need to edit the /etc/rc.local file and add

sh -c "echo 1 > /sys/block/sda/device/queue_depth"

before the exit 0 line.

---

### Post by dragos2 on 2009-10-28
Boot with a live cd then mount and test the drive again.

Also: check the cables ! I had some problems with some faulty SATA II cables.

Switch their position, plug them in different holes on to motherboard.

---

### Post by knutz on 2009-10-28
> **kbrunsting said:**
> to try running that command to disable ncq, I googled and found you need to edit the /etc/rc.local file and add

sh -c "echo 1 > /sys/block/sda/device/queue_depth"

before the exit 0 line.

Tried this and it didn't work. It still gives me a message that i permission is denied.

I have no idea what to do with this anymore.. 
I will try switching some SATA cables... See if that works.

---

### Post by knutz on 2009-10-28
I found this in my dmesg:
```
[   50.022590] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2090 irq 14
[   50.022596] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2098 irq 15
[   50.174790] ata2: port disabled. ignoring.
[   50.174852] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   50.330531] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   50.330589] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   50.331616] scsi2 : ata_piix
[   50.332907] scsi3 : ata_piix
[   50.333129] ata3: SATA max UDMA/133 cmd 0x20a8 ctl 0x20cc bmdma 0x2080 irq 18
[   50.333135] ata4: SATA max UDMA/133 cmd 0x20a0 ctl 0x20c8 bmdma 0x2088 irq 18
[   50.502565] ata3.00: ATA-0: ELITE PRO CF CARD 8GB, 20090216, max UDMA/100
[   50.502573] ata3.00: 15662304 sectors, multi 0: LBA
[   50.502577] ata3.00: applying bridge limits
[   50.518628] ata3.00: configured for UDMA/100
[   50.542549] ata3.00: configured for UDMA/100
[   50.542560] ata3: EH complete
[   50.714398] ata4.00: HPA unlocked: 2930277168 -> 2930277168, native 18446744072344861488
[   50.714410] ata4.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[   50.714416] ata4.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   50.738356] ata4.00: configured for UDMA/133
[   50.738546] scsi 2:0:0:0: Direct-Access     ATA      ELITE PRO CF CAR 2009 PQ: 0 ANSI: 5
[   50.738761] scsi 3:0:0:0: Direct-Access     ATA      WDC WD15EADS-00P 01.0 PQ: 0 ANSI: 5
[   50.886517] Driver 'sd' needs updating - please use bus_type methods
[   50.886651] sd 2:0:0:0: [sda] 15662304 512-byte hardware sectors (8019 MB)
[   50.886679] sd 2:0:0:0: [sda] Write Protect is off
[   50.886685] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.886726] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   50.886812] sd 2:0:0:0: [sda] 15662304 512-byte hardware sectors (8019 MB)
[   50.886837] sd 2:0:0:0: [sda] Write Protect is off
[   50.886842] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   50.886882] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   50.886890]  sda: sda1 sda2 < sda5 >
[   50.888526] sd 2:0:0:0: [sda] Attached SCSI disk
[   50.888629] sd 3:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
[   50.888656] sd 3:0:0:0: [sdb] Write Protect is off
[   50.888662] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   50.888703] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.888783] sd 3:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
[   50.888807] sd 3:0:0:0: [sdb] Write Protect is off
[   50.888812] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   50.888852] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   50.888859]  sdb: sdb1
[   51.363888] sd 3:0:0:0: [sdb] Attached SCSI disk
[   51.379862] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   51.379900] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   52.061575] Attempting manual resume
[   52.061582] swsusp: Resume From Partition 8:5
[   52.061585] PM: Checking swsusp image.
[   52.062157] PM: Resume from disk failed.
[   52.075428] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[   52.075446] ReiserFS: sda1: using ordered data mode
[   52.076157] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max c$
[   52.076772] ReiserFS: sda1: checking transaction log (sda1)
[   79.911096] ReiserFS: sda1: replayed 1960 transactions in 28 seconds
[   79.912364] ReiserFS: sda1: Using r5 hash to sort names


```

And a lot of these:
```
[ 1911.203711] attempt to access beyond end of device
[ 1911.203725] sdb1: rw=0, want=26486678344, limit=2930272002
[ 1911.204480] attempt to access beyond end of device
[ 1911.204492] sdb1: rw=0, want=31798291528, limit=2930272002
[ 1911.204891] attempt to access beyond end of device
[ 1911.204899] sdb1: rw=0, want=11789512320, limit=2930272002
[ 1911.205255] attempt to access beyond end of device
[ 1911.205263] sdb1: rw=0, want=31306239064, limit=2930272002
[ 1911.205638] attempt to access beyond end of device
[ 1911.205646] sdb1: rw=0, want=21577166736, limit=2930272002
[ 1911.206005] attempt to access beyond end of device
[ 1911.206012] sdb1: rw=0, want=30614685904, limit=2930272002
[ 1911.206368] attempt to access beyond end of device
[ 1911.206376] sdb1: rw=0, want=17669873584, limit=2930272002
[ 1911.206709] attempt to access beyond end of device

```


Anyone? :) 

Does this mean anything regarding this problem?

---

### Post by randyks on 2009-10-28
I found this solution to a problem similar to yours.

[link]("http://www.linuxquestions.org/questions/linux-server-73/troubleshooting-large-partition-attempt-to-access-beyond-end-of-device-676617/")

Randy

---

### Post by zmagnet on 2009-11-01
I tried disabling Intellipark as described [here (blogspot.com)]("http://chbits.blogspot.com/2009/07/fixing-wd-gps-drives-with-wdtler-and.html").

I'm not sure it resolved the problem, but it can't hurt.

---

### Post by knutz on 2009-11-03
I hate this!?!

I have tried everything now. I formatted both my disks and installed the recently released Ubuntu Server 9.10. This didn't help. I now have the drive partitioned with ext4. 

I've tried disabling the Intellipark. Didn't work.
After formatting my computer completely, the "*attempt to access beyond end of device*" didn't occur anymore.

I don't have the permission to run "*echo 1 > /sys/block/sda/device/queue_depth*". Not even as root. 
And the "*cat /sys/block/sdb/device/queue_depth*" gives me the output "*1*". Does that mean the NCQ is **disabled**? Because *hdparm* indicates that the NCQ is **enabled**. 

I have no idea what to do anymore than to destroy my Western "Crap"-ital drive in raging anger!!!
BUT, I am a student and have very [SIZE="1"]small[/SIZE] income, so I don't really want to do that. :lolflag:


Thank you for all the post and ideas to solve this problem.

I hope someone out there can help me with this or maybe you have the same problem as I do.

---

### Post by ian dobson on 2009-11-04
Hi,

If queue_depth is set to 1 then that means NCQ is enabled but the queue depth is set to 1, so it's the same as being disabled.

The only thing I can think of is that you try different options in the BIOS for your SATA controller (AHCI,ENHANCED,COMBINED) etc.

Hope you get the problems solved.

Regards
Ian Dobson

---

### Post by knutz on 2009-11-08
> **ian dobson said:**
> Hi,

If queue_depth is set to 1 then that means NCQ is enabled but the queue depth is set to 1, so it's the same as being disabled.

The only thing I can think of is that you try different options in the BIOS for your SATA controller (AHCI,ENHANCED,COMBINED) etc.

Hope you get the problems solved.

Regards
Ian Dobson


Well.. There's not really anything of that sort in the BIOS, but i read somewhere on the Internet, that if i disabled SATA it would disable the AHCI, but unfortunately my drives where invisible to the BIOS when SATA was disabled. So i couldn't boot.

---

### Post by Vegan on 2009-11-08
My advice, put Linux on the WD disk, get rid of the chip.

Then go feed the machine more RAM for performance. That and a faster NIC.

---

### Post by knutz on 2009-11-08
> **Vegan said:**
> My advice, put Linux on the WD disk, get rid of the chip.

Then go feed the machine more RAM for performance. That and a faster NIC.


I'm not going to do that. :)

The WD drive is the problem, and i already have 2gb of RAM which is more than plenty. (It uses 2-300 MB tops for my use).

---

### Post by knutz on 2009-11-10
> **knutz said:**
> I'm not going to do that. :)

The WD drive is the problem, and i already have 2gb of RAM which is more than plenty. (It uses 2-300 MB tops for my use).


Okay.

I've tried writing to CF card in the SATA converter, in the exact same way as I do to the Western Digital drive. 

**I ran these tests before I started writing to the drive:**

knutz@knutz-server:~$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   1192 MB in  2.00 seconds = 596.04 MB/sec
 Timing buffered disk reads:  124 MB in  3.04 seconds =  40.76 MB/sec

knutz@knutz-server:~$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   1202 MB in  2.00 seconds = 600.50 MB/sec
 Timing buffered disk reads:  124 MB in  3.04 seconds =  40.76 MB/sec

knutz@knutz-server:~$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   1186 MB in  2.00 seconds = 593.21 MB/sec
 Timing buffered disk reads:  124 MB in  3.04 seconds =  40.75 MB/sec

[B]
And I ran these tests while writing to the drive:[/B]


knutz@knutz-server:/media/disk$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   834 MB in  2.00 seconds = 416.52 MB/sec
 Timing buffered disk reads:  114 MB in  3.05 seconds =  37.40 MB/sec

knutz@knutz-server:/media/disk$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   806 MB in  2.01 seconds = 400.98 MB/sec
 Timing buffered disk reads:  114 MB in  3.06 seconds =  37.30 MB/sec

knutz@knutz-server:/media/disk$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   648 MB in  2.00 seconds = 323.71 MB/sec
 Timing buffered disk reads:  112 MB in  3.00 seconds =  37.29 MB/sec


As you can see the CF card handles simultaneous reading/writing much better than the Western Digital harddrive. (*the western digital drive had a "Timing buffered disk reads" at approx. 2 MB/sec*)
[B]
How is this even possible?!?[/B]

---

### Post by zmagnet on 2009-11-26
What is the manufacture date of your drive?   The one I'm having problems with is Aug 01, 2009.  I'm wondering if there's a problem with a certain lot of these drives.

---

### Post by knutz on 2009-11-26
I'll look into that when i get home.

I have spoken to WD about it, and they think the drive is defect. So i'm going to return it.

---

### Post by zmagnet on 2009-11-26
I RMA'd mine and just installed the replacement yesterday (mfg 11/10/2009).  It's too early to tell if it has the same problem.

---

### Post by knutz on 2009-11-26
> **zmagnet said:**
> I RMA'd mine and just installed the replacement yesterday (mfg 11/10/2009).  It's too early to tell if it has the same problem.

Okay, then lets hope theres no problem with the replacement. I hope this is the last of that error. 

I'll give you an update when i get the new drive. :)

---

### Post by graben3 on 2009-11-27
I have the exact same drive (Model Number: WDC WD15EADS-00P8B0)

It worked flawlessly under ubuntu 9.04 since I bought it...then it suddently stopped writing really fast.... it however still reads data fast. 

When I write to the drive, it will typically get about 300 to 700 kb/s

Before it would get around 60MB/s each time....

Im waiting to see if someone of you gets the remplacement drive and if it solved your problems...

Keep us posted !

---

### Post by raix on 2009-11-30
I've got the same problem on a raid-1 made of 2 WD15EADS-00P8B0.
Suddenly they became very slow and now I can see %wa-values up to 95%....
So of course everythin else hangs.

I tried everything...different mount options, bios update, different kernel-versions, different kernel-patches.

But nothing helps.
Keep us updatet if the replacement drive fixes this issue. Then I'm going to send mine in, too.

---

### Post by knutz on 2009-12-03
Hey everybody!

Good news. So far.

I have recieved my new Western Digital WD15EADS harddrive. I addition to that, I bought another harddrive WD15EADS harddrive, which I now use in a RAID 0 array. 

I have just installed the harddrives a few hours ago, and NO PROBLEMS whatsoever! BUT, I'm still a bit skeptical, because of the previous drive and I'm going to do some speed tests and get back to You with updates.

So far the speed is stable and fast!

/knutz

---

### Post by zmagnet on 2009-12-03
Same here.  No problems at all since I received a replacement drive.

---

### Post by Plus! on 2009-12-09
2 knutz & zmagnet:

i have encountered the same problem with 15eads :icon_frown:
could you please specify the revision and the firmware version of your RMA`d wd drive.

---

### Post by knutz on 2009-12-10
> **Plus! said:**
> 2 knutz & zmagnet:

i have encountered the same problem with 15eads :icon_frown:
could you please specify the revision and the firmware version of your RMA`d wd drive.

The WD drive i returned, gave me, using "hdparm -I /dev/sdX", this result:

```

...
Model Number:       WDC WD15EADS-00P8B0
Serial Number:      WD-WMAVU0121769
Firmware Revision:  01.00A01
...
```

My new WD drives have these specs:

```

/dev/sdb
...
Model Number:       WDC WD15EADS-00P8B0
Serial Number:      WD-WCAVU0402580
Firmware Revision:  01.00A01
...

/dev/sdc
...
Model Number:       WDC WD15EADS-00P8B0
Serial Number:      WD-WCAVU0406454
Firmware Revision:  01.00A01
...

```

As you can see, the firmware versions are the same.
So my drive have probably just been defective. 
I recommend you state your problem to WD and hear out what they say about it. 

Good luck! :D
And keep us updated. :P


/knutz

---

### Post by knutz on 2009-12-10
By the way. STILL no problems with the new drives.

They still going strong. 

/knutz

---

### Post by raix on 2009-12-14
@knutz

My sluggish drives have S/N starting with WMAVU as well....a coincidence?

Did you test your drive witht eh WD-Diag Tool before sending them hin? I let the tool test both of my drives yesterday. It ran 10Hours in total and found no errors.

---

### Post by knutz on 2009-12-14
> **raix said:**
> @knutz

My sluggish drives have S/N starting with WMAVU as well....a coincidence?

Did you test your drive witht eh WD-Diag Tool before sending them hin? I let the tool test both of my drives yesterday. It ran 10Hours in total and found no errors.

Well, I don't think the WMAVU has anything to say, because the replacement drive I received has the same first letters.
But I think it might have been an unlucky error in the beginning of the production as the defective drive had the S/N WMAVU01XXXXX, and the new one have the S/N WMAVU04XXXXX. I have no idea, what the error might have been other than a hardware failure. The firmware on the new drive I got is the same as the old one.

Well, I took a quick test without errors. But no I didn't thoroughly test my drive with WD's own tools before sending it back. I mainly tested the speed in Linux with hdparm, which, as you can see, gave me some pretty bad results. 
When I stated this issue to a WD supporter, he immediately concluded, that the drive was defective, and I should return it.
So I don't think I'm the first one with this issue. 
Try contacting WD and see what they have to say. I tried almost everything to the drive to work, without any luck. When I received the replacement, it worked flawlessly.

That's my advice :) Hope you figure it out.

/knutz

---

### Post by raix on 2009-12-14
Well my drives start with WMAVU04....
I already wrote WD an EMail but they didn't answer. 

What Tests did you do with hdparm? I can watch with top and iotop, that the io-wait goes sky-high as soon as file-intensive operations start.

Think after the Holidays I will send both drives back, as I've tried everything on the software-side.

---

### Post by knutz on 2009-12-14
> **raix said:**
> Well my drives start with WMAVU04....
I already wrote WD an EMail but they didn't answer. 

What Tests did you do with hdparm? I can watch with top and iotop, that the io-wait goes sky-high as soon as file-intensive operations start.

Think after the Holidays I will send both drives back, as I've tried everything on the software-side.

Well, I actually only used the "hdparm -Tt /dev/sdX". I had the exact same problem as you have now. In htop I could see that the drive caused, as you said, "sky-high" io-wait, causing the system to hang. When i ran the hdparm command, sometimes it would wait for several minutes before coming up with a result. So be patient. In my case, the hard drive caused the system to hang when it started to do a little simultaneous reading and writing, and that resulted in under 2 mb/s read speed from the harddrive.

I contacted wdc via this site;
[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/ask.php](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/ask.php)
where I stated my case and asked for help on the problem, and the supporter recommended med to return the drive to the place of purchase.

Hope you get in touch with them.

---

### Post by raix on 2010-01-10
So....I got my replacement drives last week and just swapped them in.
Everything runs fine now...no high %wa no hiccups. Let's hope that this doesn't happen again.

---

### Post by d$_linux on 2010-01-16
I have exactly this problem as well. I have the same model/rev. as previously posted and am experiencing the same behaviour.

I've looked into the trouble on the linux kernel mailing lists, as I found many of these types of log entries in syslog:

[FONT=Courier New][SIZE=1]Jan 15 16:51:33 kong kernel: [31801.180014] INFO: task kjournald:698 blocked for more than 120 seconds.
Jan 15 16:51:33 kong kernel: [31801.180028] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 15 16:51:33 kong kernel: [31801.180039] kjournald     D 00000000ffffffff     0   698      2 0x00000000
Jan 15 16:51:33 kong kernel: [31801.180044]  ffff88007152fd40 0000000000000046 ffff88007152fd00 0000000000015880
Jan 15 16:51:33 kong kernel: [31801.180048]  ffff8800720f1a60 0000000000015880 0000000000015880 0000000000015880
Jan 15 16:51:33 kong kernel: [31801.180051]  0000000000015880 ffff8800720f1a60 0000000000015880 0000000000015880
Jan 15 16:51:33 kong kernel: [31801.180055] Call Trace:
Jan 15 16:51:33 kong kernel: [31801.180066]  [<ffffffff811e4ff6>] journal_commit_transaction+0x166/0xe60
Jan 15 16:51:33 kong kernel: [31801.180071]  [<ffffffff8104f185>] ? finish_task_switch+0x65/0x120
Jan 15 16:51:33 kong kernel: [31801.180076]  [<ffffffff81078b20>] ? autoremove_wake_function+0x0/0x40
Jan 15 16:51:33 kong kernel: [31801.180079]  [<ffffffff8106b067>] ? lock_timer_base+0x37/0x70
Jan 15 16:51:33 kong kernel: [31801.180082]  [<ffffffff8106b0f7>] ? try_to_del_timer_sync+0x57/0x70
Jan 15 16:51:33 kong kernel: [31801.180087]  [<ffffffff811e8ead>] kjournald+0xed/0x250
Jan 15 16:51:33 kong kernel: [31801.180090]  [<ffffffff81078b20>] ? autoremove_wake_function+0x0/0x40
Jan 15 16:51:33 kong kernel: [31801.180093]  [<ffffffff811e8dc0>] ? kjournald+0x0/0x250
Jan 15 16:51:33 kong kernel: [31801.180096]  [<ffffffff81078736>] kthread+0xa6/0xb0
Jan 15 16:51:33 kong kernel: [31801.180100]  [<ffffffff810130ea>] child_rip+0xa/0x20
Jan 15 16:51:33 kong kernel: [31801.180103]  [<ffffffff81078690>] ? kthread+0x0/0xb0
Jan 15 16:51:33 kong kernel: [31801.180105]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
[/SIZE][/FONT]
Which of course led me to believe there was a problem in the kernel/ext3/whatever. (This conclusion did not sit well with me, as the linux kernel and filesystem drivers have never given me trouble once since 1998 when I started using Linux!!)

However, I see some of you believe this issue to be resolved once the Caviar Green drive has been RMA'd/replaced.

Since I have 3 machines, all of which exclusively use these exact drives, with only my server experiencing the hangs (when one of its two drives are accessed) I can only surmise that it is indeed a hardware problem centered around the Caviar Green drive.

*sigh*

Will repost again with my findings as well.

---

