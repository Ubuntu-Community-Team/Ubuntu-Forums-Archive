---
title: "Raid systems what are they  good for??"
date: 2009-02-19
forum: Server Platforms
---

### Post by hockey97 on 2009-02-19
Hi, I am really new to the scene of raid systems.

I looked on some websites and saw some explanation why it's used.

They basically said it's for performance for large amounts of data.

Is there a way where I can keep adding more and more and more hard drives?

I plan to host my own websites. I would assume I need to keep adding hard drives to just keep up with memory demand.

Is their a way I can just keep adding hard drives and have it viewed as one big hard drive.

How can I keep adding more and more hard drives? I was thinking to buy a cabinet and stack hard drives in the cabinet and have them wired to my computer.

So what do people use to help keep increasing memory for their websites.

---

### Post by E_K on 2009-02-22
> Raid systems what are they good for??

> for performance for large amounts of data

yes you can make (a) logical volume(s) out of the hard drive(s). So that multiple harddrives are seen as one by the os. The most efficient was i believe is using the same hard drives make/model/size, size of the is an important factor> 

 So what do people use to help keep increasing memory for their websites.

since websites dont have memory, i guess you mean system, then the answer would be RAM. But i bet you mean storage space :P

I myself have hardware RAID on my IBM server, with 6 disks and 3 logical drives, one for OS, one for media and one for my web content.

---

### Post by Iowan on 2009-02-22
I don't have answer, but wonder if [SAN]("http://en.wikipedia.org/wiki/Storage_area_network") is a viable option (for the big boy$).

---

### Post by capscrew on 2009-02-22
RAID is locally connected and SAN's are remote storage networks.

Just to add something to the mix; look at ZFS.  It eliminates the need for RAID in my opinion.  You have self a healing file system and zpools to add storage space.  The downside; available only on OpenSolaris or BSD at this time.  Nextenta is also a project to port ZFS to a Debian style Linux distro.

---

### Post by DGortze380 on 2009-02-22
RAID is typically used to guard against drive failure.

