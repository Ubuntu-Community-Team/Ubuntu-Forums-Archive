---
title: "Best software for pooling disks"
date: 2012-12-05
forum: Server Platforms
---

### Post by MadsRC on 2012-12-05
I have some disks that I need to connect into one filesystem, and sofar I've used mhddfs.

I recently learned there are a few others, them being unionfs and aufs, but i can't seem to find any recent information or comparisons.

There's been a few places where I've seen aufs being proclaimed lighter than mhddfs, giving better speed, and aufs also seem to be in-kernel? On the other hand I've seen a ubuntu wiki (i think it was the wiki?) from 2009'ish stating that there's problems with aufs, and you should stay with unionfs.

Needless to say, I've also read about problems with unionfs.

I know that I won't find a piece of sotware that doesn't have it's problems, but what is the best software to use?

What I'd need it to do is:
[LIST]
[*]Pool many disk's into one virtual disk
[*]Support automatic change to new disk if certain limit is reached
[*]Some kind of overflow protection
[*]Force permissions, owner and group of new files
[/LIST]

Bonus question: What filesystem to use for a fileserver?
It needs to be accessed by Linux, BSD's, Windows & OSX
Currently I used reiserfs 3.6 for my data drives.

---

### Post by rubylaser on 2012-12-05
AUFS is built into the kernel and is much faster than mhddfs.  For the features that you need, I would use AUFS. If you have use the create=pmfs option, it will automatically write to the disk with the most free space in your pool.  It will not rebalance existing data like mhddfs will on disks with existing data, but you can always move items yourself. I have a writeup on setting up AUFS as part of my [SnapRAID tutorial]("http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04").

Overflow protection is easier to do by having a bash script that runs each night and have it send you an email if you get down to 5% available.  Something as simple as this has worked for me in the past.
```
#!/bin/sh
df -H | grep -vE '^Filesystem|none|cdrom' | awk '{ print $5 " " $1 }' | while read output;
do
  echo $output
  usep=$(echo $output | awk '{ print $1}' | cut -d'%' -f1  )
  partition=$(echo $output | awk '{ print $2 }' )
  if [ $usep -ge 95 ]; then
    echo "Running out of space \"$partition ($usep%)\" on $(hostname) as on $(date)" |
     mail -s "Alert: Almost out of disk space $usep%" user.name@gmail.com
  fi
done
```

With any of these pooling solutions, you will partition each disk, and each will have their own filesystem.  I use ext4 on all of my disks. How you share the data will determine what Operating Systems can access it (CIFS, NFS, AFP). To force user:group permissions on a directory, I'd use setfacl.

---

### Post by MadsRC on 2012-12-05
Thank you rubylaser. I'll try it when I have the time in the weekend.

Would I be able to spin down my drives while not writting to them, with AUFS? Haven't tried to spin down with mhddfs yet...

If I used EXT4 for my data drives, I would only be able to access those from machine that support EXT4 system right? = No Microsoft machines. 

That's the reason I chose reiserfs, as I know that is accessible from almost any system

---

### Post by rubylaser on 2012-12-05
> **MadsRC said:**
> Thank you rubylaser. I'll try it when I have the time in the weekend.

Would I be able to spin down my drives while not writting to them, with AUFS? Haven't tried to spin down with mhddfs yet...

If I used EXT4 for my data drives, I would only be able to access those from machine that support EXT4 system right? = No Microsoft machines. 

That's the reason I chose reiserfs, as I know that is accessible from almost any system

Yes, you can spin the disks down with either mdhhfs or AUFS.

There are tools to mount ext2/3/4 partitions in Windows, or Macfuse + ext2 module but I wouldn't bother. If you needed access them from another machine, I'd just use the Live Ubuntu CD.  And, ext4 is supported on every Linux distro.

---

### Post by thnewguy on 2012-12-05
Maybe I'm missing something, but unless speed is a primary concern, I would think ZFS would be ideal for this situation. It supports pools and snapshots and is really easy to set up.

---

### Post by rubylaser on 2012-12-05
ZFS is awesome, but the OP just asked for pooling.  You can't pool disks with ZFS without first wiping out the data on them and creating a pool.  mhddfs or AUFS will allow you to easily present many disks as one volume. 

Also, I'm not sure what you mean by "unless speed is a primary concern" with ZFS.  I have 2 fileservers at home, and one of them is a (9) disk Openindiana raidz2 array. I can read/write to the array at 500-600 MB/s, so speed is not an issue with ZFS, unless you are talking about NFS sync transfers.  You can either disable the sync or use a faster ZIL to overcome this slowness.

---

