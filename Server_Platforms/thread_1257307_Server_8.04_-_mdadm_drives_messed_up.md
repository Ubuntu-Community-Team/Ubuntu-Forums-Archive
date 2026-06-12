---
title: "Server 8.04 - mdadm drives messed up"
date: 2009-09-03
forum: Server Platforms
---

### Post by NJBarraco on 2009-09-03
I have a serious situation, it is making me go crazy.

So The other day we shut down the server and add a few hard drives.
When we power the system back up, everything is normal until I log in to vmware server. All my Virtual Machines are missing. Well they are there. It says <Unavailable> 

Check my RAID using webmin, and the drives are there, but they are now mixed up. 

I Every time I boot up, it seems to change paths? (sd?#)

My question is, how can I make them static? If a drive fails, I do not want another device taking its path ot (sd?#)

What should I do, I'm sick of losing all my data :( its not fun anymore.


Configuration:
5 Seagate 500GB HDD - SATA Interface
1 Drive is the master, or where ubuntu is stored
2 Drives are running RAID1 mount path is /data (Where virtuals live)
2 Drives are running in RAID1 mount path is /backup

---

### Post by fjgaude on 2009-09-05
Okay, what does your fstab file look like?

---

### Post by NJBarraco on 2009-09-05
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9f21dd00-4b26-49e9-865f-8b14efc77809 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a240eb39-0e15-4420-afa0-f4d4d3a5defe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/md0  /data  ext2  suid,dev,exec  0  0
/dev/sdc1  /test_backups  ext3  suid,dev,exec,noauto  0  0

---

### Post by fjgaude on 2009-09-05
The only thing I'd do is use the UUID for /sdc1 in fstab.

Then I'd reinstall VMware server, if you upgraded your OS. You might have to use one of the update files to correctly compile the vmware code. If so, let me know.

---

### Post by NJBarraco on 2009-09-09
This is what my new fstab looks like, but if I pull out the second and forth drive. They are still out of order. I need them to be static. 


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9f21dd00-4b26-49e9-865f-8b14efc77809 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a240eb39-0e15-4420-afa0-f4d4d3a5defe none            swap    sw              0       0
# /dev/sdb1
UUID=0cc244e8-e8f4-4ab8-8e9b-12287c37e847 /dev/sdb1       ext3
# /dev/sdc1
UUID=1b1f9b1d-124f-4d1b-a666-24b9c0ddb9a2 /dev/sdc1       ext3
# /dev/sdd1
UUID=2378d4a3-23fa-4f2e-8b84-a3804393fdfa /dev/sdd1       ext3
# /dev/sde1
UUID=45b68965-92c7-4903-8332-786ae65b9dc8 /dev/sde1       ext3
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by fjgaude on 2009-09-09
What do you mean, out of order? Where do they show up? Do you have to name the mountpoints as the drive names?

---

### Post by NJBarraco on 2009-09-11
Well I would like sda1 and sda2 to be the main drive or root

sdb1 - DATA1
sdc1 - DATA2

sdd1 - BACKUP1
sde1 - BACKUP2


I am using mdadm and once the drives mix up my raid gets f#$ked.

---

### Post by tgrimley on 2009-09-11
mdadm assembles usin uuid doesn't it? what's the output of the blkid command?

---

### Post by NJBarraco on 2009-09-13
I would think thats what mdadm would use. But I am controlling it within webmin, which uses mount points, or the I've been calling them drive letters. (sda1)

when I run blkid, this is what I get. The drive that is formatted in fat32 is a hot swap drive we use to back things up. just ignore it. kinda? That's what actually keeps messing us up. Every time we but in a new drive everything gets out of place

/dev/sda1: UUID="2378d4a3-23fa-4f2e-8b84-a3804393fdfa" TYPE="ext3" LABEL="BACKUP                             1" SEC_TYPE="ext2"
/dev/sdc1: LABEL="BACKUP2" UUID="45b68965-92c7-4903-8332-786ae65b9dc8" SEC_TYPE=                             "ext2" TYPE="ext3"
/dev/sdb1: UUID="1b1f9b1d-124f-4d1b-a666-24b9c0ddb9a2" SEC_TYPE="ext2" TYPE="ext                             3" LABEL="DATA2"
/dev/sdd1: UUID="4AA7-DCCF" TYPE="vfat"
/dev/sde1: UUID="9f21dd00-4b26-49e9-865f-8b14efc77809" TYPE="ext3"
/dev/sde5: TYPE="swap" UUID="a240eb39-0e15-4420-afa0-f4d4d3a5defe"
/dev/sdf1: UUID="77fc3f23-1a8c-d1ca-bd80-b0e811373daf" TYPE="DATA1"

---

### Post by Nullexe on 2009-09-14
Just to chime in, this happened to me as well.  Looking for a solution.

I have been using mdadm from the command line and webmin just to view the graphs.  Its happened before when I installed a new disc but I have to go through my notes.

---

### Post by tgrimley on 2009-09-14
I'm confused why members of the same raid set don't have the same UUID in the blkid output.  I just tried making a raid1 and it they show up the same.  How did you manage to get them different?

---

### Post by fjgaude on 2009-09-14
Well, **mdadm** creates in the superblock of each drive in an array a UUID, it's not the UUID that you mount a drive from. It's the UUID that mdadm uses to auto assemble the array at boot time. This UUID is what is in the /etc/mdadm/mdadm.conf file.

The **blkid** command shows the drive mount UUID and has nothing to do with a software raid assemble UUID.

---

### Post by NJBarraco on 2009-09-24
The reason is due to the fact I re-formated the drive, and I am trying to start over again. 

Can I be pointed to a tutorial were I can set up MDADM correctly?

I have spoken to other, people and they also are having the same issue.

---

### Post by fjgaude on 2009-09-26
Is your **md0** array still in your **fstab**? It should be unless you mount it manually.

don't use any UUID for the array... it doesn't need such as **mdadm** uses the special UUID that's in the mdadm.conf file to auto assemble.

---

### Post by Vegan on 2009-09-26
I hate software RAID as they fail all the time. Go get a RAID card with a BIOS and that should cure most headaches.

Cheap cards are fine, no need for a enterprise grade card.

---

### Post by fjgaude on 2009-09-27
> **NJBarraco said:**
> The reason is due to the fact I re-formated the drive, and I am trying to start over again. 

Can I be pointed to a tutorial were I can set up MDADM correctly?

I have spoken to other, people and they also are having the same issue.

I do believe you will have to zero the superblock using **mdadm** before you can reuse the drive, i.e., start over.

```
sudo mdadm --zero-superblock /dev/sdxx
```

where sdxx is the partion to reuse.

---

