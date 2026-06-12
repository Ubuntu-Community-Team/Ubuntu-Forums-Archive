---
title: "4 of 6 RAID10 drives suddenly fail, Ubuntu 12.04.4 LTS"
date: 2014-04-06
forum: Server Platforms
---

### Post by RedScourge on 2014-04-06
Hello,

I set up a new system with 6 x 3TB drives in RAID10 far=2 layout (3 groups of 2 drives) on Friday, and suddenly I wake up Sunday morning and 4 of the 6 drives say they have failed. It was a huge pain to figure out how to install onto a RAID10 with 3TB drives, but that's another story. Eventually I settled with each of the drives having a 1MB bios grub partition, a 127mb /boot/efi partition left empty, and the rest of the space being a RAID volume, with LVM inside that volume with a small /boot partition, a / partition, and most of the space allocated to the /srv partition (setting up a VM host where all the VM files are stored in /srv). 

I was working on it for most of the time in between, despite the fact that the array was not entirely done syncing, and shortly after it was done syncing, all of a sudden this happened most of the way through a large file copy operation from a network computer to a Windows VM on this system. I was under the impression that working on the system while it syncs is fine, because it let me install an entire Windows VM and mostly configure it starting from when the sync was about 10% complete without any apparent problems all the way until it just crashed this morning. I currently don't have physical access to the system so I'm just accessing it remotely, and am afraid of restarting it for fear of not being able to get back in.

When I try to run fdisk or parted on any drive, it tells me "Bus error". When I try to run mdadm --examine /dev/md0, "state is clean, FAILED", 2 active devices, 2 working devices, 4 failed devices, and the first 4 being the ones that failed. If I try to do mdadm --examine on each of the drives, it tells me for the first four "No md superblock detected on", and then the last two give me seemingly proper output. I did not install smartmontools before the failure, so I cannot run smart on the drives.

Here's a sample from the /var/log/kern.log:

```
[71414.825777] device eth1 entered promiscuous mode
[71420.733364] device eth1 left promiscuous mode
[71420.769298] vboxnetflt: 0 out of 36 packets were not sent (directed to host)
[71424.008859] device eth1 entered promiscuous mode
[72048.963294] device eth1 left promiscuous mode
[72059.573234] device eth1 entered promiscuous mode
[80260.649493] ata8.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[80260.649497] ata8.00: failed command: IDENTIFY DEVICE
[80260.649501] ata8.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[80260.649501]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[80260.649503] ata8.00: status: { DRDY }
[80260.649506] ata8: hard resetting link
[80260.976803] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[80260.978517] ata8.00: configured for UDMA/133
[80260.978646] ata8: EH complete
[88478.554538] EXT4-fs (dm-2): Unaligned AIO/DIO on inode 1640488 by AioMgr0-N; performance will be poor.
[98222.255566] ata9.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[98222.255571] ata9.00: failed command: IDENTIFY DEVICE
[98222.255575] ata9.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[98222.255576]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[98222.255579] ata9.00: status: { DRDY }
[98222.255582] ata9: hard resetting link
[98222.582852] ata9: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[98222.584063] ata9.00: configured for UDMA/133
[98222.584133] ata9: EH complete
[110032.554117] EXT4-fs (dm-2): Unaligned AIO/DIO on inode 1640488 by AioMgr0-N; performance will be poor.
[110795.347858] ata9.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[110795.347867] ata9.00: failed command: IDENTIFY DEVICE
[110795.347875] ata9.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[110795.347877]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[110795.347882] ata9.00: status: { DRDY }
[110795.347888] ata9: hard resetting link
[110800.704389] ata9: link is slow to respond, please be patient (ready=0)
[110805.342503] ata9: COMRESET failed (errno=-16)
[110805.342511] ata9: hard resetting link
[110810.691043] ata9: link is slow to respond, please be patient (ready=0)
[110815.329140] ata9: COMRESET failed (errno=-16)
[110815.329151] ata9: hard resetting link
[110820.677702] ata9: link is slow to respond, please be patient (ready=0)
[110850.294391] ata9: COMRESET failed (errno=-16)
[110850.294402] ata9: limiting SATA link speed to 3.0 Gpbs
[110850.294407] ata9: hard resetting link
[110855.307684] ata9: COMRESET failed (errno=-16)
[110855.307696] ata9: reset failed, giving up
[110855.307702] ata9.00: disabled
[110855.307733] ata9: EH complete
[110855.307987] sd 8:0:0:0 [sdc] Unhandled error code
[110855.307993] sd 8:0:0:0 [sdc] Unhandled error code
[110855.307998] sd 8:0:0:0 [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[110855.308006] sd 8:0:0:0 [sdc] CDB: Read(16): 88 00 00 00 00 01 59 be 45 33 00 00 04 00 00 00
[110855.308029] end_request: I/O error, dev sdc, sector 5800609075

```

