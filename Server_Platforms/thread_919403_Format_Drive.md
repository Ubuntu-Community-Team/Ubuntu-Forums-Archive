---
title: "Format Drive?"
date: 2008-09-13
forum: Server Platforms
---

### Post by maxwellcom on 2008-09-13
I've set up an Ubuntu web server for learning purposes (only worked with IIS or other graphical interfaces before).  I've got openSSH and webmin working- so far so good.

The secondary physical drive on the box is still formatted with NTFS from a previous install.  What I would like to do is reformat the drive to a Linux FS (EXT3?) from the command line and locate the root web directory there.

I think I can do this via webmin, but if there's a CLI method to format drives, I'd prefer to get that figured out.

Any suggestions on how to do this or where to look for further info?

Thanks!

---

### Post by gombadi on 2008-09-14
Do you happen to know the device name?

Something like /dev/sdb or /dev/hdb

have a look at dmesg to see if you can find what name it has.
```

dmesg | less

```

**************************************************************

WARNING!!!! The following will destroy any information on the partition.
Use with caution as you could wipe all information on your system

**************************************************************

Note - Do the following as root or insert sudo in front of the following commands.

Lets say the device name is /dev/sdb

I like cfdisk but I am sure others will have different suggestions 

***** WARNING - Did you read the warning above about wiping your disk *****

```

cfdisk /dev/sdb

```


That will let you make a partition for Linux. You can delete the old ntfs partition to free up space.

Once you have a partition you refer to it with /dev/sdb1 or /dev/sdb2 etc depending on how you set up the partitions.

Everyone has there own thoughts on what file system type is best for what type of load but for this lets just use the default ext3 on the first partition on the sdb drive.

***** WARNING - Just to get the message across this will destroy the information on /dev/sdb1 so make sure you have the correct partition *****

```

mke2fs -j /dev/sdb1

```

Now you have a file system on the partition so we need to mount it.

If you have an existing web root like /var/www then move that out of the way.

```

mv /var/www /var/www.orig

```

Now make the mount point and mount the new file system.

```

mkdir /var/www
mount /dev/sdb1 /var/www

```

Check that it all worked. See that the system can find the new disk

```

df -h

```

To get the system to auto mount the new disk at each boot you need to add an entry to the /etc/fstab file. I will leave that for you :-)

---

### Post by maxwellcom on 2008-09-14
Awesome- thanks!

---

