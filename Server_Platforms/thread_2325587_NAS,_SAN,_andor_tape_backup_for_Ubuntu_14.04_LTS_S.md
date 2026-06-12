---
title: "NAS, SAN, and/or tape backup for Ubuntu 14.04 LTS Server"
date: 2016-05-23
forum: Server Platforms
---

### Post by c_xy on 2016-05-23
Hello,

We are interested in purchasing and creating a backup system for our Dell r730 poweredge server. We are running Linux and Ubuntu 14.04 LTS.

We were looking at some of backup options Dell provides:

NAS

[http://www.dell.com/us/business/p/powervault-nx/pd?oc=pv_nx3330_1060&model_id=powervault-nx](http://www.dell.com/us/business/p/powervault-nx/pd?oc=pv_nx3330_1060&model_id=powervault-nx)


With the NAS, all of Dell's products have Windows Storage Server installed on them. We want to have the ability to use rsync. Is this possible transferring files from our Linux Server to the NAS with Windows Server Storage pre-installed.

iSCSI SAN
[http://www.dell.com/us/business/p/powervault-md32x0i-series/pd](http://www.dell.com/us/business/p/powervault-md32x0i-series/pd)


We are not too familiar with SAN. Is there any advantage of using a SAN vs. NAS?


Tape backup

[http://www.dell.com/us/business/p/powervault-tl2000/pd](http://www.dell.com/us/business/p/powervault-tl2000/pd)


We want to somehow combine either SAN/NAS with the tape backup. That way, we will have to forms of backup. One to disk, and the second copy to tape.

Any input, suggestions, or feedback would be appreciated.


Thank you.


c

---

### Post by TheFu on 2016-05-28
Since nobody else responded ... 

The amount of storage determines the best backup solution, but so do the RTO and RPO requirements.  Wikipedia can explain those terms. A good worksheet to help the client determine those values, will go a long way towards ensuring the budget meets the requirements.

SAN - Storage Area Network
NAS - Network Attached Storage

These can be the same or very different.  NAS is usually over IP and SAN was over fibre channel the last time I touched it, but it could be a dedicated IP network too. A fibre channel network requires different HW and skills than an IP network.  Plus there are lots of headaches with FC cards and drivers that might be best to avoid.  Which is better is dependent on the number of servers, size of the storage, reliability needed and how flexible the storage reconfiguration needs to be.

It is impossible for someone over a forum to gather all the facts necessary to make a good decision.  Perhaps you need to engage an enterprise or technical architect with the skills needed to help make that informed decision? Depending on where you are located, I might know someone who can help.

I doubt Dell would limit their storage products to only work with Windows, but I haven't touched Dell enterprise stuff recently.

Not sure I'd use straight rsync for backups.  Take a look at rdiff-backup for starter setups, but if you have over 25 physical machines, an enterprise backup tool starts to make sense.

Do NOT mount backup storage on the machines to be backed up. That's a good way to have both the machine AND the backups encrypted by malware.  Use a C/S backup architecture.

---

### Post by darkod on 2016-05-28
If you have only Linux machines, why would you buy a server with Windows Storage Server? That way you pay for a license that you don't really need, and that you will have complications to fully integrate into your network. Plus you will end up with paid OS version that you can't even upgrade free of charge in the future.

I would buy a server with no OS so that you can install ubuntu/linux on it too. Even if it's not Dell (in case there is no product without an OS).

You can even set up ZFS on it, because in many cases that's a perfect setup for large storage.

As for doing the backups (if that's the primary role), no need to even export it as NFS or similar. You can set it up as bacula server that can take backups of all of your clients. Of course, you can set up NFS if that's what you want, and use it as you wish...

---

### Post by TheFu on 2016-05-29
Plus with ZFS, you can take advantage of zsend for backups!  That would minimize the time and have the production servers doing production work ASAP. The backup server could stream data to tape, if that is still desired.  

Don't forget to rotate the tapes off-site.  At my last job with stuff like this, we did backups locally, then pushed the data both 500 miles away to a different location AND streamed to tape storage which was rotated offsite daily by a service.  Never needed to get backups back from offsite - the locals were used ... once ... in 8 yrs there. 

It was a really bad day and left 22K people unable to do their jobs while the data was being restored.  My design included 20 min recovery capabilities, but the client always prioritized other things in the maintenance windows for over a year, so it wasn't setup.  Well, after that outage, they couldn't finish that part quickly enough ... they'd already paid for everything needed for it over a year earlier. We had all the required storage, all the professional services, just needed the maintenance window and approval to do the work from the client.  Then we suggested some other optimizations and the client chose to do everything in the worst possible order, with the highest risks and most effort to make things better.  We were moving from a 4-way strip to a 16-way stripe for the DBMS storage.  Amazing how well my memory works for THAT effort. ;(

---

### Post by gordintoronto on 2016-05-30
If you could give some indication about how much data needs to be backed up, and how volatile it is, you would get better help.

My largest client runs Windows Server, with about 700 GB of data on the server. A daily incremental backup is typically less than 6 GB. Because they archive all backups, they were spending several hundred dollars a month on tapes.

We set up a fairly modern computer on the network, running Xubuntu, as a "backup server" I installed a "quick change" drive bay so we could install a new drive in a couple of minutes. We're spending about $100 (U.S) a month on media, and the backup runs over the gigabit network five times as fast as to a local tape drive! We installed the server version of Macrium Reflect on the server.

It has been so successful that we are also backing up a dozen workstations to an external drive attached by USB 3, to the same Xubuntu computer. We have a tight schedule so there is only one backup running at any given time, otherwise the network collapses.

---

### Post by houstonbofh on 2016-05-30
First, Dell storage right now is a bit of a mess.  They got much of their storage from acquisition, and them promptly laid off the people that came with it.  This means there own knowledge of Equalogic and Compellent is a bit off... :)

Second, Windows Storage server is a complete mess, even for an all windows shop!  Not trivial to set up, and not cheap!

Now thew SAN vs NAS...  In this case, the Dell SAN you have listed is iSCSI only, and you will need another server (or two or three) to front end for it.  Again, not cheap.

Now...  A storage server is not magic.  It is a computer with a lot of disks.  In advanced cases, it is two computers and two batches of disks in one case, cross connected.  This can all be done with FOSS.  Get any old server with a bunch of full sized disks and ditch the Perc card.  Set the drives up in IT mode, and install Nas4Free (or freenas or build your own)  With NAs4Free, you get rsync, NFS, iSCSI, CIFS, Appletalk, FTP...  And ZFS for snapshots.  And it can tie into AD, so it will work for file services and backup.  And best of all, you can mount the same section of files with CIFS and NFS so you can have Windows and *nix share the same files transparently!

As for tape...  Unless you need a LOT of storage, hard drives are cheaper.

---

### Post by JulieONeilEMC on 2016-05-31
Have you looked at EMC's Data Domain?  It might be the perfect fit for your company.  You can learn more at the EMC Store.  [http://bit.ly/1saguIe](http://bit.ly/1saguIe)

---

### Post by c_xy on 2016-06-01
Everyone,

Thanks for the feedback. A lot of great suggestions. Very helpful.

I'll try to go into detail more about our setup:

Right now, our r730 server contains about 10 TB worth of data used. Maximum capacity is about 27 TB.

Roughly 10-30 GB per week are added to the server. This can vary, sometimes less, sometimes more.

darkod, it didn&#8217;t really dawn on us about simply purchasing another server without an OS and just installing Ubuntu LTS server on it. We could do that.

As TheFu suggested, we don't want to mount the backup server drives to the r730. We want to transfer files over the network. rysnc is what we are most familiar with and had success using it the past. We&#8217;ll look into rdiff
RTO and RPO aren&#8217;t crucial. This is a small workgroup (15-20). However, the data we analyze is quite large.  Initially, we receive the data in raw format on DVD&#8217;s. Once we upload and convert the data for analysis, this is when the subsequent analysis files begin consuming plenty of space.  Analysis is typically done with automated scripts. In the event of data loss, we could recreate these files from scratch. That is the worst case scenario and would take a long time. Therefore, we&#8217;d like to have two forms of backup with disk drives and tapes.

Here is the potential setup:

r730  **----------  > weekly backup via rsync  ---- > backup rack server  ----- > monthly  backup to tape ----- > LTO tape autoloader
 
In this setup we would have two forms of backups: disk and tape. The r730 has a raid5 hardware setup. We should probably setup the backup server disk drive with a raid 6 setup, which would allow for two hard-drive failures.  How does this sound?
We also looked into FreeNas. What would be the advantages/disadvantage of using FreeNas vs Ubuntu for the backup disk server?
 
For the tape drive, should we connect it directly to the backup server? Or should we write to tape over the network?

Thanks again everyone. Again, any suggestions, feedback, etc are much appreciated.
 
c

---

### Post by gordintoronto on 2016-06-01
Good to get some real data!

Have you tried to obtain performance data for your various options? In my scenario, there are many small files, which slows things down. For 10 TB of the kind of files my client has, you're talking 30 hours to back up over a gigabit network. The tape drive we were using took five times as long; I assume the latest drives are faster. However, the biggest LTO cartridge holds 6 TB, so you would need to find a way to back up half the data, then back up the other half separately.

A lot of NAS units are real stinkers; they are much slower than a modern desktop running Xubuntu, for example. Ubuntu Server with no GUI might be significantly faster, think 50% in the best case. Setting things up using the command line will be about the same, since Xubuntu does not include the easy GUI way to set up shared folders.

---

### Post by TheFu on 2016-06-01
For that amount of data I´d use 10G on a dedicated backup network - add more NICs to meet the backup window.  Streaming to tape can take a week, since they don´t care about RTO/RPO at all.  Run the numbers.

Definitely use snapshots to make the backups not need any downtime.  GUI or not shouldn´t make any performance difference on systems like he needs. Not like he´s gonna throw a Core i5 at this. He´ll use a Xeon something, I hope.

Lastly - **rdiff-backup**, not rdiff.

---

### Post by MAFoElffen on 2016-06-02
Just a note on something else to factor in... If you are private then ignore this. 

If you are public and in the USA, and you may have some source from federal funding ... you may have have any federal mandates that affect your backups and what they can be written to... I was told by an educational institution that I was involved with that they had mandates they had to conform to. They could do their local backups to disk (disk is cheap and fast) but were required, because backups contained sensitive personal data, that any backups that left their main campus had to be on tape. For some reason, that offsite backup data could leave on disk. 

Has anyone else heard of that?

---

### Post by houstonbofh on 2016-06-06
> **c_xy said:**
> In this setup we would have two forms of backups: disk and tape. The r730 has a raid5 hardware setup. We should probably setup the backup server disk drive with a raid 6 setup, which would allow for two hard-drive failures.  How does this sound?
Hardware raid is very hardware dependent.  And not really faster then software raid these days.  So if the Perc cards goes out, do you really want to be stuck waiting on Dell?
> **c_xy said:**
> We also looked into FreeNas. What would be the advantages/disadvantage of using FreeNas vs Ubuntu for the backup disk server?

Easy.  FreeNas and Nas4Free are easier to set up and manage.  Also they have a more standards compliant and more mature implementation of ZFS, and ZFS is amazing for file storage!  Snapshots rock!  As for which one...  This is a little old now, but while the specifics have changed the overall impression has not. 
[http://arstechnica.com/information-technology/2014/06/the-ars-nas-distribution-shootout-freenas-vs-nas4free/](http://arstechnica.com/information-technology/2014/06/the-ars-nas-distribution-shootout-freenas-vs-nas4free/)

---