I was going to copy more code, but the system just failed when I tried to resize an xterm window that I was copying this from and now the box won't respond at all. In retrospect this is probably because another forum thread gave me the stupid idea of running "mdadm --assemble /dev/md0 --uuid=(my arrayuuid)". Now I can't even reboot the system because it can't find the shutdown or reboot commands, yippee!

I will post more information later on perhaps when I get physical access to the server assuming I am somehow able to ever read anything from the array again, but I thought for now I would at least post this info here so that I do not lose it.

The motherboard is ASUS X79-Deluxe which has multiple storage controllers on it, there's a Marvell controller with 4 x 6gbps ports somehow apparently optimized for an SSD and a regular drive, an ASMedia controller with 2 x 6gbps ports, and an Intel controller with 2 x 6gbps ports plus 4 x 3gbps ports. I had 4 of the drives on the Marvell, and 2 of them on the Intel 6gbps, as I wanted the highest performance possible.

From the ASUS site's specifications page:

**Intel® X79 chipset : **
[COLOR=#333333][FONT=Segoe UI]2 x SATA 6Gb/s port(s), black[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]4 x SATA 3Gb/s port(s), black[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]Support Raid 0, 1, 5, 10[/FONT][/COLOR]
**Marvell® PCIe 9230 controller : **
[COLOR=#333333][FONT=Segoe UI]4 x SATA 6Gb/s port(s), dark brown[/FONT][/COLOR]
**ASMedia® ASM1061 controller : **
[COLOR=#333333][FONT=Segoe UI]2 x SATA 6Gb/s port(s), dark brown[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]2 x Power eSATA 6Gb/s port(s), green[/FONT][/COLOR]

---

### Post by CharlesA on 2014-04-06
Check your cables and run a smart test on each of the drives in the array.

---

### Post by lukeiamyourfather on 2014-04-07
It's fairly unlikely for four disks to fail at the exact same time like that. More likely is a controller has failed, power supply rail, backplane, or other component which could affect all four disks.

---

### Post by RedScourge on 2014-04-07
So I was able to get on site to see what happened, blank screen, and blank screen upon reboot, perfect. I rebooted and went into recovery mode, and apparently recovery mode has neither any smart commands nor fdisk nor parted, so I can't really examine the situation with it. mdadm --examine tells me that the first 4 drives events count is 39 and the last two is 88. If I try to recreate the thing it just says:

mdadm: CREATE user root not found
mdadm: CREATE group disk not found

and that's it.

What good is it installing a recovery mode option in the boot loader on a server OS if it doesn't let you recover anything?

---

### Post by RedScourge on 2014-04-07
After tons of trying to coax mdadm to let me restart the array, I was able to boot again, fsck detected some problems and fixed them and rebooted super fast before I could see what it fixed, and now things *appear* to be running as normal. However, I have no real way to know what happened and whether or not I can do anything to prevent this from happening again. I am going to update the first post with the full kern.log details now that I have access so that someone can maybe see something useful about what happened. My hunch is that the different disk controllers on this board are not upto the task of copying a lot of files for several hours, so I am thinking I will plug into the 6 Intel controller ports instead, as that will all be on the Intel controller, and all the activity will be within one controller. I have no idea why ASUS thought it would be a good idea to put 3 different disk controllers on the same board, but oh well.

I saw an interesting note in the ASUS X79-Deluxe BIOS manual, page 1-37:

"These SATA ports are for data drives only"

It says this regarding the Marvell controller and the ASMedia controller, but it does NOT say this regarding the Intel controller. I set up all my drives on the Marvell controller and the 2/6 Intel ports which offered 6gpbs because the Marvell controller has 4 x 6gbps ports and the Intel has 2 x 6gbps ports plus 4 x 3gpbs ports, and I figured why not go with the fastest ports? I think I may have my reason now, but again, this is not confirmed.

Edit: silly me, I can't go back and get the rest of the kern.log because that file was only written to 2 of the 6 drives and I have lost all trace of those since rebuilding the array for obvious reasons. Oh well, I will run a crapload of I/O stresstests after putting the drives back on the Intel controller ports and if I can't blow up my RAID again, I'll assume it's just that I have to avoid the Marvell controller for OS drives.

---

