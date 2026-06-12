---
title: "Ubuntu 7.10 Server Questions. SCSI/LAMP help"
date: 2008-04-09
forum: Server Platforms
---

### Post by atvar on 2008-04-09
Okay, First off, I have to admit that I'm a complete newbie when it comes to setting up a server or even operating Linux.. so be gentle.. lol

I've got Ubuntu Server 7.10 installed, and I have the GUI installed so I can have at least some level of familiarity with the computer. My first problem is, I can't seem to figure out how to make linux detect all my hardware. So, before I say anymore, heres my system specs as I know them:

2x 1.8ghz Xeon Processors
2x 500gb SCSI drives.
1x 40gb IDE drive. (Has the OS on it.)
1x CD/DVD RW Drive
1x Zip drive
1x Floppy drive
Video card doesn't matter.
And yes, it is an actual server computer. lol

So, my main issues are these:
1.) I cannot get Linux to detect and/or use the 2x 500gb SCSI Drives... This is a big problem, as 40gb will not be nearly enough storage for what I plan to do with this computer.
2.) It is not detecting that I have two 1.8 processors.. It only sees one Intel Pentium 4 1.8ghz.

If I can get these figured out, all should be much easier.

Also, while I'm here...

I initially set the OS to be a LAMP server when I installed Ubuntu 7.10 Server... However I can't seem to find any of the packages associated with Apache/MySQL as I had assumed would be included in the install.

I plan on using this computer to do many things.
a.) It will be serving as a server for a game.
b.) It will be serving as a web host for pages of mine and my friends.
c.) It will be serving as the in-home file server for me and my room-mate.

I don't believe this thing will see much outside traffic, so doing all three of these things shouldn't be too much of a problem.

All help would be appreciated! Thanks!

--Corey

---

### Post by faulkes on 2008-04-10
Detecting the SCSI drives would be on the part of the controller, so we would need
to know which SCSI controller you have (make, model, rev, all the details).  You
can look through the output of 

```

dmesg

or 

/var/log/dmesg

```

to find details.

IIRC there can be some trickery involved in how it treats CPU's, the output of

```

cat /proc/cpuinfo

```

would be most helpful.

LAMP is an option at install time, so when you installed the server it should have
been presented to you.  If you selected the option at install time, see my
last paragraph regarding documentation.

If you didn't select it, it is rather trivial to install the
components.

```

sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install mysql-server

```

You can also use aptitude to see what packages
do:

```

aptitude show mysql-server

```

In my signature you will find links to the official and community documentation, 
these are the best places to start for additional configuration information on 
the packages you are interested in.

Faulkes

---

### Post by atvar on 2008-04-11
So, a few lines dmesg that that I see that trouble me are:
```
"[   28.591739] CPU: Hyper-Threading is disabled" 
```
If I understand correctly, Xeon processors are supposed to support Hyper-Threading?

So heres all the SCSI-related items I could find.. a rather extensive and spread out list. I've cut all the extra stuff, so if I'm missing something let me know.

```
[   33.237883] SCSI subsystem initialized
[   19.920000] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   19.920000]         <Adaptec 29160 Ultra160 SCSI adapter>
[   19.920000]         aic7892: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   19.920000] 
[   19.920000] scsi 0:0:0:0: Direct-Access     SEAGATE  ST336752LW       0004 PQ: 0 ANSI: 3
[   19.920000] scsi0:A:0:0: Tagged Queuing enabled.  Depth 8
[   19.970000] scsi 0:0:1:0: Direct-Access     SEAGATE  ST336752LW       0004 PQ: 0 ANSI: 3
[   19.970000] scsi0:A:1:0: Tagged Queuing enabled.  Depth 8
[   20.170000] scsi1 : ata_piix
[   20.170000] scsi2 : ata_piix
[   21.250000] scsi: waiting for bus probes to complete ...
[   23.340000] scsi 1:0:1:0: Direct-Access     IOMEGA   ZIP 100          05.H PQ: 0 ANSI: 5
[   23.350000] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.360000] sd 0:0:1:0: [sdb] Spinning up disk.......................................................................................................not responding...
[  124.360000] sd 0:0:1:0: [sdb] READ CAPACITY failed
[  124.360000] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  124.360000] sd 0:0:1:0: [sdb] Sense Key : Not Ready [current] 
[  124.360000] sd 0:0:1:0: [sdb] Add. Sense: Logical unit not ready, cause not reportable
[  124.360000] sd 0:0:1:0: [sdb] Test WP failed, assume Write Enabled
[  124.360000] sd 0:0:1:0: [sdb] Asking for cache data failed
[  124.360000] sd 0:0:1:0: [sdb] Assuming drive cache: write through
[  124.360000] sd 0:0:1:0: [sdb] Attached SCSI disk
[  124.370000] sd 1:0:1:0: [sdc] Attached SCSI removable disk
[  124.380000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  124.380000] sd 0:0:1:0: Attached scsi generic sg1 type 0
[  124.380000] sd 1:0:1:0: Attached scsi generic sg2 type 0
[  124.380000] scsi 2:0:0:0: Attached scsi generic sg3 type 5
[  124.440000] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[  124.440000] Uniform CD-ROM driver Revision: 3.20
[  124.440000] sr 2:0:0:0: Attached scsi CD-ROM sr0
[  124.740000] Attempting manual resume

```

Aaand thats all I found for the SCSI info...

---

### Post by atvar on 2008-04-11
Sorry about the multiple posts.. I'm doing the replies piece by piece. lol

So ```
cat /proc/cpuinfo
```

returned:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 1.80GHz
stepping        : 4
cpu MHz         : 1808.488
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
bogomips        : 3619.84
clflush size    : 64

```

Still only sees one. There should be two of these processors... Unless it says there are two and I'm just not reading it correctly..

---

### Post by atvar on 2008-04-25
bump.:guitar:

---

