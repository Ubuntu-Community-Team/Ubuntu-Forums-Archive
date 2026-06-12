---
title: "Help need to fix server disk errors."
date: 2024-11-16
forum: Server Platforms
---

### Post by tross9 on 2024-11-16
My ubuntu server is throwing errors and it looks like the drive is failing.


I searched for how to fix the drive errors and tried the following but I can get it to work.

here is what I tried

> df -h   

returns  among other devices. ( note /dev/SDB does not show up but is assigned as md127 or should be If I set the rad up correctly)

 /dev/sda     
 /dev/md127   ( was a raid drive but I removed one of the drive and disabled the raid )

> umount /dev/md127    ( states drive is unmounted)

> fsck -A /dev/md127    ( aborts with msg drive is mounted)


not sure what I'm doing wrong.
here are a few of the error msg.
--
ata3.01 exception fail read DMA
BLK-update dev sdb io error sector 11.......
--
also I have a mapped/samba drive on the ubuntu server to my windows pc and when I try to copy some files from the server to the pc a whole lot of error msgs appear on the severs monitor.
--
I also get error about the MYSQL program,  ( not sure where the MYSQL programs are installed either on the SDA or the SDB drive) but I was able to backup the database.


would using clonezilla to clone the drive as is be recommended?  I could get some of the data off the drive if I cant fix it. I think clonezilla attempt to read the bad sectors.

---

### Post by TheFu on 2024-11-16
There are 2 types of errors.  Logical errors and physical errors.  

Lots can be done to address logical errors. 

Not much can be done to address physical errors - besides RAID (not RAID0) and good backups. 

Sometimes the best solution for RAID issues is to destroy the array, recreate it and restore the data from backups. RAID never replaces backups.  RAID solves 2 problems.  Backups solve 999 problems, and I'm not exaggerating. 

So, first, let's get an overview of your storage. Run these 2 command and post the command + output back here. Use forum code tags or it will be too hard to read (i.e. I won't read it).

