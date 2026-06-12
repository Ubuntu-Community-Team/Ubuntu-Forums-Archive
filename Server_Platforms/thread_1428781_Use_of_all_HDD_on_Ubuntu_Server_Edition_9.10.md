---
title: "Use of all HDD on Ubuntu Server Edition 9.10"
date: 2010-03-13
forum: Server Platforms
---

### Post by ipng on 2010-03-13
Hello :)

On my home-server i have got three hard drives, but i only use one of them.
I was wondering if anyone knew a guide, how to get use of the two other HDD?

Thanks in advance :)

---

### Post by graphius on 2010-03-13
you can set up a link in your fstab.(do a search on fstab to find a bunch of howto's) once you create a mountpoint, you will be able to access your other drives.

---

### Post by ipng on 2010-03-13
Thanks! 
I'm gonna google it right away! :D

---

### Post by The Real Dave on 2010-03-14
If you like, I'll write a quick guide to mounting another drive on Ubuntu Server :)

First, you need to find what your drive names are. Run

```
sudo fdisk -l
```

and take a note of the drive names, and partition numbers of the drive you want to mount. This would be something like /dev/sdb1 or /dev/sdc3. If there are no partitions, you'll need to create some with fdisk.

Now, create a mountpoint for your drive. You can make it whatever you want, but a common place to mount things is in the /mnt dir. Create a folder there with

```
sudo mkdir mount_name
```

Of course, you can have "mount_name" as whatever you want.

Finally, after that, we can try to mount the drive to the folder. If the partition you want to access is called /dev/sdb1 the command would be this

```
sudo mount -t auto -v /dev/sdb1 /mnt/mount_name
```

The -t option is the filesystem type. Since we don't know it, leave it to auto and let the mount command figure it out. The -v option is for verbosity, and with luck, should show something like this.

```
mount: you didn't specify a filesystem type for /dev/sdb1
       I will try type vfat
/dev/sdb1 on /mnt/mount_name type vfat (rw)

```

Now we know that the filesystem is vfat. It could also be ntfs-3g, ext3, ext4 or a few others. 

Before we proceed, unmount the drive we just mounted with 

```
sudo umount /dev/sdb1
```

You don't want to manually mount the drive everytime you boot up the server no? In that case, let's set it up to mount automatically on boot. 

You need to edit you fstab file. The options here vary quite a bit, so [this guide]("https://help.ubuntu.com/community/Fstab") will be very useful. The following is just an example.

Edit the file using Nano

```
sudo nano /etc/fstab
```

As a general rule of thumb, assuming that /dev/sdb1 was an NTFS partition, you would add a line like this to the end of the file. The line with the # in front is commented out, and is just there for your own reference.

```
#Write whatever comment you want
/dev/sdb1 /mnt/mount_name ntfs-3g defaults,uid=1000,umask=0 0 0
```

UID is your user id. If your the first user created, this will most likely be 1000. 

For a Linux partition, the line would be a bit simpler.

```
#Write whatever comment you want
dev/sdb1 /mnt/mount_name ext4 defaults 0 0
```

Finally exit and save the file with Ctrl+X, press Shift+Y and then Enter.

Test that your fstab line is correct by trying to mount it.

```
sudo mount /dev/sdb1 -v
```

It should tell you that it has been successfully mounted.

That's it. You may have to change the permissions of the mounted drive to allow you to read/write to it, but that's as simple as running

```
sudo chmod -Rv 777 /mnt/mount_name
```

followed by

```
sudo chown -R you_user_name /mnt/mount_name
```

That will change the permissions to 777 (Full access to everyone) and list every file as being owned by you. 

If you want help creating new partitions with fdisk, or even creating a software RAID with your two harddrives, I can give you a hand with that :)

---

### Post by ipng on 2010-03-14
Thank you very much!

That guide was very helpful indeed ;)

---

### Post by The Real Dave on 2010-03-14
> **ipng said:**
> Thank you very much!

That guide was very helpful indeed ;)

I'm glad it was useful :) I remember how impossible stuff like that seemed when I first started off lol :)

---

### Post by ipng on 2010-03-14
Yeah, sometimes things seems very impossible, for an Ubuntu newbie like me ;)
But i was wondering... Can you help me repartition one of my linux partition? I really want to delete all the files on one of my HDD, but i really don't know how! I've tried to Google it, but the only thing i could find was an idea of using the Ubuntu Live CD (For the desktop edition), and partition the following HDD you want to delete. Is this possible? :) 
Thanks for your kindness :)
p.s. what is a software RAID? - my guess is a way, to make two HDD into one virtual, is that right? - Best regards :)

---

### Post by DuronForever on 2010-03-14
Warning: The stuff I'm about to suggest may cause data loss if applied incorrectly.

Use the command "mount" to find out which partitions are already being used. Use "sudo fdisk -l" to find out which partitions you have. From that, figure out which partitions you want to delete. If you can't figure it out, post the output of those commands and someone can probably help.

Okay, so you've done this, and as an example I'm going to assume that you want to delete /dev/sdb3, /dev/sdb2, and the entire /dev/sdc. You will need to edit this as appropriate!

```
sudo fdisk /dev/sdb
``` 
The commands most useful are: p will print the current table, d will prompt you for a partition to delete, w will write the altered table and exit. So: enter d, enter, at the prompt say 2. Repeat for 3. You now have a bunch of empty space. Enter n for new. It will ask for the number of the partition to make, try 2. It will suggest start and end values based around the empty space, you can use those or subdivide further. After you create the new partition, use the command t and enter 83 as the type when prompted, to identify these partitions as being linux.

When done, enter p first. Check that the partitions you wanted to retain are still there, with the same start and end cylinders. If all's well, do w. Do the same for /dev/sdc, only deleting all the existing partitions and making a new sdc1 that comprises the whole disk.

Once you're done, you need to format the new disks:

```
sudo mkfs.ext3 /dev/sdb2
```
Repeat for the others. Now you can mount them as per earlier post.

An easier way to partitioning is to boot the Ubuntu LiveCD and use the graphically-based tools available there.

---

### Post by The Real Dave on 2010-03-15
The above post is perfect for creating a new partition. 

You can also change 

```
sudo mkfs.ext3 /dev/sdb2
```

to 

```
sudo mkfs.ext4 /dev/sdb2
```

to format the partiton as ext4. 

Software RAID in Ubuntu is done with a program called Mdadm. With Mdadm, you can create various RAIDs. The [Wikipedia ]("http://en.wikipedia.org/wiki/RAID")page on RAIDs is a good way to explain what they can do.

Here's a [nice guide]("https://help.ubuntu.com/community/Installation/SoftwareRAID") on setting up a software RAID in Ubuntu

---

### Post by ipng on 2010-03-16
"The Real Dave" - thanks for spendig time on my problem ;) - your guides and links was me very helpful! - THANKS!

---

