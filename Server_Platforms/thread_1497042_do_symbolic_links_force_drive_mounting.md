---
title: "do symbolic links force drive mounting?"
date: 2010-05-30
forum: Server Platforms
---

### Post by rsgooch on 2010-05-30
I have a 8.04 LTS server that i have installed a new 1TB drive.  The server is running great but I am bit confused regarding the ln -s command and drive mounting.  I have backuppc installed on the server and I am running out of storage space.  To reolve this I moved the cpool and pool directories to the 1 TB drive and type from within the /var/lib/backuppc directory ln -s cpool /store/1TB/cpool this created the symbolic link to the new drive and everything works fine. I then rebooted the server and everything is runing fine but the drive does not show up in the df -h command, however the directories appear to be mounted fine.  Can someone explain this behaviour to me so I can understand.  I thought the drive would not be mounted automatically until it was defined in the fstab. Does the ln -s command force the system to automatically mount the directories but not the volume? This behaviour has caused me to delete my backup data becuase I was sure the disk was not mounted but is was!

screen capture of df -h command:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              74G   14G   58G  19% /
varrun                4.9G  216K  4.9G   1% /var/run
varlock               4.9G     0  4.9G   0% /var/lock
udev                  4.9G   84K  4.9G   1% /dev
devshm                4.9G     0  4.9G   0% /dev/shm

note drive is not listed.

lrwxrwxrwx 1 root     root          17 2010-05-08 14:41 cpool -> /store/1TB/cpool/
drwxr-x--- 2 backuppc backuppc    4096 2010-05-30 16:20 log
drwx------ 2 root     root       16384 2008-07-28 13:05 lost+found
lrwxrwxrwx 1 root     root          14 2010-05-08 14:41 pc -> /store/1TB/pc/
lrwxrwxrwx 1 root     root          16 2010-05-08 14:41 pool -> /store/1TB/pool/
-rw------- 1 root     root     2000896 2010-04-12 10:23 server.vdi
drwxr-x--- 2 backuppc backuppc    4096 2010-05-08 14:41 trash
drwxr-xr-x 5 vbox     vbox        4096 2010-05-26 12:58 vm

this is the output of the ls -l command showing the directories connected to the new mount point.

drwxr-x---  2 backuppc backuppc 4096 2010-05-30 16:27 cpool
drwxr-x--- 11 backuppc backuppc 4096 2010-05-30 15:56 pc
drwxr-x--- 18 backuppc backuppc 4096 2008-11-10 15:00 pool

this is the output of ls -l for the /store/1TB directory which shows the directories I move to the 1TB drive.

Initally I thought I must have moved the directories to the empty /store/1TB directory instead of the drive and deleted them.  As I was deleteing them I noticed the drive light on the new drive was going crazy and stop the deletion only to find out the drive is actually mounted.  This sound like a possible bug and it has caused me a lot of grief! Am I wrong and this is normal behaviour?  I have been using linux and unix for a long time(started using TI system V in 1983)I have never seen this behaviour. Any help, or explanation on this would be greatly appreciated.

Thanks!
rsgooch

---

### Post by ian dobson on 2010-05-30
Hi,

Creating a symbolic link wont cause linux to mount  drive "by it's self". You need to manually mount the drive (/etc/fstab)

If you go to the terminal and type "mount" you'll see a list of all mount points active:-

```

root@alpha2:~# mount
/dev/md0 on / type ext3 (rw,noatime,nodiratime)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/md1 on /data type ext4 (rw,noatime,nodiratime,data=writeback,nobh,barrier=0,commit=15)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/data/apache/wss-clan on /home/wss-clan/www type none (rw,bind)
```

Regards
Ian Dobson

---

### Post by rsgooch on 2010-05-30
> **ian dobson said:**
> Hi,

Creating a symbolic link wont cause linux to mount  drive "by it's self". You need to manually mount the drive (/etc/fstab)

If you go to the terminal and type "mount" you'll see a list of all mount points active:-

```

root@alpha2:~# mount
/dev/md0 on / type ext3 (rw,noatime,nodiratime)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/md1 on /data type ext4 (rw,noatime,nodiratime,data=writeback,nobh,barrier=0,commit=15)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/data/apache/wss-clan on /home/wss-clan/www type none (rw,bind)
```

Regards
Ian Dobson

This is the results of mount command:
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)

The mount command does not show the mount point either.  I know that the drive is attached because I can remove it and the files disappear from the directory.  It is very confusing, I have not seen this behavior before. 

Any other ideas?

---

### Post by rsgooch on 2010-06-01
No on can shed some light on this problem?:confused:

---

### Post by ian dobson on 2010-06-01
Hi,

Can you try going to the directory where you think your other drive is mounted cpool? and copy a very large file into the directory and just look and see which harddisk LED lights up or do a df, copy a large file into the dir then do a df again.

Normally under linux yo create a directory under / (/mnt/usb1 for example) which is then used used as a mount point. When you mount a drive to this directory the drive you mount "overlays/hides" what already there.

If mount doesn't show your other drive then it's not mounted.

Regards
Ian Dobson

---

