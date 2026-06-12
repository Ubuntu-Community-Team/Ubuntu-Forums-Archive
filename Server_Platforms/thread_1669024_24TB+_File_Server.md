---
title: "24TB+ File Server"
date: 2011-01-17
forum: Server Platforms
---

### Post by AlexHunter on 2011-01-17
I'm looking to create a file server of over 24TB+ and was wondering if anyone knew of any barriers to doing this in Ubuntu.

I am considering limiting each server to 8TB, and creating 4 of them. I think once I take into consideration the hardware limitations, and backup (I will need a RAID configuration (still deciding)) then perhaps 24TB in one box is possibly a little unlikely!

EDIT: I'm sure you'll all ask, so here is the reason for it. I am storing months worth of CCTV data, from HD IP Cameras, of which there are 20. Each day creates around 400GB of data.

Also, the hardware has not yet been bought, so if there are any suggestions of hardware which might work well, (RAID controllers, motherboards, etc) then do let me know.

---

### Post by spynappels on 2011-01-17
What sort of connectivity do the cams require? Samba or NFS or something else? It's just that that amount of data would saturate most connections.

I presume you are using Gigabit network?

---

### Post by AlexHunter on 2011-01-17
The cameras won't be feeding directly on to the server. They will be feeding on to an already existing server with 4TB of storage running on Windows. The data is then moved on to a USB drive and will be copied on to this server every couple of days.

The server is just for storage and occasional access.

The reason for this storage is that the project is extending by a number of weeks and we want a single solution.

---

### Post by cascade9 on 2011-01-17
24TB is possible with 1 machine. You'd need a big case, and most of them top out at about 12-13 HDDs. Also a RAID card, and 8-12 port RAID cards arent cheap. 

