---
title: "Ubuntu Server 22.04.3 not detecting HDD"
date: 2023-11-17
forum: Server Platforms
---

### Post by madscientist032 on 2023-11-17
Greetings all! I am looking for support on my Jammy dedicated server. 

I recently performed a disk replacement, where I physically replaced a 2tb SATA HDD with another of the same size & capacity.

The disk in question is not part of any JBOD or RAID array. It's simply just mounted as a standard drive (/dev/sdb1) 

Prior to the replacement, I had physically cloned the old drive to the new one using a StarTech HDD duplicator.

I verified post-duplication that the data is intact & accessible on the new drive by plugging it into my Ubuntu laptop via usb-to-sata adapter. The drive does not have any issues mounting on the laptop.

However, on the server, the new drive is not visible at all. It doesn't show up in the BIOS, nor at the OS level via fdisk, and I'm not sure how to check a disk's SMART status via the terminal seeing as the drive isn't detected in the first place. 
I at least know the drive is good because it shows up on my laptop as I stated earlier, so it's either a motherboard, cable, or OS issue (or PEBKAC!). 

It's worth pointing out the original drive is already being used and it would be a bit of a hassle to clone & reinstall it into the server. I was expecting this procedure to be a drop-in & not have any issues, hence why I immediately chose to take the OG drive and wipe it instead of simply backing out the change. 

Furthermore, there are two other disks on this server that are showing up & mounting proper (512 gb NVME Boot drive and a 10TB HDD used for cold storage) so it's not like the server's completely out of the water, just the singular drive. 

Other than checking the SATA ports + cables & reseating connectors, is there anything I can do in the meantime to at least check & see if the O/S can recognize the drive? I can't back out my changes until next week at the soonest, so I figured I'd post here and get advice in the meantime. 

Thanks in advance.

---

### Post by TheFu on 2023-11-17
Some USB controllers lie about the true physical parts of HDDs.  

I've seen this with Startech and Pluggable USB adapters myself.  

In the end, I had to wipe the drive and start over with a new partition table, partitions, file system while directly connected to the system using SATA, not using the USB adapter to get it working.  This happened when I was adding an 8TB WD-Black HDD over the summer. A WD-Black drive is just about as standard a HDD as made anywhere today.  You can read more about this issue [https://www.klennet.com/notes/2018-04-14-usb-and-sector-size.aspx](https://www.klennet.com/notes/2018-04-14-usb-and-sector-size.aspx)
>  If your USB enclosure silently converts 512-byte sectors to 4096-byte sectors, then:

 [LIST=1]
[*]   If you bring a hard drive from another PC, and the hard drive uses 512-byte sectors, you will not be able to read it through the enclosure. This is exactly the issue encountered in the opening quotation.
[*]    If you put a blank 512-byte sector drive in the enclosure and format it, you will need the same or similar enclosure to access the drive. You will not be able to use it on SATA or with an enclosure that does not translate the sector size.
[/LIST]


---

### Post by darkod on 2023-11-17
If you were able to do it like that, I am always more in favor of adding the new disk in parallel, and migrate the data. Rather than cloning. Things can go wrong. For example, did the new disk have same or greater number of total sectors? You can't clone correctly to a smaller disk etc. Plus migrating allows you to rethink your setup and do improvements and reconfigurations of things that maybe you didn't set up years ago. :)

Also, you say the BIOS doesn't see it either. Stop thinking about OS at that moment, the first task is the disk to be visible in the BIOS. If it is not visible, then it is like it is not even there. So OS or fdisk or parted won't do much for you.

---

### Post by MAFoElffen on 2023-11-17
What brand and model computer is it? You say there is no HBA or RAID card right?

---

### Post by madscientist032 on 2023-11-23
Hi all and thanks for the feedback, I am marking this as solved as it was PEBKAC... details below. 

This HDD was duplicated via a Startech HDD Duplicator which I've never had issues with unless the target disc was smaller than the source OR if either of the drives were going bad. 

During the shuffle and HDD swap process the SATA cable was not fully seated/inserted into the HDD which is why it wouldn't show up in the BIOS or the O/S.

Reseating the connection was all I had to do. The HDD shows up proper now in both the BIOS and in fdisk, and the data is also there intact as expected.

```
madsci@bossvc2ubnnas:~$ sudo fdisk -l | grep sdb -A10
Disk /dev/sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000LM003 HN-M
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 05ACF1E8-CD80-462E-B89D-CD824ED54426

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 3907028991 3907026944  1.8T Linux filesystem
```

---

