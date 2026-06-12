---
title: "tar system back and restoring scripts"
date: 2010-12-16
forum: The Cafe
---

### Post by akkdx on 2010-12-16
After studying Heliode's tutorial ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)), I have written a pair of backup and restore scripts as my script learning exercise.


Backup script :
Basically the same as Heliode's tutorial.
The backup script does not support command line option.

Restore script :
targeted at fully automating the restore processes to a new disk drive, which has the following features :
[LIST=1]
[*]repartitioning the target to 1-3 partitions including swap
[*]change the file system of the restored system, also change to /etc/fstab to mount the new file system
[*]restore MRB so that a bootable system can be obtained (use chroot grub-install)
[*]option -u to force to change the target's fstab and grub to use UUID for booting and mounting
[*]option -r=new_passwd to reset the root password of the target
[/LIST]

The restore script supports command line options, e.g.:
restore-rfs.sh -b=/rfs_backup/Ubuntu10.04.tgz -f=ext4 -p -t=5000 -o=4096 -u


If you are interested in these scripts, please try them and let me know if there is any problem.


[ATTACH]180272[/ATTACH]

---

