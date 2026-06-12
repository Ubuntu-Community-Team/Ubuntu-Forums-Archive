---
title: "Ubuntu 12.04 Mdadm RAID5 Faulty Drive Replacing (Smart Errors)"
date: 2013-12-22
forum: Server Platforms
---

### Post by mcapaldo on 2013-12-22
I have a RAID5 (using motherboard all 6 sata controllers) booting off a usb flash drive.  Had Smart monitor and e-mailing setup and am getting smart error e-mail notifications on /dev/sdb1.  I can the short smart test on it and it stopped at 90%.  

Anyhow I have been playing around in virtual box (Not same system) on how to remove and replace the drive and the following works like a champ for virtualbox

sudo mdadm --detail --scan 
sudo mdadm --manage /dev/md0 --fail /dev/sdb1 
Then, remove it from the array
     Code:

     sudo mdadm --manage /dev/md0 --remove /dev/sdb1 
Then, replace it with a new one...
     Code:

     sudo mdadm --manage /dev/md0 --add /dev/sdb1 
[FONT=monospace]In VB that works great, array quickly resyncs (only using 250MB x4 VDisks).  My setup is slightly different.  When I run sudo mdadm --detail /dev/md0 I get

Clean array and drives show as:  

/dev/sdb1
/dev/sdc1
/dev/sdd1
/dev/sde
/dev/sdf
/dev/sdg

Now /dev/sdb1 is the faulty smart error drive (others short smart tested passed fine).  Can I use the
[/FONT]
sudo mdadm --manage /dev/md0 --fail /dev/sdb1  
sudo mdadm --manage /dev/md0 --remove /dev/sdb1 
 
Then, replace it with a new one...
           sudo mdadm --manage /dev/md0 --add /dev/sdb

Meaning old drive was /dev/sdb1 (originally setup raid5 during os isntall using 3 disks & have added 3 more since) 

and new is just /dev/sdb (minus the 1 at the end)

Will that work fine or am I missing a step?

I read somewhere about using fdisk to copy /dev/sdc1 /dev/sdb1 to create the same partition or something like that.  Can anyone advise, thanks in advance.

---

### Post by sparticle2000 on 2013-12-22
This site has been a great help to me. I tmay help you also.

[http://zackreed.me/articles?tag_id=22](http://zackreed.me/articles?tag_id=22)

Cheers
Spart

---

### Post by rubylaser on 2013-12-22
I would suggest you use sgdisk to copy the partition table from one of your other array members and copy to the new disk.  Let's say /dev/sdc is the disk you want to copy from and /dev/sdb is the new, replacement disk.

```

sudo -i
apt-get install parted gdisk -y
sgdisk --backup=table /dev/sdc
sgdisk --load-backup=table /dev/sdb

```

This will create a partition table on your new disk, and you can add it back to mdadm like this.
```

mdadm --manage /dev/md0 --add /dev/sdb1

```

---

### Post by mcapaldo on 2014-01-01
Well I will mark this as solved but thought I would share what I ran into.

1. sudo -i is DANGEROUS, does not even ask for a password for Root.
2. ran install parted gdisk -y and it complained about a library.  so I took out gparted and that installed ok.
3. ran sgdisk --backup=table /dev/sdd1 and it said something about converting to GPT table, I cringed, thought I hosed the whole array right there.  
4. tried sgdisk --load-backup=table /dev/sdc1 and it errored out.
5. so I ran mdadm --manage /dev/md0 --add /dev/sdc and it added it and began re-syncing the array.  Took 6 hours, and comes up clean now.  No errors, ran smart tests on all drives again, and found that e-mail from smartctl rarned me about me failing a drive and a degraded array, kinda cool.  

All is well, but /dev/sdc shows up as /dev/sdc not /dev/sdc1 as it was.  does not seem to affect anything.  Raid is back up and running.  Got a new drive to install to convert to raid6 for next task.  


-------------------Original Message-------------------------------------------
sudo -i
apt-get install parted gdisk -y
sgdisk --backup=table /dev/sdc
sgdisk --load-backup=table /dev/sdb
[/CODE]

mdadm --manage /dev/md0 --add /dev/sdb1

---

### Post by CharlesA on 2014-01-02
> **mcapaldo said:**
>  sudo -i is DANGEROUS, does not even ask for a password for Root.

Well, yeah, sudo -i logs you into a root shell, so running sudo won't prompt for a password.

As far as the /dev/sdc vs /dev/sdc1 thing, did you create a file system on the drive after you added the partition table to it?

---

### Post by rubylaser on 2014-01-02
> **mcapaldo said:**
> Well I will mark this as solved but thought I would share what I ran into.

1. sudo -i is DANGEROUS, does not even ask for a password for Root.
2. ran install parted gdisk -y and it complained about a library.  so I took out gparted and that installed ok.
3. ran sgdisk --backup=table /dev/sdd1 and it said something about converting to GPT table, I cringed, thought I hosed the whole array right there.  
4. tried sgdisk --load-backup=table /dev/sdc1 and it errored out.
5. so I ran mdadm --manage /dev/md0 --add /dev/sdc and it added it and began re-syncing the array.  Took 6 hours, and comes up clean now.  No errors, ran smart tests on all drives again, and found that e-mail from smartctl rarned me about me failing a drive and a degraded array, kinda cool.  

All is well, but /dev/sdc shows up as /dev/sdc not /dev/sdc1 as it was.  does not seem to affect anything.  Raid is back up and running.  Got a new drive to install to convert to raid6 for next task.  


-------------------Original Message-------------------------------------------
sudo -i
apt-get install parted gdisk -y
sgdisk --backup=table /dev/sdc
sgdisk --load-backup=table /dev/sdb
[/CODE]

mdadm --manage /dev/md0 --add /dev/sdb1

As CharlesA said sudo -i isn't anymore dangerous than using sudo <command>, it's just logging you into a root prompt (you still need a password the first time).  You have just added the raw disk to the array rather than a partition on the disk that is equally sized to your other disks.  This could potentially cause a problem in the future if you have to replace a disk and it is slightly smaller than your previous disk, it won't let you you add it to the array (this is very unlikely).  Anyways, glad you got it working.  And, I would definitely recommend you convert to RAID6 (the reshape will take a long time).

---

