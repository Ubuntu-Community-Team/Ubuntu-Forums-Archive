---
title: "install secong hard drive on 8.04 server"
date: 2008-12-18
forum: Server Platforms
---

### Post by john.gregory on 2008-12-18
I just installed ebox (based on ubuntu 8.04 server). I am using it as a file server and want to add another hard drive to the server. I have attached the second drive. It has old partitions on it that I want to delete and reformat. How do I do this from the command line? The drive is recognized when I run sudo fdisk -l. It has 4 separate linux partitions on it now.

Any help is greatly appreciated. I'm not a complete newbie; but feel free to treat me like one.

john

---

### Post by RealPSL on 2008-12-19
First make sure that you backup anything on the new drive that you want to keep because we are going to destroy the data.

```
sudo fdisk /dev/sdb
```

This assumes that the second drive you want to remove the partitions from is /dev/sdb.

Use "p" to print the partitions on the drive from the fdisk prompt.

Use "d" to delete any existing partition that is on the drive.

Once all the partitions have been deleted use "n" to create a new partition of type primary and it should be the first partition.

Save your changes using "w". I have not done this in a while and you make have to reboot for the kernel to reload the partition table at least that is how it used to work.

The next step is to create a new file system on the drive. Assuming the drive as sdb and it is the first partition run the command ```
sudo mke2fs -j /dev/sdb1
```

Use ```
blkid
``` to list the UUID of each drive. Create the directory you want to mount the drive to e.g. ```
sudo mkdir /big_space
```

Add the following line to /etc/fstab using ```
gksu gedit /etc/fstab
```

"UUID=insert-your-uuid-from-blkid-here /big_space ext3    defaults        0       2"

Note that the above is one line. Now mount the file system with ```
sudo mount /big_space
```

---

### Post by john.gregory on 2008-12-19
Thanks RealPSL. Problem solved.

---

