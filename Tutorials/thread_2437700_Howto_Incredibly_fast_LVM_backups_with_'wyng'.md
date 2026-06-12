---
title: "Howto: Incredibly fast LVM backups with 'wyng'"
date: 2020-02-27
forum: Tutorials
---

### Post by tasket on 2020-02-27
[SIZE=+2]
Introduction[/SIZE]

[Wyng]("https://github.com/tasket/wyng-backup") is a backup utility designed to take advantage of snapshot-capable storage systems like thin-provisioned LVM (or simply "thin LVM") to make incremental backups fast. This type of storage holds information about the time and locations where volumes were changed, which enables programs like Wyng to forgo the extensive pre-backup scanning of data that "advanced" backup tools like rsync, borg and duplicity do for each backup in order to find changes. When you have source data that weighs in at tens of gigabytes or even terabytes, the difference in delays and resource usage from (not) scanning whole volumes can make or break your ability perform backups.

Wyng also takes a cue from OS X Time Machine, permitting quick recovery of disk space from old backups so that new backups can be added on a frequent basis. The only catch for gaining this speed and convenience is that the backup destination must reside on a Unix-like filesystem, which today is very common.


[SIZE=+2]Prerequisites[/SIZE]

The local system (the source to be backed-up) currently must be running Linux with at least Python 3.5 and thin-provisioning-tools installed. A thin LVM storage pool should also be setup to hold the local volumes. On a Qubes OS system, thin LVM was probably setup when the OS was installed; on Ubuntu or other Linux some further configuration (such as creating the pool within the volume group) is probably required even if it was installed to LVM format &#8211; see the linked Tecmint article for examples.


[SIZE=+2]Getting Wyng[/SIZE]

Wyng is currently available [from github]("https://github.com/tasket/wyng-backup"), just use the *Clone or Download* button (also, my GPG public key is available if you wish to verify in git).

The program itself is simply the 'wyng' file, which requires at least Python version 3.5 to run; this can be placed wherever you choose, such as '/usr/local/bin'. The LVM 'thin-provisioning-tools' package is also required to make backups.

```
$ unzip wyng-backup-master.zip
$ sudo cp wyng-backup-master/wyng /usr/local/bin
$ sudo chmod +x /usr/local/bin/wyng
```


[SIZE=+2]Initialize an archive[/SIZE]

To configure an archive to store our backups, use **wyng arch-init** command like so:
```
$ sudo wyng --local=myvg/mypool --dest=internal:/mnt/backups arch-init
```
The above command will point Wyng to our local LVM storage pool at "myvg/mypool". On a Qubes system this setting would be "qubes_dom0/pool00". We're also pointing to an "internal:" destination which in this case is simply a filesystem mounted at "/mnt/backups".

In addition to locally mounted filesystems, Wyng can also backup to remote systems via the SSH protocol.


[SIZE=+2]Create an initial backup[/SIZE]

To start backing up volumes we can now simply **add** the volume names to the configuration and then tell Wyng to **send** them...
```
$ sudo wyng add vm-work-private
Volume vm-work-private added to archive config.

$ sudo wyng add documents
Volume documents added to archive config.

$ sudo wyng send
Preparing snapshots...
  Initial snapshot created for vm-work-private
  Initial snapshot created for documents

Sending backup session 20200204-161849 to /mnt/backup

Volume : vm-work-private
  100%   1141.0MB

Volume : documents
  100%   32070.5MB 
```
Since these are initial (full) backups, they will take about as long and use about as much disk space as with other backup tools. However, any time we perform a **send** in the future, Wyng will automatically go into its fast incremental mode. We can keep adding more volumes as we wish and Wyng will automatically know to do a full backup on their first session. Also notice the "backup session" is identified as the current local date-time starting with the year and ending with seconds.

Subsequent backups will always be incremental and should run quite fast. We need only tell Wyng to **send**:
```
$ time sudo wyng send
Preparing snapshots...
Acquiring deltas.

Sending backup session 20200205-110000 to /mnt/backup

Volume : vm-work-private
  100%   31.1MB

Volume : documents
  No changes.

real    0m10.953s                                                                                                                        
user    0m3.128s                                                                                                                        
sys     0m2.837s 

```
This time around Wyng is performing incremental backups and it says "Acquiring deltas", which is the change information that makes it so fast. Note that the volume _'vm-work-private'_ had 31.1MB of changes while _'documents'_ had none so Wyng could skip over it in an instant. And this time, instead of taking many minutes like the initial backup session, both volumes were completed in just seconds as the **time** command reveals.


[SIZE=+2]Restore[/SIZE]

Restoring volumes is easy with the **receive** command, we just tell Wyng where to save the restored data and which volume we want:
```
$ sudo wyng --save-to=/dev/myvg/documents receive documents
```
If we are recovering a crashed system and have no locally saved Wyng configuration, we can explicitly tell Wyng where the archive is located and it will automatically read the configuration from there:
```
$ sudo wyng --from=internal:/mnt/backups --save-to=/dev/myvg/documents receive documents
```
Note that **--save-to** can also point to a regular file to create a disk image.

Finally, we can tell Wyng to receive an older version of the volume, if that's what we need:
```
$ sudo wyng list documents
Sessions for volume documents :
  20200204-161849  20200205-133214  20200205-233038  20200206-120001

$ sudo wyng --session=20200205-133214 --save-to=/dev/myvg/documents receive documents
```


[SIZE=+2]Maintenance[/SIZE]

Space can be freed from an archive by removing older backup sessions with the **prune** command. A session or range of session times must be specified with **--session**. For example, the following will remove one session from the volume 'documents':
```
$ sudo wyng --session=20200204-161849 prune documents
```
A range of date-times can also be used; just add a second date-time to **--session** separated by a comma. The **--all-before** option is an even more convenient alternative:
```
$ sudo wyng --all-before --session=20200205-230000 prune
```
Here, all backup sessions created before 11PM on Feb. 5 are removed. Also note the volume name can be omitted; as with the **send** command, omitting the volume will apply the operation to all volumes in the archive.

Another of Wyng's features is a snapshot-rotation method that saves space on the source system and helps address a common problem with snapshots: As they age waiting for the next backup to occur, snapshots consume more and more space in the overall storage pool. Simply schedule **wyng monitor** to run periodically and the old snapshots' metadata will be condensed and their data blocks freed by replacing them with fresh snapshots.


[SIZE=+2]Wrap up[/SIZE]

As you might have guessed by now, backing up whole volumes with Wyng is somewhat like using **zfs send** on disk images but without the special requirement of running ZFS on the backup drive or server. Wyng leverages a copy-on-write technology that can be found on any modern Linux system; Thin LVM is there waiting for us to use it, and I think more people should try it out!

Being oriented to block-level access Wyng is also well-suited to virtual machines, Docker containers, etc. &#8211; especially on systems where the admin environment requires very tight security (mounting guest filesystems can be risky).

For an overview and details on all of Wyng's functions, please see the project Readme. You can also contact the author via email or on ubuntuforums.org or the qubes-users mailing list.

[HR][/HR]

Note: For updates on this tutorial, checkout my project [wiki page.]("https://github.com/tasket/wyng-backup/wiki/Making-incredibly-fast-LVM-backups-with-Wyng")

---

### Post by tasket on 2020-03-17
Wyng beta5 release is now out....

[https://github.com/tasket/wyng-backup](https://github.com/tasket/wyng-backup)

---

