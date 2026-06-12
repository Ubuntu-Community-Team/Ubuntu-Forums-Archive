---
title: "Need to resize harddisk"
date: 2019-01-29
forum: Virtualisation
---

### Post by joshi82 on 2019-01-29
Greetings,

I have a virtual server up and running on a local ESXi installation, hosting our emails. The details are as follows:

```
root@mailsrv:~# lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0  2,2T  0 disk
&#9500;&#9472;sda1   8:1    0  487M  0 part /boot
&#9500;&#9472;sda2   8:2    0  3,7G  0 part [SWAP]
&#9500;&#9472;sda3   8:3    0  3,7G  0 part /
&#9500;&#9472;sda4   8:4    0    1K  0 part
&#9500;&#9472;sda5   8:5    0  3,7G  0 part /usr
&#9500;&#9472;sda6   8:6    0  1,9G  0 part /home
&#9500;&#9472;sda7   8:7    0  7,5G  0 part /tmp
&#9500;&#9472;sda8   8:8    0 14,9G  0 part /var
&#9492;&#9472;sda9   8:9    0  1,9T  0 part /srv
sr0     11:0    1 1024M  0 rom


root@mailsrv:~# pydf
Filesystem  Size  Used Avail Use%                                                               Mounted on
/dev/sda3  3691M 1010M 2475M 27.4 [################...........................................] /
/dev/sda1   456M  114M  318M 25.0 [###############............................................] /boot
/dev/sda6  1844M 2904k 1730M  0.2 [...........................................................] /home
/dev/sda9  1932G 1809G   36G 93.6 [#######################################################....] /srv
/dev/sda7  7380M  601M 6382M  8.1 [#####......................................................] /tmp
/dev/sda5  3690M 1999M 1484M 54.2 [################################...........................] /usr
/dev/sda8    15G 6400M 7711M 43.0 [#########################..................................] /var


root@mailsrv:~# fdisk -l
Medium /dev/sda: 2,2 TiB, 2362232012800 Bytes, 4613734400 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes
Typ der Medienbezeichnung: dos
Medienkennung: 0x581f6499


Gerät      Boot    Start       Ende   Sektoren Größe Id Typ
/dev/sda1           2048     999423     997376  487M 83 Linux
/dev/sda2         999424    8812543    7813120  3,7G 82 Linux Swap / Solaris
/dev/sda3        8812544   16625663    7813120  3,7G 83 Linux
/dev/sda4       16627710 4192206847 4175579138    2T  5 Erweiterte
/dev/sda5       16627712   24438783    7811072  3,7G 83 Linux
/dev/sda6       24440832   28344319    3903488  1,9G 83 Linux
/dev/sda7       28346368   43968511   15622144  7,5G 83 Linux
/dev/sda8       43970560   75218943   31248384 14,9G 83 Linux
/dev/sda9       75220992 4192206847 4116985856  1,9T 83 Linux

root@mailsrv:~# parted
GNU Parted 3.2
/dev/sda wird verwendet
Willkommen zu GNU Parted! Rufen Sie »help« auf, um eine Liste der verfügbaren Befehle zu erhalten.
(parted) print free
Modell: VMware Virtual disk (scsi)
Festplatte  /dev/sda:  2362GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
Disk-Flags:


Nummer  Anfang  Ende    Größe   Typ       Dateisystem     Flags
        32,3kB  1049kB  1016kB            Freier Platz
 1      1049kB  512MB   511MB   primary   ext2
 2      512MB   4512MB  4000MB  primary   linux-swap(v1)
 3      4512MB  8512MB  4000MB  primary   ext4
        8512MB  8513MB  1048kB            Freier Platz
 4      8513MB  2146GB  2138GB  extended
 5      8513MB  12,5GB  3999MB  logical   ext4
 6      12,5GB  14,5GB  1999MB  logical   ext4
 7      14,5GB  22,5GB  7999MB  logical   ext4
        22,5GB  22,5GB  713kB             Freier Platz
 8      22,5GB  38,5GB  16,0GB  logical   ext4
 9      38,5GB  2146GB  2108GB  logical   ext4
        2146GB  2362GB  216GB             Freier Platz

```

