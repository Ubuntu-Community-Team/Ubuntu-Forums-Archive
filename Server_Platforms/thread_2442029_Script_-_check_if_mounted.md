---
title: "Script - check if mounted"
date: 2020-04-28
forum: Server Platforms
---

### Post by aljames2 on 2020-04-28
Curious if this line in a bash script will work, or if there is a cleaner way to do it.  
Basically want to check if the mount exists and if not, mount it, and if the mount fails write to the log file.  Otherwise, continue.

```

MNT=/some/location
mountpoint -q "$MNT" || /bin/mount -v /dev/vg1/data $MNT || { echo "$(date) mount storage data failed" >> ~/backup_errors.txt ; exit 1; }

```

---

### Post by erind on 2020-04-28
I think it should be something like so (untested):

```
MNT=/some/location
mountpoint -q "$MNT" || { /bin/mount -v /dev/vg1/data $MNT || { echo "$(date) mount storage data failed" >> ~/backup_errors.txt && exit 1; } }

```

Just test it. However for complex tests branches I'd write something like the following:

```
MNT=/some/location

if ! mountpoint -q "$MNT"
 then
  if ! /bin/mount -v /dev/vg1/data $MNT
   then
    echo "$(date) mount storage data failed" >> ~/backup_errors.txt && exit 1; 
  fi
fi
```

---

### Post by LHammonds on 2020-04-29
My solution to this was to test for the existence of a file.  I did not want to rely on "mount" error codes and whatnot...just whether it was mounted or not.

To this end, I create an empty "offline.txt" file in the mount location (when it is not mounted).  If the mount is active, that file is hidden so you can just do a simple "if file exists" check to see if the mount is actively working.

Here is a quick example:
```

if [ -f /mnt/myshare/offline.txt ]; then
  echo "Location is not mounted.  Mounting share now..."
  mount -t cifs //srv-backup/myshare /mnt/myshare --options nouser,rw,nofail,noexec,credentials=/etc/cifspw
  sleep 2
  if [ -f /mnt/myshare/offline.txt ]; then
    echo "Mount failed."
  else
    echo "Mount successful."
  fi
fi

```

LHammonds

---

### Post by ahbart on 2020-04-29
From my raspberry I backup to a synology. In the backup script I have the folowing code to check the mount:
```
if mount | grep /mnt/backup > /dev/null; then
    echo "already mounted"
else
    echo "not yet mounted, I wil mount now"
    sudo mount -t cifs -o username=$USERNAME,password="$PASSWORD",uid=1000,gid=1000 //192.168.188.30/RaspberryPi/Backups /mnt/backup
    echo $
fi 
```
This is working well

---

### Post by ahbart on 2020-04-29
From my raspberry I backup to a synology. In the backup script I have the following code to check the mount:
```
if mount | grep /mnt/backup > /dev/null; then
    echo "already mounted"
else
    echo "not yet mounted, I wil mount now"
    sudo mount -t cifs -o username=$USERNAME,password="$PASSWORD",uid=1000,gid=1000 //192.168.188.30/RaspberryPi/Backups /mnt/backup
    echo $
fi 
```
This is working well

---

### Post by rbmorse on 2020-04-29
> [COLOR=#000000]To this end, I create an empty "offline.txt" file in the mount location (when it is not mounted). If the mount is active, that file is hidden so you can just do a simple "if file exists" check to see if the mount is actively working. [/COLOR]

That's actually very clever.  I'm going to steal it.

---

### Post by ahbart on 2020-04-29
Agree!! I'm going to use this idea too. A file called offline.txt in the unmounted mount directory ;) I like that.

---

### Post by aljames2 on 2020-04-29
Thanks for the tips all..

however, my case is not to test the mount of a network share, instead I want to test if a logical partition on a separate storage drive (same machine) is mounted before starting a server backup script.  I normally leave my storage drives unmounted until doing a backup.  Is there another way to do this without putting a test against "mount"?

---

### Post by LHammonds on 2020-04-29
@aljames2, would the exact same logic still apply even if in reverse?  Check to see if a file exists (if the partition is there)....and if it is not, the it is not mounted.

The mount command in my example is not important...I even thought about just typing "insert mount command here" to keep from detracting from the logic.

---

### Post by aljames2 on 2020-04-29
True...I didn't think of that.  Simple.  Thx again !

---

### Post by yetimon_64 on 2020-04-29
You could try the mount command against input from the readlink command to do this. I found a few years ago when writing a custom mount / unmount script for dealing with hidden partitions on my multiboot install that using the next code and logic works well.

The basic command I use for mount testing (to check if mounted)...
```
mount | grep -qs $(readlink -f "/mnt/backup")
``` Note, I've used your backup location here.

The bash logic may go something like (**the check here is to test if NOT mounted**, note the "!" after the "if") ...
```
if ! $(mount | grep -qs $(readlink -f "/mnt/backup")); then
   sudo mount -t cifs -o # .... add your full mount command here.
fi
```
The above logic checks if the mount is missing and mounts it if needed. If the mount is already up the above code block is skipped and the main backup script moves onto your next command.

Regards, yeti.

**Edit:** the above code can also be used to check if a partition is mounted by pointing the readlink command to the blockfile for the partition in /dev/disk/by-uuid (or by label or name etc; I found using UUIDs the safest means of checking mounts with partitions).

---

