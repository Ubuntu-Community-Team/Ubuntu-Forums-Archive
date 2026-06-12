---
title: "hardware raid"
date: 2022-03-02
forum: Server Platforms
---

### Post by kb3mkd2 on 2022-03-02
I recently acquired an old server with a hardware raid card. It has a 3ware PCI card providing 2 raid arrays. one is a ~500Gb mirror and the other is a 4.5Tb raid 5 made of 6 drives.
lsblk is showing sda at 500Gb. sdb at 2Tb, sdc at 2Tb, and sdd at  560Gb

lspci hs the following line
07:00.0 RAID bus controller: 3ware Inc 9650SE SATA-II RAID PCIe (rev 01)

lsmod contains the line
3w_9xxx                45056  2



Why are the drives not matching up with what the raid controller is actually producing?
How do I fix this?

---

### Post by CharlesA on 2022-03-02
Where are you seeing the drives set up? Are they in the configuration screen of the RAID card or elsewhere?

Normally, a hardware RAID card will be invisible to the OS - that was the case with my LSI 9260-8i - all I saw when I did an fdisk -l was a single huge volume.

Can you post the output of the following commands:

```
sudo lspci -vv
```

```
sudo fdisk -l
```

```
sudo lsblkd -c /dev/null
```

EDIT: I couldn't find any real info on this card for Ubuntu - only references to the drives.

