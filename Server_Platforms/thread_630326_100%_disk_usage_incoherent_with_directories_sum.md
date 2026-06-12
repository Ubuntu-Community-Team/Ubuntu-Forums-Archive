---
title: "100% disk usage incoherent with directories sum"
date: 2007-12-03
forum: Server Platforms
---

### Post by wodan on 2007-12-03
Hi boys,

I'm Italian and my English is very poor so... sorry! :(

Anyway, I've got a problem with my file server based on 6.06.1 LTS.

I created it one year ago more or less, and I had never problems with it until few day ago when...
```
carlo@nas:~$ df -h
Filesystem            Dimens. Usati Disp. Uso% Montato su
/dev/hda1             9,0G  9,0G     0 100% /
varrun                 62M  216K   62M   1% /var/run
varlock                62M  4,0K   62M   1% /var/lock
udev                   62M   60K   62M   1% /dev
devshm                 62M     0   62M   0% /dev/shm
/dev/md0              151G   53G   91G  37% /media/raid1
```

This server is used by 10 people (by XP clients), but anyone has an own home directory to save personal file or settings: they use the server just a storage machine, working on the data of the raid1 (/media/raid1).

The only thing I've made is verify the space used by any directory of the file system, except /media, and this is the output of "du" command:
```
carlo@nas:/$ sudo du -hs
4,3M    bin/
9,5M    boot/
0       cdrom/
4,0K    debootstrap/
196K    dev
3,3M    etc/
36K     home/
4,0K    initrd/
76M     lib/
48K     lost+found/
--	media/ (I don't check it, there's mounted only the raid1)
4,0K    mnt/
4,0K    opt/
129M    proc/
28K     root/
8,1M    sbin/
4,0K    srv/
0       sys/
8,0K    tmp/
270M    usr/
100M    var/
```

Now, I don't understand why if the sum of the directories space is minor than 9,0G, the "df" command tell me that I've not more free space in the root mount point...:confused:

Any suggestions?

Thanks a lot and really sorry for my English.

wodan

---

### Post by MJN on 2007-12-03
Your du output doesn't make sense - are you sure you just copy-and-pasted the output? The -s flag ought to just print out the summary.

