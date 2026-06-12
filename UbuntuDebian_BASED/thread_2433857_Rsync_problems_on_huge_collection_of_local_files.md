---
title: "Rsync problems on huge collection of local files"
date: 2019-12-26
forum: Ubuntu/Debian BASED
---

### Post by Alistair George on 2019-12-26
I have a 450Gb USB drive which has backintime/rsync backups I wish to move to a new 4Tb Seagate USB. 
I have tried various rsync options to move the desired directories and thousands of files about 50Gb, and each time after about a day or so, the Seagate just sits there acting like data is being transferred, but its not. I can kill the rsync process and the Seagate keeps flashing (data active) with nothing being sent. After ages, the drive stops. But rsync never completes the backup process; Ive tried several times typically:

sudo rsync -aHPqs --safe-links --ignore-existing --max-size=200m /media/alistair/USB450G/backintime/alsmain_2018/root .

rsync seems to run for say 4 hours without any problem, then gets slower, then there is a choking - I can tell this by checking destination directories.

Destination is NTFS and has been checked several times for errors (under Windows) its brand new. Source is another smaller Seagate 500Gb ext4 also checked using gparted.

This has got me stymied. Why should rsync gradually choke? System resources are not being hogged by anything under task manager used swap is well below available, cpu is running around 5-10%, nothing seems untoward.

Any ideas?
Thanks,
Alistair.

---

### Post by howefield on 2019-12-26
Support thread, so moved to the "[s]*General Help*[/s] "*Ubuntu/Debian BASED*" forum.

What version of Ubuntu are you using ?

```
cat /etc/*-release
```

---

### Post by Alistair George on 2019-12-26
Apologies:
```
DISTRIB_ID="elementary"
DISTRIB_RELEASE=0.4.1
DISTRIB_CODENAME=loki
DISTRIB_DESCRIPTION="elementary OS 0.4.1 Loki"
NAME="elementary OS"
VERSION="0.4.1 Loki"
ID="elementary"
ID_LIKE=ubuntu
PRETTY_NAME="elementary OS 0.4.1 Loki"
VERSION_ID="0.4.1"
HOME_URL="http://elementary.io/"
SUPPORT_URL="http://elementary.io/support/"
BUG_REPORT_URL="https://github.com/elementary/"
VERSION_CODENAME=loki
UBUNTU_CODENAME=loki
```

Note Ive tried using other boot images eg elementaryos-5.1-stable.20191202.iso slitaz but problem persists.

---

### Post by TheFu on 2019-12-26
The target cannot be NTFS if you expect to use any backup that uses hardlinks for versioning.  Back-in-Time does. And since Unix backups **Must** retain not just the data and directories, but the owner, group, permissions, ACLs and xattrs as well, rsync to NTFS will drop most of those and will not be useful for system-level backups.

In short, if you must use NTFS as a storage target, then you'll need to use a different backup tool, like **duplicity** which stores not just the data but the file metadata inside the backup "chunk" files.

If you can change to a native, Linux, file system like ext4 or ZFS or xfs, then all sorts of other, extremely efficient, backup tools are possible.

---

### Post by Alistair George on 2019-12-27
Hi there Fu. Thanks for suggestion. I was under the impression that ntfs-3g allowed keeping most of the permissions and link that ext can do.
However, I dont think that is the cause for the problem I am experiencing, which is really slow rsync performance and file performance in general to this new Seagate 4tb drive.
What you may be suggesting, is that the EXT file system works a lot faster with Ubuntu than NTFS file system which may be the case. Im going to drop down to Windoze and do some speed tests on same drives and report back.
Also plan to format partion part of the 4tb as ext4.
Below are performance of my 2 external USB Seagate drives - the ext formatted one has excellent response, the ntfs 4Tb one has an alarming deteriorating poor response, with unusual write twice as high as read.
[4Tb drive]("https://imgur.com/YlwHc0W")
[450Gb Drive]("https://imgur.com/hmymvdJ")
Its weird how erratic the 4tb performance is,

---

### Post by vidtek on 2019-12-27
I have tried doing exactly what you are doing and have run into the same problems.  I tried every backup under the sun rsync, timeshift, just in time, clonezilla, fsarchiver, and several windaz efforts I just got totally frustrated.  Slow backups, timing out and sometimes they just sat there for days on end.

