---
title: "Understand why Server Disk Usage at  100%"
date: 2011-03-18
forum: Server Platforms
---

### Post by tpi on 2011-03-18
Hi, I've got a server running Ubuntu Server 10.04 from a month more or less. It is used principally (at the moment only) as a file server.
Today I cannot connect using vnc (I recieved Connection Refused), I tried to connect via ssh and after I log I recieve this message:

```
Linux myserver 2.6.32-24-server  #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 x86_64  GNU/Linux
Ubuntu  10.04.1 LTS
  
Welcome to the Ubuntu Server!
 *  Documentation:  
  
   System information as of Fri Mar  18 15:36:09 CET 2011
  
   System load:  0.18                     Processes:          154
  Usage of /:   98.7% of 27.50GB   Users logged  in:    0
  Memory usage: 16%                  IP address for lo:   127.0.0.1
  Swap usage:   0%                     IP address for br0:  192.168.123.106
  
   => / is using 98.7% of  27.50GB
  

This is the result of df -h
File system            Dim. Usati    Disp. Uso% Montato su
/dev/md0               28G   28G      0 100%   /
none                    2,0G  244K  2,0G   1%  /dev
none                     2,0G     0    2,0G   0%  /dev/shm
none                    2,0G  1,1M  2,0G   1%   /var/run
none                    2,0G     0    2,0G   0%   /var/lock
none                    2,0G     0    2,0G   0%   /lib/init/rw
/dev/md2               92G 553M    87G   1%   /opt
/dev/md3p1          801G  299G  503G  38%   /mnt/share
//192.168.123.12/public
                          462G  428G   30G   94% /mnt/backups


As you can see I've got an mdadm Raid1 with
/dev/md0 of about 30GB mounted at /  (ext4)
/dev/md2 of about 100GB  mounted at /opt (ext4)
/dev/md3p1 is the share space 

The network folder is an external nas for backups.

When I installed the system the /dev/md0 was used for a 33%,  I don't understand what is using my disk space. I cannot use baobab as i cannot log into the gui and this is the result of the du -sxh * command launched from /:

7,7M    bin
19M      boot
4,0K    cdrom
248K    dev
9,1M    etc
285M    home
0        initrd.img
157M    lib
0       lib64
16K     lost+found
4,0K     media
12K     mnt
366M    opt
du: impossibile accedere a  "proc/14108/task/14108/fd/4": Nessun file o directory
du: impossibile  accedere a "proc/14108/task/14108/fdinfo/4": Nessun file o directory
du:  impossibile accedere a "proc/14108/fd/4": Nessun file o directory
du:  impossibile accedere a "proc/14108/fdinfo/4": Nessun file o directory
0        proc
1,4M    root
7,1M    sbin
4,0K    selinux
4,0K     srv
0       sys
32K     tmp
2,0G    usr
267M    var
0        vmlinuz

```

what do you think? do you have any suggestion?

thank you, I really don't know where to look at...
Federica

---

### Post by psusi on 2011-03-18
If you can't find the files using up the space with du, then it may be orphan files; files that have been deleted, but a process still has them open.  A reboot should clear that.  You also might want to force a fsck on boot:

sudo touch /forcefsck

---

### Post by SeijiSensei on 2011-03-18
Unmount the filesystems that are not part of the root (/opt, /mnt/share, and /mnt/backups) and run du again.  One possibility is that you wrote files to those directories thinking the other filesystems were mounted when they weren't.  Suppose, for instance, that the system failed to mount /mnt/backups for some reason.  When the backup runs, the files will still be written to /mnt/backups, but now they'll be part of the root filesystem on /dev/md0.  Once the mounting problem is fixed, those files will be hidden "beneath" the mounted filesystem.  You'll never see them as long as the other filesystems are mounted.

If your backups are run from a script, have the script check and make sure the remote filesystem is mounted before transferring the files.  Have it send you an email if there's an mounting problem.

---

### Post by volkswagner on 2011-03-18
I did not see the total usage when listing contents of "/".  Did it show ~28G.

You can try --max-depth command to narrow down the area.

```
sudo du / --max-depth=1 -h
```

You may want to unmount any shares or added disks.

Duh looks like you did that.  But I still did not see the total in your post.  did "du" pick up the total?

Did you run
```
ls -alt /
```

to see if the large file is in the root?

Again I'm only asking because I did not see the total.


Also booting a live CD may help pinpoint the issue by running df and du commands.

---

### Post by BkkBonanza on 2011-03-19
Most likely SeijiSensei is right. The reason du doesn't show the 26G missing is because it is hidden under a mounted filesystem. umount them and run du again on /

That will likely turn up what has used up that space.

---

### Post by tpi on 2011-03-21
Hi, thank you everyone for the answers. I could make the check only today but now I can confirm you that SeijiSensei was right. After I unmount /mnt/backups I found that the folder  was keeping busy the 26GB missing.

Finally I changed my backup script to this:

```
if [`/bin/mount -l | /bin/grep //192.168.123.12/public` = ""]; then 
    echo "00 - Network source not mounted - Do nothing" 
else 
    # network source mounted
    rsync -r -t -v --progress -i /mnt/share/01_LAVORI/ /mnt/backups/01_LAVORI/ 
fi
```

I hope it will work, thank you all again.

Federica

---

### Post by SeijiSensei on 2011-03-21
> **tpi said:**
> SeijiSensei was right

(Polishes his Ubuntu Sheriff badge)

> Finally I changed my backup script to this:

```
if [`/bin/mount -l | /bin/grep //192.168.123.12/public` = ""]; then 
    echo "00 - Network source not mounted - Do nothing" 
else 
    # network source mounted
    rsync -r -t -v --progress -i /mnt/share/01_LAVORI/ /mnt/backups/01_LAVORI/ 
fi
```

I hope it will work, thank you all again.

Federica

You need to use spaces to delimit the square brackets like this:

```
if [ "`/bin/mount -l | /bin/grep //192.168.123.12/public`" = "" ]; then 
    echo "00 - Network source not mounted - Do nothing" 
    echo 'Count not mount network source' | mail -s 'Backup problems' frederica@example.com
else 

```

I also added quotes around the backtick output.  It's a good general practice, especially if you need to match a string with embedded spaces.

As I said before, if you're running this script unattended, I'd recommend having the script mail you an error message if it fails.  If you don't have the "mail" command (it doesn't ship with Ubuntu by default), install the bsd-mailx" package.

Good luck, Frederica.

---

