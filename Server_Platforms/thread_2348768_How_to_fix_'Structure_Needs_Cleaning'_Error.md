---
title: "How to fix 'Structure Needs Cleaning' Error"
date: 2017-01-07
forum: Server Platforms
---

### Post by agarwaldvk on 2017-01-07
Hi Everyone


I had been copying/pasting files from my Windows PC (running Windows 10) to my server PC (running Ubuntu 16.04 LTS) using Windows Explorer.

Three (3) files come up as with the 'Structure Needs Cleaning' Error. I know which drive that is on (its on my /sdb1 partition)


Any suggestions as to how can I remove these files from the system. Surprisingly, these aren't even visible in Windows Explorer. I can't even delete from the ubuntu terminal.

What can I do?


This is what comes up from these files

```

ls: cannot access '/sharedfiles/media/Movies/Hindi/Others/Aashiqui 2.avi': Structure needs cleaning
ls: cannot access '/sharedfiles/media/Movies/Hindi/Others/Aitraaz.mkv': Structure needs cleaning
ls: cannot access '/sharedfiles/media/Movies/Hindi/Others/Safar.mpg': Structure needs cleaning


```


Edit :-
Can I use the following safely (these I found somewhere on the net)  :-

```

debugfs -w /dev/sdb1                 --This file is on sdb1 partition - opening partition in read write mode

Then type in these commands in sequence one after the other
clri /sharedfiles/media/Movies/Hindi/Others/Aashiqui 2.avi
clri /sharedfiles/media/Movies/Hindi/Others/Aitraaz.mkv
clri /sharedfiles/media/Movies/Hindi/Others/Safar.mpg

```


Best regards


Deepak

---

### Post by agarwaldvk on 2017-01-09
Hi


Any suggestions on this one please!

It was suggested that I run the 'e2fsck' command but after reading a little bit about it I understand that it should not be run on a mounted device.

Can someone please advise the sequence of steps that I should carry out to (I am very very new to linux based systems and don't want to muck it up in trying to do things not knowing what I am doing) :-

1. unmount this partition
2. run the e2fsck command
3. then reboot the system - will this device be remounted as the fstab entry for the device/partition


Best regards


Deepak

---

### Post by ian-weisser on 2017-01-09
Your sequence is correct, if sdb1 is merely a data partition and not your main system partition.

If sdb1 is your main system partition, then do not unmount. Instead, shut down your machine and boot from a LiveUSB. Your sda/sdb labels may be different after each boot, so check the characteristics of each partition carefully. 

When fsck tries to fix the partition, you may lose some data...or it may wind up in the 'lost and found' directory). Since your filesystem is already corrupted, backing up seems not a useful option anymore, sorry.

---

### Post by agarwaldvk on 2017-01-10
Hi ian_weisser


Thanks for your response.

Do I need to use the -ccf option or just the command as is without any options? I am just being awfully careful because of my limited knowledge in this area!


Best regards


Deepak

---

### Post by ian-weisser on 2017-01-10
sudo fsck /dev/<unmounted_partition>

 No other options.
fsck doesn't have a -ccf option.

---

### Post by agarwaldvk on 2017-01-11
Hi ian_weisser


Tried to unmount the partition using :-

sudo umount /sharedfiles/media                         (this is where the drive/partition /dev/sdb1 is mounted)

Got "target is busy" error

Then tried lsof command as follows with the output like so :-

```

agarwaldvk@MyHomeServer:~$ sudo lsof /sharedfiles/media
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/108/gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
smbd    1702 root  cwd    DIR   8,17     4096    2 /sharedfiles/media
smbd    1702 root   35r   DIR   8,17     4096    2 /sharedfiles/media
smbd    1702 root   36r   DIR   8,17     4096    2 /sharedfiles/media

```

How do I unmount this partition so that I can run the fsck command - something is definitely wrong with my system - some of the video files just don't play which used to play well not so long ago.


Not sure if its a good idea to use

```

sudo umount -f /sharedfiles/media

```


Best regards


Deepak

---

### Post by darkod on 2017-01-11
If the partition you want to unmount has samba shares on it, you need to stop the smbd service first. For 16.04 the command is:
```
sudo systemctl stop smbd.service
```

For 14.04 or earlier it would be:
```
sudo service smbd stop
```

After that you can unmount the device and run the fsck.

---

### Post by agarwaldvk on 2017-01-11
Hi darkod


Thanks for your response. I knew you are a legend.

I do have Samba shares on that partition. I will stop the Samba service and try that again tonight. Hopefully, that should fix the problem.

Something obviously has gone wrong with the system there because I notice that when I play any video from the partition (currently use WD TV Live media player) and try and play the video from a point say 40 minutes from the current point, it just sits there and doesn't move forward. This seems to only happen with videos on that partition - I have only tried a few of the videos but I believe that it would the same with all of them as this might be related to a system problem on that partition (in my case the whole physical drive)

I will try that tonight and see what happens - shall keep you posted. I am hoping that I won't loose my data - all 1.7 Tb of it that resides on that partition.



