---
title: "Trying to figure out xfsdump"
date: 2010-05-26
forum: Server Platforms
---

### Post by nemein on 2010-05-26
We just picked up a new server running ubuntu9 (but I'm going to upgrade it to 10 before putting it into production) that has primarily xfs file systems that I have never dealt w/ before[1].  Attached to the machine is a LTO-5 drive I want to use for backups.  On the root partition (ext4) I'm able to use the dump command w/o problems[2] so I'm pretty sure the drive itself is working fine.  When it comes to the xfs partitions though I'm having some problems getting things to work right.  I found the xfsdump command but I seem to be missing something.  Below are a couple of attempts[3].  After the first attempt I ran xfsrestore and while everything seemed to be there, when I did an extract all that returned was the directory structure, the actual files weren't restored.  Due to the highly redundant nature of the data[4] I added a couple of "foo" files spread throughout the dir structure and did the second dump.  Again though during the restore the files showed up on the list but extracting them only restored the dir structure.  So something isn't working right.

My questions are:
- Am I using the right parameters?  I added the -E and -F after some initial tests failed completely, 0 byte dump size.  Should I be specifying a block size w/ this drive (the -m and -b options right)?  What would be appropriate for the LTO-5?

- Along the same lines the -E isn't going to be very useful for incremental backups (what I usually do is run incrementals weeknightly on the same tape and then do a full backup once a week on a different tape - I keep a rotation of 5 tapes going).  Any suggestions there?

- Why is everything finishing "xfsdump: Dump Status: INTERRUPT"?

- Any problems w/ doing this on a live file system?  Should I be looking at trying to implement some sort of "snapshot" thing w/ this (something else I haven't manually done so hints/clues/suggestions there would also be appreciated ;)).

If there's any questions of me please let me know.  I'm going to keep testing/looking around but any advice is appreciated.

TIA







[1] In case it matters

df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            945754564   3030396 894682592   1% /
udev                   4097000   4097000         0 100% /dev
none                   4097000         0   4097000   0% /dev/shm
none                   4097000       328   4096672   1% /var/run
none                   4097000         0   4097000   0% /var/lock
none                   4097000         0   4097000   0% /lib/init/rw
/dev/sda1                93307     20039     68451  23% /boot
/dev/sdd1            8788867036      4416 8788862620   1% /export/archive
/dev/sdb1            2929524700 1608224368 1321300332  55% /export/home
/dev/sdc2            976399700      4256 976395444   1% /export/projects
/dev/sdc1            1952993928 1608224528 344769400  83% /local/home

/etc/mtab
/dev/sda3 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda1 /boot ext3 rw 0 0
/dev/sdd1 /export/archive xfs rw 0 0
/dev/sdb1 /export/home xfs rw 0 0
/dev/sdc2 /export/projects xfs rw 0 0
/dev/sdc1 /local/home xfs rw 0 0



[2] dump -0 -a -u -f /dev/nrst0 /dev/sda3


[3]
FIRST TEST
Script started on Tue 25 May 2010 07:00:41 PM PDT
root@dmz3:/tmp# xfsdump -l 0 -v verbose -E -F -L test -M test -f /dev/nrst0 /local/home
xfsdump: using file dump (drive_simple) strategy
xfsdump: version 3.0.2 (dump format 3.0) - Running single-threaded
xfsdump: level 0 dump of dmz3:/local/home
xfsdump: dump date: Tue May 25 19:01:02 2010
xfsdump: session id: 6fcb7199-c63d-4a70-b734-f56eb90cbeb7
xfsdump: session label: "test"
xfsdump: ino map phase 1: constructing initial dump list
xfsdump: ino map phase 2: skipping (no pruning necessary)
xfsdump: ino map phase 3: skipping (only one dump stream)
xfsdump: ino map construction complete
xfsdump: estimated dump size: 1646224879680 bytes
xfsdump: creating dump session media file 0 (media 0, file 0)
xfsdump: dumping ino map
xfsdump: dumping directories
xfsdump: dumping non-directory files
xfsdump: ending media file
xfsdump: media file size 4186902528 bytes
xfsdump: dump size (non-dir files) : 2723371768 bytes
xfsdump: NOTE: dump interrupted: 509 seconds elapsed: may resume later using -R 
option
xfsdump: Dump Status: INTERRUPT

SECOND TEST
Script started on Wed 26 May 2010 05:29:29 AM PDT
root@dmz3:/tmp# xfsdump -l 0 -E -F -L test -M test -v verbose -f /dev/nrst0 /local/home
xfsdump: using file dump (drive_simple) strategy
xfsdump: version 3.0.2 (dump format 3.0) - Running single-threaded
xfsdump: WARNING: most recent level 0 dump was interrupted, but not resuming tha
t dump since resume (-R) option not specified
xfsdump: level 0 dump of dmz3:/local/home
xfsdump: dump date: Wed May 26 05:29:55 2010
xfsdump: session id: a09c3caa-6f05-4d38-a3fa-3d76312e3416
xfsdump: session label: "test"
xfsdump: ino map phase 1: constructing initial dump list
xfsdump: ino map phase 2: skipping (no pruning necessary)
xfsdump: ino map phase 3: skipping (only one dump stream)
xfsdump: ino map construction complete
xfsdump: estimated dump size: 1646224906176 bytes
xfsdump: positioned at media file 0: dump 0, stream 0
xfsdump: WARNING: erasing media
xfsdump: creating dump session media file 0 (media 0, file 0)
xfsdump: dumping ino map
xfsdump: dumping directories
xfsdump: dumping non-directory files
xfsdump: ending media file
xfsdump: media file size 4186902528 bytes
xfsdump: dump size (non-dir files) : 2723371600 bytes
xfsdump: NOTE: dump interrupted: 530 seconds elapsed: may resume later using -R 
option
xfsdump: Dump Status: INTERRUPT


[4] I took a small section of data from our current server and copied that into a dir calling "1".  "1" was copied to "2".  "1" and "2" were moved into "3", which in turn was copied into "4".  "3" and "4" were moved into "5" and so on until I reached "9" and the drive was pretty much full.  So it is a HIGHLY REDUNDANT data set... not sure if this matters though.

---

