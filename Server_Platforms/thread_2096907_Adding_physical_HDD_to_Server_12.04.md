---
title: "Adding physical HDD to Server 12.04"
date: 2012-12-21
forum: Server Platforms
---

### Post by Jorel on 2012-12-21
Hi guys,,

I'm studying on how to add additional space to my 12.04 server,, but most of the tips are for VM box,, my plan it to add physical HDD to my mounted /var (if its possible) because i have running HDD with several mounts on it with a simple set-up of dividing the space to different mounts "/",, but i noticed that i may need a bigger space on my /var mount that im planning to build a WEB server and SQL server for database... but im doubtful on taking off a space on my other mount due that i cannot afford for a downtime specially this season,, hope you can help me with this guys..

thanks in advance..

---

### Post by darkod on 2012-12-21
You can add more disks any time. But expanding the /var partition (I assume it's separate partition what you call mount) is not that easy unless you have LVM installation.

Lets assume you don't have LVM. After you install the new disk and create one or more partitions on it (use the size you want for partitions but plan good), you will have to boot the server with either the desktop live cd, or any bootable system/rescue cd. I would prefer the live cd.

You create a temp mounts for both old and new /var, for example inside live mode create:
```
sudo mkdir /mnt/oldvar
sudo mkdir /mnt/newvar
```

After that mount the old and new partitions in the corresponding temp mount points, and copy the content either by rsync, cp or what ever you prefer to use.
If you use cp for example don't forget to use the options -ax to keep ownership and permissions intact. Like:
```
cd /mnt/oldvar
sudo cp -ax * /mnt/newvar/
```

After the copy is finished, open the /etc/fstab of the server OS and replace the old /var partition/UUID with the new one. Reboot and see if it worked.
If you want, on the new disk you can start using LVM even when you didn't in the original install. So you will have some more flexibility with partition sizes in the future. You can even move your current partitions/mounts one by one into this new LVM, and after all of them are moved and working then add the old disk to the LVM too.

---

### Post by CharlesA on 2012-12-21
The alternative to what darkod said is to clone the existing drive that /var is on and expand the partition.

Personally I would use the copy method.

---

### Post by Jorel on 2012-12-22
Hi Darkod & CharlesA,,

thanks for these steps.. i never thought that LVM is the one i needed in the 1st place... coz i got a SAMBA problem with my 1st setup with LVM,, so i thought LVM is not good for my need so go with the simple setup,, but still i got miscalculated things that ill be needing in the future like expanding spaces or moving / copying...

---

### Post by Wim Sturkenboom on 2012-12-23
I don't know what you're current setup exactly is but my first step is always to move the mysql databases out of /var to either a seperate partition or a dedicated directory (and modify the musql configuration accordingly); that way run-a-way logfiles will not interfere with mysql. And websites are moved to a user's home directory (for ease of jailing).

This might be a good opportunity to move the mysql databases to their own disk/partition.

---

### Post by Jorel on 2012-12-27
Hi Wim,,

so you are saying that i can add physical HDD and create another mount there?? and i will leave the /var for WebServer?? coz i will add also a MailServer, and i believe that it will be also included where Mysql server is,, right?? my server has ordinary setup,, no LVM or RAID.. just separated all "/" mounts... 
like:
/ = 20gb
/tmp = 5gb
/boot = 1gb
/home = 5gb and so on...... (i dont know what setup is that)

Thanks..

---

### Post by spynappels on 2012-12-27
You could also create a partition on the new disk and mount it as a sub-directory under /var such as /var/mysql_disk and you can move all dbs there. This would also ensure runaway logs could not interfere with the dbs as mentioned before.

---

### Post by Wim Sturkenboom on 2012-12-27
I'm not familiar with mail servers, so can't help there. I'm not a huge fan of partitioning too much. Problem will always be that one partition is full while there is plenty of space on others.

You can create a mountpoint in /mnt for a harddisk (partition) dedicated to mysql; in the example below I will call it *mysqlserver*.
```

sudo mkdir /mnt/mysqlserver

```

Next you can determine the block id of the partition on the new harddisk (I assume you have partitioned and formatted the partitions) using the _blkid_ command
```

wim@i3-2120:~$ sudo blkid
[sudo] password for wim: 
/dev/sda1: LABEL="System Reserved" UUID="E05A431C5A42EEBA" TYPE="ntfs" 
/dev/sda2: LABEL="Win7" UUID="54C65509C654ECAC" TYPE="ntfs" 
/dev/sda3: UUID="15274769-0777-4a8e-a167-ec7501f8665a" TYPE="swap" 
/dev/sda5: UUID="2e61cbc5-d982-4ada-8af7-cbdea09bb295" TYPE="ext4" 
/dev/sda6: UUID="0a1c5d63-223f-4dc3-9ab8-46f566f5fa7b" TYPE="ext4" 
/dev/sdb1: LABEL="WinXP" UUID="2020F32C20F30814" TYPE="ntfs" 
/dev/sdb5: LABEL="WinXPData" UUID="20982C20982BF2C8" TYPE="ntfs" 
/dev/sdb6: LABEL="SHARED_FAT" UUID="880A-66E0" TYPE="vfat" 
/dev/sdb7: UUID="c7f8f5d5-d24e-43ac-9b7f-2b31804a58ac" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb8: UUID="0173d67a-bb5c-43bf-91c8-1fe03c5ff641" TYPE="swap" 
/dev/sdb9: UUID="ba587de2-a984-4d69-9070-17b17aeed06b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="photos" UUID="6ff7017c-e4d9-49ba-9a1b-b62e45dab820" TYPE="ext3" 

```
The last one is a harddisk with one partition dedicated (on my system) to store photos; for you it can be dedicated to mysql or whatever

To mount add a line to /etc/fstab
```

# photos (/dev/sdc1)
UUID="6ff7017c-e4d9-49ba-9a1b-b62e45dab820" /mnt/photos ext3 defaults 0 2

```
Replace */mnt/photos* by the */mnt/mysqlserver* if you followed the example earlier and use the correct type (ext3 in the example above, you might have ext4 or something else).

You can testdrive by mounting like this
```

sudo mount /mnt/photos

```
If it does not throw errors, the partition will automatically be mounted at the next reboot. Else fix the errors.

Next you can copy the existing databases using _cp -R -p_ (note the -p option to preserve ownership and permissions) to you new partition, modify the mysql configuration and restart the mysql daemon. I prefer copying over moving as you still have your original to fall back on when using copy.

I would also move webpages to /home. But your /home of 5 GB might be too small for that.

---

### Post by Jorel on 2012-12-30
Hi guys,, 

im having trouble with live cd in install type step,, im stuck on it and cannot move on to the next step... i have three options there, "Install along side" , "Erase ubuntu" and "Something else",, next is when im choosing either "Install ubuntu" or "Something else", im getting to the "Add" a new partition step and when i select the whole new HDD to be "logical" and "end location" "EXT4" and i labeled it as "/mnt/sql" and hit Install now,, i got an error saying "No root filesystem is defined"....

thanks in advance guys..

---

### Post by darkod on 2012-12-30
Is this on the new hdd or the old one?

If you are only trying to add the new disk, you don't do that with the installer. The installer process is only to install a whole new OS, not to add disks.

Also, when creating a single partition taking the whole disk there is no point the partition to be logical. Make it primary, it will be the only one anyway. You use logical partitions when you need more than 4 partitions on the disk.

Are you trying to only add the new disk or to reinstall the whole OS from start?

---

### Post by Jorel on 2012-12-30
Hi Darkod,

Actually im trying to add a new HDD now to merge with my old one,, eventually im lost and i tried the steps that you instructed...

---

### Post by darkod on 2012-12-30
I never said to use the installer. I said to use the live cd and boot into live mode (Try Ubuntu) option.

Then first create a new primary partition on the new disk. You can use Gparted from the live cd to do that. Open Gparted, select the correct disk in the drop down field top right, select to create new primary ext4 partition on the whole disk, and then click the green button in the toolbar to execute the changes.

After that you should have one ext4 partition on the new disk, it will probably be called /dev/sdb1. Note down the exact device name of that partition.

After that create new temporary mount point:
sudo mkdir /mnt/newvar

Mount the system root partition to /mnt:
sudo mount /dev/sdaX /mnt
sudo mount /dev/sdb1 /mnt/newvar

Note that if you don't understand the commands ask first, don't simply retype them. I am working under the assumption you can recognize which partition is which and you understand what is going on, otherwise I can't know your system setup exactly.

If you don't understand this, before you start anything boot your OS and post the output of:
```
df -h
sudo blkid
```

If you do understand it, after mounting the correct partitions above, go to the var folder and start copying:
cd /mnt/var
sudo cp -ax * /mnt/newvar/

After that is done, rename the old var folder, create new /var folder, and the correct fstab entry for it:
```
sudo mv /var /old_var
sudo mkdir /var
```

The entry in fstab should be like:
```
UUID=<string>   /var   ext4   defaults   0   2
```

You can find the UUID string of the new partition you created with the sudo blkid command mentioned earlier.

Reboot and it should work.

The above approach is without using LVM. I think this is a good opportunity to introduce LVM in your system but you will have to investigate little bit how it works and what to do. The choice is yours whether to use it or not.

PS EDIT: You have to understand that with the above process the disks will not be merged. You will only have new bigger /var folder and the size of it will be the same as the size of the new partition/disk. The only way to try and merge the disks as far as I know is LVM. The above procedure is NOT LVM.

---

### Post by Jorel on 2012-12-30
Hi darkod,

im in this step now,, and i created a 
/dev/sda1

but im not really sure about the "/dev/sdaX" ,

> **darkod said:**
> 
Mount the system root partition to /mnt:
sudo mount /dev/sdaX /mnt
sudo mount /dev/sdb1 /mnt/newvar


df- h :
Filesystem    Size  Used  Avail Use%  Mounted on
/cow          2.0G   49M   1.9G   3%  /
udev          2.0G   8.0K  2.0G   1%  /dev
tmpfs         788M   820K  788M   1%  /run
/dev/sr0      702M   702M     0 100%  /cdrom
/dev/loop0    673M   673M     0 100%  /rofs
tmpfs         2.0G   20K   2.0G   1%  /tmp
none          5.0M   4.0K  5.0G   1%  /run/lock
none          2.0G   76K   2.0G   1%  /run/shm

sudo blkid :
/dev/loop0: type="squashfs"
/dev/sdb1: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb2: UUID="bunch of numbers" TYPE="ext4" 
/dev/sdb3: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb5: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb6: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb7: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb8: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb9: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb10: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb11: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb12: UUID="bunch of numbers" TYPE="ext4"
/dev/sr0: LABEL="ubuntu 12.04 LTS i386" TYPE="iso9660"
/dev/sda1: UUID="bunch of numbers" TYPE="ext4"
(sorry i just typed it in)

---

### Post by darkod on 2012-12-30
The X should be replaced with the correct partition number. Actually I just remembered that you have separate /var partition.

You needed to run df -h from the booted OS, not from live mode. That will show which partition is mounted where. So we can give you exact commands to run.

Boot the installed system and post the df -h results.

---

### Post by Jorel on 2012-12-30
so you mean that /dev/sdaX is where my old "/var" is?

Filesystem Size Used Avail Use% Mounted on
dev/sda1   19G  683M 18G     4% /
udev       1.9G 4.0K 1.9G    1% /dev
tmpfs      773M 508K 773M    1% /run
none       5.0M    0 5.0M    1% /run/lock
none       1.9G    0 1.9G    1% /run/shm
dev/sda8   4.7G 198M 4.3G    5% /tmp
dev/sda2   952M  54M 851M    6% /boot
dev/sda5   4.7G 199M 4.3G    5% /home
dev/sda11  4.7G 198M 4.3G    5% /srv
dev/sda12  1.8T 356G 1.4T   21% /office
dev/sda10  4.7G 198M 4.3G    5% /opt
dev/sda6   4.7G 907M 3.6G   21% /usr
dev/sda7   4.7G 496M 4.0G   11% /var
dev/sda9   4.7G 198M 4.3G    5% /usr/local

sudo blkid :
/dev/sdb1: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb2: UUID="bunch of numbers" TYPE="ext4" 
/dev/sdb3: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb5: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb6: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb7: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb8: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb9: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb10: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb11: UUID="bunch of numbers" TYPE="ext4"
/dev/sdb12: UUID="bunch of numbers" TYPE="ext4"
(sorry i just typed it in again)

and i removed the new HDD 1st coz i think im not yet done with the process and it is not booting in.

---

### Post by darkod on 2012-12-30
But you didn't even start, you just created a partition on the new hdd. The new hdd should not interfere with the boot process unless there is some old bootloader on it, and you set the computer to boot from it.

It is important to have both disks connected since disconnecting one can make the letter change. You see right now /dev/sda is the older disk, since there is only one in the machine. But earlier you had the new disk as /dev/sda. The letter should not move around.

Connect the older disk to a sata port with lower number, like SATA0 on your board. Connect the new disk to a sata port with higher number. That way when the bios detects them, the older disk is always sda and the new is sdb.

Also I can notice that /dev/sda7 is your /var partition and it is only 11% full. You still have space to use before adding a new disk but you can do it now if you want to.

I think you made too many separate partitions. As you can see in the df -h results most of them are like 5% full, and they keep a lot of free space that other partitions can't use.

I suggest you use LVM on the new disk. Later you can add the partitions on the old disk to the LVM too, one by one. That would be real merging of the space.

If you still want to continue without LVM, connect the new disk again in a sata port higher than the old disk, boot the computer (it should boot OK), and post the result of df -h again to make sure which disk is which.

---

### Post by Jorel on 2012-12-30
yeah i realized it also that i have some unused spaces... because in my calculations, that my company is having with their database is around 15GB per year and we have 3 department that will be serving the server, so i assume that i'll be needing 50gb for it, and i'll be starting to build (i hope to build ;) ) a mail server and i dont know yet how big ill be needing for that and webserver that will be hosting a dynamic and static sites... at first i wanted it to be as a whole but i experienced some problems with my SAMBA, so i decided to go with this kind of setup not knowing i will be having this kind of problem in the future,, but im expecting some weird problems, this is my 1st working server anyway..