With a 12 port RAID card, 12 x 2TB drives, you'd get 24TB. Thats without RAID reduncancy, which in the case of RAID 5 would drop the usable stoage to 16TB. You could use 3TB drives, for 36TB total, and 24TB usable storage, but I'm not sure about how the new advanced format drives would deal with RAID (and all the 3TB drives I've seen arent 'RAID' models anyway).

---

### Post by spynappels on 2011-01-17
It might be a good idea to build some smaller iSCSI storage servers and map LUNs on them to the windows server as separate "HDDs" That gives a more scalable system with less risk of a single point of failure, apart from the Windows server.

---

### Post by ContagiousIdea on 2011-01-17
Get some of these just in bigger arrays: [http://www.amazon.com/Mediasonic-3-5-Inch-eSATA-Enclosure-HF2-SU2S2/dp/B002UUPWP6/ref=pd_cp_e_1](http://www.amazon.com/Mediasonic-3-5-Inch-eSATA-Enclosure-HF2-SU2S2/dp/B002UUPWP6/ref=pd_cp_e_1)

Then make a raid of each box, then lvm the boxes together to some giant storage... that might work

---

### Post by psusi on 2011-01-17
I read an article not too long ago where a guy picked up a x4 lane SAS controller for like $150, and a 9 port x4 lane sas expander from HP for like $200 and a big chassis to hold all the drives and connect 32 2 tb sata drives to one computer.

---

### Post by Vegan on 2011-01-17
Commodity 16 bay 4U chassis are < $1000 and are fine for storage arrays. A few rows of them can create PB storage quickly.

With 2 TB disks, you would need only 2 such machines for the desired 24TB storage.

Using SAMBA you can even have the Windows based machine save to the network storage easily. No need for a USB stick/drive.

---

### Post by ian dobson on 2011-01-17
Hi,

Just be careful with the file system you use. I think the e2fstools used by ext4 are limited to 16Tb. XFS could be a possibility but a fsck in such a large file system would require huge amounts of ram. Talking about ram I'd recommend 16gb if you have a 24Tb in file systems.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-01-17
Hi,

Just be careful with the file system you use. I think the e2fstools used by ext4 are limited to 16Tb. XFS could be a possibility but a fsck in such a large file system would require huge amounts of ram. Talking about ram I'd recommend 16gb if you have a 24Tb in file systems.

Regards
Ian Dobson

---

### Post by Fire_Chief on 2011-01-17
> **cascade9 said:**
> 24TB is possible with 1 machine. You'd need a big case, and most of them top out at about 12-13 HDDs. Also a RAID card, and 8-12 port RAID cards arent cheap. 

With a 12 port RAID card, 12 x 2TB drives, you'd get 24TB. Thats without RAID reduncancy, which in the case of RAID 5 would drop the usable stoage to 16TB. You could use 3TB drives, for 36TB total, and 24TB usable storage, but I'm not sure about how the new advanced format drives would deal with RAID (and all the 3TB drives I've seen arent 'RAID' models anyway).

You may want to check your calculations for RAID5 arrays. RAID5 usable storage is roughly determined by N-1 * Drive size, assuming all the drives are of identical size. So while 12 drives at 2 TB each is indeed 24 TB of raw space, the RAID5 usable space is 11 drives * 2 TB or 22 TB usable...not 16. Likewise with 3 TB drives, space is 33TB usable in RAID5.

See more info here: [http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5]("http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5")

Cheers!

---

### Post by Vegan on 2011-01-17
RAID6 is far better, can tolerate 2 disk failing. Given disks are all bought at once, not an unrealistic scenario. Keep you job and use RAID6.

That and buy at least 4 extra disks per year the array has to operate so that repairs are quick. A box or 5 of disks is handy in a larger installation so that workers can move fast.

---

### Post by CharlesA on 2011-01-17
With an array with that many drives, I'd go with RAID-6 over RAID-5 for the reasons Vegan mentioned.

---

### Post by theDaveTheRave on 2011-01-17
I like Vegan's point about having a bunch of spare disks, very sensible.

Also, with the use of mount points you could even have the disks separated into separate machines - or housed in separate boxes.

Then have 2 servers seeing the same set of HDD, and use one as a slave in case of failures.

Remember to try to get everything separated, even locations if possible. It is going to add to the cost, but if the data that you are storing is that important you may want to at least give the option of easier disaster recovery to your bosses.

Also 2 servers means that you can have a 'stable system' and a 'test' of the next version of LTS, then simply update the second when you are happy that there are no problems with the newer version - you should investigate how this will affect the various processes if they are of a different version (particularly of your backup software).

And I don't know if you have thought about compressing the data? especially as it gets older - assuming that you aren't going need the older stuff so often.

David

---

### Post by cascade9 on 2011-01-18
> **Fire_Chief said:**
> You may want to check your calculations for RAID5 arrays. RAID5 usable storage is roughly determined by N-1 * Drive size, assuming all the drives are of identical size. So while 12 drives at 2 TB each is indeed 24 TB of raw space, the RAID5 usable space is 11 drives * 2 TB or 22 TB usable...not 16. Likewise with 3 TB drives, space is 33TB usable in RAID5.

See more info here: [http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5](http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5)

Cheers!

Yep. 

Thats what I get for posting at X A.M. and not thinking right... :( 

I was basing that on an old 'rule' that some big iron user was always drumming into me-run a hotspare for every 2 discs. That would be overkill, and to be honest I cant even remember why he had such an extreme number of hotspares. 

+1 to RAID6 (I should never have even siad 'RAID 5 ' with that many discs IMO). 

A huge NAS would also be an option, but from the prices I'm seeing, it would end up as expensive, or more expensive than a RAID6 setup.

---

### Post by CharlesA on 2011-01-18
I have two "offline spares" if one of my drives goes down, but I'm only running a 3-disk RAID-5 Array. The controller I'm using allows for a hot spare, but I don't really want to cram another drive in the case I'm using.

I can see the value of having a hot spare, but with that many disks, I'm not quite sure how it would work.

---

### Post by nutznboltz on 2011-01-23
Given 24 TB and 400 GB/day ingest...

Have you looked into Openstack Object Storage?
[http://openstack.org/projects/storage/](http://openstack.org/projects/storage/)
> OpenStack Object Storage is software for creating redundant, scalable object storage using clusters of commodity servers to store terabytes or even petabytes of accessible data. It is not a filesystem or real-time data storage system, but rather a long term storage system for a more permanent type of static data the can be retrieved, leveraged, and then updated if necessary.

S3 API for Openstack Object Storage is underway [https://blueprints.launchpad.net/swift/+spec/bexar-s3api](https://blueprints.launchpad.net/swift/+spec/bexar-s3api)

or eucalyptus walrus?  It's the S3 compatible component of the eucalyptus stack.
[http://open.eucalyptus.com/wiki/EucalyptusWalrusInteracting_v1.6](http://open.eucalyptus.com/wiki/EucalyptusWalrusInteracting_v1.6)

or HDFS
[http://hadoop.apache.org/hdfs/](http://hadoop.apache.org/hdfs/)

An S3 store can be mounted using [http://code.google.com/p/s3fs/](http://code.google.com/p/s3fs/)

---

### Post by nutznboltz on 2011-01-23
XFS speaks for itself

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706136](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706136)

[http://ubuntuforums.org/showthread.php?t=1646711](http://ubuntuforums.org/showthread.php?t=1646711)

---

### Post by elico on 2011-01-23
definitly i would go for XFS... cause you need storage spetaily file-system...
and specific in your case it seems a storage only system so i think that:
OPENFILER for os will be much more friendly for this specific usage.
but if you want to work on this computer start with basic ubuntu desktop LTS os on raid mirror and... do what ever you want with it.

---

### Post by doogy2004 on 2011-01-23
Have you thought about ZFS for a file system that large?

You may want to check out Solaris 11 Express, Open Indiana, Nexenta Core, Nexenta Stor, etc....

---

### Post by the_one(2) on 2011-01-24
If you are planning to use software raid (you probably aren't) you shouldn't use ubuntu. mdadm in ubuntu is ridiculously out of date.

---

### Post by disabledaccount on 2011-01-25
> **the_one(2) said:**
> If you are planning to use software raid (you probably aren't) you shouldn't use ubuntu. mdadm in ubuntu is ridiculously out of date.Ubuntu uses 2.6.7.1 (AFAIR), Debian has 2.6.7.2 (marked as stable). Newer versions are testing/unstable. If you know about some significant differences between those stable versions, please let me know...

---

