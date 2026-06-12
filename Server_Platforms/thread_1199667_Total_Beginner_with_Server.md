---
title: "Total Beginner with Server"
date: 2009-06-29
forum: Server Platforms
---

### Post by Ed Case on 2009-06-29
Hello all, great support here (I'll need it). I have obtained an old Compac server and tried to load 9.04 without success, it reports CD Rom not found. I now have ver 6.06 installed and it worked fine. The first problem is, what command line do I use to access the other 3 SCSI drives on the server. For info, the server will not support windows and I cannot install Gnome. Thanks in advance,

Ed Case

---

### Post by cmnorton on 2009-06-30
Sounds like you need /etc/fstab entries for these drives.

What's the output of df?

---

### Post by mwcrowley on 2009-06-30
what's the output of sudo fdisk -l
the "-l" is a dash lowercase L

---

### Post by Ed Case on 2009-07-01
Thanks guy's, I'll try those soon. I got Internet connection up and running and downloaded Samba for file sharing and workgroup, but the snb.conf file is empty. Grrrr
:mad:

---

### Post by Ed Case on 2009-07-02
Thanks for the patience guys. Internet fixed, Samba getting close. I did as you both suggested and yes CMN, these are shown in fdisk, but only one shown in "df". They do not appear in "/etc/fstab". How can I add them please?

---

### Post by decoherence on 2009-07-02
> **Ed Case said:**
> Thanks for the patience guys. Internet fixed, Samba getting close. I did as you both suggested and yes CMN, these are shown in fdisk, but only one shown in "df". They do not appear in "/etc/fstab". How can I add them please?

The specific lines to add to /etc/fstab depend on the output of the 'sudo fdisk -l' command.

You can do 'sudo fdisk -l > fdiskOutput.txt' which will put the output of the command in the file fdiskOutput.txt... if you can then move that file to a system with a GUI, it might make it easier to post the output here so we can make up a sane entry.

In any case, to edit /etc/fstab you'll do

> sudo nano /etc/fstab

As you'll see, it's a simple text file that can be edited with any reasonable text editor. Adding things is just a matter of appending lines to the end. For instance

> /dev/sdb1 /media/windows  ntfs iocharset=utf8,umask=000    0  0 

would be a valid example, though the values may not be the same for you. "/dev/sdb1" is a device name which you'll get from fdisk -l. "/media/windows" is where, on the filesystem, you want the partition to be accessible from (this is ultimately up to you.) "ntfs" specifies a Microsoft NTFS type filesystem... you'll get filesystem type information from fdisk -l as well. The rest of the command is tweaks for NTFS. If you aren't mounting NTFS, you'll want something different.

---

### Post by scorp123 on 2009-07-02
> **Ed Case said:**
> ... and downloaded Samba for file sharing and workgroup I hope you used the packet manager?

As for the empty smb.conf ... Maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Just ignore the LDAP bits if you're not interested in that and all the rest that doesn't concern you.

---

### Post by Ed Case on 2009-07-02
Thanks for the information both, Samba was fine after a server restart. As for the rest, I will get the 'fdisk' info to you ASAP, I may have to write it out by hand, but you never know. The server is Ubuntu only and will not support graphics,

Thank you

---

### Post by decoherence on 2009-07-02
I just thought of something....

Is set nowrap on or off by default with nano? I can never remember. If nano tries wrapping your lines, it will screw things up royally when you edit /etc/fstab.

Before you edit /etc/fstab, edit /etc/nanorc and check for the following lines

```
## Don't wrap text at all.
# set nowrap
```

Change it to

```
## Don't wrap text at all.
set nowrap
```

(just get rid of the number sign in front of 'set', if it isn't done already)

(believe it or not, this is easier than explaining vi)

(we really need that [PolicyKit integration]("http://ubuntuforums.org/showthread.php?t=1002627&highlight=policykit")...)

---

### Post by Ed Case on 2009-07-02
Thanks yet again guy's, I tried the code to save output to a file, but everytime I got a "permission denied" error even after changing the nano code. Anyway, I have written out an "fdisk -l" section to give you an idea, this is for "SDC"

Disk: /dev/sdc: 4293Mg
255 heads, 63 sectors per track, 522 cylinders, units = cylinders of 16065*512 = 8225280

Device boot

/dev/sdc3 start 1, end 1, 8001 blocks, ID12 System: Compaq Diagnostics

Others are similar but System is Linux

Thanks, hope this makes sense to you all,

Regards

---

### Post by Ed Case on 2009-07-03
Ok guys, I really appreciate your help. I have now got the fdisk -l to save, so here it is:-

Disk /dev/sda: 4293 MB, 4293632000 bytes 255 heads, 63 sectors/track, 522 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes     Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *           1         496     3984088+          83                    Linux 
/dev/sda2             497         522      208845              5                    Extended
/dev/sda5             497         522      208813+          82                    Linux swap / Solaris

Disk

/dev/sdb (Sun disk label): 255 heads, 63 sectors, 520 cylinders
Units = cylinders of 16065 * 512 bytes

   
Device Flag      Start                End                     Blocks                                  Id   System

/dev/sdb1             0                514                    4128705   83                           Linux native

/dev/sdb2  u        514              520                     48195     82                           Linux swap
/dev/sdb3             0                520                     4176900    5
  
Whole disk
Disk /dev/sdb1 (Sun disk label): 255 heads, 63 sectors, 520 cylinders
Units = cylinders of 16065 * 512 bytes

      Device           Flag     Start       End    Blocks   Id      System

/dev/sdb1p1                   0       514     4128705   83    Linux native

/dev/sdb1p2  u             514      520     48195     82     Linux swap

/dev/sdb1p3                  0       520   4176900    5       Whole disk



Disk /dev/sdb3 (Sun disk label): 255 heads, 63 sectors, 520 cylinders
Units = cylinders of 16065 * 512 bytes

    Device Flag       Start       End     Blocks    Id          System

/dev/sdb3p1           0       514   4128705    83      Linux native

/dev/sdb3p2  u     14         520    48195     82      Linux swap

/dev/sdb3p3             0       520   4176900    5      Whole disk



Disk /dev/sdc: 4293 MB, 4293632000 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes   
Device Boot      Start         End      Blocks   Id      System
/dev/sdc3               1           1        8001     12      Compaq diagnostics

Disk /dev/sdd: 4293 MB, 4293632000 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   
Device Boot      Start         End      Blocks   Id  System
/dev/sdd3               1           1        8001   12  Compaq diagnostics


Hope you get some clues from this!

---

### Post by decoherence on 2009-07-03
From the looks of things, you want to mount /dev/sdb1.

First try this...

```
sudo mount /dev/sdb1 /mnt
ls /mnt
```

Hopefully you'll see the appropriate list of files. If that works, the next thing to do is create a mount point... this will basically be the 'name' of your disk as it appears in Ubuntu and it can be whatever you like. For this example, I'll pretend you want to call your partition "Bob." As root, do ```
mkdir /media/Bob
``` (you can actually put it wherever you like, but under '/media' is conventional) and put the following in your /etc/fstab.

```

/dev/sdb1    /media/Bob    ext3    defaults    0    0
```

That's a very generic mount... it might need to be tweaked, but it's something to try.

Finally, see if it worked by unmounting sdb1 from /mnt, reloading /etc/fstab and checking that sdb1 now mounts under /media/Bob

```
sudo umount /mnt
sudo mount -a
ls /media/Bob

```

You should see the same list of files as earlier.

Let us know how it goes...

---

### Post by windependence on 2009-07-03
Before you get too far into this you should know that on most of those old Compaqs, you need a Compaq Smart Start disk to configure the machine and RAID devices. Most likely the reason it has three drives is to set up a RAID 5 array. You boot from the disk, and from there you set up the RAID array, and other bios options including support for whatever OS you are using. Linux will then see the RAID array as just one disk and you can go from there. Your storage capacity will be the size of two disks since one gets used for parity in RAID5.

If you tell me what model Compaq you have, I can tell you more about it and possibly let you know what version of Smart Start to use.

-Tim

---

### Post by Ed Case on 2009-07-03
Thanks windependance. The server is an OLD, maybe 1990's, ProLiant 3000 with 4* 4.3Gb SCSI drives with onboard controller and 128Mg RAM. It was obtained as a project and so no Compaq disks were available. Any advice greatfully received.

---

### Post by Ed Case on 2009-07-04
Ok guys, I think I have had a success with sdb. It was not formatted apparently. I made the mistake of formatting before partitioning, but it seems Ok now. Now I need to know how SMALL the partitions can be, so that maximum space is available for storage? Thanks again

---

### Post by windependence on 2009-07-05
> **Ed Case said:**
> Thanks windependance. The server is an OLD, maybe 1990's, ProLiant 3000 with 4* 4.3Gb SCSI drives with onboard controller and 128Mg RAM. It was obtained as a project and so no Compaq disks were available. Any advice greatfully received.

Ed, I have the exact same server here. You will need Smart Start 5.5. This link is extrememly hard to locate, but HP still has the download. 

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=18964&prodSeriesId=345557&prodNameId=344318&swEnvOID=210&swLang=8&mode=2&taskId=135&swItem=MTX-597d7cb6b45d493285e27c1412](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=18964&prodSeriesId=345557&prodNameId=344318&swEnvOID=210&swLang=8&mode=2&taskId=135&swItem=MTX-597d7cb6b45d493285e27c1412)

The real download link is [ftp://ftp.hp.com/pub/products/servers/supportsoftware/ZIP/smartstart-5.50-0.zip](ftp://ftp.hp.com/pub/products/servers/supportsoftware/ZIP/smartstart-5.50-0.zip) if you want to use something like wget to download it.

All SmartStart versions are here:  [ftp://ftp.hp.com/pub/products/servers/supportsoftware/ZIP/](ftp://ftp.hp.com/pub/products/servers/supportsoftware/ZIP/)

Your server is not an old relic, but a viable box for some tasks like web serving. I have parts and drives if you need them. I think I have some either 9.1GB or 18.2 GB drives that will work in that server if you want them.

-Tim

---

### Post by Ed Case on 2009-07-05
Thanks windependance, I just dowloaded the ISO on my WinXP machine, just need to image it to a cd now. Regards the spare parts, I am in the UK so postage will be a little pricey (maybe). I need some more memory, there is only 128 in it, can you tell me the exact memory type as ther is only a compaq label on the blocks, thanks again for all the advice and help,

Ed

---

### Post by windependence on 2009-07-06
It's probably 72 pin SDRAM, could be EDO I have to check. I have at least 1GB in that machine, but it's like 32 SIMMS. ;-)

If you are interested, the memory isn't worth much, and I can send it USPS if you are in the UK rather inexpensively. You can PM me if you want and I'll give you my e-mail address. 

Use the SmartStart utility by booting from the disk, and then configure your BIOS options first. Don't worry about the version of Linux that you can set in the BIOS, it will even work set to Solaris, or HPUX. The big advantage is you can finally set up your RAID array correctly with the disk.

-Tim

---