The 36GB free space are causing me serious headache, so I wanted to extend the partition. First I extended the vmdk within ESXi, and then I wanted to extend the partition within linux, which failed (lack of knowledge from my side). Then I booted into a partedmagic live cd and wanted to extend the partition, with failed too. I lost the screenshots, but it was related to the disk size, because MBR layouts cannot handle more than 2TB. Apparently moving to GPT would reinitialize the disk, which is certainly not
what I want.

My questions now are:
- how can I extend the partition to it´s maximum logically possible size, without utilizing the live disc (interim fix)?
- how can I migrate to mbr without messing around too heavily with the whole system?

I woud like to avoid mounting another new virtual GPT disk into srv, because that means 1. I need to migrate all the data and 2. I have loads of allocated space that is unused, which is less than optimal.

Any help is highly appreciated. If you have another way for me to go I am very open for it.

Thanks in advance
Joshi

---

### Post by ajgreeny on 2019-01-29
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by tension_ on 2019-01-29
Hi [COLOR=#000000]joshi82 your lucky one /srv partition is last one :)[/COLOR]

[COLOR=#000000]I will make snapshot and after that something like this:

[/COLOR]
[LIST=1]
[*][COLOR=#000000]sudo fdisk /dev/sda9[/COLOR]
[*]m to show menu
[*]p to show partition table
[*]d delete partition number 9
[*]n to create new one from this sectors 75220992
[*]enter to the last one
[*]w to write and exit disk
[*]sudo resize2fs /dev/sda9 to extend disk
[/LIST]

Hope this helps you.

---

### Post by oldfred on 2019-01-29
Never used virtualization.

But you do have to use gpt for drives over 2.2TiB.
No idea if this works or not for a virtual install:
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by TheFu on 2019-01-29
A quick fix would be to run **tune2fs** and release the 5% reserved blocks for the partition.  I always have to check the manpage to get the right option.  Don't do it on OS partitions, but for all others, I can't see why not.  Especially data partitions.```


       -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by  privileged  processes.   Reserving some number of filesystem
              blocks for use by privileged processes is done to avoid filesys-
              tem  fragmentation,  and  to  allow system daemons, such as sys-
              logd(8), to continue to function correctly after  non-privileged
              processes  are  prevented  from writing to the filesystem.  Nor-
              mally, the default percentage of reserved blocks is 5%.
```


Virtualization doesn't matter for disk management inside the VM. It all works the same.  The stuff outside the VM is like swapping HDDs.

GPT is necessary to access any storage on a HDD over 2.2TB, but you can use MBR to access it upto that limit.  Also, GPT doesn't have extended partitions which lock all the partitions numbered over 5. In GPT, all partitions are primary with not real-world limit on how many you can have.

If I had this issue, I'd add a fresh vHDD just for the problem partition, boot from a liveCDrom, move all the data over, then fix the fstab to point to the new location and remove the old location.  With all the partitions you are using, perhaps using LVM would solve many issues. Then you could have 2 partitions, but 15 LVs (think of them as logical partitions), which can be resized up/down as needed.  Down resizing is only possible with EXT4 and from a liveBootCD, but resizing larger can be done while the system runs. Zero downtime, about 10 seconds for the command.  Just need to have space unallocated in the PE and VG.  You can also use LVM to span disks, if needed or to move data from 1 disk to another.  If you had used LVM on the existing disk, moving almost everything to a new vHDD wouldn't be hard or need downtime.

Then I'd create a new vHDD with GPT sized however I needed it.  Then repartition as necessary for the OS, but use LVM for the non-OS stuff. 

And don't forget that you can move data using the normal backup/restore techniques.  I assume you aren't using ESX tools for backups when treating a VM like a physical machine is much more efficient. I made the mistake of trying to use VM tools to do backups for 3 yrs.  What a waste of time.  Now our backups are much more efficient, faster, use less space and are more secure.

---

