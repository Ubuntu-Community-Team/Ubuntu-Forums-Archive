---
title: "Ubuntu as a Network Backup Server"
date: 2019-10-01
forum: Server Platforms
---

### Post by slkamath on 2019-10-01
Hello Everyone,

I have assembled system with below configurations

RAM - 8GB
Processor - i5, 4th gen
Board - Intel Server Board
HDD - 500GB UBUNTU 16.04 Server OS,
HDD - 10TB Storage

I want to make this system as Network Backup Server. So I want that backup as below mentioned way.

we have nearly 50+ systems and in that nearly 40 Systems are Ubuntu with all the variant (12.04 to 18.04). In that I have installed Samba and made one folder as Backup and I want that to be backed up from the Server (without going to the client systems). So someone please guide me which better way I can do this backup from server system?

We have 1 NAS backup from Netgear and in that there is ReadyNAS software through this I am doing the backup from server (without going to client systems). 

Like that any software which I can install Ubuntu Network Backup Server so that I can configure & controll all the backup from Server.

Many thanks in advance.

Lokesh Kamath

---

### Post by deadflowr on 2019-10-01
Something like bacula maybe.

---

### Post by slkamath on 2019-10-01
Thank You.

In Bacula can i track the backup from server?

Lokesh Kamath

---

### Post by TheFu on 2019-10-01
Don't use samba. That is a terrible solution and loses 50% of what you need in a backup.  

Don't use any network file sharing protocols, unless you want malware to be able to destroy your backups too.  You want the server to "pull" the backups. They need to be encrypted, transmitted over an encrypted network tunnel, network and storage efficient.  Having the backup storage encrypted would be smart too.  Imagine if the HDD needs warranty work. Would you really like to ship it somewhere holding all the backups for all those systems, unencrypted?  I have some dead, non-encrypted, disks here, because we chose not to send them in for warranty. 

Any disk over 4TB in size, we partition to have no more than 4TB partitions.  This is a backup/recovery choice for us.  I know I can get 4TB disks for under $100 easily without hassles for spending approval.  10TB disks are harder to get without that hassle, so it is just easier to keep partitions limited in size.

If the clients are running ZFS or LVM, then you can create a snapshot of the running system and mount that snapshot to create the backups from. Selectively pulling only the information needed.

[LIST=1]
[*]Create pre-backup data to make restoring packages, storage layouts, LVM/ZFS stuff easier. Place that data where it will be included in the backups.
[*]Create a list of installed packages - apt-mark
[*]Dump any DBs to text files. This is less important if LVM snapshots are used. mysqldump
[*]Remove any unwanted cruft BEFORE moving on. I remove all flash/html5 "local objects" and browser cache files, for example.
[*]Run any pre-backup scripts, if any exist.
[*]Create any LVM snapshots. This is instantaneous.
[*]Mount the LVM snapshots somewhere on the client, perhaps /mnt/ss
[*]Use an excellent "pull", versioned, backup tool launched from the server to "pull" the snapshot data. rdiff-backup
[*]umount the LVM snapshots
[*]delete any LVM snapshots
[*]Run any post-backup scripts, if any exist. If LVM isn't used, perhaps restart a web server or DBMS server?
[*]Remove any backup versions older than needed. 180 days is common 
[/LIST]
Backing up everything is a waste of time and storage, especially on systems that run the same OSes.  The only reason to backup everything is if the team performing the restore are idiots and need 1-step processes.  However, backing up everything makes moving to different hardware more difficult / impossible for Windows due to license keys and picky check on motherboards.

With rdiff-backup, it is best to only have 1 backup command involved. This is why all the snapshots need to be created and mounted before the backup command is run.

It should be clear that the backup server must have ssh access into each client using ssh-keys.  It should connect as a root-equiv account, but not as root.  I'd have the pre-backup/post-backup scripts scp'd to the client system initially. That way, the name and location and management of those scripts is centralized on the backup server. 

That list of steps is for each system. In general, the backup storage will be the slowest part of this system, so having only 1 client backup running at a time is smart.  Most of my backups take 2-8 minutes nightly, but some servers take 20-30 minutes.  If you have 50 servers, the backups won't complete in the backup window.  You'll need to be more selective about which systems get backed up every day or get more hardware and faster networking.  Perhaps making desktop backups every other day would spread the time commitment sufficiently?  

Any unsupported OS needs to be taken off the network ASAP.  All unsupported Linux systems have remote root access if they aren't under paid maintenance and patched.

As to the details for each of these steps, search these forums. I've been part of multiple discussions. 2-3 months ago, someone else posted their script using LVM snapshots. While they didn't do all that I suggested, they seem to be happy.

As for backing up non-Unix systems, I cannot help.  I take the few Windows systems down every quarter and make an image-based backup.  It is terribly painful.  Every attempt to get a clean backup for them without imaging the disks has always failed.  We don't leave any important data on Windows overnight. It is all written to a Linux server which is included in our backups.

Hopefully, this is useful.  I am worried about the daily backup window not being met.  Inside enterprises, we routinely run up against that requirement and would have to add more tape drives to 10Gbps backup servers to support the necessary overnight backup window. It was mostly for weekends when "full backups" were performed.  rdiff-backup doesn't do "full" backups after the first one. From that point forward, the last backup looks like a mirror (a la rsync), but ownership, permissions, ACL changes over time are also maintained with rdiff-backup.  All that data would be lost if samba was used with the most efficient *nix backup tools.  rsync, and other hard-linked versioning techniques have the issue with losing permissions over time. Only the most recent permissions are retained.

Bacula is a popular tool for mixed environments. I decided it against deploying it, but it might work for your needs.

As to exactly WHAT gets included in the backups, that is completely dependent on the system purpose. We do not backup the OS, for example.  For our email gateway, 180 days of backups is ... let me check ... 140 MB. It only contains settings and firewall rules and package lists.  Rebuilding it takes just a little over 20 min.  My main desktop backs up a little over 7GB and only retains 60 days of versioned backups. Total storage used is just under 8GB for all those versions.
Different servers backup different things. In general, restoring from backups will take 30-45 minutes, clock time. Usually about 5 minutes of admin time to follow the documented restore procedure for each system. They are all snowflakes, but the restore process begins by doing a fresh, minimal, Linux install with only the ssh and rdiff-backup tools included.

There are lots of other methods too.  Versioned, encrypted, daily, "pulled" is what matters. Being efficient with storage might be secondary for many. It wasn't for me.  Over the last 25+ yrs, I've tried many, many different backup solutions. Free, commercial, simple, GUI, scripted.  With and without virtual machines.

---

### Post by slkamath on 2019-10-02
Thank you so so much.

You have given the brief & your over all experience in this. I will try with Bacula.

Once again Thank You so much. If I get any doubt I will ping.

Lokesh Kamath

---

### Post by mastablasta on 2019-10-02
have a look ar UrBackup and BackupPC.

here is a wiki list: [https://en.wikipedia.org/wiki/List_of_backup_software](https://en.wikipedia.org/wiki/List_of_backup_software)

---

### Post by slkamath on 2019-10-02
Thank you so much.

I will check and ping you for any doubt.

Once again Thanks.

Lokesh Kamath

---

