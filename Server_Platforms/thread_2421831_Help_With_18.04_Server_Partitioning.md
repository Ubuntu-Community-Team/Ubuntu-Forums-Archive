---
title: "Help With 18.04 Server Partitioning"
date: 2019-06-27
forum: Server Platforms
---

### Post by ewm on 2019-06-27
Hi, I have read through many articles on this forum and the general web regarding partitioning of a server and I get more confused with every reading.so would appreciate some advice. I am configuring a server for our local museum for internal use only. We have been donated  a machine that has 1x250Gb SSD and 2x500Gb SSDs. The Server will be running as a LAMP system with a custom web based interface. The thinking is to use the 250Gb drive for the operating system with at least a separate /home directory. and put /var/www on one of the 500Gb drives. Use the other 500Gb drive for say a weekly backup of the first 500Gb drive. We also have 2X1Tb external HDDs for offsite backup purposes. The 250Gb drive is more than adequate for the OS plus the LAMP software. I cannot foresee a situation where the 250Gb drive will run out of space. Would it be advisable (possible) to put the /var/log onto the left over 250Gb space.? I know that there are many varying opinions about this subject but as one person put it "don't overthink about it" Any help would be gratefully received.

---

### Post by TheFu on 2019-06-27
I'm a little tired now, so hopefully this will make sense.

If this isn't a system that needs to be available all the time, simplicity is the best choice.  Don't hook up storage that you don't need.  For most quality SSDs, the lifetime is determined by the TBW.  Check all the disks, including the SSDs for those values.  You'll need both the actual values using **smartctl** and the warranty amounts for each disk.  Pick the disk with the most remaining TBW and use that.  Remove the other SSDs from the system. Extra storage inside a machine tends to get wasted.  Lots of storage makes backups longer and more complex.  Keep it simple. Only the storage you actually need should be allocated for use.

For a single web server, in a non-critical role, I'd have only enough storage connected as required.
The OS won't use more than 25G, so even the smallest SSD will have over 200G free for other stuff.  That would be a huge website.  Huge.
I wouldn't put logs or swap onto other disks.

As you read elsewhere, don't over think it.  1 drive.  Partitioned simply.  If you are new, don't go crazy.  If you understand LVM, use that to make resizing the LVs easier later.  If you are willing to learn about LVM, then you can let the installer setup the LVM stuff and resize the LV for the OS down to 25G, create an LV for /var/www and size it with about 25G to start (or whatever size you know the website will require).

BTW, I follow this practice.  I've allocated less than 50% of the available storage on my systems.  I use LVM.
```
$ sudo vgs
  VG        #PV #LV #SN Attr   VSize   VFree   
  ubuntu-vg   1   4   0 wz--n- 464.54g 260.08g

```
260G free out of 464G available.  That's just what is allocated to LVs.  Each LV is about 50% empty.  For me, LV/partitioning is all about backup and disaster recovery plans.

If you want better help, boot off a USB flash drive with any Ubuntu Desktop release and run **inxi -Fz**, then post those results using code tags. This will provide an overview of the server hardware.  If the output posted here doesn't line up like it does in a terminal, try again with the code tags.

---

### Post by ewm on 2019-06-28
Hi, Thank you for your response which has helped clarified my thinking. A word on the storage space, we are currently digitising our museum archives that contain lots of documents and photographs. I could recommend maximum resolutions for the scanning of these items (60 years worth of collecting) but nobody knows how much storage space it will all eventually use up, hence the 500Gb drives. 
After reading your comments I am leaning towards taking one of the 500Gb drives and carving out a portion for the normal /root /home partitions and then using the balance for the /var/www partition in LVM format. This last partition could if necessary be extended onto the 250Gb drive whilst the remaing 500Gb drive can be kept as a spare.  I suppose there is no real correct answer as to how everything should be configured but I would appreciate your comment on my proposed arrangement.
Again many Thanks

---

### Post by TheFu on 2019-06-28
Either use LVM or don't.  Don't mix and match.  /home/ shouldn't need to be a separate LV on a server. It isn't like anyone will be using it.  The admin and document management people might have a few scripts there, but they shouldn't have room to store data there.  
I suspect you are confused about /root vs /.  /root == the root userid's HOME. It should have very little inside it. Perhaps a backup script and some server config setting backups. In short, there's no reason for /root or /home to be separate on a server 99.9999999% of the time.
/ is the LV/partition where everything else mounts. Usually it is the LV were the OS and everything not personal for a userid would be stored.  Best not to confuse / and /root/.

