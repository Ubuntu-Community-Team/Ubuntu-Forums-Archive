---
title: "Timeshift - Backup of snapshots via Rclone"
date: 2020-05-29
forum: Ubuntu, Linux and OS Chat
---

### Post by 3-mark-2 on 2020-05-29
I'm fairly new to Linux and I running Ubuntu 20.04 on a raspberry pi 4. I wanted to keep regular snapshots of the system so I've installed Timeshift. However, I noticed that the disk space was quite large. I'd like to keep some extra snapshots backup away from the system so I've also been backing up the snapshots to by Google Drive account using Tar to create a backup of the snapshot and Rclone to get it to Drive. I've got this working successfully.


However, should the worst happen, can actually use these tarred files if I can get them back to the timeshift snapshot directories? Here's the script I run in cron (Timeshift is running in its own, perhaps that's not right though).


```

#!/bin/bash
readonly SCRIPT_NAME=$(basename $0)


log() {
  echo "$@"
  logger -p user.notice -t $SCRIPT_NAME "$@"
}


err() {
  echo "$@" >&2
  logger -p user.error -t $SCRIPT_NAME "$@"
}
#First lets see what snapshots are available and create tar.gz files for them if they are not already there
cd /timeshift/snapshots/
log "Changed directory to " $(pwd)
for i in *
do
  #is i a directory? If not continue
  if [ ! -d ${i} ]
  then
    continue
  fi
  log "check if ./snapback/${i%/}.tar.gz exists and if not create it"
  if [[ ! -f "../snapback/${i%/}.tar.gz" ]]
  then
    tar -czvf "../snapback/${i%/}.tar.gz" "$i"
    log "created: ../snapback/${i%/}.tar.gz"
  fi
done


#Next see what .tar.gz files are present and delete them if their snapshots are deleted
cd /timeshift/snapback/
log  "Changed directory to " $(pwd)
for i in *
do
  #is i a file? If not continue
  if [ ! -f ${i} ]
  then
    continue
  fi
  log "check if ./snapshots/${i%.tar.gz} exists and if not delete the file"
  if [ ! -d "../snapshots/${i%.tar.gz}" ]
  then
    rm $i
    log "Deleted $i"
  fi
done


#Finally Backup any .tar.gz to Google Drive files that are not backed up and delete those that are no longer there
log "Begin Sync with Google Drive"
/usr/bin/rclone sync --update --verbose --transfers 30 --checkers 8 --contimeout 60s --timeout 300s --retries 3 --low-level-retries 10 --stats 10s --drive-use-trash --include "*.tar.gz" "/timeshift/snapback" "GoogleDrive-SystemBackup:Pi/Backup"
log "Completed Sync with Google Drive"

```

---

### Post by TheFu on 2020-05-29
I would never use a tgz as part of a backup or restore strategy if the total size was over 50MB.  There are so many better tools.

[s]Tar is going to dereference all the hardlinks, so the file size is going to explode as you create the tar.[/s] That almost certainly isn't what you want.  [https://www.gnu.org/software/tar/manual/html_node/hard-links.html](https://www.gnu.org/software/tar/manual/html_node/hard-links.html) says I'm wrong. If you are seeing the tar size explode, check whether the dereferencing is actually happening.

I'm not a fan of hard-link-based versioning backup tools for a number of reasons.  There are specific failures that can happen even when everything works perfectly with those tools.  Timeshift, Back-in-Time, and rsync-based on hardlink versions are all the same and have the same problems. For example, all of these require a Unix file system be used. NTFS and FAT-whatever cannot be used.  All of them lose the owner, group, and permission changes over time.  That's where I've been burned.

I use rdiff-backup.  The command looks very similar to rsync. It uses a reverse-differential type of backup for older versions.  However, rdiff-backup does not encrypt the data. For that, you'd need to add encryption on.  That's easy either at the file system level or as a pipe between other processes using openssl or gpg in the middle.

No way would I use any cloudy service to store backups unless I'd pre-encrypted all the data being transmitted. I'd have a simple algorithm to ensure the encryption key changed daily, if not more often.  
Perhaps {my key}-{hostname}-{`date "+%F"`} ... so my key would be something I knew, and the rest is just there to provide length.

But in the end, which backup method works best for any system depends on what the desired outcome for the restore process actually is.  There are trade-offs in each solution.  Time vs storage required. Complexity vs 1-click restores. Flexibility vs complexity.  Security vs convenience.  We can't have them all.

Image-based backups break flexibility, versioning, and have huge total sizes, but the restore is 1 command.
File-based backups require a little more complexity during the restore, which can be terrible at 4am. 

Anyways, work backwards from the desired restore process to get the backups you want.
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
I do a modified file-based backup. The OS is not included, but settings for it and servers along with data ARE. I always create some handy system information just prior to creating the backups too, so at restore time I can decide if I want exactly the same storage config or something different.  This is part of the flexibility.  Moving from system A to system B is pretty painless.

---

### Post by 3-mark-2 on 2020-05-29
Ok, I understand what you mean I about the linking in the tar files. Timeshift uses Rsync internally so I have a backed up dataset. I don't have any non-NTFS/FAT locations on my network this being my first Linux machine so if I want to backup my snapshots this would need to be put in the cloud.

So, If I'm using Timeshift in Rsync mode:


[LIST]
[*]What's the best way to best way to backup the snapshots to a single file if not using Tar? I'm going to use Rclone to get that file to Google Drive as I have unlimited space on there.
[*]If I need to restore from a file on Google Drive can I just move the restore the file in Google Drive to the Timeshift snapshots directory. This was my original question.
[*]If the latter is not possible, can you suggest a backup system that will allow me to specify X weekly backups and Y daily backups the way Timeshift is allowing me to. I can probably write a shell script to do so, I just need to be able to backup my system to Google Drive and restore it should I need to.
[/LIST]

---

