---
title: "fstab software raid setup"
date: 2010-08-10
forum: Server Platforms
---

### Post by ptmuldoon on 2010-08-10
I'm setting up a 4 drive 1TB each software raid in Ubuntu server.  In learning, I've read to edit/add to fstab the UUID of the drives to ensure they are mounting to the correct paths on bootup.

In setting up the raid.  Do I include all 4 drives plus the raid array as mount points in fstab?

Would something like this be correct? (ignore the same UUID #s as I haven't actually set it up yet)

```

UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/drive1 ext4 defaults 0 1

UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/drive2 ext4 defaults 0 1

UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/drive3 ext4 defaults 0 1

UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/drive4 ext4 defaults 0 1

UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/array1 ext4 defaults 0 1
```

---

### Post by ootuoyetahi on 2010-08-10
> **ptmuldoon said:**
> I'm setting up a 4 drive 1TB each software raid in Ubuntu server. In learning, I've read to edit/add to fstab the UUID of the drives to ensure they are mounting to the correct paths on bootup.
 
In setting up the raid. Do I include all 4 drives plus the raid array as mount points in fstab?
 
Would something like this be correct? (ignore the same UUID #s as I haven't actually set it up yet)
 
```

UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/drive1 ext4 defaults 0 1
 
UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/drive2 ext4 defaults 0 1
 
UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/drive3 ext4 defaults 0 1
 
UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/drive4 ext4 defaults 0 1
 
UUID=3e0c116a-6f2c-4578-9c51-8e6088a8a8fd /mnt/array1 ext4 defaults 0 1
```
 
Nope, just the array.

---

### Post by arrrghhh on 2010-08-10
> **ootuoyetahi said:**
> Nope, just the array.

What he said :D

No need for the individual entries, the OS only sees all of those HDDs as one BIG hdd.  (How big depends on how you slice it - RAID0, RAID1, etc.)

---

### Post by ptmuldoon on 2010-08-10
ok, but one more question than.

If your not assigning the UUID of the 4 drives, than how do ensure the array drives are being mounted to the correct sdb1 - sde1, etc on boot up?

Right now when I boot, the drives appear to be being mounted randomly, with the root appearing on sda one time, and than sdc another.

---

### Post by arrrghhh on 2010-08-10
Well with software RAID have you setup mdadm?

[How-To on software RAID](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by ptmuldoon on 2010-08-10
Yes, I've installed mdadm, and using webmin to create the array.   And I have successfully created the raid array as well for drives sda - sdd

But when I add some other drives, on bootup the drives get reassigned different sdxy values, with drive in the array changing to sde and sdf, thus i'm unsure if that will affect the raid array

---

### Post by arrrghhh on 2010-08-10
> **ptmuldoon said:**
> Yes, I've installed mdadm, and using webmin to create the array.   And I have successfully created the raid array as well for drives sda - sdd

But when I add some other drives, on bootup the drives get reassigned different sdxy values, with drive in the array changing to sde and sdf, thus i'm unsure if that will affect the raid array

I don't think webmin is mentioned anywhere in that how-to.  I use webmin, but I don't think it's a good idea to have it setup software RAID arrays for you.  Monitor/manage them perhaps, but I wouldn't recommend it to setup the array.

Use what works for you, but if it's not working... then perhaps you should re-evaluate what you're using.

---

### Post by ptmuldoon on 2010-08-10
ok, I can try setting it up via terminal.  And I'm still new at it, but the steps seem similar where your assemlying the array based on dev/sda1 /dev/sdb1, etc.

So what happens to the array when on a bootup those drives are assinged an sdxy outside of what you assembled?

---

### Post by arrrghhh on 2010-08-10
> **ptmuldoon said:**
> So what happens to the array when on a bootup those drives are assinged an sdxy outside of what you assembled?

I think you may be over-complicating it.  This shouldn't happen if the device is in an array, it won't appear as a separate hdd to the system (once it's in an array, that is).

---

### Post by Jaken Veina on 2010-08-10
Webmin creates the array just fine, if you know what you're doing. I did so just last night, although, without a knowledge of how to do it manually, you may not quite understand what you're doing.

Properly setting up an array manually involves five basic steps. 

Partition the drives with a single partition each, labeled as a RAID partition. It's been mentioned to me that this is not really necessary, but when I went to build the array in Webmin, it yelled at me for not having a partition 1 on my drives...

Create a new array with mdadm, using the following command, with your own values
```
mdadm --create /dev/md0 --level=5 -raid-devices=4 /dev/sd[b-d]1
```

Add an entry for this array in /etc/mdadm/mdadm.conf. In theory, this shouldn't be necessary either, but not doing so has caused problems for me.
```
ARRAY /dev/md0 devices=/dev/sd[a-d]1
```
OR
```
ARRAY /dev/md0 uuid=b23f3c6d:aec43a9f:fd65db85:369432df
```
If you really do experience sda, sdb, etc. being assigned differently at each boot, use the second version. The UUID is specific to the array, and created randomly by mdadm upon creation. You can get the UUID for the array with
```
mdadm --detail /dev/md0
```
after creating the array. With this second version, mdadm reassembles the array after boot from the superblocks on each drive. The superblock is a block of data put at the end of each drive in the array, which contains all the information on the array given by mdadm --detail, so the array can be assembled automatically.

Once the array has finished building/synchronizing (check /proc/mdstat), use mkfs to build a filesystem on /dev/md0, or whatever your array's name might be.

Finally, for mounting, you are mounting /dev/md0, which is a single device that references the RAID array as a whole. 
```
mount -t ext4 /dev/md0 /mount/RAID
```

---

### Post by ptmuldoon on 2010-08-10
A many thanks to everyone for the help.  I "think" i'm good now.  My issue was consistently the array not being found on reboot.  By adding the array uuid to the mdadm config file seems to have done the trick.

ARRAY /dev/md0 uuid=b23f3c6d:aec43a9f:fd65db85:369432df

---

