---
title: "Verifying data vs backup with rsync after mdadm crisis"
date: 2013-06-15
forum: Server Platforms
---

### Post by apokkalyps on 2013-06-15
I recently had a huge cascade mdadm raid failure, where 3 or 4 disks had to be ddrescued to other disks and then force assembled back together.  Afterwards the ext4 partition wouldn't mount because of invalid group descriptors (and who knows what else).  I ran fsck -y /dev/md0 and it had to fix tons of stuff in many passes.  The file system is mounting now and superficially everything looks fine, but I am worried about possibly having "bits transposed" etc in random files.  (is this even possible?)

I have a backup of the array, and I was trying to run rsync (dry-runs) to compare volumes and look for non matching files.  Rsync by default only checks file sizes so I am using the checksum option.

My rsync command is like this 
```
rsync -avHcn /media/md1 /media/vault
```
(md1 is the backup and vault is the primary)

This returns TONS of files (maybe everything?) so I broke it down smaller

```
rsync -avHc --dry-run /media/md1/Scripts /media/vault/Scripts
sending incremental file list
Scripts/
Scripts/SortFiles2 (another copy).sh
Scripts/SortFiles2 (copy).sh
Scripts/SortFiles2.sh
Scripts/SortFiles3.sh
Scripts/Sortfiles1.sh

sent 268 bytes  received 31 bytes  598.00 bytes/sec
total size is 13350  speedup is 44.65 (DRY RUN)
```

But then I run
```
md5sum /media/md1/Scripts/Sortfiles1.sh  /media/vault/Scripts/Sortfiles1.sh 
34c72e175a02e3bafdf172a9a4465c92  /media/md1/Scripts/Sortfiles1.sh
34c72e175a02e3bafdf172a9a4465c92  /media/vault/Scripts/Sortfiles1.sh
```

also running 'cmp' on the files returns nothing, and even running the same rsync command on one particular file shows no changes

```
rsync -avH --dry-run /media/md1/Scripts/Sortfiles1.sh  /media/vault/Scripts/Sortfiles1.sh 
sending incremental file list

sent 57 bytes  received 12 bytes  138.00 bytes/sec
total size is 4333  speedup is 62.80 (DRY RUN)
```

Am I missing something with the rsync syntax?  My understanding is that one -v should only list the files that have differences detected and would be copied in a standard non-dry-run.

I also noticed that if I do the same rsync command with slashes at the end of the directories (to mean the contents of the directories as opposed to the directories themselves, which should really be irrelevant here as long as they are consistent)

```
rsync -avHc --dry-run /media/md1/Scripts/ /media/vault/Scripts/
sending incremental file list

sent 234 bytes  received 12 bytes  492.00 bytes/sec
total size is 13350  speedup is 54.27 (DRY RUN)
```

I'm really confused, am I just misunderstanding the -v option in rsync?  Why does it list them when comparing Scripts but not Scripts/?  Is there a better tool for doing what I'm trying to do?

---

### Post by rubylaser on 2013-06-15
Rsync is the correct tool for this job, and using the trailing slashes on each path is the way you would want to run this sync action.  Here's an example on my array.  I just copied my scripts folder from /root/scripts to /root/scripts_test/

Here's with the slashes left off.
```

root@fileserver:~# rsync -avHc --dry-run scripts scripts_test
sending incremental file list
scripts/
scripts/CPUTempShutdown.sh
scripts/SnapRAIDSync.sh
scripts/diskAlert
scripts/disk_health_check.sh
scripts/empty_movie_folder_cleanup.sh
scripts/glacierBackup.py
scripts/glacier_backup.sh
scripts/lw_backup.sh
scripts/msg.txt
scripts/remove_old_kernels.sh


sent 518 bytes  received 46 bytes  1128.00 bytes/sec
total size is 17691  speedup is 31.37 (DRY RUN)

```

and with
```

root@fileserver:~# rsync -avHc --dry-run scripts/ scripts_test/
sending incremental file list
./


sent 494 bytes  received 45 bytes  1078.00 bytes/sec
total size is 17691  speedup is 32.82 (DRY RUN)

```

Note that my perfectly functioning box works exactly like yours :)

Here's an md5sum of each file in both directories.  As you can see, they are all exactly the same.
```

root@fileserver:~# cat scripts_file.md5 
744ba7dc3e157403e4beb29f4dc02813  /root/scripts/msg.txt
fec555e28872459adebea5000e02a3c4  /root/scripts/CPUTempShutdown.sh
0c1a55de522f64eec59bfbfbeac1e0b8  /root/scripts/glacierBackup.py
06470d3a96e92c516e42e05cb3996b8d  /root/scripts/remove_old_kernels.sh
abdce1dd98dfa9433825eab3e508611e  /root/scripts/lw_backup.sh
e4103944b3ec36736bb8322a764b72df  /root/scripts/SnapRAIDSync.sh
74b7b03227e43eebef2e70a178f6ca23  /root/scripts/empty_movie_folder_cleanup.sh
7dea25ba80aeb678fc637d0f6cb60780  /root/scripts/glacier_backup.sh
12576c7ec8f73191311b8454d1eb6a05  /root/scripts/diskAlert
1418f14884e3e06efee781c23af20013  /root/scripts/disk_health_check.sh
root@fileserver:~# cat scripts__test_file.md5 
744ba7dc3e157403e4beb29f4dc02813  /root/scripts_test/msg.txt
fec555e28872459adebea5000e02a3c4  /root/scripts_test/CPUTempShutdown.sh
0c1a55de522f64eec59bfbfbeac1e0b8  /root/scripts_test/glacierBackup.py
06470d3a96e92c516e42e05cb3996b8d  /root/scripts_test/remove_old_kernels.sh
abdce1dd98dfa9433825eab3e508611e  /root/scripts_test/lw_backup.sh
e4103944b3ec36736bb8322a764b72df  /root/scripts_test/SnapRAIDSync.sh
74b7b03227e43eebef2e70a178f6ca23  /root/scripts_test/empty_movie_folder_cleanup.sh
7dea25ba80aeb678fc637d0f6cb60780  /root/scripts_test/glacier_backup.sh
12576c7ec8f73191311b8454d1eb6a05  /root/scripts_test/diskAlert
1418f14884e3e06efee781c23af20013  /root/scripts_test/disk_health_check.sh

```

and here's a diff of both.
```

root@fileserver:~# diff /root/scripts /root/scripts_test/
root@fileserver:~# 

```

I would say that based on everything you've shown so far that your data is okay.

---

### Post by apokkalyps on 2013-06-17
The benchmark is much appreciated.  Thank you.

I did it with slashes after the paths and it worked as expected.  When I first posted, I thought the slashes only showing differing files had to do with them being only nested 1 deep, although with the slashes on the root of my array, it went as deep as neccessary and came up with 4 or 5 corrupted files out of 8TB, exactly what I was hoping for, I will restore those specific files from my backup.

Am I correct in assuming that the reason it was listing ALL the files was because 
```
rsync /media/md1 /media/vault
```
was comparing /media/md1 with a nonexistant folder /media/vault/md1 instead of /media/vault?

---

### Post by rubylaser on 2013-06-17
> **apokkalyps said:**
> 
Am I correct in assuming that the reason it was listing ALL the files was because 
```
rsync /media/md1 /media/vault
```
was comparing /media/md1 with a nonexistant folder /media/vault/md1 instead of /media/vault?
Yes you are.  I'm glad your data is all intact :)  Congratulations on have a good, functioning backup system in place.

---