There are many types of RAID, IMO they're not worth a darn until you get to RAID 5. Some here will disagree with me, that's fine, decide for yourself. [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

RAID in and of itself is NOT a backup method.

Yes you an use a RAID array and have it appears to the OS as 1 drive.

Consider TRUE HARDWARE RAID, as it will be portable between Operating Systems with little difficulty. Software RAID is an issue with Ubuntu.

Lastly, Web Site Files are not typically very large, how many sites are you planning on hosting, why so concerned with storage. Hard drives are comparably cheap, you can build a 5TB array for a few hundred dollars, that's A LOT of space.

---

### Post by ikonia on 2009-02-22
What are raid systems good for, well an interesting question,

for hosting websites as you want.....well no, not really.

mirroring your disk with raid 1 would be an excellent way to stop data loss on disk failure.

How much do you plan on hosting ???? I mean how big can websites get on a server that you need to keep adding disks before you out grow the size of the server.

Raid 6 can have disks added dynamically, but I wouldn't say that's what your looking for.

You could look at LVM for adding disks and managing and increasing file systems, but again - your hosting websites, not massivly dynamic data sizes.

eg: a 10GB website would be massive - a 100 Gig disk which is small by today's standards, you could fit 9 on there easy, 


You also seem to be confusing disk space with memory, your disk space does not need to match your memory or even "keep up" with your ram, the ram is used for serving the webpages - not storing them, so for example, the ram would be used for storing backend database indexs, cached queries or bound varibles, it would also be used for the actual web server process.

Before you start playing around with raid systems which as you say is new to you, I think you should look at your current requirements and do a sizing exercise for say the next 1 to 3 years, no point adding 10TB of disk space to a machine, if you can't put enough CPU/ram in it to be able to serve the volume of connections and queries you'll get.

---

### Post by jerrrys on 2009-02-22
"Is there a way where I can keep adding more and more and more hard drives"

check out raid5

three types of raid:
1 software raid, not very popular, seams to do more harm than good
2 fake raid, usually part of the mobo or a cheap card, this is what i got and not happy with it, a resource hog
3 hardware raid, the best, comes with its own cache (ram if you will), fast. just take lots of money with you when you go to buy it.

can you justify it? probally not. its a toy for the big boys and really not used to its potential in the home environment...nuf said

---

### Post by bigbearomaha on 2009-02-22
I would say most that use RAID, even the "big boys" use it for redundancy/uptime.  RAID 5 and 6 being the two most valuable to them in that circumstance

mostly, if one hard drive experiences failure, your site doesn't go down in flames, you pull out the bad drive and replace it into the array with a good blank one which RAID will populate with images from the others.


RAID drives are still susceptible to data corruption and loss.  Which means that you still need to have a solid backup/recovery plan in place.

If what you are doing can be done on one hard drive, then RAID may be an option to maintain high uptime for you. ( the data is mirrored over a span or array of several, likely 3 or more identical hard drives) all being an exact duplicate of the others and the system able to survive and continue on if even all but one fail.

Have fun, learn lots

Big Bear

---

### Post by PilotJLR on 2009-02-23
> **jerrrys said:**
> 
three types of raid:
1 software raid, not very popular, seams to do more harm than good
2 fake raid, usually part of the mobo or a cheap card, this is what i got and not happy with it, a resource hog
3 hardware raid, the best, comes with its own cache (ram if you will), fast. just take lots of money with you when you go to buy it.


I disagree with this. Hardware RAID is proprietary, so if you raid card fails, then you better have it under warranty!

Linux software RAID is the way to go. Good performance (using a newish CPU) and very very stable and reliable. You can move the disks from controller to controller, and even change motherboards, and the array still works.

For a home server, a local RAID 5 or RAID 1 makes great sense. Just remember that RAID does not equal backup! Important files still need to be backed up to removable media, like CD's.

---

### Post by Faolan on 2009-02-24
The performance of a hardware raid card is far greater than the performance of a software solution. This is because of the dedicated processor (often dual core on the mid to high end cards)for the checksum calculations, dedicated cache with the additonal option of battery backups and the fact they work at hardware level without a interface.

In addition a good hardware raid card will also allow staggered start up. This is important to preserve hard drive life and also reduce the strain on your PSU. Essentially if you have three or more drives then when you power up it can (and does) make the system unstable. Of course you could get a bigger PSU but...

The other great advantage is that the disk space is seen as one whole drive presented to the OS this is important if you've ever had to try and repair the drives.

The idea behind RAID is redundancy and uptime. It was designed for corporations and organisations who need data 24/7 with little or no impact to business operations. It can be part of a back up solution but it should not be relied on. This because if you experience data corruption it will affect all drives.

RAID is also used extensively for databases in where data access times are critical.

I have seen 6 15k SAS drives totally saturate the PCIe interface and the newer SSDs from Intel do the same with less drives (2 I believe).

I run a hardware RAID myself but I use 4 SAS drives in RAID 10 more for the fact it's less inconvenient for me to rebuild the OS if a drive fails but I also have an image which can be deployed in the case of a corrupt drive.

When deploying RAID make sure you do:

1) Get the same brand of drive and firmware revision but different manufacturing dates. Spindle vibrations can cause havoc with head reads (and in rare cases head crashes). This is why it's essential to get drives that are identical. Read patterns can change between firmware revisions.

2) Ensure you have sufficient cooling. The drives will generate a lot of heat as they are generally working together. There is a number of hot swap bays on the market from companies such as IcyBox which will give you both cooling and hot swap abilities.

3) Plan how you are going to use the RAID and what is required. 

4) Power - are you going to be using a UPS and/or a battery based cache?

5) Costs - When an array fails you are advised to replace all drives at once due to the extra stress of one failing.

6) Storage - How much storage do you need. This will affect the RAID level you use in as much the costs will.

7) Hot Spares - are you going to be using hot spares? Hot Spares can help prevent a total RAID collapse if a drive fails. A hot spare is a drive that's put into standby mode in the event of a live drive failing. It will rebuild the array on to the disk. You would replace the array (or drive depending on your budget and reliability requirements) and then the drive would either go back into standby when replaced or the new drive will become the hot spare, this is dependant on manufacturer.

8) Buy enterprise class drives - They are designed for the harsh environment than an array creates. 

Expansion of a RAID is impossible (well unless you use something like a ReadyNAS with X-RAID). Normally you will have to rebuild the complete array. This because of the way RAID works. RAID will only see the space of the smallest drive in the array, so if you have 3 36Gb drives and 1 72Gb then then array will consist of 4x36Gb drives.