In the end I just went out and bought  a couple more hdd's the same size as my data drive 4tb and my multimedia drive 5tb and every month yank them out and clone them with a welland dual docking solution.

That way I know all my documents, photos videos and other digital stuff I have accumulated over the last 40 years of computer stuff is still there.  I even have a database programme I wrote in 1986 written in Dbase3 for all my customers in my tv repair shop in Western Australia when I lived there and all their details, no privacy issues back then!

---

### Post by TheFu on 2019-12-27
> **Alistair George said:**
> Hi there Fu. Thanks for suggestion. I was under the impression that ntfs-3g allowed keeping most of the permissions and link that ext can do.
No. That is incorrect.  That part of the code has never worked well enough to trust.  I had it working about 2 weeks last May.  Then came back to it a later and all the permissions and ownership was lost. DO NOT TRUST IT.  Don't use NTFS for OS backups of Unix systems.  You can backup data (video and music files) or put full bit-for-bit image backups (fsarchiver) on NTFS, but for anything else, it is next to useless.

It is your time and data to waste, but you've been warned. 

> **Alistair George said:**
> However, I dont think that is the cause for the problem I am experiencing, which is really slow rsync performance and file performance in general to this new Seagate 4tb drive.

NTFS uses FUSE drivers on Linux. It isn't able to be fast. No FUSE file systems will be as fast as a kernel driver will be.  There is a mount option that can help a little big_writes.  Add that to the fstab mount data for the NTFS storage.

How can I say this nicely.  Seagate has earned a poor reputation for storage sized between 750GB and 6TB.  There are published reports from a backup storage provider, backblaze, who buys hundreds of thousands of HDDs from every vendor about the failures of different vendors and different models of storage. Their reports showed that seagate drives had about 2x the failure rates of all other vendors for certain sizes. The good news is that seagate appears to have solved that problem with 8TB and larger HDDs and actually has much better than average failure numbers, if that makes sense.

> **Alistair George said:**
> 
What you may be suggesting, is that the EXT file system works a lot faster with Ubuntu than NTFS file system which may be the case. Im going to drop down to Windoze and do some speed tests on same drives and report back.
Not all EXT are the same.  EXT3 and EXT4 are 1000x better from ext2, which isn't journaled. I use ext4 for all file systems unless there is a specific reason to use something else.  

> **Alistair George said:**
> 
Also plan to format partion part of the 4tb as ext4.
Below are performance of my 2 external USB Seagate drives - the ext formatted one has excellent response, the ntfs 4Tb one has an alarming deteriorating poor response, with unusual write twice as high as read.
[4Tb drive]("https://imgur.com/YlwHc0W")
[450Gb Drive]("https://imgur.com/hmymvdJ")
Its weird how erratic the 4tb performance is,

Sorry, I can't/won't see those images. I don't know much about Windows.  Try to avoid it as much as possible.

---

### Post by Alistair George on 2019-12-29
//NTFS uses FUSE drivers on Linux. It isn't able to be fast.
Your comment would apply if the drive was working as claimed, but I am now convinced the Seagate Expansion drives are junk as far as decent overall speed is. What Ive found is that windoze deleting files from the Seagate is as slow, or slower than ntfs drivers under Elementary OS, which is also jolly slow. 
With the view of partitioning to existing NTFS and EXT4, I decided to remove the hundreds of thousands of files from Backintime to make the re-partition faster.
I tried rsync: sudo rsync -av --delete "/media/alistair/Seagate Expansion Drive/backups/alsmain_2018/empty_dir" * //empty_dir is an empty directory
that was still slow, so used 
sudo rm -rfdv *
Still slow, so dropped into a Windows Live mode and tried there which was even worse. The IO tested speed on the Seagate under windoze was fine around 44mbs, but using any utility (and command) to delete thousands of files ground the drive down to a snails pace.
Back to linux, and having tried to delete the same bunch of files previously using rsync and rm, I found a perl script that was so much faster, and left no dross as the other delete methods had I was amazed.
Ive been programming for over 40 years, in 7 programming languages except perl; to me is a totally weird language, but crikey it works and I have no idea why it should be so much better than terminal calls which are direct OS but it is massively better.
5,000 files deleted off the same ntfs mongrel Seagate drive in 5-8 seconds, with no refuse eg 'unable to open file' crap some other methods did.
Ive modified the script to suit, if you dont understand, dont ask, but please be careful if you use it.