```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

If the setup uses LVM, you should also run and post these commands:
```
sudo pvs
sudo vgs
sudo lvs
```

If BTRFS or ZFS are involved, I can't help, but you need to be clear about that.

After we see that output, next steps can happen.
I don't need descriptions of the output.

For logical errors, the first step is to run an **fsck** on the unmount file system device.  The device for the file system will be in the output requested above.  Many issues can be solved by that.
BTW, you have looked at the system logs already, right?

---

### Post by tross9 on 2024-11-17
thanks to replying   I do not have direct access to the server from any remote pc.  so I need to write down and retype the output  ( typos may occur)

I've attach a text doc of the output

[ATTACH]294535[/ATTACH]

as I was trying to write down the DF output , the server keep throwing the ata3 errors msgs, after about 5 to 10 minutes the errors stop showing and the  DF command  stopped showing any info in drive SDB.
 I needed to shutdown -h then power it back on to get the info on SDB to start showing.  shutdown -r  did not seem to restart SDB.

---

### Post by TheFu on 2024-11-17
> **tross9 said:**
> thanks to replying   I do not have direct access to the server from any remote pc.  so I need to write down and retype the output  ( typos may occur)

You should use redirection to store the output into a file [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) , copy the files using a USB drive.  Typos will lead to mistakes - by me and by you.  That link has multiple tips about using redirection.  _Learn them. Know them. Love them._

If a HDD is disappearing, it is likely failing. Hope you have backups and a replacement storage device ready.

Looking at attachments feels like work.

---

### Post by TheFu on 2024-11-17
Ok, first, if you typed all that, ouch. I wouldn't have.  Definitely learn to use redirection.

There are 2 storage devices in the system. I don't see any connections between sda and sdb, so whatever you did related to RAID didn't work. It was a complexity and waste of your time from the output.

You used LVM, but only for the OS and swap.  BTW, the root LV shouldn't be over 35GB in size.  You should have made other LVs for other needs.  The output shows it is 1.8TB in size. That's just crazy.

Any chance you setup a server without really knowing what you were doing?  We all start out that way.
What you've done on sdb is very odd.  You have both LVM and RAID on the same area?  I can't really tell. Perhaps the indentation is wrong?  I have never seen anything like what has been posted before.  The attempted LVM setup on sdb1 could easily have corrupted the attempt at RAID1. 

Was there ever a 3rd disk for the RAID1 previously?

As it is now, I think you should backup everything you can ASAP, run some SMART tests to check whether the disks are failing or not, and then start over with a fresh install with more consideration about storage layouts and methods.  That's easy for me to say from here.

In general, RAID1 should only be used for HA needs.  It never replaces the need for backups.  RAID solves 2 issues. Availability and, perhaps, sometimes, performance.  But RAID on a single device does nothing. Nothing at all.

LVM provides flexibility, but only when used correctly.  Much of that flexibility comes by NOT allocating all the storage. Only allocate what you actually need to the different "parts" of the system that need it.  I've posted and written in these forums many times about how to setup LVM.  Go find one of those posts, read it and ask questions if it isn't clear.

When using SW-RAID, it is common to use RAID1 and then to place LVM onto the full RAID1 device for better storage management.  LVM can create RAID storage too, but it is ugly and not as easy to restore after a failure.  That's an opinion.  OTOH, I don't know how to convince Ubuntu to setup mdadm RAID for the OS during installation, but I do know how to convert an LVM install into an LVM-RAID1 setup  post install.  Again, LVM-RAID is ugly.

I stopped using RAID when I switched to better SSDs.  SSD failure rates are very small and most of them should last 10 yrs, so backups are all I use.  NVMe SSD storage is already so fast that any RAID1 performance gains wouldn't matter at all.

Anyway, ask specific questions if you have any.  I think regaining access to your RAID1 storage beyond what is already possible is unlikely, since it appears to be failing. **Backup everything ASAP.**

---

### Post by tross9 on 2024-11-17
thanks again for replying.



[COLOR=#000000]"[/COLOR][COLOR=#ff0000]Definitely learn to use redirection[/COLOR][COLOR=#000000]."    I'll look into that.[/COLOR]
"[COLOR=#ff0000]If a HDD is disappearing, it is likely failing[/COLOR][COLOR=#000000]. "  That what I was afraid of. started looking for a new drive was the first thing I did before posting this, but hoped that it was just bad sectors.
        so , any suggestions where to look on how to correctly rebuild the server from scratch, the right way? not what I build.  
           I'll be adding or using it for the following: 
            1) Lamp  ( mainly for the PHP website and database)
            2) samba share
[/COLOR]
lets start with the history.

1) "[COLOR=#ff0000]Any chance you setup a server without really knowing what you were doing?[/COLOR][COLOR=#000000] "    [/COLOR][SIZE=3]yes[/SIZE][COLOR=#000000],  this server was setup back around 2016 or earlier , had no knowledge of Ubuntu or Linux back then, I [/COLOR][COLOR=#000000]followed a setup tutorial that used LVM for the drives. and keep using it if I need to rebuild the server.[/COLOR][COLOR=#000000]
2) "[/COLOR][COLOR=#ff0000]You have both LVM and RAID on the same area?[/COLOR][COLOR=#000000] "[/COLOR][COLOR=#000000] SDB was setup as a LVM non-raid and I got a second 1TB drive and created the Raid for SDB [/COLOR][COLOR=#000000](still as a LVM partition)[/COLOR][COLOR=#000000]. [/COLOR][COLOR=#000000]
3) then I ran the  Raid for About 4-5 yrs , then in 2019, I needed the second 1TB for my main PC (it's 1TB drive was failing, it was create in 2008 with the 1TB) broke/disabled the mirror and left it as you see it.
4) yes, I do backup the two of the most important systems and data (from the server I backup the database to my main PC and clone it to an external SSD) 

as to the data lost from the server, I'll probable lose my folder where I keep my software [/COLOR][COLOR=#000000]Patches [/COLOR][COLOR=#000000]on my server (  mostly games patches and most likely  I can get the patches off the internet if I need them)


My expertise is in sql databases and programing for them ( VB, C#, MS VS 2007, 09 etc... , PowerBuilder ( old Sybase program similar to VS)
 

in a nutshell. if we use the Microsoft course level to describe my knowledge.   ( where 100 is beginner) 

as to servers
Ubuntu = 100  -- so yes I can setup the server but cant completely understand what I'm doing.  
MS Servers   = 300

databases
Informix  =   150
Sql = 300    ( MsSql , Mysql, etc)


again thanks for the help.[/COLOR]

---

### Post by TheFu on 2024-11-18
I know next to nothing about recent MSFT stuff.  Haven't programmed on MS-Windows since the 1990s and I've avoided it as much as possible since about 2008.  In short, 100, 300 means nothing to me, but I don't think it is relevant.

Leaving a RAID broken for years is a poor administrative choice. Either have RAID and maintain it or don't.

There are step by step guides on the internet for how to setup storage for a server.  Some links are posted by others in these forums over the last 10 yrs.  It isn't something that interests me.  I'm more about "why", not "what to type".  The *what to type* is spelled out in the manpages on every Linux system already.

I'll spend 2 minutes searching for a server-setup guide .... if nothing is added to this post, then I didn't find one in that 2 minutes, but I'm positive they are in these forums.  BTW, if you read the header, all those posts for guides are about to disappear in a few weeks, so don't wait.

---

### Post by tross9 on 2024-11-18
Thanks for looking for setup guides and thanks for helping me out.

---

### Post by TheFu on 2024-11-18
> **tross9 said:**
> Thanks for looking for setup guides and thanks for helping me out.

I fear the guide links I was thinking of have been removed from these forums - lots of us older guys have been dying off, so our personal websites get taken down after death by our families.  I think the username was "Hammond" who used to provide links to his base server setup with LVM.  I looked for his personal website. Couldn't find it either.

More and more, older posts have been disappearing.  I've noticed that some of my diagrams have been removed. Don't know why and I didn't do it.  OTOH, these forums are going away next in January, so nobody will be posting here. Haven't decided about Discourse.

---

### Post by bobunderwood99 on 2024-11-18
TheFu,

I think you're thinking of "LHammonds".

---

### Post by TheFu on 2024-11-18
> **bobunderwood99 said:**
> TheFu,

I think you're thinking of "LHammonds".

Yep!  He's still around here too. That's good news!  I've had too many online friends disappear this year, and a few IRL friends too. ;(

[https://ubuntuforums.org/showthread.php?t=2459660&p=14028065#post14028065](https://ubuntuforums.org/showthread.php?t=2459660&p=14028065#post14028065) has a link, but it won't open for me.  Maybe the wayback machine has it or it is down temporarily?  IDK.  This sort of stuff is why I run a Wallabag Server - so when things I want as reference are found on the internet, I can grab a local copy that can't disappear.  I didn't snag anything from LHammond as our skills overlap, sorry.  I did snag a bunch of LVM articles, but mostly around snapshots, thin provisioning and use with LXD. None of that is helpful for this thread.

---

### Post by sgt-mike on 2024-11-19
ZFS vs MDADM  raid might be a option that the OP might consider, when /if rebuilding. 
Not sure what the OP's objectives are. (I mean we know he wants to fix the array, but rather long term storage redundancy needs 1, 2, or 3 disk failure)

I have ran both I did like mdadm in a raid 5 array, but ZFS seems to be way easier to setup / maintain, but then again I haven't ran it for years yet. Like some on here have. But so far it's been great. Both have strong points. 
I went 9 drives wide @ 4TB a drive with a ZFS pool and will soon add at least three hot spares to that data pool. 

My post doesn't fix the OP issues but does provide food for thought for the OP in a planning stage.
And yes you can add hotspares to a mdadm raid 1 array. **Which is the take away.** Hotspares allows time to get a new drive into the array/pool.

Like the The Fu says raid is not a backup. Personally I store backups and snapshots separately. I'm constantly (as in daily) going to my NFS server via ssh to check the drives health. Only thing a raid does is allows you time to get a drive in before 1 drive failure turns into two or three failing drives, other than get a group of drives to act as one. Primary idea is to replace the drive before it actually fails.

The Fu will know way more than I on how to fix this to work with LVM. I Just wanted to throw the hotspare idea out there.

---

### Post by rebeccatucker on 2024-11-19
Great

---

### Post by tross9 on 2024-11-24
update:   ( I am going to replace the sdb drive but I want to test a few things first)

1) it looks like the Mysql database on sdb is sitting on a badblock, when I stop the mysql pgm the server stop throwing sector errors.
    when I stop mysql, the /dev/sdb no longer appears in the df -h but /dev/md127 is still listed.   (md127 is the raid of sdb)

what i would like to do.

1) fix the bad sectors/blocks so the server stops throwing errors.

optional -  remove the raid ( drop md127 leaving sdb without formatting, if possible, this can wait till the new drive is in)
 
so far I did the following , but not sure if it fixed the errors.

1) /etc/init.d/mysql stop   ---  this stop the server from throwing errors, if i did not stop mysql , after about 10 - 20 minutes sdb not md127 would not display in the output of df -h
2) sudo badblocks -sv /dev/md127 > badblocksoutput    -- listed error  (20/0/0)
3) sudo fsck -t ext4 -L badblocksoutput /dev/md127    ---- ran to completion 
4) rebooted server
5) still throws sector errors.  ( until mysql is stopped)

If I understand FSCK correctly with the option used above, it should have tried to mark/add the bad blocks to a list and try to move the data if possible, i think it may have marked the blocks but mysql is still pointing to the bad blocks (step 5) or fsck did not mark the blocks.

not sure what to do now, assuming the blocks are mark, how can I check to see if the server has mark the bad blocks or how to manually mark them , if did not mark them.
 

TIA

Tim

fyi -- at the time the Raid was setup as a temp backup solution till I could get a permanent solution in place and not knowing how to remove the raid without loosing data I left it as is.

[COLOR=#ff0000]"Only thing a raid does is allows you time to get a drive in before 1 drive failure turns into two or three failing drives," [/COLOR]    -- that was my original idea for the raid.

---

### Post by TheFu on 2024-11-24
Hard disks have extra sectors on them that are automatically remapped so the disk will continue to work.  If those spares run out, time for a replacement. Period.

Use SMART data to see how many and how quickly the reallocations are happening.

---

### Post by tross9 on 2024-11-25
I have to apologize, I failed to state that when mysql is trying to load, it is throwing only one sector error , it displays the same sector over and over until I stop mysql.

what I'm look for is 
1) what disk utilities I need to run to check and fix drive errors, which option to use, and which order to run the utilities, if more than one is needed. 
2) how to tell if the bad blocks and sectors have been marked so that the system knows not to use them.

this Ubuntu server is a Home system and I'm using it to try to learn how to setup one up correctly and maintain it correctly, and not doing it that well . (note: man pages are not my friend, utube vids work better for me)
   the long term goal ( when I have the money for this) is to have it as a database, file shares and cloud server for my windows Pc's.  and back up the server to an external device. for now just a DB and testing server.

until you mentioned smart monitor, I had no clue it existed, and I'm not sure how to use it correctly. 
   
again thanks for all of the replies

Tim

---

### Post by TheFu on 2024-11-25
Google found this: [https://forums.linuxmint.com/viewtopic.php?t=255457](https://forums.linuxmint.com/viewtopic.php?t=255457)
and
[https://www.tecmint.com/check-linux-hard-disk-bad-sectors-bad-blocks/](https://www.tecmint.com/check-linux-hard-disk-bad-sectors-bad-blocks/)  I've found Tecmint is a reputable site for Linux stuff.

If you want a DBMS backup, you'll need to use some smart methods to get a clean backup that isn't corrupted, since DBMS files are always open and being modified. Stopping the DB is 1 method. There are a few others that don't require stopping the DBMS.

BTW, MySQL has been out of favor for nearly a decade now.  MariaDB replace it. You can learn about the history of those changes, if you care. They are API compatible and the team behind MariaDB were the original creators who chose to leave Oracle.

---

### Post by tross9 on 2024-11-26
thank you, I'll look at these.

---