further on, its ok now, i just misplaced the SATA slots so it didnt worked earlier...

Filesystem Size Used Avail Use% Mounted on
dev/sda1 19G 683M 18G 4% /
udev 1.9G 8.0K 1.9G 1% /dev
tmpfs 773M 656K 773M 1% /run
none 5.0M 0 5.0M 1% /run/lock
none 1.9G 0 1.9G 1% /run/shm
dev/sda8 4.7G 198M 4.3G 5% /tmp
dev/sda2 952M 54M 851M 6% /boot
dev/sda5 4.7G 199M 4.3G 5% /home
dev/sda11 4.7G 198M 4.3G 5% /srv
dev/sda12 1.8T 356G 1.4T 21% /office
dev/sda10 4.7G 198M 4.3G 5% /opt
dev/sda6 4.7G 907M 3.6G 21% /usr
dev/sda7 4.7G 496M 4.0G 11% /var
dev/sda9 4.7G 198M 4.3G 5% /usr/local

sudo blkid :
/dev/sda1: UUID="numbers" TYPE="ext4"
/dev/sda2: UUID="numbers" TYPE="ext4"
/dev/sda3: UUID="numbers" TYPE="swap"
/dev/sda5: UUID="numbers" TYPE="ext4"
/dev/sda6: UUID="numbers" TYPE="ext4"
/dev/sda7: UUID="numbers" TYPE="ext4"
/dev/sda8: UUID="numbers" TYPE="ext4"
/dev/sda9: UUID="numbers" TYPE="ext4"
/dev/sda10: UUID="numbers" TYPE="ext4"
/dev/sda11: UUID="numbers" TYPE="ext4"
/dev/sda12: UUID="numbers" TYPE="ext4"
/dev/sdb1: UUID="numbers" TYPE="ext4"


