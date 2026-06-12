---
title: "Damaged File System"
date: 2010-12-10
forum: Server Platforms
---

### Post by MickSulley on 2010-12-10
Hi,

I have a server running Ubuntu server 10.04 32 bit.  I ran an update via
aptitute and it hung.  When I try to reboot it seems to go through all the normal
stuff but terminates with -

GRUB loading.
        [Linux-bzImage. setup=0x3400, size=0x3f66c0]
error: out of partition
        Failed to boot default entries.
Press any key to continue...


If I press any key it just repeats the message

I have booted from a live CD, I can open GParted and see my drive - 
Partition   File System Size            Used      Unused     Flags
/dev/sda1 ! unknown      977.00 KiB     ---       ---        bios_grub
/dev/sda2   ext2         244.14 MiB     81.84 MiB 162.30MiB
/dev/sda3 ! lvm2         1.82 TiB       ---       ---        lvm

The ! on sda1 and sda3 is actually a warning symbol.

If I look at info, sda1 says
! Warning
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)

sda3 says
! Warning
Logical Volume Management is not yet supported.

Any ideas what I can do to get it running again?

Thanks
Mick

---

### Post by disabledaccount on 2010-12-10
You are running server edition - on what hardware? This is important, because it looks like your "server" is just normal pc, without hdd redundancy. If it's so, then you should realize that "usual pc" often hungs because of low-quality PSU, Motherboard and RAM errors. Utill You elliminate those possibilities recovering data from hdd is risky, because unstable hardware cannot work predictably - it will make errors beacause of errors.

First step is to launch some live-USB/CD system and:
a) test RAM with memtest, then HW stability with some stress-tests
b) get info about partitions with help of parted/fdisk/gparted
c) take a look what testdisk is able to detect
d) run fsck, but this is risky untill you're know what you're doing.

---

### Post by elico on 2010-12-10
before everything i will try to connect this drive to another machine or use a livecd\dvd os 
it can be some kernel or grub problem and not the drive itself.

i had something else.
i replicated my server to backup drive for server upgrade and after the server was working for hours i connected the new os drive and when i tried to copy the information from one drive to another i got some error message about the files and when i tired to see what the problem was i almost died cause there were no partitions on the drive so i had to restore everything using a software that cost me 39 Euro =\ (thanks god it worked)

---

### Post by disabledaccount on 2010-12-11
Both of You have problems with partition tables: **MickSulley**'s hdd most propably has partitions with wrong number of blocks and/or wrong start block number.
**elico**: your partition table has been completely messed or deleted during disk operations.

There is no way that this was software bug. Such things happens also on all other OSes including winblows. In general, there are 3 possible causes that can lead to overwriting of random disk blocks, without warning or question about permissions:
- CPU or RAM errors (overclocking, faulty components)
- unstable hdd/system power
- internal hdd errors (damaged cache chip, firmware bugs, bad actuator connections, sector relocation events, etc)
Additionally, sometimes link errors are possible, but this mainly affects old ATA drives.

Previously, I forget to mention about SMART : look at C7 parameter (UDMA CRC error rate) - if it is greater than zero you have link problems and **very high chance** to damage data during write operations. Other very important parameters are **Realocated Sectors Count** and **Write Error Rate**.
Linux system logs often tells everything about hdd problems - but you need access to log files first.

elico: I suppose that you have wasted 39euro - in most cases such problems can be easily solved with testdisk or even fdisk ;)

---

### Post by MickSulley on 2010-12-12
I have run testdisk, it took 24 hours for the deep analysis.  I now have the log file (attached) but I am not sure where to go from here.  Can anyone help please?

Thanks
Mick

---

### Post by iponeverything on 2010-12-12
```
There is no way that this was software bug.
```

Famous last words. 

Just for fun sometime you should try doing some software proofs.. They get ugly very quickly.

---

### Post by disabledaccount on 2010-12-13
iponeverything: perhaps I should say "there is **almost** no way..." ;)

MickSulley: wow, nice mess... you are using HFS? ... :shock: ... :p

I needn't to use testdisk with GPT yet - however gfdisk is what you can use to check/restore GPT header and partition table from backup (which was automatically created). What type of filesystem You expect to be on the 1st and 3rd partition?

---

### Post by HermanAB on 2010-12-13
Howdy,

My tuppence worth:
You absolutely have to run a 'server' on a battery back-up UPS.  That will eliminate most all random problems.

Secondly, I almost never update my servers.  Generally, I install a server, lock it down best I can and then I leave it alone till the hardware fails in about 5 years.  Frequently, a server will run continuously for its whole life without a single update or reboot.  An update has to be extremely serious before it is worth applying. The last time I did any updates (and only to certain machines), was with the SSL bugs of a year or so ago.

Linux is extremely robust, if you keep your fingers off it.

---

### Post by Vegan on 2010-12-13
I experience malfunctions all the time so I simply mechanized backups and run with it.

---