> #!/usr/bin/perl
# FastRemove - remove whole directory trees like rm -r
#moded by A George; use at your own risk!
#EXAMPLE call under linux or windows: perl /home/alistair/perl/fastremove.pl . (deletes everything in current directory)
#tested under Linux deleted 5,000 files in 8 seconds on ntfs partition; heaps faster than anything under windoze
#ui error (not bug) couldn't rmdir directory .: Invalid argument at /home/alistair/perl/fastremove.pl line 17.
use File::Find;
$SIG{INT} = \&interrupt; #trap Ctrl-C 
die "Erroneous app call. Usage: $0 dir ..\n" unless @ARGV;
 print "This script is DANGEROUS - Are you sure you want to delete EVERYTHING in directory ",@ARGV," (y/n): ";
 chomp(my $input = <STDIN>);
if ($input !~ /^[Y]?$/i) {exit();}
print "##FastRemove execute; each dot is a deleted file\nRemoves EVERYTHING out of current directory\nProcess can be interrupted by Ctrl-C\n";
 find {
 bydepth => 1,
 no_chdir => 1,
 wanted => sub {
 if (!-l && -d _) {
 print STDERR "\nDeleted: $_\n";
 rmdir or warn "couldn't rmdir directory $_: $!";
 } else {
 print STDERR ".";
 unlink or warn "couldn't unlink file $_: $!";
 }
 }
 } => @ARGV;
sub interrupt {print "\nProcess interrupted by Ctrl-C\n"; exit(0);}

Once I have the second partition on Seagate changed to ext4 I'll advise its performance here. Have 3 * usb big drives and 2 are Seagate and the other is Samsung which was really good until it started playing up (smart errors) the smaller Seagate a 500Gb under ext4 is fast and furious; no problems at all Uncle Arthur, its just the new Seagate Expansion 4tb that is problematic.

---

### Post by vidtek on 2019-12-29
AlistairGeorge-

Something I thought you may find useful, fsarchiver is able to backup drives formatted in one file system to a backup file, then restore the data to a totally different file system.  It can also restore to unlike drive/partition sizes, provided the target has enough room to fit the data.

For example, you have an ntfs formatted 2tb drive, with it's data taking up 750gb. of space in a 1.9tb partition.

You backup (compressed if you like) to another drive somewhere and the backup file may be 500gb.  

You then have a 1tb drive formatted down to say 9.2gb with ext4.

Fsarchiver can then transfer that data to the 1tb drive complete keeping all data intact.

Neat huh?

