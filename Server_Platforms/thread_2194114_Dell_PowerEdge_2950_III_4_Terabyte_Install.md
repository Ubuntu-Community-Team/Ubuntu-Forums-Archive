---
title: "Dell PowerEdge 2950 III 4 Terabyte Install"
date: 2013-12-16
forum: Server Platforms
---

### Post by wallie356 on 2013-12-16
First time poster and user but I've been reading through everything that I could get my hands on. I have a few, what might seem like, basic questions but I've not found answers online that I can draw from with certainty.

I just bought a Dell PowerEdge 2950 Gen III Server with 2x146GB 15K SAS hard drives but I need about 1 terabyte of disk space initially with the possibility of increasing the size to 10 terabytes later on. I'm trying to configure the server with growth in mind. I intend on buying 2X1 terabyte disk or 2x2 terabyte 3.5 7.2k disks. My questions are as follows:

1. It seems that installing Ubuntu server 13.04 on a 2 or 4 TB disk is a bad idea, and I'll be better off installing the OS on a partition. However, where do I find instructions for that? I can create a virtual disk using the bios and perform the instructions in the following link: [http://www.howtoforge.com/perfect-server-ubuntu-13.04-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-13.04-apache2-bind-dovecot-ispconfig-3) 

2. The dell server is certified for Ubuntu 10.04. WIll there be a problem using the latest server OS?

3. Is there any use for the 2x146GB 15K SAS disks that I currently have, like using it for OS install since it can't be part of my RAID 1 or RAID 5 (still trying to decide)? Could it serve as the partition for the OS alone? If so, how do I do that? Will this also mean that future upgrades will be easier by just replacing the 146GB disk with a higher capacity one?

4. Also, should I be using the RAID hardware that came with the server or the software RAID?

When responding, can you please be somewhat detailed or point me to where to get more pertinent information as I'm a completely new linux user and I have no server administration knowledge but **I do follow instructions pretty well**. :lolflag:

Thanks for your help in advance!

---

### Post by tgalati4 on 2013-12-16
What is the use case for this server?  That would determine how you set it up.  I would personally use the hardware RAID, because it is generally faster and has a battery backup to write the cache in case of power failure.  Be sure to put a beefy UPS on this system.  With a lot of drives spinning, you want some power protection.  You can use the small disks for the OS.  Partition them in half or quarters so you can put multiple operating systems on them if you want to play with centos, or bsd, or xen, etc.

Read up on the server documentation which can be found by searching *NewDocs* in the link below.  There are hundreds of pages to go through.

---

### Post by wallie356 on 2013-12-17
Thanks tgalati4! The server will be used as a web server for a java-based business application.

---

### Post by SeijiSensei on 2013-12-17
Install the OS to the 146GB array.  Mount the new drives someplace like /media.

Use the hardware RAID for the SAS drives.  They will appear as a single device, usually /dev/sda.  

If you decide to partition that array manually, I'd suggest

Primary partitions
512 M /boot
2 X physical memory swap

Secondary partition/logical devices
40 GB /
40 GB reserve for future OS installs for testing purposes
remainder /home

You could put /home on the big drives instead.  It depends on how much information you are storing and how it will be shared.

---

### Post by wallie356 on 2013-12-17
Thanks SeijiSensei! 

I currently have the OS installed on the 146GB drive and I used Guided LVM to partition the disk. When asked, I used 19 GB for the guided partitioning but I now get an error when installing more software because the root directory is 100% full.  I'm guessing that I can increase the 19GB but just don't know how.

How do I put the big drive on  /home after I've already finished the OS and other program installs?

I'm also confused how to use the large drives since mySQL is installed on the smaller drive. The database will be the part that consumes the storage space. I'm guessing there'll be a reference somehow between the software resident on the smaller drive and the database that should be on the larger drive in a way similar to saving data on different network drives in a window environment?

As you can see, I have a lot of catching up to do so that I won't ask these seemingly simple questions as I perform the needed mental acrobatics.

---

