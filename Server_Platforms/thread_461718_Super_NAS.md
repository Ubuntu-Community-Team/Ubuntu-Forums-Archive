---
title: "Super NAS"
date: 2007-06-02
forum: Server Platforms
---

### Post by Pontifex on 2007-06-02
I'm not exactly sure where to put this, so I posted copies of it in the 'Servers & Security' [1] forum as well as 'Programming Talk' [2].  I'll hope you forgive the imposition, but I wanted to maximize my returns.  Feel free to merge / close threads as you see fit, though I will repost useful comments as needed to continue the discussion.

I've been messing around with storage for most of my adult life (15 or so on to 25 this year).  I've accrued  a massive amount of data and I've been looking for better ways to manage it.  In the past I've just bought big hard drives and shared them via a Linux box.  I usually hover around 300GB-500GB of live data at a time.  In the past I've messed around with LVM, which I was delighted to see incorporated into Ubuntu in a fairly painless fashion; Nothing like my long hours of diagnosing and  lost data.

I've since broken down and bought myself a NAS [3].  I love the thing to death.  But now I have a great deal of left over IDE and (old) SATA drives, that I used to use for storage.  I was seriously considering putting something like 12 drives in one computer off several Promise controllers, but that didn't turn out to be viable (Promise doesn't support more than _one_ controller per computer, I can get two working but three requires some hacking).  So I'm left with a lot of hardware sitting around that I can't turn into a single storage option.  If I could put them all together and RAID them, I'm pretty sure I could get something like 700GB out of them.

Ever since I encountered the &#8220;Promise Problem&#8221;, I've been toying around with the idea of putting together several computers that could share data (via SMB or something similar).  This would be just like what I've been doing for years.  So I thought to myself why not have a series of computers all sharing data and presenting themselves as one large logical drive.  The back end would have some serious RAID of course, but it sounds feasible.

I'm almost sure someone must have thought of something like this before.  But for the life of me I don't know what they would have called it.  I checked SAN [4], but that seems a bit overkill.  At least in it's current Enterprise form.  The closest thing I can find seems to be a &#8220;NAS Head&#8221; [5] which would mediate between my network and a SAN.  But a quickly google search doesn't show anyone with that sort of project going.  Nor a simple SAN program I could drop into my theoretical network of computers.

The problem doesn't sound too hard.  Start with something simple, like a boot CD.  Knoppix or something similar.  Boot up a terminal and a file sharing daemon and you have a simple NAS.  Step two: Slave them together.  Create a &#8220;controller&#8221; program and integrated it into your CD, the thing seeks out NAS's on the network and adds the storage advertised by our little NAS's to the controllers table of available storage.  The controller indexes where it can put things - you could use a database for this, which would necessitate a hard disk, but still it wouldn't kill the project &#8211; and downloads digests of where things are on its children.  Whoops, we're getting some network chatter here, let's make the protocol event driven and incremental; That way we minimize network usage except for file transfers.  You could do one better for security and create use accounts on the slaves to only be accessible to the controller; Random strings for Usernames and Passwords or something similar.  Then just point everyone to the controller and have them use it like a regular NAS.  No one's the wiser  You could then integrate RAID into the slaves and some fancy logic to figure out what the best redundant configuration for each slave would be and shuffle around data until everything is stable.  You'd then have a scalable network of computers that emulate a highly redundant and theoretically infinite NAS.

That doesn't sound too bad.  Tell me someone's done something like this before so I don't have to spend a couple months coding it myself. ^_^

[1] - [http://ubuntuforums.org/showthread.php?p=2765540](http://ubuntuforums.org/showthread.php?p=2765540)
[2] - [http://ubuntuforums.org/showthread.php?p=2765536](http://ubuntuforums.org/showthread.php?p=2765536)
[3] - [http://www.newegg.com/Product/Product.aspx?Item=N82E16822329031](http://www.newegg.com/Product/Product.aspx?Item=N82E16822329031)
[4] - [http://en.wikipedia.org/wiki/Storage_Area_Network](http://en.wikipedia.org/wiki/Storage_Area_Network)
[5] - [http://en.wikipedia.org/wiki/Network-attached_storage#NAS_heads](http://en.wikipedia.org/wiki/Network-attached_storage#NAS_heads)

---

### Post by craigp84 on 2007-06-02
Hi,

GFS may be worth a look - [http://www.redhat.com/software/rha/gfs/](http://www.redhat.com/software/rha/gfs/)

> Promise doesn't support more than _one_ controller per computer

Why not use different controllers from different mfrs. Or just switch wholesale to another mfr. I believe most of the SIL chipset based cards are capable of having many instances per box.

-c

---

### Post by dannyboy1121 on 2007-06-02
Sounds like you're looking to run some kind of NAS virtualisation layer across your estate. Complex stuff.

I don't know if it stretches that far - but Openfiler does some pretty fantastic NAS/SAN stuff.

[http://www.openfiler.com/](http://www.openfiler.com/)

---

### Post by Pontifex on 2007-06-02
> 
GFS may be worth a look - [http://www.redhat.com/software/rha/gfs/](http://www.redhat.com/software/rha/gfs/)


Yes, GFS looks great.  I'm investigating how much they want for a solution and support.  But it does seem a bit much for the sort of thing I'm looking for.  Usually there's some sort of free or low cost solution hacked together by some Linux coder.  I was really hoping to start with that, since I know that this sort of thing is usually Enterprise level (as here) and subsequently, really expensive.

> 
Why not use different controllers from different mfrs. Or just switch wholesale to another mfr. I believe most of the SIL chipset based cards are capable of having many instances per box.


MFR?  I assume from the context you mean 'Manufacturer', right?  From here [1] I don't see any SIL based cards.  Only SIIG, is that what you meant?

There seems to be some additional confusion about what to call PCI add in cards that provide additional IDE slots for the computer.  Some call them hard disk controllers, which seems to be incorrect according to wikipedia [2]:

"The disk controller (or "hard disk controller") is the circuit which allows the CPU to communicate with a hard disk, floppy disk or other kind of disk drive."

Which would imply another name that I could use to search.  Newegg uses this nomenclature to refer to the definition as above.  Which is less than helpful.  This article [3] refers to the controllers as the circuitry embedded in the hard drive to access it, the interface on the motherboard that terminates the IDE cable as the "host adapter".  But this [4] seems to expand the term host adapter to include the add-in cards described above.  But a google search for the term "promise ide host adapter" returns as it's first link "IDE Controller Cards - The Mouse Pad".  Hopelessly confusing when trying to find information.

Needless to say trying to find reviews of a mass of host adapters is very difficult.  I have not found a company (from the list on newegg below) that will actually say whether their controllers can co-exist with other Host Bus Adapter's.  So you're guess is as good as mine on whether or not they can actually scale to more than one per machine.  Needless to say I'm not going to switch HBA's until I know there's a significant improvement over my reliable Promise ones.

Which leads me back to Horizontal Scaling as I outlined above.

> 
I don't know if it stretches that far - but Openfiler does some pretty fantastic NAS/SAN stuff.


It looks like this is what I'm looking for.  I'll have to cobble together some machines to test it on, so I may be a few weeks.  Thank you!  I'll report back my findings.

[1] - [http://www.newegg.com/Store/SubCategory.aspx?SubCategory=410&name=HDD-Controllers-RAID-Cards](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=410&name=HDD-Controllers-RAID-Cards)
[2] - [http://en.wikipedia.org/wiki/Hard_drive_controller](http://en.wikipedia.org/wiki/Hard_drive_controller)
[3] - [http://electronics.howstuffworks.com/ide.htm](http://electronics.howstuffworks.com/ide.htm)
[4] - [http://en.wikipedia.org/wiki/Host_adapter](http://en.wikipedia.org/wiki/Host_adapter)

---

### Post by craigp84 on 2007-06-03
> I was really hoping to start with that

GFS is open source and free to use. But it really would be cleaner (read: easier) if all the disks were in the one box :-)

> MFR? I assume from the context you mean 'Manufacturer', right?

Yeah

> From here [1] I don't see any SIL based cards. Only SIIG, is that what you meant?

No SIL. It's a cheap but very popular SATA chipset which is pretty well supported by linux. I don't have the name of an example card to hand - the only box i have that uses one has a no-name card. However here's the relevant parts of the dmesg from that box, in case this helps googling any:

```

SCSI subsystem initialized
libata version 2.00 loaded.
sata_sil 0000:02:0d.0: version 2.0
ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 209
ata1: SATA max UDMA/100 cmd 0xE082A080 ctl 0xE082A08A bmdma 0xE082A000 irq 209
ata2: SATA max UDMA/100 cmd 0xE082A0C0 ctl 0xE082A0CA bmdma 0xE082A008 irq 209
ata3: SATA max UDMA/100 cmd 0xE082A280 ctl 0xE082A28A bmdma 0xE082A200 irq 209
ata4: SATA max UDMA/100 cmd 0xE082A2C0 ctl 0xE082A2CA bmdma 0xE082A208 irq 209
scsi0 : sata_sil
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
ata1.00: ATA-7, max UDMA/133, 976773168 sectors: LBA48 NCQ (depth 0/32)
ata1.00: ata1: dev 0 multi count 16
ata1.00: configured for UDMA/100
scsi1 : sata_sil
ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
ata2.00: ATA-7, max UDMA/133, 976773168 sectors: LBA48 NCQ (depth 0/32)
ata2.00: ata2: dev 0 multi count 16
ata2.00: configured for UDMA/100
scsi2 : sata_sil
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
ata3.00: ATA-7, max UDMA/133, 976773168 sectors: LBA48 NCQ (depth 0/32)
ata3.00: ata3: dev 0 multi count 16
ata3.00: configured for UDMA/100
scsi3 : sata_sil
ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
ata4.00: ATA-7, max UDMA/133, 976773168 sectors: LBA48 NCQ (depth 0/32)
ata4.00: ata4: dev 0 multi count 16
ata4.00: configured for UDMA/100
  Vendor: ATA       Model: ST3500641AS       Rev: 3.AA
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
SCSI device sda: drive cache: write back
 sda: sda1 sda2 sda3
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3500641AS       Rev: 3.AA
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
SCSI device sdb: drive cache: write back
SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
SCSI device sdb: drive cache: write back
 sdb: unknown partition table
Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3500641AS       Rev: 3.AA
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
SCSI device sdc: drive cache: write back
SCSI device sdc: 976773168 512-byte hdwr sectors (500108 MB)
SCSI device sdc: drive cache: write back
 sdc: unknown partition table
Attached scsi disk sdc at scsi2, channel 0, id 0, lun 0
  Vendor: ATA       Model: ST3500641AS       Rev: 3.AA
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdd: 976773168 512-byte hdwr sectors (500108 MB)
SCSI device sdd: drive cache: write back
SCSI device sdd: 976773168 512-byte hdwr sectors (500108 MB)
SCSI device sdd: drive cache: write back
 sdd: sdd1 sdd2 sdd3
Attached scsi disk sdd at scsi3, channel 0, id 0, lun 0

```

> I don't know if it stretches that far - but Openfiler does some pretty fantastic NAS/SAN stuff.

OpenFiler is *really* excellent.

---

### Post by Pontifex on 2007-06-04
> 
GFS is open source and free to use. But it really would be cleaner (read: easier) if all the disks were in the one box


True enough.  But with something like this it would seem that some sort of minimal support would be required; Since I don't have immense amounts of free time to dick around with it, until it worked.  Also since the support is for pay, as with other things there is nearly no (reliable) free support, while with another free support / free software model I'd be getting deployment guides for nothing.

Disks in the same box is the key to the whole problem.  Getting everything to work together in one box is proving to be expensive and time consuming.  Which makes sense, since shoving more disks into a box than it was supposed to support, plagues more than just me.

This article on wikipedia ([http://en.wikipedia.org/wiki/Scalability#Scale_vertically](http://en.wikipedia.org/wiki/Scalability#Scale_vertically)) supports this and I intuitively understand why.  Since nearly always making something more complex (e.g. adding more storage) requires more investment in some critical resource (e.g. time and ease of diagnosis).  The trade off with networking nodes together (as described above, horizontal scaling) would be in access time and reliability.  More links and interconnections with the storage medium, the more could go wrong and the more time it takes to access data.  But for this sort of "data warehousing" I'm talking about, those drawbacks are less than fatal.  In fact the software used to tie all my little nodes together would be much simpler than for the same vertical solution; Or around there, I'm not sure where the optimal point is to switch between vertical and horizontal strategies.  But for my setup and resources, it's well past the time.

---

### Post by Pontifex on 2007-06-04
> 
No SIL. It's a cheap but very popular SATA chipset which is pretty well supported by linux.


Never post at 3 am.  I know that rule but ignored it in this case.  So I missed this thing you said.  I could use the SIL controllers, but unfortunatly none of the drives I'm using are SATA; On a side note not all of them are ATA 133!

Thanks though.  I'll keep that in mind.

---

### Post by craigp84 on 2007-06-05
Just came across this: [http://wiki.digitalbazaar.com/en/Starfish_Distributed_Filesystem](http://wiki.digitalbazaar.com/en/Starfish_Distributed_Filesystem)

-c

---

### Post by Pontifex on 2007-06-05
I checked them out.  They look like a superior solution, but are they actually still existant?  All I see from links from their wiki are 503's.

---

