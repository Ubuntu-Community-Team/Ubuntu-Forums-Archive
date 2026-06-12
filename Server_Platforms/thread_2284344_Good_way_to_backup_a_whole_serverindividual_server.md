---
title: "Good way to backup a whole server/individual server files?"
date: 2015-06-28
forum: Server Platforms
---

### Post by Raner on 2015-06-28
What would be a good way to backup 1) a whole server, and 2) individual files on the server?

For 2), I had the idea of creating a remote mount on the server and then copying files into it and then unmounting the remote folder. I would do this via sshfs.

I don't know about my options for 1) since the server will be in use as it is backed up. I am not familiar with many linux backup programs.

---

### Post by nerdtron on 2015-06-28
Backup solutions are posted here quite a lot and there are a dozens of solution fit for different situations

I'm not sure how to backup the whole server because I don't do it. What I backup are the config files on the server and just the list of applications installed. In case of server, just reinstall the server, install the applications and then restore all necessary config files for the programs on the server.

For individual files/directories, you can just create a compressed tarball of your files and them copy them to another machine via network. Tools you'll need is the tar utility for archiving and the rsync utility to remote copy files. This is just a simple way to backup and works quite well for a few server setups.

---

### Post by Raner on 2015-06-30
rsync was something I hear about frequently.

Can I rsync the server while it is running? Can I rsync individual files while they may be opened?

---

### Post by matt_symes on 2015-06-30
Hi

> **Raner said:**
> rsync was something I hear about frequently.

Can I rsync the server while it is running? Can I rsync individual files while they may be opened?

To answer both your questions, yes and yes, although you may not want to backup a file if it is opened for writing as, depending on the file, it may be in an inconsistent state.

I use rsync myself to backup my laptop files to my backup server using WOL to wake up my backup server when I need to backup and then shutdown the backup server afterwards.

Kind regards

---

### Post by TheFu on 2015-07-01
"Server" is a little vague.  The way to backup a file server is different from a DB server which is different from a remote desktop server used by 500 remote users.  The applications running at the time of the backup matter.  

Nerdtron is right - this is a commonly asked question.

There are different techniques for
* bit-for-bit images
* just data
* just settings
* just large media files
* DBs
* Depends on the total amount of data and how often that data changes too.  If the data is 300MB and changes yearly, then daily backups might not be needed.  OTOH, if you have 30G of data that constantly changes, daily, versioned, backups ... or even more often might be required.

sshfs is probably NOT the method to be used if there is more than 500MB of data. Same for tar/gtar/star .... those should probably be avoided. For small data stuff - it is fine, of course.

For servers that need to be up all the time, LVM snapshots might play a part in your backup methodology. 
[https://www.howtoforge.com/linux_lvm_snapshots](https://www.howtoforge.com/linux_lvm_snapshots) but getting the data to a remote location is still necessary.

I use rsync for large media collections where the file contents never change. Versioned backups just don't make sense and the backup storage would be cost prohibitive.

For user data, emails, system settings and lists-of-installed packages, I use rdiff-backup. As things change over time, the backups show the changes. Restoring files from yesterday is trivial - last week, last month, 2 months ago is just a little harder.

For small DBs, I dump the DB to a text file that can be imported, then have rdiff-backup grab it. This ensures the DB data is in a "consistent state" - not corrupted.

So - you can see there are a few different methods base on the needs.

Like nerdtron, I do not backup the full OS. That saves about 4-6G per system in backup storage. For 1 system, maybe that doesn't matter, but for 20-50-200 systems, it adds up - BIG TIME.

Rdiff-backup isn't perfect, but it does work. I've had to restore machines a few times every year and it always worked (after the initial learning was over).  I've tried a few others and tested a restore  from each - the results were less than perfect for me.

If you are manually managing backup sets yourself, you are doing it all wrong.  Backups need to be automatic, quick, efficient with storage and networking.  

One of my servers has 120 days of daily backups. It doesn't hold **any** data, just settings, so all that is backed up is what is needed to restore it to the required state.  It is internet facing, so high risk, hence the 120 days.  How much backup storage is needed for this? ... 
```
# rdiff-backup --list-increment-sizes spamcache
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed Jul  1 01:10:05 2015         16.1 MB           16.1 MB   (current mirror)
Tue Jun 30 01:10:07 2015       279 bytes           16.1 MB
Mon Jun 29 01:10:05 2015       279 bytes           16.1 MB
Sun Jun 28 01:10:05 2015       992 bytes           16.1 MB
Sat Jun 27 01:10:05 2015       832 bytes           16.1 MB
Fri Jun 26 01:10:05 2015       279 bytes           16.1 MB
Thu Jun 25 01:10:06 2015       279 bytes           16.1 MB
....
Mon Apr  6 01:10:05 2015       280 bytes           16.1 MB
Sun Apr  5 01:10:06 2015       280 bytes           16.2 MB
Sat Apr  4 01:10:05 2015       643 bytes           16.2 MB
Fri Apr  3 01:10:05 2015       280 bytes           16.2 MB

```

Looks like 16.2 MB.  Why wouldn't I have 120 days when that is all it needs?
How much time do backups normally take?```

=== Time for Backups to spamcache === 
StartTime 1435727405.00 (Wed Jul  1 01:10:05 2015)
EndTime 1435727410.35 (Wed Jul  1 01:10:10 2015)
ElapsedTime 5.35 (5.35 seconds)
TotalDestinationSizeChange 279 (279 bytes)
```
Looks like 5.4 seconds. Nice.  Of course this is a highly specialized server.

For a file server, things take a little longer - about 7.5 minutes.
For my desktop, just under 5 minutes.  It is only 14G in total storage.
Pretty efficient on time.

Blog server ... 1.5 min to backup/  It doesn't have much data - less than 2G.

Hope these data points help you decide.

Oh ... and the old school backup schedule with weekly fulls, then daily incrementals is just crazy unless you use some old-school backup tool like backula or dump and restore (really old-school). [http://blog.jdpfu.com/2009/03/25/backup-schedules-and-retention](http://blog.jdpfu.com/2009/03/25/backup-schedules-and-retention)

Lots of options.

---