---

### Post by netztier on 2009-02-24
> **Faolan said:**
> Expansion of a RAID is impossible (well unless you use something like a ReadyNAS with X-RAID). Normally you will have to rebuild the complete array. 

While this statement holds for the array itself, one can work around this by using LVM2 (logical volume manager) atop the array(s). When using software RAID, the virtual /dev/mdX devices are the "Physical Volumes" in LVM, which is the "lowest layer".

One can continue to add more single drives (or /dev/mdX arrays) to the "Physical Volumes (PV)".  Then you add them to existing or additional "Volume Groups (VG)" which then in turn hold the (possibly multiple) "Logical Volumes (LV)". Like partitions, these LVs can be formatted with file systems and be mounted via /etc/fstab.

As a VG grows by adding physical devices (PVs) to it, the size of the LVs inside the VG can also be adjusted, and the filesystems inside the LVs can be grown or shrunk - only if the chosen file system supports this without reformatting, of course.

This is one way to "just add disks", it is by no means easy, but it can be done without rebuilding a whole array. As always, a good backup strategy is advisable before doing changes to the LVM configuration. 

"You DO have Backups, don't you?"

regards

Marc

---

### Post by Faolan on 2009-02-24
> **netztier said:**
> While this statement holds for the array itself, one can work around this by using LVM2 (logical volume manager) atop the array(s). When using software RAID, the virtual /dev/mdX devices are the "Physical Volumes" in LVM, which is the "lowest layer".

I will amend that for future reference. Thanks Marc I had forgotten this method under Linux and to be honest I don't think many corporations would want to do this. Is there a performance issue doing it this way?

I suspect SAN systems from HP do something similar as I have seen a 300Gb drive (6 disks) array upgraded to a 750Gb array (again 6 disks) but I've got no idea of what the procedures was.

---

### Post by netztier on 2009-02-24
> **Faolan said:**
> and to be honest I don't think many corporations would want to do this. Is there a performance issue doing it this way? 

I wouldn't know about performance issues, but I do know that using LVM is a very good approach if you are using "direct attached storage" like SCSI or SATA disks -- as opposed to SAN (Fibre Channel or iSCSI) based storage.

Back at my former job, some eight years ago, I was a greenhorn in terms of system administration when the local AIX sysadmin showed me that using LVM had immense advantages in that it decouples your partitions (i.e. your file systems) from the size, number and geometry of the underlying disks or disk arrays.

I know little about Sun's ZFS, but I think that I have understood that it offers all in one package: RAID-like features for redundancy, the virtualisation like LVM does and the actual file system itself. That should keep the learning curve short: no need to learn mdadm, LVM and file system handling in three different places; all is done via zfs-related commands and interfaces.

> 
I suspect SAN systems from HP do something similar as I have seen a 300Gb drive (6 disks) array upgraded to a 750Gb array (again 6 disks) but I've got no idea of what the procedures was.

Storage Arrays of this class are capable of doing virtualisation at almost any layer in their internal architecture. Quite impossible to guess from the outside :-)

regards

Marc

---

### Post by matey3 on 2009-02-24
excellent thread.

does anyone know if there is such a thing as stripe set in linux?

for what I have seen out there if you have a raid controller in your system you can use its bios to setup mirroring or diff. raid levels.
as someone said tho, using the lvm can solve the problem.
I think the file allocation table is where the different disk configurations can be set any way so whats the difference if it is written into your disk or in the mfg's bios??!
at least with lvm you get to write what you want at will.

i think with new sata disks you can build an array in any system without spending more money?!

---

### Post by DGortze380 on 2009-02-24
> **matey3 said:**
> excellent thread.

does anyone know if there is such a thing as stripe set in linux?