(and probably i will keep in mind about the LVM after i finished most of my projects... so that i can focus again in my server.)

---

### Post by darkod on 2012-12-30
If you are ready to consider LVM, this is the perfect moment. If you apply this change without LVM on the new disk at least, it will be much more difficult later (not impossible).

Anyway, if you wish to proceed without LVM, boot into live mode now, open terminal and start making the temporary mountpoints and copying things. You current /var partition is /dev/sda7 and you wish the new one to be /dev/sdb1.
```
sudo mkdir /mnt/oldvar
sudo mkdir /mnt/newvar
sudo mount /dev/sda7 /mnt/oldvar
sudo mount /dev/sdb1 /mnt/newvar
cd /mnt/oldvar
sudo cp -ax * /mnt/newvar/
```

When that finishes, all should be copied to the new location keeping the ownership and permissions.

After that unmount the temp mounts and mount the root partition so you can edit the fstab:
```
sudo umount /mnt/oldvar
sudo umount /mnt/newvar
sudo mount /dev/sda1 /mnt
sudo nano /mnt/etc/fstab
```

In the fstab opened with the nano editor, replace the UUID (the long string) of /dev/sda7 in the line specifying the /var mount, with the UUID of /dev/sdb1 (that is your new /var partition). Make sure the string is correct, all letters and numbers. After you are done editing, save the file with Ctrl+O, Enter. Then close nano with Ctrl+X.

