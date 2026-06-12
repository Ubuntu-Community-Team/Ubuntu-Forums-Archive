---
title: "Formatting a 3TB drive GUID partition table"
date: 2012-08-23
forum: Server Platforms
---

### Post by saphil on 2012-08-23
How do I get the server to see a 3TB drive? I was told to drop the old partition table and put a guid partition table on instead.  That I did but the drive still only reads out at 802GB.  What am I missing in the recipe?  I want to end up with NTFS on it because that is all the person I am sending it to can read, but it cannot be a mbr partition table or whatever MS puts on their extra-large drives because I cannot read it on my Ubuntu servers or Debian servers.  

I am writing this from a Debian server with a 3.2.0 kernel.  My Ubuntu Server is a Ubuntu10.04 server with 2.6.32-41 kernel. The Ubuntu server could be too old, I guess, but the Debian one is running Wheezy with backports on.

Wolf

---

### Post by oldfred on 2012-08-23
Windows 7 reads gpt drives, but can only boot from gpt drives if UEFI not BIOS.

If you format your 3TB drive with MBR, it should be just over 2TB. Not sure how you are getting 802GB? 

Download gdisk and post this:

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Change sda to your drive.
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by saphil on 2012-08-24
I had blown away the partition table before, but when I plugged it back into the Windows7 box, storage management required me to agree to a partition table, and that is the table it added in with a protective mbr partition.

The disk is
a hitachi 
0F12460MKC5800P13
P/N 0F12460          S/N YNG1WUWA
CAPACITY:3TB       MLC:MKC580     FW:580
LBA:5.860.533.168 SECTORS  CHS:16383/16/63
MADE IN THAILAND BY Hitachi Global E182115 T
---------------------------------------------------------------
RATED:5v 430mA.12V 400mA       SATA 6.0      Gb/s
HDS5C3030ALA630


```
root@LTS-TEST-01:~# parted /dev/sdb unit s print
Model: Generic External (scsi)
Disk /dev/sdb: 1565565872s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End      Size     File system  Name                          Flags
 1      34s    262177s  262144s               Microsoft reserved partition  msftres

root@LTS-TEST-01:~# gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 1565565872 sectors, 746.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7AFF6247-38A4-4D96-856C-57A6E5179E2F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1565565838
Partitions will be aligned on 8-sector boundaries
Total free space is 1565303661 sectors (746.4 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
```

---

### Post by darkod on 2012-08-24
Creating gpt table is easy, not sure if the person you are sending it too might have problems though. You don't want to use the MS way since it doesn't work on your end, but if the other person has MS only it might not read the linux way (although it should).

Otherwise, for gpt table simply use parted:
sudo parted /dev/sdb
mklabel gpt
quit

You can also use parted to create partition(s). And then you can format them with mkfs or similar. I think it should work for ntfs too. I'm pressed for time right now to add those commands.

PS. You can see that MS created some reserved partition, parted doesn't do that.

---

### Post by saphil on 2012-08-24
I followed the parted instructions and am left with this:
```
wolf@LTS-TEST-01:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 1565565872 sectors, 746.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7FE58B4D-B23B-4646-B9D2-C3535754A8EC
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1565565838
Partitions will be aligned on 2048-sector boundaries
Total free space is 1565565805 sectors (746.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

```
I can't sort out why it cannot see the whole drive.

---

### Post by oldfred on 2012-08-24
I am surprised Microsoft is putting a system reserved partition and also starting at sector 34. The system reserved is a hidden partition for boot code with Windows UEFI boot loader. But you are not using UEFI nor have efi partition which has to be first if using UEFI. And both Windows & gparted start partitions at 2048 now for better compatibility with new 4K drives. Yours is not showing as a 4K drive, but maybe that is part of the issue.

What does gparted say. I have used gparted to format my drives gpt, but all mine are smaller.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by saphil on 2012-08-24
GPartEd sees it as the 802GB drive.  
I am pretty sure there isn't a selective de-gausser in use in my office.  It is very weird.
The MS documentation I saw suggested going in at the bios level and making sure the sectors were bigger than 512.  Maybe that would help.  Physically hammer in the number of sectors.