[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

All these stripe (also RAID 2, technically)

RAID 0
IMHO, totally pointless. Plain old, striped across multiple disks.

RAID 3 
IMHO, totally pointless. Only allows for parity drive failure without destroying the array.

RAID 4
Again, IMHO, pointless. Allows for simultaneous access to multiple disks, but still uses a single parity disk.

RAID 5
Potentially useful, allows for any single drive failure without data loss and typically hot swapping

---

### Post by netztier on 2009-02-24
> **matey3 said:**
> 
for what I have seen out there if you have a raid controller in your system you can use its bios to setup mirroring or diff. raid levels.
as someone said tho, using the lvm can solve the problem.


If you want RAID-5, then mdadm is the way to go. Best use cases for RAID are RAID-1 (mirroring) and RAID-5 (Striping with distributed parity). mdadm will build either for you, and it (basically) does not care how these disks are connected to the system: SATA, PATA, USB, whatever. For reasons of performance symmetry, it is of course advisable to combine only similar drives connected identically to the system. 

mdadm doesn't even care about drives - it wants to see partitions. So yes, you could do something weird and set up a mirror with two identically sized partitions on a single drive. I wouldn't, though ;-).

LVM just helps to to aggregate (different Phycsical Volumes to a Volume Group) and then slice up (a Volume Group into Logical Volumes) your storage, so you don't have to care if that very-large filesystem you need today fits onto a particular drive or not.

Like this, LVM takes over some functionality of RAID-O (striping), and it can even do RAID-1 (mirroring) itself, and you can tune across how many drives you want the LV to be striped (check the man page of the **lvcreate** command).

> **matey3 said:**
> 
I think the file allocation table is where the different disk configurations can be set any way so whats the difference if it is written into your disk or in the mfg's bios??!
at least with lvm you get to write what you want at will.


Avoid the term "file allocation table" by all means. Thats something horrible from the historic dimensions of computing when dinDOSaurs were walking the earth and floppy disks were common to boot from. There even was a certain coM$pany that continued to abuse the FAT as a file system for harddisks.

What each disk holds in it's first data sectors is a *partition table*, that tells anyone reading the disk how it is sliced up and what size, where and which type the slices are. **fdisk** or **cfdisk** are the tools to inspect or change a partition table.

None of that gets written to the BIOS - all that is determined via the BIOS is the sequence how the connected disks are inspected for a master boot record which then in turn holds the information about where to start loading an operating system from.

If you have a hardware RAID controller, it will not show the single disks to the BIOS (and the OS), but one or more virtual disks of the size and geometry that you configured in the controllers setup feature. 

That has some advantage, as in that you don't have the complex storage setup in the OS, it will only see simple "disks". However it has the disadvantage that the OS has no clue about what is going on on the RAID and how healthy the disks are. You then need some monitoring software that knows how to talk to your raid controller and can write status and event messages.

> **matey3 said:**
> 
i think with new sata disks you can build an array in any system without spending more money?!

This does not depend on SATA disks per se - all of this works as well with PATA, IEEE1394 or USB disks. At least theoretically :-)

---

### Post by dajasc on 2009-02-24
The only time I've used RAID was a fake RAID 1 array on my wife's desktop.  I did it because it worth the $100 for insurance against hearing complaints if a drive failed and she had to be without a computer for a few hours.  Well, one did fail.  She never even noticed it had died.  I through a new one in, it rebuilt itself, best $100 I've spent in a while.

---

### Post by 3L33T on 2009-02-24
> **DGortze380 said:**
> 
RAID 0
IMHO, totally pointless. Plain old, striped across multiple disks.


I'm not sure I'd call it 'pointless'.  It is called RAID 0 for a reason and one of those reasons is better performance.  Unfortunately, there is no redundancy with RAID 0.  I use RAID 0 for my Winblows 2003 SBS swap and as a database temp dbspace.

---

### Post by DGortze380 on 2009-02-24
> **3L33T said:**
> I'm not sure I'd call it 'pointless'.  It is called RAID 0 for a reason and one of those reasons is better performance.  Unfortunately, there is no redundancy with RAID 0.  I use RAID 0 for my Winblows 2003 SBS swap and as a database temp dbspace.

I said in my opinion... that's fine, I know it's purpose, and I know that I personally have seen no significant performance gain over a single drive, hence my opinion, pointless.

---

### Post by cenwesi on 2009-06-04
Good thread and read as i now have more hard drive and trying to decide how to setup things and also utilize the space properly.

I currently have:
3 x 500gig WD drive
1 x 1Tb seagate (i think)
1 x 1Tb WD Mybook ( i use this for backup for now)
2 x 1.5Tb seagate