I did find this reference for Debian, though. Does that show you anything about the arrays?
[https://wiki.debian.org/LinuxRaidForAdmins#A3w-9xxx](https://wiki.debian.org/LinuxRaidForAdmins#A3w-9xxx)

---

### Post by kb3mkd2 on 2022-03-04
> **CharlesA said:**
> Where are you seeing the drives set up? Are they in the configuration screen of the RAID card or elsewhere?

Normally, a hardware RAID card will be invisible to the OS - that was the case with my LSI 9260-8i - all I saw when I did an fdisk -l was a single huge volume.

That's what i thought!

> **CharlesA said:**
> 
Can you post the output of the following commands:

```
sudo lspci -vv
```

```

07:00.0 RAID bus controller: 3ware Inc 9650SE SATA-II RAID PCIe (rev 01)
        Subsystem: 3ware Inc 9650SE SATA-II RAID PCIe
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at ca000000 (64-bit, prefetchable) [size=32M]
        Region 2: Memory at c8300000 (64-bit, non-prefetchable) [size=4K]
        Region 4: I/O ports at 3000 [size=256]
        Expansion ROM at c8320000 [virtual] [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: CorrErr- NonFatalErr- FatalErr- UnsupReq-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- NonFatalErr- FatalErr- UnsupReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x8, ASPM L0s L1, Exit Latency L0s <512ns, L1 <64us
                        ClockPM- Surprise- LLActRep+ BwNot- ASPMOptComp-
                LnkCtl: ASPM Disabled; RCB 128 bytes Disabled- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s (ok), Width x4 (downgraded)
                        TrErr- Train- SlotClk- DLActive+ BWMgmt- ABWMgmt-
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr-
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+
                AERCap: First Error Pointer: 00, ECRCGenCap+ ECRCGenEn- ECRCChkCap+ ECRCChkEn-
                        MultHdrRecCap- MultHdrRecEn- TLPPfxPres- HdrLogCap-
                HeaderLog: 00000000 00000000 00000000 00000000
        Kernel driver in use: 3w-9xxx
        Kernel modules: 3w_9xxx

```



> **CharlesA said:**
> 
```
sudo fdisk -l
```



```

Disk /dev/loop0: 55.45 MiB, 58130432 bytes, 113536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 55.52 MiB, 58204160 bytes, 113680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 117.21 MiB, 122896384 bytes, 240032 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 61.91 MiB, 64897024 bytes, 126752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 70.32 MiB, 73728000 bytes, 144000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 67.94 MiB, 71221248 bytes, 139104 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 43.6 MiB, 45703168 bytes, 89264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes








Disk /dev/sda: 465.67 GiB, 499989348352 bytes, 976541696 sectors
Disk model: 9650SE-12M DISK
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A433C0DF-977B-4CCE-BC7E-E194EDFF929F


Device       Start       End   Sectors   Size Type
/dev/sda1     2048      4095      2048     1M BIOS boot
/dev/sda2     4096   2101247   2097152     1G Linux filesystem
/dev/sda3  2101248 976539647 974438400 464.7G Linux filesystem




Disk /dev/sdb: 1.102 TiB, 2199023255040 bytes, 4294967295 sectors
Disk model: 9650SE-12M DISK
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe292fbba


Device     Boot Start        End    Sectors Size Id Type
/dev/sdb1          63 4294965246 4294965184   2T 42 SFS




Disk /dev/sdc: 1.102 TiB, 2199023255040 bytes, 4294967295 sectors
Disk model: 9650SE-12M DISK
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe292fbb9


Device     Boot Start        End    Sectors Size Id Type
/dev/sdc1          63 4294965246 4294965184   2T 42 SFS




Disk /dev/sdd: 560.58 GiB, 601899402240 bytes, 1175584770 sectors
Disk model: 9650SE-12M DISK
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe292fbb8


Device     Boot Start        End    Sectors   Size Id Type
/dev/sdd1          63 1175582721 1175582659 560.6G 42 SFS




Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 200 GiB, 214748364800 bytes, 419430400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```


> **CharlesA said:**
> 
```
sudo lsblkd -c /dev/null
```

```

lsblkd: command not found

```

> **CharlesA said:**
> 
EDIT: I couldn't find any real info on this card for Ubuntu - only references to the drives.

I did find this reference for Debian, though. Does that show you anything about the arrays?
[https://wiki.debian.org/LinuxRaidForAdmins#A3w-9xxx](https://wiki.debian.org/LinuxRaidForAdmins#A3w-9xxx)

The link above is supposed to lead to tools for this but that goes nowhere.

thank you for your response.

---

### Post by CharlesA on 2022-03-04
> **kb3mkd2 said:**
> 
```

lsblkd: command not found

```


I made a typo. The command should have been, but that doesn't matter now.

```
sudo blkid -c /dev/null
```

> **kb3mkd2 said:**
> 
The link above is supposed to lead to tools for this but that goes nowhere.

thank you for your response.

Bah. I did a little more research and found this post, which mentions "auto-carving" to break up disks larger than 2TB.
[https://www.truenas.com/community/threads/4tb-disks-attached-to-3ware-9550se.38970/](https://www.truenas.com/community/threads/4tb-disks-attached-to-3ware-9550se.38970/)

It found a tool that you could install on Debian to check the status of the RAID card:
[https://www.unixteacher.org/blog/installing-tw-cli-on-debian/](https://www.unixteacher.org/blog/installing-tw-cli-on-debian/) , which leads to here:
[http://hwraid.le-vert.net/wiki/3Ware](http://hwraid.le-vert.net/wiki/3Ware)

You can try installing that and see what the properties of the array look like.

Was this array used on a different machine in the past? Do you need to keep any of the data from the currently configured raid?

---

### Post by MAFoElffen on 2022-03-05
> **CharlesA said:**
> 
... which leads to here:
[http://hwraid.le-vert.net/wiki/3Ware](http://hwraid.le-vert.net/wiki/3Ware)


This 'link' is where I used to go for all my hardware RAID needs for all my servers...

I did the same looking for what I needed, that is where I found the most..

---

### Post by kb3mkd2 on 2022-03-06
Why is this showing up as [kde]? i registered this thread as [server]!

this is a recently acquired server. i wiped the contents of the raid. i haven't installed anything new yet other than putting Ubuntu server on the OS drive.

I found that tw-cli tool and tried the following

```

sudo tw-cli show


Ctl   Model        (V)Ports  Drives   Units   NotOpt  RRate   VRate  BBU
------------------------------------------------------------------------
c4    9650SE-12ML  12        8        2       0       1       1      -

```
```

sudo tw-cli /c4 show


Unit  UnitType  Status         %RCmpl  %V/I/M  Stripe  Size(GB)  Cache  AVrfy
------------------------------------------------------------------------------
u0    RAID-1    OK             -       -       -       465.651   RiW    ON
u1    RAID-5    OK             -       -       256K    4656.56   RiW    ON


VPort Status         Unit Size      Type  Phy Encl-Slot    Model
------------------------------------------------------------------------------
p0    OK             u1   931.51 GB SATA  0   -            ST31000524NS
p1    OK             u1   931.51 GB SATA  1   -            ST31000524NS
p4    OK             u1   931.51 GB SATA  4   -            ST31000524NS
p5    OK             u1   931.51 GB SATA  5   -            ST31000524NS
p7    SMART-FAILURE  u0   465.76 GB SATA  7   -            ST3500514NS
p8    OK             u1   931.51 GB SATA  8   -            ST31000524NS
p9    OK             u1   931.51 GB SATA  9   -            ST31000524NS
p11   OK             u0   465.76 GB SATA  11  -            ST3500514NS

```

The correct output of the lsblk command - the part that matters to this thread
```

sda                         8:0    0 465.7G  0 disk
&#9500;&#9472;sda1                      8:1    0     1M  0 part
&#9500;&#9472;sda2                      8:2    0     1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0 464.7G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   200G  0 lvm  /
sdb                         8:16   0     2T  0 disk
&#9492;&#9472;sdb1                      8:17   0     2T  0 part
sdc                         8:32   0     2T  0 disk
&#9492;&#9472;sdc1                      8:33   0     2T  0 part
sdd                         8:48   0 560.6G  0 disk
&#9492;&#9472;sdd1                      8:49   0 560.6G  0 part

```

The raid was set up and used in the server as-is using windows 7 for several years. i don't want to use windows.

Other than replacing the card, is there any way to correct the auto carving?

---

### Post by CharlesA on 2022-03-07
What do you get when you run this:

```
sudo tw-cli /c4 show autocarve
```

More info on other commands can be found here:
[https://www.physics.mcgill.ca/~merp/tw_cli.8.html](https://www.physics.mcgill.ca/~merp/tw_cli.8.html)

---

### Post by kb3mkd2 on 2022-03-07
[QUOTE=CharlesA;14084678]What do you get when you run this:

```
sudo tw-cli /c4 show autocarve
```


Autocarve policy was on. I set it to off, rebooted, and still see the virtual disks.

i verified that autocarve policy is off.

But at least I now know where to research this further. 

Thank you for pointing me in the right direction.

---

### Post by kb3mkd2 on 2022-03-07
Since it had nothing on it, I went ahead and destroyed the array and rebuilt it. It is now showing correctly.

Mark this one solved!

---

### Post by CharlesA on 2022-03-07
> **kb3mkd2 said:**
> Since it had nothing on it, I went ahead and destroyed the array and rebuilt it. It is now showing correctly.

Mark this one solved!

That would do it. According to the documentation, anything created with the policy on would still have it in effect.

Glad you got it sorted. :)

---

