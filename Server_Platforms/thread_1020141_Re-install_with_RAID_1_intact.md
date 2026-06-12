---
title: "Re-install with RAID 1 intact"
date: 2008-12-23
forum: Server Platforms
---

### Post by borahshadow on 2008-12-23
Hi I'm sure that this is possible but I want to make sure before I do anything drastic to my server.

I have a server with / on a small old hard drive and /dev/md0 made up of 2 250 GB drives in RAID 1.

Is it possible to format and reinstall the 6GB drive without touching the RAID array? Can the array be configured in the installer or am I better to just do it after words if so how?



Thanks

---

### Post by fjgaude on 2008-12-23
If the two-drive array, raid1, was created with **mdadm**, I'm sure it will come up again when you re-install a new Ubuntu OS on the single boot drive.

After you have the OS running, simply install mdadm and it will auto create the **/etc/mdadm/mdadm.conf** file.

You will, of course, have to place a line in your ```
/etc/fstab
``` file for it the array to auto mount.

Let us know how you are doing.

---

### Post by borahshadow on 2008-12-23
ok so I can just look at my current fstab to get the approprite line for my array. Then install like normal from the server cd and install mdadm and it will do everything automatically?


EDIT: one more question I just had. I just quickly looked at my fstab and saw that I apparently have 2 swap partitions. One on each of the 250 GB drives. Is this bad? will this cause any complications in the installation of the new OS.

Oh and yes they are mdadm arrays on dapper server single boot.

---

### Post by fjgaude on 2008-12-23
> **borahshadow said:**
> ok so I can just look at my current fstab to get the approprite line for my array. Then install like normal from the server cd and install mdadm and it will do everything automatically?

[COLOR="Navy"]No, no... you might wish to re-name your mdadm.conf file, but when you re-install mdadm let it auto create the new one.[/COLOR]

EDIT: one more question I just had. I just quickly looked at my fstab and saw that I apparently have 2 swap partitions. One on each of the 250 GB drives. Is this bad? will this cause any complications in the installation of the new OS.

[COLOR="Navy"]Gosh, you mean that the raid1 has something to do with your booting? If not, then when you install the new OS on a new drive it will setup the swap partition on that drive. Of course, you can create a swap or two on the raid1, on each drive. Likely they are already there. If they are, then in the fstab after you have installed the new OS you can change the lines to point to the drives of the raid1 array.[/COLOR]

Oh and yes they are mdadm arrays on dapper server single boot.

What arrays are on the boot drive presently? Gosh, you have work to do.

---

### Post by borahshadow on 2008-12-23
sorry I think you misunderstood me.
> No, no... you might wish to re-name your mdadm.conf file, but when you re-install mdadm let it auto create the new one.
Why do I need to copy the mdadm.conf? I know I probably should any way but... if I'm going to use an automatically created one?
I only talked about fstab because I'll need to add the array back to my fstab once I reinstall to get it to mount automatically.
> 
Gosh, you mean that the raid1 has something to do with your booting? 
nope the raid is just one big drive mounted in /data

>  If not, then when you install the new OS on a new drive it will setup the swap partition on that drive.
Alright I understand that it will want to make a swap on the drive. I just wondered if I had room on my 6GB drive for swap and the OS but I just checked I'm only using 1.5 GB for the OS.

> Of course, you can create a swap or two on the raid1, on each drive. Likely they are already there. If they are, then in the fstab after you have installed the new OS you can change the lines to point to the drives of the raid1 array.

I think this is how it is already set up. Wouldn't this be bad because if one drive failed then the server would crash?

---

### Post by fjgaude on 2008-12-24
You either re-name or delete the **mdadm.conf** file... the data on it is no good when your new OS comes up. That is why a new has to be created and it is best to have the new **mdadm** create it.

After you are settled, use **blkid** to find the UUID of swap files you created on the raid1 and use both in your **fstab**.

You are good to go.

---

### Post by keithweddell on 2008-12-24
You won't need to do all this - at least if you use the alternate install CD.  You can reinstall the OS on the single drive, configure the RAID drives and decide which partitions should or shouldn't be reformatted - all from the installer.  Your fstab will be set up ready for when you boot into the new install.  I have done this for every release since Dapper.

Keith

---

### Post by borahshadow on 2008-12-24
> **fjgaude said:**
> You either re-name or delete the **mdadm.conf** file... the data on it is no good when your new OS comes up. so just format and let it delete the file? why is the old mdadm config no good?
> 
You won't need to do all this - at least if you use the alternate install CD. You can reinstall the OS on the single drive, configure the RAID drives and decide which partitions should or shouldn't be reformatted - all from the installer. Your fstab will be set up ready for when you boot into the new install. I have done this for every release since Dapper.
Great, my original question was trying to ask if this was possible. Is it safe enough that the raid drives won't accidentally get formated?
Does the alternate CD install the server? I've never used the alternate CD.