Post the output of **sudo du -h --max-depth=1 /** and **sudo du -h --max-depth=1 --apparent-size /** as it may be you've got some files with holes in (a common occurance with torrent applications that reserve space in advance of downloading the data) and hence df might be counting the holes whereas du isn't.

Mathew

---

### Post by wodan on 2007-12-03
First of all, thanks for the answer!
> **MJN said:**
> Your du output doesn't make sense - are you sure you just copy-and-pasted the output? The -s flag ought to just print out the summary.
You're right, I've launched the command "targeting" every directory of the file system and then used "copy-and-paste" to summarize the results... sorry, I didn't say it.


Now I've learned to use more correctly this command (thanks!) and these are the outputs:
```
$ sudo du -h --max-depth=1 /
Password:
48K     ./lost+found
3,3M    ./etc
95G     ./media
91M     ./var
76M     ./lib
270M    ./usr
4,3M    ./bin
9,5M    ./boot
196K    ./dev
36K     ./home
4,0K    ./mnt
130M    ./proc
28K     ./root
8,1M    ./sbin
8,0K    ./tmp
0       ./sys
4,0K    ./srv
4,0K    ./opt
4,0K    ./initrd
4,0K    ./debootstrap
96G     .

```
```
$ sudo du -h --max-depth=1 --apparent-size /
Password:
48K     ./lost+found
1,9M    ./etc
94G     ./media
86M     ./var
70M     ./lib
198M    ./usr
4,1M    ./bin
9,4M    ./boot
158K    ./dev
25K     ./home
4,0K    ./mnt
129M    ./proc
12K     ./root
7,8M    ./sbin
8,0K    ./tmp
109M    ./sys
4,0K    ./srv
4,0K    ./opt
4,0K    ./initrd
4,0K    ./debootstrap
94G     .

```

---

### Post by MJN on 2007-12-03
Hmm...

In all honesty I don't know! As mentioned I was expecting the two outputs to be very different but the small difference is neither here nor there.

Maybe try posting the output of **sudo tune2fs -l /dev/hda1** so show us the the block status (i.e. how big the blocks are, how many are used/free etc, and how much of the partition has been reserved for root).

Sorry for the all these extra questions but I'm not entirely sure what's wrong so I'm hoping something will jump out at us!

Mathew

---

### Post by wodan on 2007-12-03
> **MJN said:**
> Sorry for the all these extra questions but I'm not entirely sure what's wrong so I'm hoping something will jump out at us!
Don't worry Mathew... as newbie as I'm, I can only give thanks you.

This is the output:
```
~$ sudo tune2fs -l /dev/hda1
Password:
tune2fs 1.38 (30-Jun-2005)
Filesystem volume name:   /
Last mounted on:          <not available>
Filesystem UUID:          039a8570-ebab-42e7-9455-f91ef5a1a70e
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1193696
Block count:              2383636
Reserved block count:     119181
Free blocks:              10836
Free inodes:              1140417
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16352
Inode blocks per group:   511
Last mount time:          Sun Nov 25 12:34:46 2007
Last write time:          Sun Nov 25 12:34:46 2007
Mount count:              6
Maximum mount count:      30
Last checked:             Fri Jun 29 08:03:32 2007
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
First orphan inode:       769570
Journal backup:           inode blocks
```

What can I say further?
This file server is always online, but it is protected by an IpCop firewall; all the people read and write datas on raid1 disks through Samba shared directory, haven't home nor shell access server because I used "-m /dev/null -s /bin/false" options during account creations.

---

### Post by MJN on 2007-12-04
Hmm... (again!)
 
The block counts agree pretty much with the df output and so it certainly looks like the partition is indeed full...
 
So where's the space being used? Well, and this is my last 'guess' before I give up totally...
 
The answer was likely staring at us in the face - /media is reported as using 94GB yet your /dev/md0 mount on /media/raid1 is reported as using only 53GB so where is the other 39GB? Try running **sudo du -h --max-depth=1 /media** and seeing if there's anything in that tree.
 
Indeed, you could also try unmounting /dev/md0 from /media/raid1 as there could well be data underneath the mount point!
 
Mathew

---

### Post by wodan on 2007-12-04
Ok, this is the output
```
$ sudo du -h --max-depth=1 /media
Password:
4,0K    /media/cdrom0
4,0K    /media/floppy0
53G     /media/raid1
43G     /media/NAS-BACKUP
95G     /media
```
where - /media/NAS-BACKUP is the mount point of a NAS to backup raid1 datas scheduling in - /etc/crontab rsync commands.
```
$ less /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/md0        /media/raid1    ext3    defaults        0       2
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# collegamento NFS con il NAS-BACKUP
192.168.1.4:/BACKUP     /media/NAS-BACKUP     nfs rw,hard,intr 0 0
```

> **MJN said:**
> So where's the space being used?
I really don't know and I'm so... sad... :(

---

### Post by MJN on 2007-12-04
Try unmounting /dev/md0 and re-running the du command on /media as it might be that you've already got data in /mount/raid1 underneath where you mount your drive.
 
Mathew

---

### Post by wodan on 2007-12-04
> **MJN said:**
> Try unmounting /dev/md0
It's strange...
```
$ sudo umount /dev/md0
umount: /media/raid1: device occupato
umount: /media/raid1: device occupato
$
$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sda1[0] sdb1[1]
      160079552 blocks [2/2] [UU]

unused devices: <none>
```
"occupato" means "busy"... nobody's using the server now and no scheduled rsync command is running...
```
top - 19:58:17 up 9 days,  7:24,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  62 total,   1 running,  61 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7% us,  0.3% sy,  0.0% ni, 99.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    126028k total,   123052k used,     2976k free,    16732k buffers
Swap:   361420k total,      128k used,   361292k free,    69288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7984 carlo     16   0  2076 1032  804 R  1.0  0.8   0:00.18 top
    1 root      16   0  1468  468  412 S  0.0  0.4   0:05.18 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:11.72 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0
   64 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
   65 root      15   0     0    0    0 S  0.0  0.0   0:03.65 pdflush
   67 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
   66 root      15   0     0    0    0 S  0.0  0.0   0:40.55 kswapd0
  659 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1732 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1733 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata_hotplug/0
 1737 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1738 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 1739 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
 1740 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3
 1833 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 2039 root      10  -5     0    0    0 S  0.0  0.0   0:13.46 md0_raid1
 2088 root      15   0     0    0    0 S  0.0  0.0   0:01.24 kjournald
 2267 root      12  -4  2104  640  464 S  0.0  0.5   0:01.85 udevd

```
but I find it
```
$ ps aux|grep mdadm
root      3805  0.0  0.5   1892   644 ?        Ss   Nov25   0:39 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
```

Why is my - /dev/md0 busy?
I'll try later? I know only these commands to monitor the raid state.

---

### Post by stroyan on 2007-12-04
The du command will only report on the size of files that are accessible in the
file system.  But files that have been unlinked will continue to require disk space
as long as they are held open by some process.  Your difference in file space
is likely to be caused by a large file or files that have been unlinked but held open.
You can look for such files with the lsof command
```
sudo lsof +L1
```
That will report all open but deleted files and the processes that have them open.
It is normal for some files to be held open like that.
Don't kill processes just because they are holding open closed files.
But do look for a really large file that would be causing your problem.

---

### Post by MJN on 2007-12-04
Good idea. Should a reboot automatically eliminate unlinked files as a potential cause?

For the unmounting, it s considered 'busy' if you happen to be within the mount point at the time (e.g. in /media/raid1/....) so make sure you're not.

Mathew

---

### Post by stroyan on 2007-12-04
A reboot will certainly remove unlinked files as a potential cause, as it will require stopping all running processes.  An unmount of a file system would also require that you already forced processes to close all linked and unlinked files under that file system.  Of course, unmounting / requires a reboot (or some very clever use of pivot_root).

The lsof command is also very helpful for identifying why a file system is busy.
You can use ```
lsof /media/raid1
``` to see why it can't be unmounted.
lsof will report both open files and use as current working directory.

---

### Post by wodan on 2007-12-04
> **stroyan said:**
> You can use ```
lsof /media/raid1
``` to see why it can't be unmounted.
lsof will report both open files and use as current working directory.
Thanks a lot, I solved it (a client was still connected to the file server): Mathew, this is the output that you asked me:
```
$ sudo umount /dev/md0
$ sudo du -h --max-depth=1 /media
4,0K    /media/cdrom0
4,0K    /media/floppy0
4,0K    /media/raid1
43G     /media/NAS-BACKUP
43G     /media
```
while this is the output of stroyan's command:
```
~$ sudo lsof +L1
lsof: WARNING: can't stat() tmpfs file system /dev/shm/var.run
      Output information may be incomplete.
lsof: WARNING: can't stat() tmpfs file system /dev/shm/var.lock
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE  SIZE NLINK   NODE NAME
smbd    3750 root    2w   REG    3,1 50911     0 769570 /var/log/samba/log.smbd.1 (deleted)
smbd    3750 root    5w   REG    3,1 50911     0 769570 /var/log/samba/log.smbd.1 (deleted)
getty   3857 root  txt    REG    3,1 14684     0 719692 /sbin/getty
getty   3858 root  txt    REG    3,1 14684     0 719692 /sbin/getty
getty   3859 root  txt    REG    3,1 14684     0 719692 /sbin/getty
getty   3860 root  txt    REG    3,1 14684     0 719692 /sbin/getty
getty   3869 root  txt    REG    3,1 14684     0 719692 /sbin/getty
getty   3872 root  txt    REG    3,1 14684     0 719692 /sbin/getty
```


What do you think if I tell you that I "rebooted" the server twice few days ago? :(

---

### Post by stroyan on 2007-12-05
The open and deleted files look very small indeed.  The recent reboot would have
corrected any large deleted but open files.

  (It does look like you haven't rebooted since updating /sbin/getty.  That might be
an issue if it corrected an important security flaw.)

  The /media/NAS-BACKUP mount point is another likely place to have files hidden
from the 'du' command.  If that was not correctly mounted then a backup
might have put really large files in the /media/NAS-BACKUP directory of the "/"
filesystem.  You could check that by unmounting /media/NAS-BACKUP and
having a look in the directory.

There is an interesting way to look at the directory under a mount point such
as that.  Using mount with the --bind option you can see the directory beneath
a mount point without unmounting the file system that covers the directory.
```
mkdir peek
sudo mount --bind / peek
ls -l peek/NAS-BACKUP
sudo umount peek
rmdir peek
```
That will make the peek directory a synonym to / which does not have
the NFS filesystem mounted over the top of the peak/NAS-BACKUP directory.

---

### Post by wodan on 2007-12-05
> **stroyan said:**
> The open and deleted files look very small indeed.  The recent reboot would have
corrected any large deleted but open files.

  (It does look like you haven't rebooted since updating /sbin/getty.  That might be
an issue if it corrected an important security flaw.)
Sorry stroyan but... can you explain me this point with other words, please?

> The /media/NAS-BACKUP mount point is another likely place to have files hidden
from the 'du' command.  If that was not correctly mounted then a backup
might have put really large files in the /media/NAS-BACKUP directory of the "/"
filesystem.  You could check that by unmounting /media/NAS-BACKUP and
having a look in the directory.
I have created my "peek" directory in - /media/raid1 because I have not space in - / ... ](*,)
```
$ cd /media/raid1/
$ sudo mkdir peek
$ sudo mount --bind / peek/
$ cd peek/media/
$ du -sh NAS-BACKUP/
8,4G    NAS-BACKUP/
```

Can we say that you find the solution?

You are really great!!! Thanks Mathew! Thanks stroyan!

After the "repulisti" I have obtained
```
$ df
Filesystem         blocchi di   1K   Usati Disponib. Uso% Montato su
/dev/hda1              9384676    602984   8304968   7% /
varrun                   63012       184     62828   1% /var/run
varlock                  63012         4     63008   1% /var/lock
udev                     63012        60     62952   1% /dev
devshm                   63012         0     63012   0% /dev/shm
/dev/md0             157566460  54894068  94668416  37% /media/raid1
```

Another question: how can I prevent this situation?



Thanks, thanks, thanks, for the support, for the patience, to teach me new commands and to teach me how use better these which I know!
(Probably my English is very unnerving but I hope that the essence... :-D )

---

### Post by MJN on 2007-12-05
> **wodan said:**
> Another question: how can I prevent this situation?

Well, the problem is not so much mounting a device over the top of an already used position within the filesystem but rather something writing to the mount point even without anything mounted there.

There may well be a fancy solution to this but what I do is to create a hidden file on the mounted device (e.g. **touch /media/NAS-BACKUP/.driveismounted**) and then I get my backup script(s) (or anything else that happens to write automatically to that drive) to check for the existance of that file. If it's not there then the drive is probably not mounted and hence the backup (or whatever) should abort.

Here's the code snippet I use, place towards the beginning of my backup script (the script is called from cron and is usually silent - the warning written to STDOUT will get e-mailed to me to alert me to the problem):

```
# Check to see if the remote drive is mounted otherwise rsync will work on
# empty mount points with the potential for undesirable consequences!
if [ ! -f "/mnt/remote/REM-BACKUP/.driveismounted" ];
    then
       echo -e "'/mnt/remote/REM-BACKUP/.driveismounted' appears not to exist hence it is assumed that the backup drive is not mounted. Backup aborted!\n"
       echo -e "Current mounted drives:\n"
       mount
       exit
fi
```I was originally going to parse the output of the 'mount' command to check if the drive(s) are mounted but at least the above code also checks that the drive is alive.

Mathew

P.S. No need to apologise about your English - I probably would not have given it a second thought!

---

### Post by stroyan on 2007-12-06
The output from your run of "lsof +L1" showed six /sbin/getty processes that
were using an unlinked version of the file.  Something has deleted the version of
the file that those processes were started from and put a new one in place.
That is normal for an update such as 'apt-get install util-linux" or a new
security update to the util-linux package installed by update-manager.
When an executable file is unlinked the file is preserved until all processes
running the file exit.  That means that the existing getty processes are still using
old code.  Any getty process started after the update will use new code.
(If you didn't actually update the util-linux package then the changed file would
be very alarming.  The tripwire package is designed for monitoring changes to
system files like this.)

As Mathew noted, you can check for the existence of a file to verify that the
mounted volume is present.  Or you can set really restrictive permissions on
the mount point directory so access will fail when the normal file system is not
mounted over the top of the directory.    (But a process running as root might
still run successfully even if the directory has 000 permissions.)

---