Unmount the root temp mount:
```
sudo umount /mnt
```

Reboot without the cd and you should have your new bigger /var. You can check again with df -h and it should say that sdb1 is mounted as /var instead of sda7 and you should have more free space.

---

### Post by Jorel on 2012-12-31
Hi darkod,

im just curious, is this really /dev/sda1 or /dev/sdb1?

> **darkod said:**
> 

sudo mount /dev/sda1 /mnt



Sorry for my doubt,, i mount sda1 and tried the steps and all are working ok as of now,, (hope i followed it correctly)... it is now the new HDD and has bigger space, but i noticed that it consumed a 7.3G,, i dont know why it got that big (hope i can still hear why it got that big so i know what to expect in the near future hehehe :D ), but among things i want to thank you for your help,, your help is really appreciated.... 

Happy New Year Guys.... !!!

---

### Post by darkod on 2012-12-31
Yeah, in the second block of commands it was /dev/sda1 on purpose, not a typo. This is because sda1 is your root partition and you needed to mount root to edit the /etc/fstab.

Are you saying that the new /var now has 7.3GB used space? It was only about 500MB on the old disk, it should be similar after you copied it. Unless you already had something copied on /dev/sdb1.

Can you post the df -h again from the installed OS, not live mode?

---

### Post by Jorel on 2012-12-31
Hi Darkod,

df -h :
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G  638M   18G   4% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           773M  888K  772M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
/dev/sda8       4.7G  198M  4.3G   5% /tmp
/dev/sda2       952M   54M  851M   6% /boot
/dev/sdb1       466G  7.3G  435G   2% /var
/dev/sda10      4.7G  198M  4.3G   5% /opt
/dev/sda11      4.7G  198M  4.3G   5% /srv
/dev/sda5       4.7G  199M  4.3G   5% /home
/dev/sda6       4.7G  907M  3.6G  21% /usr
/dev/sda12      1.8T  356G  1.4T  21% /office
/dev/sda9       4.7G  198M  4.3G   5% /usr/local

i just noticed before, the time that after i created the table in the live CD, there's a tiny colored part, so i assumed that there's something on it already..

---