As for LVM, let the installer handle it during install, then reduce the / LV to be 25G and create /var/www/ to be whatever size you KNOW you will need, but not the full amount available in the VG.  With SSDs, it is important to not use 20% of the storage to vastly improve storage life. I would start with 100GB for /var/www/.  You can increase the size as needed while the system is live if you use LVM and EXT4.  A DBMS can be actively writing during this process.  Reducing the size of an LV is also possible with EXT4 as the file system, but the file system needs to be unused (not mounted) for that to happen.  In short, it is 5 seconds to increase the size, but a major hassle to reduce it.

I have some professional experience with document management, both in govt and private worlds.

Scanning paperwork above 300dpi is a waste of storage. You also need to try using OCR and ensure that at least the metadata about every document is accurate.  The single most important thing about any document was the creation date.  Scanning usually doesn't get got OCR results, so if you can, get the original computer file for any documents you can.

If a document cannot be found using full text search which weighs the metadata slightly higher than the text, then it is worthless.  A document that can't be found isn't worth having.

I won't pretend to know the resolution for historical documents, but whatever it is, it still needs correct metadata.  Anyone who needs really high resolution scans should probably make their own, as needed.

I don't know what you know about PDF.  PDF files have versions and F/LOSS Linux doesn't support versions later than v1.6 much.  For v1.7 and later PDF files, you'll either need paid, commercial tools, or accept they cannot be read by most F/LOSS parsers/search indexing tools.

If you haven't looked into DMS already and don't have a strong preference, I was an enterprise architect at an enterprise on the DMS standards team.  I've used a bunch of different DMS and selected a few for projects and ran an Alfresco setup for a few years.  That was over 10 yrs ago, but the main issues still remain from what I can see.

---

### Post by ewm on 2019-06-28
I take your point about not mixing and matching and no need for a separate home partition. I have been running a test set up on an old computer at home the and Collection Manager software allows for the uploading of original PDF documents and the Universal Viewer allows searching within these documents. I have tried this out and it works well. The bulk of the archives is however comprised of typewritten or hand written documents. Many of them particularly the ones written in ink are fading and the paper has become friable. These documents need to be captured electronically before they deteriorate much further.
We will figure out the best way to handle these documents by experimentation before doing the serious cataloging. The first thing is to get the working server up and running so that the digitisation of the accession records can start.
Thanks for your advice, it has certainly simplified the way forward. One final question you say that for SSDs one should keep 20% of the total storage space unused. What happens when the usable space becomes full and you add another drive to the LVM, do you leave the 20% unused on the first drive and add 20% of unused space to the second i.e do you just partition each drive to appear 20% smaller than the actual size?

---

### Post by TheFu on 2019-06-29
For SSDs, we have to remember that the controller inside the SSD is constantly converting the physical storage information into the logical storage we see. It is performing wear levelling behind the scenes. Our partitions and PVs have very little to do with the reality of SSD internal storage layout.  20% is a round number not some perfect answer to all "how much" questions. Better quality, enterprise, SSDs have more built-in over-provisioning. By providing more on our own, we are simply helping the SSD last longer. 
[https://www.kingston.com/us/ssd/overprovisioning](https://www.kingston.com/us/ssd/overprovisioning)
[https://www.seagate.com/tech-insights/ssd-over-provisioning-benefits-master-ti/](https://www.seagate.com/tech-insights/ssd-over-provisioning-benefits-master-ti/) 

LVM is freakin' amazing!  Best to find an LVM guide that explains things.  PVs can be moved to new/different partitions, resized, etc.  

Same for VGs, which can be merged, reduced, converted, exported, imported, ... 

The superpower for LVs is resizing and converting between linear, stripped, mirrored setups.
Many of these things can happen while the storage is online. If a VG has plenty of room, unallocated, then extending an LV is about 5 seconds of typing.

---

### Post by ewm on 2019-06-29
Thanks a ton for your help - I have done some more investigation and will also follow up on your links. Have a good weekend.

---