Currently without the two 1.5Tb and the MyBook, i have all the drive as LVM. 
I am more worried about if any drive fails i loose EVERYTHING and that is why i have the 1Tb Mybook for backup. But now that i have the two 1.5TB i really want to redo my system and would like some help from you guys. 

PS: I would still like to make use of LVM but i want that RAID features. I am stuck between Raid1 and Raid5.

---

### Post by DGortze380 on 2009-06-04
> **cenwesi said:**
> Good thread and read as i now have more hard drive and trying to decide how to setup things and also utilize the space properly.

I currently have:
3 x 500gig WD drive
1 x 1Tb seagate (i think)
1 x 1Tb WD Mybook ( i use this for backup for now)
2 x 1.5Tb seagate

Currently without the two 1.5Tb and the MyBook, i have all the drive as LVM. 
I am more worried about if any drive fails i loose EVERYTHING and that is why i have the 1Tb Mybook for backup. But now that i have the two 1.5TB i really want to redo my system and would like some help from you guys. 

PS: I would still like to make use of LVM but i want that RAID features. I am stuck between Raid1 and Raid5.

Nothing to be stuck on there. If you're going to run RAID, run RAID 5. Otherwise don't bother. Either way, keep incremental backups.

---

### Post by Skip Da Shu on 2009-06-04
[QUOTE=DGortze380;6781706]There are many types of RAID, IMO they're not worth a darn until you get to RAID 5. Some here will disagree with me, that's fine, decide for yourself. [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)/QUOTE]

Agree with all else but can't let this RAID 5 thing go unless you consider RAID10 beyond RAID5 (and imho, it is).  Especially if you're doing cheap (software) RAID like poor lil' ol' me.  ;-)

---

### Post by Skip Da Shu on 2009-06-04
> **Faolan said:**
> The performance of a hardware raid card is far greater than the performance of a software solution. This is because of the dedicated processor (often dual core on the mid to high end cards)for the checksum calculations, dedicated cache with the additonal option of battery backups and the fact they work at hardware level without a interface.  The stuff I've read does NOT back this up if you are looking at sub $400 RAID cards and modern multi-core CPUs for RAID 0, 1 or 10.  I might agree for RAID5 and I think RAID6 is a hardware only solution today.  

Maybe I missed where this thread turned from ... well you can read the 1st post... to enterprise data center solutions with budgets for that.  What is the scope here?  Are we doing the data center, Joe's Pawn Shop & Tax Accounting or home networks with a SAMBA server for the video collection?  I think they need different answers.

---

### Post by Skip Da Shu on 2009-06-04
> **PilotJLR said:**
> I disagree with this. Hardware RAID is proprietary, so if you raid card fails, then you better have it under warranty!

Linux software RAID is the way to go. Good performance (using a newish CPU) and very very stable and reliable. You can move the disks from controller to controller, and even change motherboards, and the array still works.

For a home server, a local RAID 5 or RAID 1 makes great sense. Just remember that RAID does not equal backup! Important files still need to be backed up to removable media, like CD's.

OK, I'm with this guy.  For most small/medium biz applications and certainly for home use software RAID 0, 1, 10 (depending on goal) is the answer.

Oh yea, I just converted my software RAID 1 to a software RAID 10 to both double it's size and get a nice little perf boost also.  Fail one drive in the original array, take it out and build the rest... then copy data from it back into the new array.  When done, add the disk back to the original (/dev/md0) array and let'm rebuild.  No 'live CD' required (no OS on the array).

---

### Post by 3L33T on 2010-12-09
> **DGortze380 said:**
> I said in my opinion... that's fine, I know it's purpose,


reaaaallly?

> 
... and I know that I personally have seen no significant performance gain over a single drive, hence my opinion, pointless.

...personally? OK, I dont know the extent of your "personal" experience, but, in todays google-centric world you'll see dozens of threads and arguments about "which is better? RAID 0 striping or plain old single drive" and you'll see that hands down a RAID 0 will outperform a single drive configuration.  The key in RAID 0 versus plain hard drive setup is the configuratble striping size of 64K increments.  IF you're telling me that a RAID 0 with large stripe size (or small depending on application) has "...no significant performance gain over a single drive..."  I beg to differ.  Show me a single drive (excluding SSD's) configuration that can outperform a RAID 0 drive.

---