---

### Post by rubylaser on 2012-08-24
Your [motherboard SATA controller / or docking station]("http://ubuntuforums.org/showthread.php?t=1710201") needs to support hard drives that are > 2TB for them to display all available space properly in the BIOS for the OS to recognize them as 3TB drives.  If it doesn't show up as a 3TB drive in the BIOS, it won't once it boots either. What is the make and model of your motherboard?

---

### Post by saphil on 2012-08-27
> **rubylaser said:**
> Your [motherboard SATA controller / or docking station]("http://ubuntuforums.org/showthread.php?t=1710201") needs to support hard drives that are > 2TB for them to display all available space properly in the BIOS for the OS to recognize them as 3TB drives.  If it doesn't show up as a 3TB drive in the BIOS, it won't once it boots either. What is the make and model of your motherboard?

This is a HP proliant dl165 g7 i-U pizza-box server.  There are some bios updates but the closest OS I can find at hp support is RHEL.

```
lts-test-01
    description: Rack Mount Chassis
    product: ProLiant DL165 G7 (590261-001)
    vendor: HP
    serial: MXQ1250CN3
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=rackmount sku=590261-001 
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: HP
          physical id: 0
          version: O37
          date: 03/23/2011
          size: 64KiB
          capacity: 4032KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int14serial int10video acpi usb biosbootspecification


```It will probably take me a few minutes with some tools to get the motherboard part number.

[Edit] There is an advisory for this and a suggested solution [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02910174&lang=en&cc=us&taskId=101&prodSeriesId=4194641&prodTypeId=15351](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02910174&lang=en&cc=us&taskId=101&prodSeriesId=4194641&prodTypeId=15351) 
However my server is not running Windows.  The suggested file for RHEL is[I] CP015807.scexe
[/I]```
When I run that file it gives this error:
./CP015807.scexe: 153: ./CP015807.scexe: pushd: not found
./CP015807.scexe: 158: ./CP015807.scexe: popd: not found
./ccissflash: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

```
wolf@LTS-TEST-01:~/hp$ locate libstdc++.so.6
/usr/lib/x86_64-linux-gnu/libstdc++.so.6
/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.17

```

---

### Post by saphil on 2012-08-28
One possible solution I am pursuing is to download the firmware bootable update disc from HP and use it to get the systems to a place where they can see over 2.2TB drives.

---

### Post by saphil on 2012-09-04
The bootable firmware disk booted but the gui-based updater failed.  I got a centos live disk and flashed the bios through that.  I still haven't quite gotten the drive repartitioned.

---

### Post by saphil on 2012-10-02
Still stuck on the sector size.  Can't see 3TB in either Ubuntu, Debian or Windows.

---

### Post by oldfred on 2012-10-03
Is BIOS now show it correctly? Unless BIOS sees it, no operating system will work.

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Similar issue with some USB ports?
USB adapter may show drive as 1/8 size, use SATA port for 4K drives

---

### Post by saphil on 2012-10-03
> **oldfred said:**
> Is BIOS now show it correctly? Unless BIOS sees it, no operating system will work.

None of the new bios setup pages offer me a way to directly edit the drive,  Before I blew away the old GUID partition table, this disk read properly as 3TB on the Windows machine, through USB and eSATA.  I can edit inside fdisk and made the sectors 4k, but there is still work to do on it.

---

### Post by hoek on 2013-07-03
> **saphil said:**
> None of the new bios setup pages offer me a way to directly edit the drive,  Before I blew away the old GUID partition table, this disk read properly as 3TB on the Windows machine, through USB and eSATA.  I can edit inside fdisk and made the sectors 4k, but there is still work to do on it.

The difference is the full drive is supported through USB and eSATA but, as a SATA drive it is not supported. If not supported in BIOS it wont be supported in the OS. At least this is my guess.

---