### Post by SeijiSensei on 2013-12-17
> **wallie356 said:**
> I currently have the OS installed on the 146GB drive and I used Guided LVM to partition the disk. When asked, I used 19 GB for the guided partitioning but I now get an error when installing more software because the root directory is 100% full.  I'm guessing that I can increase the 19GB but just don't know how.

I haven't used LVM in a very long time.  Was there any free space set aside?  You could join some or all of it with the partition that is full.

> How do I put the big drive on  /home after I've already finished the OS and other program installs?

It sounds like you might want to divide the big array into a couple of partitions, one for /home and one for /var/lib/mysql where the database will reside.  You would need to divide each disk identically, then use mdadm to create two separate RAID arrays, let's say /dev/md0 and /dev/md1.  Format each of them as ext4 like this:

```
sudo fsck -t ext4 /dev/md0
sudo fsck -t ext4 /dev/md1
```

How much space you choose to allocate to the two partitions is up to you. 

Now you need to mount these devices temporarily so you can transfer some files.  

```

sudo mkdir /mnt/d0
sudo mkdir /mnt/d1
sudo mount /dev/md0 /mnt/d0
sudo mount /dev/md1 /mnt/d1

```

Now let's transfer the contents of /home to md0 and of /var/lib/mysql to md1.

```

cd /home
sudo rsync -av . /mnt/d0

# just in case
sudo service mysql stop

cd /var/lib/mysql
sudo rsync -av . /mnt/d1

```

Now the two RAID drives will mirror the contents of /home and /var/lib/mysql.  Now we just have to mount them.  First, let's move the old /home out of the way, then mount /dev/md0 as /home.

```

cd /
sudo mv home home.old
sudo mkdir home
sudo chown root:root home
sudo chmod 0755 home
# unmount /dev/md0 from its temporary location
sudo umount /mnt/d0
# mount /dev/md0 as /home
sudo mount /dev/md0 /home

```

and the same for /var/lib/mysql

```

cd /var/llib
sudo mv mysql mysql.old
sudo mkdir mysql
sudo chown mysql:mysql mysql
sudo chmod 0700 mysql
sudo umount /mnt/d1
sudo mount /dev/md1 /var/lib/mysql

```

Finally make sure the contents of your home directory is still available with "ls -a ~".  Then make sure MySQL starts up by running "sudo service mysql start".

Notice that /var/lib/mysql is owned by user and group mysql with no file permissions granted to any other user.

You'll want to [add entries to /etc/fstab]("https://help.ubuntu.com/community/Fstab") to mount these devices automatically at boot.

Another, somewhat less complicated method is to use "symbolic links" or "symlinks."  This time, I'll assume you've created just one large partition on each of the array drives, then created a single MD device called /dev/md0 that you have mounted at /media/storage.

Now you can do this:
```

cd /
sudo rsync -av home /media/storage
cd /var/lib
sudo rsync -av mysql /media/storage

```

Now there will be two directories on the array, /media/storage/home and /media/storage/mysql.  Now let's link to them to replace the existing directories:

```

cd /
sudo mv home home.old
sudo ln -s /media/storage/home
cd /var/lib
sudo mv mysql mysql.old
sudo ln -s /media/storage/mysql

```

If you now type "ls /" you'll see that home is a pointer to /media/storage/home; an "ls /var/lib" should produce similar results. Now references to /home will use /media/storage/home and similarly for /var/lib/mysql.  This might be an easier and more flexible method than mounting fixed partitions.

Once you're sure everything is running correctly, you can delete those home.old and mysql.old directories.

---

### Post by tgalati4 on 2013-12-18
It's important to update the BIOS using the utilities from Dell.  Don't forget to update the RAID BIOS as well.  The hardware RAID has additional features such as hot-swap, passive mirroring, warm-spare, and health status, so you will want to read up on it's features and use them if they help your use case.

Since this is an operational machine, not a development machine, you want reliability.  So clean out the machine well, reseat RAM and all cables.  Check the voltages come from the 2 power supplies.  Locate some spare fans since they will probably fail before other components.  Load some utilities to read fan speed so that you can get a heads up when they go high-RPM--a sign of excessive heat or a fan failure.

It would be good to source some extra disks.  I don't know if they came larger than 146GB, you will have to research that.

---

