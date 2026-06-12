---
title: "hard disk half full, system says no space left"
date: 2011-06-30
forum: Server Platforms
---

### Post by PHSchi on 2011-06-30
Hi!

For our workgroup I set up a server which is basically 10.04.2 with kernel 2.6.32-32-server on a SSD and all the data on a RAID 5 consisting of 4 2TB hard disks, thus a maximum of 6TB space for data on the RAID. Having multiple users with different amounts of data from different scientific data source I set up an lvm on top of the RAID
  --- Physical volume ---
  PV Name               /dev/sdb2
  VG Name               home-data
  PV Size               5,45 TiB / not usable 3,00 MiB
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              1427652
  Free PE               209335
  Allocated PE          1218317
and 
  --- Volume group ---
  VG Name               home-data
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  7
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                6
  Open LV               6
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               5,45 TiB
  PE Size               4,00 MiB
  Total PE              1427652
  Alloc PE / Size       1218317 / 4,65 TiB
  Free  PE / Size       209335 / 817,71 GiB

With these Volumes:
 LV      VG          Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  4D      home-data   -wi-ao   1,82t                                      
  Apotome home-data   -wi-ao  93,13g                                      
  Genomes home-data   -wi-ao   1,82t                                      
  home    home-data   -wi-ao 465,66g                                      
  photos  home-data   -wi-ao 465,66g                                      
  srv     home-data   -wi-ao   9,31g

Here is the problem: The volume Genomes (or /genomes) is half full 
sudo df -ah
/dev/mapper/home--data-Genomes
                      1,9T  850G  920G  49% /genomes
but the system states it as full whenever I try to add more data (tried cp and rsync). There is no quota set to the volume (I have quotas in place for users home folders. These are only for max amount of disk space, not max file number, and I am still able to move/add files elsewhere so there seems to be no interference). 
So frankly, I am at a loss. What's the problem?

Any help appreciated. 

Thanks,

Phil

---

### Post by rubylaser on 2011-06-30
> **PHSchi said:**
> Hi!
I set up an lvm on top of the RAID
  

Not that it matters at this point, but why did you do this?  A single filesystem on top of mdadm would have probably accomplished everything you needed to, and decreased the complexity in the process.

What is the output of
```
mount
```I can see the system retaining 5% of your disk space if your using EXT4, and didn't do something like this to your filesystem to prevent it from holding that back.
```
tune2fs -m 0 /genomes
```But, not 50% :)

Also, what's the output of this on your mdadm array
```
mdadm --detail /dev/md0
```

Also, can you cd into that directory and make a file from there?  And what's the exact error message that it gives you?
```
cd /genomes
touch testfile.out
rm testfile.out

```

If that works, can you make a temporary 1GB file there?
```

dd if=/dev/zero of=/genomes/testfile.out bs=1M count=1000

```

---

### Post by PHSchi on 2011-06-30
Hi!

Thanks for advice. Before trying what you suggest, just need to clarify it's a hardware raid. Thus no mdadm.
Why did I do it? Well read about lvm, sounded interesting and useful, so let's try it....

---

### Post by PHSchi on 2011-06-30
Ah yes, and it's ext4.
Well, then:
mount gives

mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
/dev/sda1 on /boot type ext4 (rw)
/dev/mapper/tmp--var--usw-tmp on /tmp type ext4 (rw)
/dev/mapper/tmp--var--usw-var on /var type ext4 (rw)
/dev/mapper/home--data-srv on /srv type ext4 (rw)
/dev/mapper/home--data-Apotome on /apotome type ext4 (rw)
/dev/mapper/home--data-home on /home type ext4 (rw,usrquota)
/dev/mapper/home--data-Genomes on /genomes type ext4 (rw)
/dev/mapper/home--data-4D on /4d type ext4 (rw)
/dev/mapper/home--data-photos on /photos type ext4 (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

while
touch testfile.out
touch: cannot touch `testfile.out': No space left on device

So that is the output I always get when cp or rsync or whatever to /genomes now. Sorry for not stating it that way originally.

Finally after
tune2fs -m 0 /dev/mapper/home--data-Genomes

the problem remains.

---

### Post by SeijiSensei on 2011-06-30
What does df show?  Is the root partition full?

---

### Post by PHSchi on 2011-06-30
nope:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              14G  5,0G  8,1G  39% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                  1,9G  268K  1,9G   1% /dev
none                     0     0     0   -  /dev/pts
none                  2,0G  164K  2,0G   1% /dev/shm
none                  2,0G  644K  1,9G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
/dev/sda1             230M  134M   85M  62% /boot
/dev/mapper/tmp--var--usw-tmp
                      4,6G  138M  4,3G   4% /tmp
/dev/mapper/tmp--var--usw-var
                      9,2G  959M  7,8G  11% /var
/dev/mapper/home--data-srv
                      9,2G  150M  8,6G   2% /srv
/dev/mapper/home--data-Apotome
                       92G  188M   87G   1% /apotome
/dev/mapper/home--data-home
                      459G   86G  350G  20% /home
/dev/mapper/home--data-Genomes
                      1,9T  850G 1013G  46% /genomes
/dev/mapper/home--data-4D
                      1,9T  196M  1,8T   1% /4d
/dev/mapper/home--data-photos
                      459G   26G  411G   6% /photos
rpc_pipefs               0     0     0   -  /var/lib/nfs/rpc_pipefs
nfsd                     0     0     0   -  /proc/fs/nfsd
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc

---

### Post by rubylaser on 2011-06-30
I shouldn't have assumed you where using mdadm :)  Well based on what df reports, it thinks you have a good amount of space available.  Can you post your /etc/fstab so we can see that.  This seems like a quota is in place even though you said that one isn't.

And, maybe look at ```
quotacheck -va
```
or
```
quota
``` on the user that you're trying to write to the directory with.

Also, have you looked at the logfiles or used tail -f to watch the logfiles while you try to write to this directory, to see if it gives you any hints.

---

### Post by PHSchi on 2011-06-30
/var/log$ tail -f *

nothing suspicious comes up from there when touch file in /genome, also not when sudo touch file (just as a test). no report at all, to be precise. my mysql was generating some errors, but that stopped, when I shut down the service. however, not affecting my general prob.
fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=44819d9c-f24b-4021-91c9-bee1e0c1e754 /               ext4    errors=remount-ro 0       1
/dev/mapper/home--data-4D /4d             ext4    defaults        0       2
/dev/mapper/home--data-Apotome /apotome        ext4    defaults        0       2
# /boot was on /dev/sda1 during installation
UUID=87113739-a09a-4ee4-b0bc-bf4e83ee40c5 /boot           ext4    defaults        0       2
/dev/mapper/home--data-Genomes /genomes        ext4    defaults        0       2
/dev/mapper/home--data-home /home           ext4    defaults,usrquota        0       2
/dev/mapper/home--data-photos /photos         ext4    defaults        0       2
/dev/mapper/home--data-srv /srv            ext4    defaults        0       2
/dev/mapper/tmp--var--usw-tmp /tmp            ext4    defaults        0       2
/dev/mapper/tmp--var--usw-var /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=e753ef80-6057-48f9-9c96-ac3f2317251f none            swap    sw              0       0

/genomes$ quota
Disk quotas for user xxx_yyyyy (uid 1000): none

/genomes$ quotacheck -va
quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotacheck after an unclean shutdown.
quotacheck: Quota for users is enabled on mountpoint /home so quotacheck might damage the file.
Please turn quotas off or use -f to force checking

If I remember rightly I haven't even set a quota for my users home, just for the other users. Can check, but shouldn't matter as it seems, or should it?:confused:

---

### Post by i.r.id10t on 2011-06-30
Do you have lots of little files? You may have free space, but no inodes to reference that free space with ...

Try 

df -i

And see what you get

---

### Post by rubylaser on 2011-06-30
I didn't even think if inodes with scientific data and tons of small files, this definitely could be the problem.

[http://serverfault.com/questions/104986/what-is-the-maximum-number-of-files-a-file-system-can-contain]("http://serverfault.com/questions/104986/what-is-the-maximum-number-of-files-a-file-system-can-contain")

---

### Post by tgalati4 on 2011-06-30
That could be the 64,000 subdirectory question.

---

### Post by PHSchi on 2011-07-01
Jap, you are right:  ;-)
/dev/mapper/home--data-Genomes
                     1907456 1907456       0  100% /genomes

Also I exactly now where these files are and where they come from. However, what do I do about it, i.e. where and how do I store them....

Thanks to everybody !!!

---

### Post by frncz on 2011-07-01
This is perhaps naive, but can you tar or zip them?

---

### Post by PHSchi on 2011-07-01
sure, i can, and that was the first thing obviously i thought about. however, the file structure these analysis puts out is very deep, so achieving and compressing will take ages. still, if that's the only way for long term storage, that's the way to go then.

---

### Post by SeijiSensei on 2011-07-01
A quick Google search brought up [this page](https://ext4.wiki.kernel.org/index.php/Considerations_when_creating_ext3_filesystems#Number_of_inodes):

> The number of inodes in the system can not be changed after the filesystem is created, at least without growing the filesystem. If the filesystem is grown using resize2fs (wihch requires increasing the size of the partition or logical volume on which the filesystem resides, of course), the number of inodes in the filesystem will grow, but only in rough proportion to the number of blocks in the filesystem.

The proportion of inodes to disk space available is controlled by the -i option to mke2fs.

There is no harm in creating too many inodes, except that time to fsck the filesystem will grow a small amount, and space that could be used for file storage will be reserved for the inode table.


So if you can back up the files to another medium, you could recreate the filesystem with a larger number of inodes using "mke2fs -i".

---

### Post by PHSchi on 2011-07-01
Thanks! Cool. Going to try that. (should have googled myself!). Thanks again to everybody!

---

### Post by Rob Frost on 2012-03-13
Hi guys, I have a similar problem to this within my root file system in that Ubuntu is mis-reporting the available space. Can anybody help?

The command df -h

shows /dev/md1 910G in size, mounted on / with 870G used. But it shows 100% Use and 0 Available.
Both Shift-deleting files (I've deleted 40G of files), and deleting then locating all Trash folders and emptying them, successfully free up disk space but fail to make any more space available.

I have an additional 1.8TB mdadm volume mounted at /home/raid2 and my suspicion is that this is confusing Ubuntu re the available space, i.e. Ubuntu is deducting disk usage within the 1.8T from the 910G available on /.

Any ideas / suggestions to determine if that is in fact the case, and to diagnose and fix this issue?

P.S. baobab is giving an error baobab:5165 error in dir /home/design: Error stating file '/home/design/.gvfs': Permission denied.  Probably not relevant, but thought I'd mention it.

---