Best regards


Deepak

---

### Post by victoriastuart on 2017-03-30
Thank you!  This helped me with a rsync (rsnapshot backup error on my Arch Linux x86_64 system!

I had an old, deeply-nested file that was throwing that error (rsnapshot.log),

```
[victoria@victoria rsnapshot_backups]$ sudo rm -fR hourly.5/

    rm: cannot remove 'hourly.5/snapshot_root/mnt/Vancouver/temp/temp - old/temp - 09 (Dec 07, 2014 - Sep 02, 2015)/a_OLD-gmail/victoria.a.stuart@gmail.com/[Gmail]/LINUX/rsync, rsnapshot; Other backups/19.bak': Structure needs cleaning
```

... i.e.,

```
rm: cannot remove .../19.bak': Structure needs cleaning
```

HERE IS THE PROBLEM:

```
[victoria@victoria snapshot_root]$ cd mnt/Vancouver/temp/temp\ -\ old/temp\ -\ 09\ \(Dec\ 07\,\ 2014\ -\ Sep\ 02\,\ 2015\)/a_OLD-gmail/victoria.a.stuart@gmail.com/\[Gmail\]/LINUX/rsync\,\ rsnapshot\;\ Other\ backups/

[victoria@victoria rsync, rsnapshot; Other backups]$ ls -l

    ls: cannot access '19.bak': Structure needs cleaning
    total 0
    -????????? ? ? ? ?  ? 19.bak        ## << THE PROBLEM!!
```

[ See also: [https://www.reddit.com/r/linuxquestions/comments/4b47r2/has_anyone_ever_gotten_structure_needs_cleaning/](https://www.reddit.com/r/linuxquestions/comments/4b47r2/has_anyone_ever_gotten_structure_needs_cleaning/) ]

```
[victoria@victoria LINUX]$ e2fsck -c /dev/sda1

    e2fsck 1.43.4 (31-Jan-2017)
    /dev/sda1 is mounted.

    WARNING!!!  The filesystem is mounted.
    If you continue you ***WILL***
    cause ***SEVERE*** filesystem damage.

    Do you really want to continue<n>? no
    check aborted.

[victoria@victoria LINUX]$ sudo umount /dev/sda1

umount: /mnt/Backups: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)

[victoria@victoria LINUX]$ lsof /dev/sda1

    COMMAND   PID     USER   FD   TYPE DEVICE SIZE/OFF     NODE NAME
    bash     3736 victoria  cwd    DIR    8,1     4096 23179487 /mnt/Backups/rsnapshot_backups/hourly.5/snapshot_root/mnt/Vancouver/temp/temp - old/temp - 09 (Dec 07, 2014 - Sep 02, 2015)/a_OLD-gmail/victoria.a.stuart@gmail.com/[Gmail]/LINUX

[victoria@victoria LINUX]$
```

## MANUALLY KILLED PID 3736

```
[victoria@victoria ~]$ sudo fsck.ext4 /dev/sda1

    e2fsck 1.43.4 (31-Jan-2017)
    Backups contains a file system with errors, check forced.
    Pass 1: Checking inodes, blocks, and sizes
    Inode 147983579 has an invalid extent
    (logical block 0, invalid physical block 0, len 0)
    Clear<y>? yes
    Inode 147983579, i_blocks is 624, should be 0.  Fix<y>? yes
    Pass 2: Checking directory structure
    ...
```

### OOPS!! ACCIDENTALLY CANCELED THAT CHECK (ABOVE); RE-RUN:

```
[victoria@victoria ~]$ time sudo fsck.ext4 /dev/sda1

    e2fsck 1.43.4 (31-Jan-2017)
    Backups contains a file system with errors, check forced.
    Pass 1: Checking inodes, blocks, and sizes
    Pass 2: Checking directory structure
    Pass 3: Checking directory connectivity
    Pass 4: Checking reference counts
    Pass 5: Checking group summary information
    Block bitmap differences:  -(1184247168--1184247245)
    Fix<y>? yes
    Free blocks count wrong for group #36140 (1273, counted=1351).
    Fix<y>? yes
    Free blocks count wrong (495802063, counted=495802141).
    Fix<y>? yes

    Backups: ***** FILE SYSTEM WAS MODIFIED *****
    Backups: 7418099/152621056 files (0.2% non-contiguous), 725140195/1220942336 blocks
    Command exited with non-zero status 1
    12:22.84

[victoria@victoria ~]$
```

REBOOTED.  ALL SEEMS FINE.  :-)  WENT INTO BACKUPS DRIVE, DELETED [sudo rm -f] THAT FILE:

```
/mnt/Backups/rsnapshot_backups/hourly.5/snapshot_root/mnt/Vancouver/temp/temp - old/temp - 09 (Dec 07, 2014 - Sep 02, 2015)/a_OLD-gmail/victoria.a.stuart@gmail.com/[Gmail]/LINUX/rsync, rsnapshot; Other backups/19.bak
```

Q.E.D.?!  :D

---

