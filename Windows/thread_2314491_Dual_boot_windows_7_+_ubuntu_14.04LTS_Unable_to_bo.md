---
title: "Dual boot: windows 7 + ubuntu 14.04LTS: Unable to boot to Windows now"
date: 2016-02-21
forum: Windows
---

### Post by anupam6 on 2016-02-21
Hello ,
My machine is Lenevo ThinkPad T530- i7 8GBRAM- UEFI dual support BIOS.
Before installing ubuntu on separate partition, my disk status was:
/dev/sda1: C drive : Windows 7  BOOT NTFS 75GB Encrypted - Primary 
/dev/sda5: D drive : NTFS 25GB Encrypted - Logical
/dev/sda6: F drive : NTFS 70GB - Logical
Free space 70GB
To install ubuntu, added 3 partitions from unallocated space:
/dev/sda7: /root : ext4 20GB
/dev/sda8: swap: 4GB
/dev/sda9: /home: ext4 45GB

So, I Installed ubuntu on /dev/sda7 on top of windows which was on /dev/sda1.
At time of installation, ubuntu was not able to detect Windows and I continued to install ubuntu on these 3 new partitions.
Now, I dont see any grub loader at startup and it directly boots into ubuntu.
I tried to enable dual boot for windows which resides on C drive (/dev/sda1) by fixing using Boot Repair from ubuntu Live CD. But even that didnt help to get me see grub boot loader at startup itself.
This is text of Boot Repair summary : [http://paste.ubuntu.com/15160659/](http://paste.ubuntu.com/15160659/)

below is some text from this summary: It says unable to mount /dev/sda1 Is it because its encrypted? PLEASE HELP!!
```
============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.4 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
..
...
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   157,288,447   157,286,400   7 NTFS / exFAT / HPFS
/dev/sda2         157,292,542   973,137,374   815,844,833   f W95 Extended (LBA)
/dev/sda5         157,292,544   681,605,819   524,313,276   7 NTFS / exFAT / HPFS
/dev/sda6         681,607,168   828,407,789   146,800,622   7 NTFS / exFAT / HPFS
/dev/sda7         828,409,856   870,353,504    41,943,649  83 Linux
/dev/sda8         870,354,944   878,755,499     8,400,556  82 Linux swap / Solaris
/dev/sda9         878,755,840   973,137,374    94,381,535  83 Linux

```


Please Help to enable boot in Windows 7 as well.
THis is my office laptop and so very scared now :(
Thanks,

Tags: dual boot windows7, ubuntu, encrypted windows partition, mount failure, unknown type, windows ubuntu dual boot grub

---

### Post by yancek on 2016-02-21
For some reason, the windows partition was not detected by Grub.  Boot Ubuntu, open a terminal and run these two commands consecutively:

> sudo os-prober
sudo update-grub

Watch the output for a windows entry.  I don't know if this will work if your windows partiton is encrypted but you can try it.

---

### Post by anupam6 on 2016-02-21
> **yancek said:**
> For some reason, the windows partition was not detected by Grub.  Boot Ubuntu, open a terminal and run these two commands consecutively:



Watch the output for a windows entry.  I don't know if this will work if your windows partiton is encrypted but you can try it.

sudo os-prober 
This command listed only ubuntu os. Not the windows which I wanted to see.
Any further help?

---

### Post by oldfred on 2016-02-21
Encrypted systems often have an encrypted boot, not the standard Windows boot. 
So you should not dual boot on same drive, or at minimum need grub's boot files on another drive or flash drive.

Since Windows is encrypted grub will never see the Windows install. And Linux encryption is different that Windows encryption so not compatible.

Hope you have data well backed up.

Boot-Repair may have backed up MBR, and you may be able to restore it to boot Windows. try that first.
Some Windows encryption tools have ways to recover MBR, but you need their live repair tools. Best to check on their forum.

Did you have permission from your company to install Ubuntu? Some companies take security very strongly and do not like users modifying system.

---

### Post by anupam6 on 2016-02-21
So, is there way to boot into Windows at all? Ex even if I uninstall ubuntu now, can I boot into Windows then? assuming c drive was encrypted.

---

### Post by oldfred on 2016-02-22
Windows standard repair fixMBR or Boot-Repairs standard Windows fix uses Syslinux which works just like Windows own standard MBR, will boot un-encrypted Windows.

No idea if it works with encrypted Windows or even know what type of encryption you have. 

One previous user did install his grub boot loader to a flash drive to boot Ubuntu, but kept Windows encrypted boot loader.
One user was able to find instructions on the encryption vendors site on restoring the MBR to boot encrypted Windows again, not a Linux issue.

Moving thread to Windows sub-forum.

---

