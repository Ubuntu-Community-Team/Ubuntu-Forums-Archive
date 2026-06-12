---
title: "Boot Problems after Dual-Boot Hard drive clone"
date: 2015-09-18
forum: Windows
---

### Post by leonard032 on 2015-09-18
So, about two weeks ago my Windows XP installation (it's for my games :D) stopped working right. After much headache I managed to figure out it had something the hard drive. Turns out the drive was failing. [This thread]("http://ubuntuforums.org/showthread.php?t=2293370"), which I posted earlier, helped me clone to a new drive, however I did run into some problems along the way, since the new drive was smaller than the old one. Anyway I finally managed to clone the partitions to a new disc. Now however, I can't get it to boot. I had expected boot problems, but I can't seem to fix them, so now I come here looking for help from the hive mind ;).

What I have done.
[LIST=1]
[*]With the help of some good folks here I figured out it was a hard drive failure, not a virus that was affecting my computer. 
[*]I shrunk the linux partition as small as I could (I didn't have much data on it yet). 
[*]I mounted the windows XP partition and deleted files until it was small enough to fit on the new hard drive along with the linux one. 
[*]I used ntfsresize with --bad-sectors in order to shrink the filesystem. 
[*]I follow [this]("http://ubuntuforums.org/showthread.php?t=1244058") guide to shrink the partition to match. 
[*]I use ddrescue to clone the partition to the new disk. 
[*]I created a new linux swap partition of the same size on the new disk. 
[*]I edited /etc/fstab of the new partition to update the UUIDs. 
[*]I ran e2fsck on the new linux partition. 
[*]Reinstalled/updated grub using [this]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd"). 
[*]I tried to run chkdsk on the new Windows partition using the Recovery Console on the installation CD, but it did seem to do anything. I could not select my Windows installation, and it ran for only a couple seconds. 
[*]The computer would not boot so I tried updating grub again, [this]("http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/") way. It didn't work. 
[*]I tried purging the grub, it didn't work either. 
[*]I tried changing the boot flag from the windows partition to the linux one. That didn't work either. 
[*]Now I'm here. 
[/LIST]

Other information:
[LIST]
[*]I currently cannot mount the new Windows partition, The command ```
sudo mount /dev/sda1 /mnt
``` returns ```
mount: /dev/sda1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
``` 
[*]Looking at it in GParted the partition shows and exclamation point, and "unknown" filesystem. 
[*]fdisk gives me this ```
lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/loop0: 615.1 MiB, 644939776 bytes, 1259648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 111.8 GiB, 120060444672 bytes, 234493056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa164c1df

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 209717247 209715200  100G  7 HPFS/NTFS/exFAT
/dev/sda2       209717248 231346175  21628928 10.3G 83 Linux
/dev/sda3       231346176 234491903   3145728  1.5G 82 Linux swap / Solaris

Disk /dev/sdb: 14.9 GiB, 16025387008 bytes, 31299584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1          32 31299583 31299552 14.9G  c W95 FAT32 (LBA)

Disk /dev/zram0: 1.2 GiB, 1300193280 bytes, 317430 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/zram1: 1.2 GiB, 1300193280 bytes, 317430 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
``` 
[*]While parted give me this ```
lubuntu@lubuntu:~$ sudo parted -l
Model: ATA SAMSUNG SP1213C (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  107GB  107GB   primary                  boot
 2      107GB   118GB  11.1GB  primary  ext4
 3      118GB   120GB  1611MB  primary  linux-swap(v1)


Model: General USB Flash Disk (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        lba


Model: HL-DT-ST DVDRAM GSA-4167B (scsi)
Disk /dev/sr0: 724MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start  End    Size    File system  Name   Flags
 1      2048B  6143B  4096B                Apple
 2      678MB  680MB  2327kB               EFI


Model: Unknown (unknown)
Disk /dev/zram0: 1300MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1300MB  1300MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram1: 1300MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1300MB  1300MB  linux-swap(v1)
``` 
[*]The 16 GB drive is my USB stick.
[*]When I mean "won't boot" it means that I get the good ol' BIOS beep and see the manufacturer pictures. Then the first part of GRUB (I'm guessing?), the blinking cursor at the top of the screen, after a few moment it goes down a couple lines and keeps blinking there.
[*]The linux installation I have is lubuntu 15.04 and is on a 10.31 GB ext4 partition at /dev/sda2.
[*]The Windows is an XP installation on a 100GB ntfs partition at /dev/sda1.
[*]The linux swap is 1.5 GB on /dev/sda3.
[*]In order to do all this I am using my lubuntu 15.04 live CD. 
[/LIST]

I created this new thread because my problem is not really hardware related anymore, I hope that is OK. I do want to be clear that I am thankful for the help TheFu and weatherman2 have already given me.

Thanks!

---

### Post by oldfred on 2015-09-18
Moving to Windows sub forum since Windows issues.
You may get better help in a Windows forum?

Windows has to have boot flag. Grub does not use boot flag to boot Windows or Linux. Grub2's os-prober looks for Windows boot files by name. And NTFS partition must not need chkdsk or have other issues for grub to be able to chain load to Windows.

You probably had old install starting at sector 63, all new installs use sector 2048 for compatibility with new 4K drives and SSDs. That alone will require several runs of chkdsk. And you need boot flag on NTFS partition for chkdsk to see Windows. Also the partition boot sector PBR must have a NTFS signature inside it. That would include reference to ntldr as Windows boot process is MBR -> PBR and then ntldr. Grub skips MBR and chain loads directly to PBR of partition with ntldr.
       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

But if you had bad sectors and even one sector was not cloned correctly you will not have a working system.

Also see if you have a correct PBR. 
       
 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

Testdisk can restore from the backup assuming it is ok, or create a new BS (PBR) that is good enough for XP and then chkdsk can finish working to fully repair it.

Partition boot sector is the first sector of a partition and has a structure like the MBR. It is called PBR or BS boot sector.

---

### Post by leonard032 on 2015-09-20
The backup boot sector is bad as well. I tried to Rebuild BS, it takes a while, and when I come back to it it's just on the main page again.

On the Analyse page, it shows two NTFS partitions, which means an error. I tried a quick search and it didn't come up with any NTFS partitions, just the Linux and swap, so then I did a deep search, which gave me this ```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14596 255 63

The harddisk (120 GB / 111 GiB) seems too small! (< 240 GB / 223 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  HPFS - NTFS          13080  76 53 26134 119 33  209715200
   HPFS - NTFS          13135 225 19 26190  12 62  209715200
   Linux                13214  40 11 25166  94 16  192012288
   HPFS - NTFS          13595  18 56 26649  61 36  209715200
   HPFS - NTFS          14594 254 63 29189 253 62  234468612


```
After hitting continue I am greeted with this ```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14596 255 63
     Partition               Start        End    Size in sectors
 D HPFS - NTFS              0   1  1 14594 254 63  234468612
 D HPFS - NTFS              0  32 33 14596  81 13  234487808
>D Linux                13054  75 14 14400 161 33   21628928
 D Linux Swap           14400 161 34 14596 113 45    3145728
 D Linux Swap           14402   9  8 14596 113 45    3123200


```
I can look at the files in the first NTFS partition, but not the second. However I'm not sure what I should set them all to. I'm guessing I should set the NTFS partition that works to "Primary Bootable" the linux to logical, and the swaps to logical?

---

### Post by oldfred on 2015-09-20
I have not had to use testdisk to restore a partition. It does find just about every version of partitions you ever had on drive. So it finds the older ones. And then you have to select the combination that does not overlap. But not sure if you can just add a missing partition or have to reset all?

But you should not have to restore any partitions, as partition table was correct. You just needed the PBR restored.
Windows also has to total rebuild of PBR. I think this is in Windows 7 or later repair consoles:

 Really using bootsect.exe to restore partition boot sector - PBR
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Bootsect.exe updates the master boot code (BS) for hard disk partitions
in order to switch between BOOTMGR and NTLDR.
You can use this tool to restore the Boot_Sector (BS) on your computer.

   /nt52 Applies the master boot code (BS) that is *compatible* with NTLDR to SYS,
ALL, or <DriveLetter>. The operating system installed on SYS, ALL, or
<DriveLetter> must be older than Windows Vista.

   /mbr Updates the Master Boot Record (MBR) without changing the Partition_table
on sector 0 of the disk that contains the partition specified by SYS, ALL,
or drive letter.

   When used with /nt52 option, the Master Boot Record (MBR)
is *compatible* with operating systems older (XP) than Windows Vista.

   When used with the /nt60 option, the Master Boot Record (MBR) is
*compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by leonard032 on 2015-09-20
I don't have a Windows 7 CD though, so how can I use this? And I thought there was something wrong with the partition table, otherwise parted would know what kind of filesystem the windows partition is.

---

### Post by oldfred on 2015-09-20
When you list partitions it knows that it is NTFS as the MBR partition table has the correct code.
But then in trying to mount it, it finds incorrect data in the PBR or partition boot sector. See Multibooter's site linked above for more detail. Pictures alone just about explain it all.

---

### Post by leonard032 on 2015-09-20
Ok so I don't need to mess around with the partition table.
Forgive me for being stupid but what should I do? TestDisk doesn't seem to work, should I not leave it and see if it gives any errors before Rebuild BS returns to the main menu?
Do I need to somehow download bootsect and run it?

---

### Post by oldfred on 2015-09-20
I think you can download a full install of Windows and use it for 30 days before buying it, it has the recovery tools also.
There are sites that have the Windows 7 repair ISO, but they now charge for it. Not sure if anything else is available. You may try the Windows forums to see.

I would try testdisks rebuild BS, but I do not know why it would take a long time. And you usually have to run chkdsk from a Windows repair after that. Be sure to use correct Windows version. I used a Windows 7 repair CD to run chkdsk on XP. It worked better than XP's chkdsk but then it wanted to boot with bootmgr (Win 7's) not ntldr which is for XP. I think used testdisk to restore backup PBR.

---

### Post by leonard032 on 2015-09-21
OK, I tried Rebuild BS again and watched it the whole time. As soon as it had finished searching all 209715200 sectors it exited immediately without any messages back to the main screen, this one:
```
Disk /dev/sda - 120 GB / 111 GiB - CHS 14596 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0  32 33 13054  75 13  209715200

Boot sector
Status: Bad

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.




>[  Quit  ]  [Rebuild BS]  [  Dump  ]
```
There's another laptop in the house that runs Windows 10, I'm going to see if I can make some sort of recovery CD with that, and then use bootsect.exe.

---

### Post by oldfred on 2015-09-21
I think these are all similar, may show more details with one version or other. Windows 10 should be similar.

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)
Manually create repair flash, shows files & locations
[http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools](http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools)

---

### Post by leonard032 on 2015-09-21
Well that's a pain in the rear: the laptop doesn't have a CD drive, but the desktop can't boot from USB. If I put it on a USB, transfer the USB to another desktop and then burn the files to a CD *there* it should work...
One thing though, the Windows 10 is 64 bit, but the Windows XP is 32, with the recovery CD work right?

---

### Post by oldfred on 2015-09-21
All the recommendations I have seen were to have same 32 or 64 bit version for Windows repairs. I know chkdsk works, not sure about anything else.

But you should have a Windows 10 repair flash drive anyway, so make that.

---

### Post by leonard032 on 2015-09-21
Well, I guess I'm out of options then. Even if I went and found a recovery ISO and downloaded it, who's to say it would even work? And considering how corrupt the filesystem seems to be I'll bet I would keep having problems in the future.
Thanks very much for all your help, I have certainly learned a lot through this.

---

### Post by leonard032 on 2015-09-21
Well, turns out there was a windows 10 cd lying around from upgrading a different computer. I booted from it and tried to run bootsect, this is what I got.
With the command
```
bootsect /nt52 SYS /mbr

The system partition was not found:
The requested system device cannot be found.
```
And then
```
bootsect /nt52 C: /mbr

Target volumes will be updated with NTLDR compatible bootcode.
C: (\\?\Volume{a164c1df-0000-0000-0000-100000000000})

Could not open the volume root directory:
The parameter is incorrect.

\??\PhysicalDrive0

Successfully updated disk bootcode.

Bootcode was successfully updated on at least one volume.
```

I then tried to run chkdsk but it told be it couldn't as chkdsk wasn't supported for RAW and the partition was RAW. It still doesn't boot.

Anything else to try or was that really my last hurrah!

---

### Post by oldfred on 2015-09-21
Is boot flag still on NTFS partition? 
Windows only repairs the NTFS with boot flag.

Perhaps something got fixed and now what does testdisk show?

---

### Post by leonard032 on 2015-09-21
Ok, now I *really* have no idea what's going on. The boot flag is still on that partition, and testdisk shows the same, but some other things are different.
First of all, after that bootsect ran I tried booting again, that didn't work so I wanted to try chkdsk again, the XP one. So I booted that disc and tried to run chkdsk, if I didn't put any parameters in it would say that the disk was ok and didn't need to be checked, if I wanted I could force it with /r. Then it listed a bunch of info about the partition or drive (size stuff), I'm not sure. If I added the /r then it would say "The volume appears to contain one or more unrecoverable problems." and then go on the list the info, which it didn't use to.
I then stumbled on a list of the other commands which were available on the Recovery Console, two of which were "fixboot" and the other "fixmbr". I tried running the "fixboot" first it seemed to work, but said the drive was FAT and then "fixed" the boot sector. I then ran "fixmbr" it first warned that thing were unusual but I told it to go ahead. That didn't fix things.
Then I decided to try running Windows 10 chkdsk. So booted onto that disk and ran chkdsk there, it asked me a coulpe of times if I wanted to change folders into files after uncorrectable errors. I said yes the first time, then no on later times after noticing a large amount of pages of people trying to recover there stuff after chkdsk had converted it into files. Finally it ended asking me if I wanted to change a bunch of clusters into files, I said no as well.
Now I'm booting back on the lubuntu live CD and I seem to have done something. The hard drive partition is now showing up in pcmanfm, but it seems... a little off. The partition is now showing up as FAT16 in GParted. (see attached screenshots)

Have I done something stupid? Or are we progressing?

Edit: Where before I could see my files after doing a scan in testdisk, not it's just a see of red files, unnamable files.

---

### Post by oldfred on 2015-09-21
It should not be FAT and it does not now look like testdisk is finding file names?

You can in disks change partition type. Not sure if Disks is in your flavor, but you should be able to install it. Or you can use command line, you want type 07 for NTFS. Do not format just change partition type.

       change sda1 to type 07 - note spaces and see man sfdisk
sudo sfdisk --change-id /dev/sda 1 07

---

### Post by leonard032 on 2015-09-21
Doesn't change what shows up GParted.

---

### Post by oldfred on 2015-09-21
What does this show?
sudo parted -l

I do not like that gparted says file size is 99.9 GB empty and it is a 100GB partition??

---

### Post by leonard032 on 2015-09-21
```
lubuntu@lubuntu:~$ sudo parted -l
Model: ATA SAMSUNG SP1213C (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  107GB  107GB   primary  fat16           boot
 2      107GB   118GB  11.1GB  primary  ext4
 3      118GB   120GB  1611MB  primary  linux-swap(v1)


Model: HL-DT-ST DVDRAM GSA-4167B (scsi)
Disk /dev/sr0: 724MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start  End    Size    File system  Name   Flags
 1      2048B  6143B  4096B                Apple
 2      678MB  680MB  2327kB               EFI


Model: Unknown (unknown)
Disk /dev/zram0: 1300MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1300MB  1300MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram1: 1300MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1300MB  1300MB  linux-swap(v1)
```

And for the heck of it I tried fdisk as well.
```
lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/loop0: 615.1 MiB, 644939776 bytes, 1259648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 111.8 GiB, 120060444672 bytes, 234493056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa164c1df

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 209717247 209715200  100G  7 HPFS/NTFS/exFAT
/dev/sda2       209717248 231346175  21628928 10.3G 83 Linux
/dev/sda3       231346176 234491903   3145728  1.5G 82 Linux swap / Solaris
```

That it says 99.9 is empty disturbes me too. I also find it weird, if you look in the second screen shot above the "107 GB" drive has a size of only 10MB?

---

### Post by oldfred on 2015-09-21
Now I am confused. 
Parted says FAT16 and fdisk says NTFS?
I thought they both read partition table and should be identical, just in slightly different formats.

You have the Linux partition at about 10GB & NTFS at 100GB. That seems consistent.

---

### Post by leonard032 on 2015-09-21
If you look at the code in the first post it's the same, except parted didn't know the filesystem, now it "knows" a wrong one. :/
Any other ideas or shall I start the reinstall?

---

### Post by oldfred on 2015-09-21
I guess reinstall is best option.

---

### Post by leonard032 on 2015-09-22
We certainly gave it the old college try! Maybe somebody in the future will gain something from it.

---