Here is a link to the website for more information: [http://www.fsarchiver.org/]("http://www.fsarchiver.org/")

---

### Post by TheFu on 2019-12-29
When HDDs are really slow, there are a few things that could be at issue:
[LIST]
[*]bad controllers; try a different SATA controller, USB controller
[*]bad connections; check the SATA/USB connection; reseat/reconnect all connections
[*]not enough power; "portable disks" powered only with USB are slow. Use external power plugs.
[*]misaligned partitions; This is new for AF (4KB sector) disks. fdisk and parted have checks for it. 20-40% performance hit
[*]not using optimal mount options; NTFS has big_writes option which usually make a 30% performance gain
[*]not using kernel file system drivers; Popular core F/LOSS and Unix file systems have kernel drivers. Prefer those over non-Linux drivers.  Effectively, it means we need to choose ext4 almost always.
[*]millions of tiny files; lots of files means having to read lots of _stat() calls which slows down all file operations.
[*]Failing disk; check the SMART data, but 22% of the time, disks fail without any negative SMART information seen. This can be a disk platter issue or the disk controller inside the drive.
[/LIST]

---

### Post by Alistair George on 2019-12-29
Hi VidTek. Thanks for suggestion, but had looked at that fsarchiver earlier. *FSArchiver is a system tool that allows you to save the contents of a file-system to a compressed archive file.*
What I need is a faster (file) replacement for rsync and/or the rm -r-d command. The latter has been achieved with the perl script.
Last night I set task of (caja) copy from ntfs partition to ext4 partition. The job hung with permissions issue and estimated completion time of 17 hours.
I've decided to go further with the perl script to include (recursive) dircopy, dirmove and dirdelete. Perl can preserve file attributes across linux partitions, and whatever attributes are on ntfs. Once Ive got the script working, will do an a/b compare to rsync and GNU mv.

---

### Post by vidtek on 2019-12-29
AG-  Glad you are progressing with the issues that forced me to just give up and buy a couple of extra drives.

Funny thing is I also use 2 x 4tb Seagate USB Expansion 2 1/2" drives too as my main data and backup.

I just ripped them both out of their cases and stuck one inside my tower along with the 5 tb. WD drive 3 1/2" I use for my multimedia setup.

Like I said I whack both Seagates and WD drives into the cloning dock once a month.  It takes about 6 hrs to clone the 4tb drives in the dock, and 

about 4 1/2 hrs for the WD drives.

---

### Post by Alistair George on 2019-12-29
Hi vidtek again.....Im putting the finishing touches on perl script would you like to try it out when done? do you know how to run perl scripts?

---

### Post by TheFu on 2019-12-29
Here's my media rsync script to backup a 4TB data disk to another 4TB data disk.
```
$ EXCLUDES="--exclude .Trash-1000 --exclude lost+found --exclude ZCS-2012"
$ ionice rsync -av --stats --progress $EXCLUDES --delete-before /misc/D5/ /misc/b-D5/
```

This is just 1 of the 20TB of storage and only a media/data file backup.

For OS and HOME directory backups, I want versioning.  
Basically, that is 
```
sudo rdiff-backup    --exclude-special-files   /usr/local  /root  /home  /opt  /etc  /var/www /var/lib/libvirt /Backups/$HOSTNAME/
```
The first run takes whatever an rsync takes for time.
All runs after that only transmit changed/new files  or changed/new metadata about files.  For most systems, it is 2-4 minutes.

Yes, some pre-backup data is gathered to make restoring the system to the same place it was before possible.  For example, the list of manually installed packages.  I use a perl script for my backups, 
```
`$aptmark showmanual | tee $local_backup/apt-mark.manual`;
######[ to restore pkgs ]#######
### sudo apt-mark auto $(cat pkgs_auto.lst)
### sudo apt-mark manual $(cat pkgs_manual.lst)
### sudo apt-get -u dselect-upgrade

```

I also backup ruby gems, cpanm module lists, etc.
```
# Daily dump of current ruby gems to $HOME/backup - 
 `$gem list --local > $local_backup/gem.list`;
# Daily dump of current CPAN modules to $HOME/backup - cpan -l
 `$cpan -l > $local_backup/cpan.list ` if ( -e "/usr/local/lib/site_perl");
```

Restore process is:
[LIST=1]
[*]Fresh install of same/similar Ubuntu flavor to old or new system
[*]Restore all the backed-up data, except /etc/ files.  Selectively restore those as needed - /etc/apt/,  /etc/ufw/, /etc/iptables/, /etc/hosts, /etc/netplan/ (or network), and a few other files that I manually changed over the days, months, years, prior.
[*]Take the list of manually installed packages and feed those into apt-mark and apt-get to install.  It is important to have both data and settings already in the expected locations BEFORE installing the packages so those settings are used.
[/LIST]
This method works well for me and others. 15 min for a fresh OS install, using the normal, stock, installer. Change the storage however you like, diff file systems, diff storage amounts, LVM or not, whatever. 15 min to restore the backup data - pick the version you want from last night, 13 days ago, 79 days ago, whenever.  I usually have 90 - 180 days of backup versions per system.  That's 30 minutes to a restored system that "feels" just like the prior system.  Only huge data like videos and audio files might not be restored at this point.  Best of all, the backups don't grow by the first backup size. They grow only as much as the diff-gz for each new file requires. 60 days of versioned backups usually take 10-20% more storage than the original mirror size.  A server with 10G in a backup is 13G for 90 days of versioned backups.  Why wouldn't people choose that? 

Been using this method for about 9 yrs now.  About once a year, I'll either do something stupid or have a HDD fail on one of the systems and get to use the backups to restore.

Some systems don't hold any data, so the backups only contain configs/settings for that server.  My email gateway server uses less than 50MB for 180 days of versioned backups.  Heck, there is little reason I shouldn't keep every version until it is time to move to a fresh install of that gateway. Backups are tiny.
 
All backup systems/solutions are an exercise in trade-offs.

---

