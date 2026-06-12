---
title: "Asking advice on how to handle filesystem errors on EXT4"
date: 2012-04-24
forum: Server Platforms
---

### Post by Gestas on 2012-04-24
Hi UF,

First of all, thanks to anyone taking time to read this / respond to this.

My problem is the following: This week one of my production servers had a ful stop. Wich I was able to repair.

It is a server with a RAID5 setup EXT4 filesystem on /
Ubuntu server 10.04 LTS 64 bit

This week, the filesystem went in to a emergency "read only" modus after a disk IO error. The logs showed disk 2 of 4 disconnect, and then went in to read only (no further logging from that point onward).

Being able to connect to the server still, I could force a reboot (with no fsck in the boot). The filesystem showed some errors after that. The raid seemed completely healthy, and I cannot explain the disk IO message in the log.

Running the following command: 

sudo e2fsck /dev/mapper/server01-root -nv 

(using -nv to not execute changes on it)

gave me:

> e2fsck 1.41.11 (14-Mar-2010)
Warning!  /dev/mapper/server01-root is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/mapper/server01-root contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 10747959 was part of the orphaned inode list.  IGNORED.
Deleted inode 10748262 has zero dtime.  Fix? no

Inode 90963974 was part of the orphaned inode list.  IGNORED.
Inode 90963975 was part of the orphaned inode list.  IGNORED.
Inode 90963976 was part of the orphaned inode list.  IGNORED.
Inode 90963979 was part of the orphaned inode list.  IGNORED.
Inode 90963980 was part of the orphaned inode list.  IGNORED.
Inode 90963981 was part of the orphaned inode list.  IGNORED.
Inode 90964063 was part of the orphaned inode list.  IGNORED.
Inode 90964064 was part of the orphaned inode list.  IGNORED.
Inode 90964065 was part of the orphaned inode list.  IGNORED.
Inode 90964066 was part of the orphaned inode list.  IGNORED.
Deleted inode 90964068 has zero dtime.  Fix? no

Inode 90964069 was part of the orphaned inode list.  IGNORED.
Inode 90964085 was part of the orphaned inode list.  IGNORED.
Inode 90964086 was part of the orphaned inode list.  IGNORED.
Inode 90964087 was part of the orphaned inode list.  IGNORED.
Inode 90964800 was part of the orphaned inode list.  IGNORED.
Inode 90964801 was part of the orphaned inode list.  IGNORED.
Inode 90964802 was part of the orphaned inode list.  IGNORED.
Inode 90964803 was part of the orphaned inode list.  IGNORED.
Inode 90964807 was part of the orphaned inode list.  IGNORED.
Inode 95684109 was part of the orphaned inode list.  IGNORED.
Inode 95684865 was part of the orphaned inode list.  IGNORED.
Inode 95686900 was part of the orphaned inode list.  IGNORED.
Inode 95720847 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(36896--36918) -(43264--43518) -(43028288--43028298) -(125391463--125391464) -125740702 -(382767770--382767776) -(382819836--382819839) -(382874126--382874654) -384872073
Fix? no

Free blocks count wrong (707905525, counted=707803062).
Fix? no

Inode bitmap differences:  -10747959 -10748262 -(90963974--90963976) -(90963979--90963981) -(90964063--90964066) -(90964068--90964069) -(90964085--90964087) -(90964800--90964803) -90964807 -95684109 -95684865 -95686900 -95720847
Fix? no

Free inodes count wrong (179880519, counted=179885747).
Fix? no


/dev/mapper/server01-root: ********** WARNING: Filesystem still has errors **********


  196025 inodes used (0.11%)
     650 non-contiguous files (0.3%)
     227 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 182124/417
12388363 blocks used (1.72%)
       0 bad blocks
       1 large file

  159759 regular files
   22129 directories
     104 character device files
      26 block device files
       2 fifos
   24291 links
    8696 symbolic links (8042 fast symbolic links)
      46 sockets
--------
  215053 files

I want to repair the filesystem, but need to take this server down to do it. It is probably going to take a long time to do it (4 TB in Raid 5) I want to ask for your advice in this. Does it need repair fast (can it get worse)? Or is it not so bad, to keep a FS running with errors for a few days / weeks, untill we roll out new servers (on 12.04, but that is not the point).

Thanks a million for any response.

Cheers,

Gestas

---

### Post by ian dobson on 2012-04-24
Hi,

Running a full fsck on a large ext4 doesn't take too long (about 5 minutes on my 8Tb RAID5 partition).

I would recommend you run a check/fix as soon as possible. The corruption could get worse/the sever might fall over if it hits the corruption (Just think to what would happen if the server tries to access a file that has a bad/incorrect inode and ends up reading totaly the wrong information).

The errors your seeing don't actually look so bad, from what I understand the errors are just that an inode has been allocated to a list thats not being used anymore (the inode should be on the free list).

Regards
Ian Dobson

---

### Post by Gestas on 2012-04-30
Thank you for your reply, im going to try this in off hours as soon as possible. Because it obviously needs to be done, reading your answer.

Hopefully it will come back-up, and save me a trip to the datacentre ;) 

And I'll report back here when it's done.

Thanx again for your answer, it is greatly appreciated.

---

### Post by Gestas on 2012-04-30
Just did a reboot with command:

```
sudo shutdown -rF now
```

It should force a fsck. It rebooted pretty fast, so not sure if the fsck is performed in its entirety.

Now the output of...

```
e2fsck /dev/mapper/server01-root -nv
```

is:

> /dev/mapper/server01-root: ********** WARNING: Filesystem still has errors **********


  191160 inodes used (0.11%)
     643 non-contiguous files (0.3%)
     227 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 182527/406
12485789 blocks used (1.73%)
       0 bad blocks
       1 large file

  160154 regular files
   22126 directories
     104 character device files
      26 block device files
       2 fifos
   24291 links
    8696 symbolic links (8042 fast symbolic links)
      47 sockets
--------
  215446 files

I read somewhere else, you cant do the fsck on a mounted filesystem as it does not give accurate info on the state of a fs.

It seems to be running fine, but I want to prevent future problems if that is possible.

Any ideas?

Much obliged.

Gestas

---

### Post by ian dobson on 2012-04-30
Hi,

Maybe try

sudo touch /forcefsck
sudo reboot

Regards
Ian Dobson

---

### Post by LHammonds on 2012-04-30
I am a Linux newbie so don't take what I say as any kind of expert...but if you are having problems with your root partition, I would think the solution to fix it (since it has to be unmounted) would be to boot a rescue CD and then run the check on the hard drive...which none of the file systems will be mounted at this point.

LHammonds

---

### Post by Gestas on 2012-05-21
Im still looking to do this at an opportune time, to get the errors out the filesystem. Will post an update when I do get able to get the errors of the filesystem.

The problem does seem consistent though. No growing number of errors.

---

