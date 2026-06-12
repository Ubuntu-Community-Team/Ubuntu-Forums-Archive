---
title: "Is the Linux kernel interacting with the SSD RAID0 cache?"
date: 2014-01-13
forum: Ubuntu, Linux and OS Chat
---

### Post by bartfife on 2014-01-13
[SIZE=3][FONT=arial]I have successfully completing a dual-boot configuration of Ubuntu 13.10 and Windows 8.1 on a Dell XPS8700 with SSD caching of a HDD. The following article [http://ubuntuone.com/2MQe9Wi5POr46RIqVVdZVm](http://ubuntuone.com/2MQe9Wi5POr46RIqVVdZVm) explains the origin of the following unresolved questions...[/FONT][/SIZE]

[SIZE=3][FONT=arial]After reading the IRST Linux Software Users Manual[[SUP]1[/SUP]]("http://ubuntuforums.org/#sdfootnote1sym"),I concluded the following:[/FONT][/SIZE]

[LIST]
[*][COLOR=#000000][FONT=Liberation Serif][SIZE=3]The    [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]Ubuntu    13.10 [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]kernel    [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]is    based on v3.11.3 upstream Linux kernel that [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]provides    RAID level support. The [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]mdadm    utility 3.0 [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]support[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]s[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]    the Intel Matrix Storage Manager metadata format [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]for[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]    RAID 0, RAID 1, RAID 10, and RAID 5.[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Liberation Serif][SIZE=3]To    use the RAID features in mdadm, set up the RAID volume using the    Intel Matrix Storage Manager option ROM. To enter the option ROM    user interface, click [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Liberation Serif][SIZE=3]CTRL[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Liberation Serif][SIZE=3]+[/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Liberation Serif][SIZE=3]I    [/SIZE][/FONT][/COLOR]**[COLOR=#000000][FONT=Liberation Serif][SIZE=3]when    prompted during boot.[/SIZE][/FONT][/COLOR]
[*]    [COLOR=#000000][FONT=Liberation Serif][SIZE=3]Mdadm    supports the Intel Matrix Storage Manager (IMSM) meta data format    when specified with the IMSM meta data option. [/SIZE][/FONT][/COLOR]
[/LIST]

[SIZE=3][FONT=arial]I didn't understand the 'IMSM meta data option' in the third point above.
[/FONT][/SIZE]
[SIZE=3][FONT=arial]I decided to try leaving SSD caching enabled, install mdadm, and then see if the LiveCD Ubuntu installation could 'see' the HDD in the second 'Installation Type' screen. This was *unsuccessful*.
 
[/FONT][/SIZE][SIZE=3][FONT=arial]I assumed the LiveCD Ubuntu kernel couldn't see the HDD because the SSD was acting as a 'gateway'. But since mdadm had been installed, why was the kernel unable to interpret the IMSM meta data?
[/FONT][/SIZE]
[SIZE=3][FONT=arial]From a LiveCD Terminal session I wanted to see if the RAID configuration file was aware of the SSD RAID0(Cache). But based on the blank “Personalities” message in the attached photo (NORAID.jpg), I assume the SSDRaid0 configuration is NOT even visible to mdadm; OR …?

[/FONT][/SIZE][ATTACH=CONFIG]249476[/ATTACH][SIZE=3][FONT=arial]
[/FONT][/SIZE]

[SIZE=3][FONT=arial]So, I got round this problem as described in [http://ubuntuone.com/2MQe9Wi5POr46RIqVVdZVm](http://ubuntuone.com/2MQe9Wi5POr46RIqVVdZVm). 
[/FONT][/SIZE]
[SIZE=3][FONT=arial]But this leaves a couple of unanswered questions:[/FONT][/SIZE]


[LIST=1]
[*][SIZE=3][FONT=arial]Why can the HDD instance of the Linux kernel interact with the HDD when the SSD Raid0 (cache) is enabled, but the LiveCD Ubuntu installation process could not?[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Is the HDD instance of the Linux kernel communicating directly with the HDD and ignoring the SSD cache?[/FONT][/SIZE]
[/LIST]
[SIZE=3][FONT=arial][1]("http://ubuntuforums.org/#sdfootnote1anc")[http://www.intel.com/support/chipsets/rste/sb/CS-033622.htm](http://www.intel.com/support/chipsets/rste/sb/CS-033622.htm)[/FONT][/SIZE]

---

### Post by bartfife on 2014-01-21
I have included below the section of the dmesg log that refers to the disk configuration. At line 0.885877 you can see the 32gb SSD that I wondered if it was being used. Can I infer that the message on line  0.886941,  sdb: unknown partition table, means the operating system is going to ignore the SSD?

 ```
  0.521888] ahci 0000:00:1f.2: version 3.0[    0.521995] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    0.522051] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x23 impl RAID mode
[    0.522053] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.522059] ahci 0000:00:1f.2: setting latency timer to 64
[    0.527736] r8169 0000:03:00.0: irq 47 for MSI/MSI-X
[    0.527895] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90000048000, f8:b1:56:b2:d2:17, XID 0c000800 IRQ 47
[    0.527898] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.535648] scsi0 : ahci
[    0.535705] scsi1 : ahci
[    0.535747] scsi2 : ahci
[    0.535790] scsi3 : ahci
[    0.535830] scsi4 : ahci
[    0.535871] scsi5 : ahci
[    0.535938] ata1: SATA max UDMA/133 abar m2048@0xf7316000 port 0xf7316100 irq 46
[    0.535940] ata2: SATA max UDMA/133 abar m2048@0xf7316000 port 0xf7316180 irq 46
[    0.535941] ata3: DUMMY
[    0.535941] ata4: DUMMY
[    0.535942] ata5: DUMMY
[    0.535944] ata6: SATA max UDMA/133 abar m2048@0xf7316000 port 0xf7316380 irq 46
[    0.559307]    avx       : 34066.000 MB/sec
[    0.560537] device-mapper: dm-raid45: initialized v0.2594b
[    0.775479] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.855516] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.855534] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.855549] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.856543] ata1.00: ATA-9: ST2000DM001-1CH164, CC27, max UDMA/133
[    0.856546] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.857625] ata1.00: configured for UDMA/133
[    0.857771] scsi 0:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    0.857888] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    0.857890] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    0.857900] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.858014] sd 0:0:0:0: [sda] Write Protect is off
[    0.858017] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.858119] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.863688] ata2.00: ATAPI: HL-DT-ST DVDRW/BDROM CH20N, A201, max UDMA/133
[    0.867601] ata2.00: configured for UDMA/133
[    0.876675] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRWBD CH20N    A201 PQ: 0 ANSI: 5
[    0.881260] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.881263] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.881265] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.881472] ata6.00: ATA-8: LITEONIT LMT-32L3M mSATA 32GB, LWDA, max UDMA/133
[    0.881474] ata6.00: 62533296 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.881864] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.881866] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.881867] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.882090] ata6.00: configured for UDMA/133
[    0.885582] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.885584] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.885686] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.885730] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.885877] scsi 5:0:0:0: Direct-Access     ATA      LITEONIT LMT-32L LWDA PQ: 0 ANSI: 5
[    0.885965] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    0.885980] sd 5:0:0:0: [sdb] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    0.886142] sd 5:0:0:0: [sdb] Write Protect is off
[    0.886145] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.886204] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.886941]  sdb: unknown partition table
[    0.887215] sd 5:0:0:0: [sdb] Attached SCSI disk
[    0.904524] GPT:Primary header thinks Alt. header is not at the end of the disk.
[    0.904526] GPT:3907022632 != 3907029167
[    0.904527] GPT:Alternate GPT header not at the end of the disk.
[    0.904528] GPT:3907022632 != 3907029167
[    0.904529] GPT: Use GNU Parted to correct GPT errors.
[    0.904539]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sda10
[    0.905659] sd 0:0:0:0: [sda] Attached SCSI disk
```

---

### Post by oldfred on 2014-01-21
The Intel SRT uses RAID somehow. It does not seem to be any standard RAID.

Uses remove RAID meta-data from hard drive & SSD and install Ubuntu. You can then re-implement Intel SRT if desired. Some have installed to hard drive, some install to SSD, and a few with larger SSDs like yours have found the SRT only uses part of SSD, and have installed / into SSD and restored SRT.
Since Intel SRT, install seems to be similar regardless of computer brand. But other features may make a difference. 
What computer, chip & video do you have?

          Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by bartfife on 2014-01-21
Thank you, 'oldfred', for your answer.

The system is a Dell XPS8700 with Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz (fam: 06, model: 3c, stepping: 03); 16gb RAM, and an NVIDIA GT650 Ti video card. 

I have been successful installing Ubuntu 13.10 on the HDD alongside Windows 8.1. To do this I performed the steps at the end of this reply, which didn't involve removing any RAID metadata because I was not planning on using the SSD for Ubuntu.

What puzzled me was an apparent inconsistency between how the LiveCD Ubuntu install required the BIOS SATA setting to be changed to AHCI, but after the installation of Ubuntu on the HDD, Ubuntu can boot with the BIOS SATA set to RAID. In fact, I was worried that Ubuntu may damage the RAID metadata on the SSD.

Based on my very limited understanding of the kernel output in dmesg, it appears /dev/sdb/ is being ignored. Also, the disk configuration only shows sda:

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda8        30G  4.7G   24G  17% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.9G  4.0K  7.9G   1% /dev
tmpfs           1.6G  1.2M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.9G  712K  7.9G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda10      853G  1.1G  809G   1% /home
/dev/sda1       496M   54M  443M  11% /boot/efi

```

So it appears when Ubuntu boots from my system it ignores the BIOS SATA set to RAID.  That's fine by me, because I presume that means the RAID metadata on the SSD won't be damaged. Do you agree with this assessment?

That leaves me with 1 question. Why did the Ubuntu LiveCD install process need BIOS SATA set to AHCI?


_Steps to install Ubunut 13.10 alongside Windows 8.1 _

[COLOR=#222222][FONT=arial]UEFI-Secure-ONchanged to UEFI-Secure-OFF.[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]IRSTacceleration of HDD turned off.[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]SATAchanged from RAID to AHCI.[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]BIOSboot sequence changed to:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]1.Optical Disk Drive[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]2.UEFI-OS[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]3.Windows Boot Manager[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]The Ubuntu 13.10 installation: (although all the Windows partitions were on /dev/sda, the installation ignored them)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-installed /dev/sda8.../[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-installed /dev/sda9...swap[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-installed /dev/sda10.../home[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]And it detected the EFI partition: /dev/sda1.../boot/efi[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]SATAchanged from AHCI to RAID[/FONT][/COLOR]


[COLOR=#222222][FONT=arial]HDDaccelerated using SDD through IRST application[/FONT][/COLOR]

---

### Post by oldfred on 2014-01-21
I know they have made improvements. Early on the installer would not see anything with Intel SRT systems. Then install worked but grub would not correctly install.
It looks like resetting BIOS is a good alternative to removing RAID meta data at least with the newer versions.

Some with larger SSDs like yours found that the Intel SRT only used a small parted of SSD. The rest is unallocated.
gparted does not work with RAID, so those users must have seen the partition size from Windows?

Dell's seem pretty common across models as to issues & solutions. These may have some more suggestions.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---

### Post by bartfife on 2014-02-02
Thank you, Oldfred, for the observation that the installer is constantly being improved. I can certainly confirm that the installer correctly configured GRUB for dual-boot. I did NOT have to use the Boot-repair utility :P.

As you expected, the SSD in it's current BIOS SATA RAID configuration isn't visible from Gparted. It is also NOT visible from Windows Diskpart. Although I can't see how much of the SSD is being used for caching, I'm not concerned. 

My reason for opening this discussion, was a naive concern that the Linux kernel may be interacting with the SSD with the potential of interfering with the IRST Windows caching function. After seeing the kernel dmesg "[COLOR=#000000]sdb: unknown partition table"[/COLOR], and observing the SSD doesn't appear in the disk configuration, I believe Ubuntu will not be interacting with the SSD.

Thank you for helping me work out an answer.

---

### Post by bartfife on 2014-02-02
I forgot to mention I found a rather interesting article describing a system where Windows IRST caching and Linux Bcache coexist as follows:

[COLOR=#301E0B][FONT=Verdana]* SSD 1 is split into 22GB for the Linux OS and 90GB for the Windows C drive[/FONT][/COLOR]
[COLOR=#301E0B][FONT=Verdana]* SSD 2 is split into 56GB for the Linux BCache cache device and 56GB for the Windows Intel Smart Response cache[/FONT][/COLOR]
[COLOR=#301E0B][FONT=Verdana]* HDD 3 and 4 are combined into a single 2TB RAID 0 striped device ([/FONT][/COLOR][fakeRAID]("https://help.ubuntu.com/community/FakeRaidHowto")[COLOR=#301E0B][FONT=Verdana]) and is then split into two separate 1TB partitions, one for my Linux /data/ [/FONT][/COLOR][BTRFS]("http://wikipedia.org/wiki/Btrfs")[COLOR=#301E0B][FONT=Verdana] partition and one for my Windows D: drive.

[/FONT][/COLOR][https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows](https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows)

---

