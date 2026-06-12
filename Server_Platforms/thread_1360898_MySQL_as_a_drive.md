---
title: "MySQL as a drive"
date: 2009-12-21
forum: Server Platforms
---

### Post by StrangeWill on 2009-12-21
Simple enough, mount a drive on /var/lib/mysql, copy files to it... correct?

Err, I get a database:
#mysql50#lost+found 	

Well MySQL is obviously confused, I know that is my lost+found directory, should I just ignore it, or is there something I should do about this weird side affect?

---

### Post by BkkBonanza on 2009-12-21
> **StrangeWill said:**
> 

Err, I get a database:
#mysql50#lost+found 	


Just what is this supposed to mean? You see this as output in the error log or what?

You should be able to mount to /var/lib/mysql no problem. But you did take stop mysql server first right? You can't copy the files over if you mount on top of the location where they exist and if mysql isn't stopped it will still have open handles to the old files.

1. stop mysql
2. rename current dir, mv /var/lib/mysql /var/lib/old-mysql
3. make a new mount point, mkdir /var/lib/mysql
4. mount your drive at /var/lib/mysql
5. copy files, cp -r /var/lib/old-mysql/* /var/lib/mysql
6. start mysql
7. when sure it works you can remove the old-mysql dir

---

### Post by Vegan on 2009-12-22
What king of performance problem would there be for a 1Gb network be for a mount coming from another server in the LAN.

Eventually I will be using 10Gb but not this year.

I was also thinking about the advantage/disadvantage(s) of a dedicated MySQL server for a blade based block of machines.

An 8U machine has 50 drive bays, so databases could be potentially be huge.

---

### Post by BkkBonanza on 2009-12-22
A network mount would have it's performance limited by whatever LAN arangement you have. Usually this would be significantly reduced compared to a local drive. I'm not sure but it may be worse if caching is not implemented for the remote mount. Database use is significantly boosted by normal drive cache features of Linux. Of course, as the database grows beyond RAM limits this becomes less of an advantage.

Usually if you want performance then you would have fast local drives on a dedicated SQL server machine.

---

### Post by StrangeWill on 2009-12-28
> **BkkBonaza said:**
> Just what is this supposed to mean? You see this as output in the error log or what?

You should be able to mount to /var/lib/mysql no problem. But you did take stop mysql server first right? You can't copy the files over if you mount on top of the location where they exist and if mysql isn't stopped it will still have open handles to the old files.

1. stop mysql
2. rename current dir, mv /var/lib/mysql /var/lib/old-mysql
3. make a new mount point, mkdir /var/lib/mysql
4. mount your drive at /var/lib/mysql
5. copy files, cp -r /var/lib/old-mysql/* /var/lib/mysql
6. start mysql
7. when sure it works you can remove the old-mysql dir
I get a database with that name in my database list. It's the lost files dir for the ext3 drive. I can't (err... shouldn't) move or delete it, it's part of file system recovery.

The other databases work fine, it's just this lost files directory that for some reason looks like a MySQL database in phpMyAdmin that is weird. It isn't system breaking.

I *can* just ignore it, I was just wondering if this could lead to any problems with the system...

---

### Post by BkkBonanza on 2009-12-28
Ok. I understand what you're saying now.

You can look in the lost+found directory. If there are files in there you may want to check the contents as it would be lost file fragments from fsck checks. Usually there is nothing in there. You can remove the directory because if a fsck finds lost data in future it will create it again. Removing it won't cause any issues. If there is files in there you can just move them elsewhere or if you're sure that you don't need to recover the data from them you can delete them. 

Another perhaps cleaner solution would be to NOT mount the root of that drive for mysql. Instead move the databases to a /data directory on the drive. Then use a symlink to bring the files into the correct mysql location.

eg.

mount /dev/sdX /mnt

ln -s /mnt/data /var/lib/mysql

(you would have to remove the /var/lib/mysql directory to create the symlink)
(you can mount wherever you like if not /mnt)

---