---

### Post by keithweddell on 2008-12-24
Make sure that you use manual partitioning and be careful to check which paritions you set to reformat.  As long as you are careful there should be no problem.  But it's always worth having a backup just in case.

The alternate cd can install desktop or commandline.  Thinking about it, I'm pretty sure I've used ther server CD to do this as well.  Give it a go - you can always bail out if the partitioner doesn't pick up the RAID.
Just make sure you bail before saving any changes to disk.

Keith

---

### Post by borahshadow on 2008-12-24
> **keithweddell said:**
> Make sure that you use manual partitioning and be careful to check which paritions you set to reformat.  As long as you are careful there should be no problem.  But it's always worth having a backup just in case.

The alternate cd can install desktop or commandline.  Thinking about it, I'm pretty sure I've used ther server CD to do this as well.  Give it a go - you can always bail out if the partitioner doesn't pick up the RAID.
Just make sure you bail before saving any changes to disk.

Keith

Alright thanks I already downloaded the server CD so I'll just make sure everything else I need is backed up and be careful when I give it a go. Probably after Christmas.


Thanks everybody for helping especially on Christmas Eve

---

### Post by borahshadow on 2008-12-29
Ok I gave it a go. I made sure the partitioner didn't format the raid devices. and set it to install on the 6GB drive. I got a grub error where the installer saw the 6GB disk as SCSI 3 and the raid disks as 1 and 2 so it told grub to look on 2,0 (grub starts numbering with 0) but grub needed to look on 0,0 

That let it boot but now I don't have my raid array. There are 4 entries in my fstab one for (I'm assuming) the 6GB disk 2 for the swaps and one for a cd drive. I installed mdadm but it didn't detect and configure anything.

---

### Post by borahshadow on 2008-12-29
Ok sorry to double post but...
I ran sudo mdadm --assemble --scan and it found and assembled my array. I made the /data directory and could mount it manually but I just need a listing in fstab for it.

---

### Post by fjgaude on 2008-12-30
> **borahshadow said:**
> Ok sorry to double post but...
I ran sudo mdadm --assemble --scan and it found and assembled my array. I made the /data directory and could mount it manually but I just need a listing in fstab for it.

Could you show us what the **/etc/fstab** file looks like now? And also, after you have mounted the array, what **df -h** shows?

After that it will be easy to know what has to go into the fstab file for auto mounting the array.

---

### Post by borahshadow on 2008-12-30
Ok I did some searching and found some info that I used to make a fstab entry and after a reboot It worked but I'll post that stuff you asked for anyway to make sure I did it right.

fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=0a903984-7bbe-46f4-948c-e867f12a1444 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=ef0e12a0-b0a5-4107-aa54-fb579c1e7d49 none            swap    sw              0       0
# /dev/sdb1
UUID=1aeb6e24-88b6-4451-aad1-c84d3691b357 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/md0
UUID=c9a59039-8256-45e7-b194-92ed3be0bda7 /data           ext3    defaults,relatime      0     2

df -h

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             6.0G  825M  4.9G  15% /
varrun                347M  176K  347M   1% /var/run
varlock               347M     0  347M   0% /var/lock
udev                  347M   56K  347M   1% /dev
devshm                347M     0  347M   0% /dev/shm
/dev/md0              229G  164G   54G  76% /data

thanks


Oh I just thought what about my old dapper fstab here it is just in case.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/md0        /data           ext3    defaults        0       2
/dev/sda1       none            swap    sw              0       0
/dev/sdb1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Ok thanks

---

### Post by fjgaude on 2008-12-31
```
UUID=c9a59039-8256-45e7-b194-92ed3be0bda7 /data ext3 defaults,relatime 0 2 
```

Change the above line to:

```
/dev/md0 /data ext3 defaults,relatime 0 2
```

and see what happens. Your UUID for the array is likely not good anymore.

The rest are likely okay. Let us know what happens.

---

### Post by borahshadow on 2008-12-31
Oh thanks but I think it is working fine now. I grabbed a new UUID from /dev/disk/by-uuid when I put that uuid in there. Dapper didn't use uuids but hardy changed to using them by default so I decided that I would too.

The part I had a question about was whether defaults,relatime was ok or if I needed to change that.

---

### Post by fjgaude on 2008-12-31
It's okay by me... you might study the **man** pages for **fstab** to get a good feel for all the options.

Happy all seems okay now.

---

### Post by borahshadow on 2008-12-31
I might do that. Thanks for all your help.

---

