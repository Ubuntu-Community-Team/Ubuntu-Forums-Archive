---
title: "Changing space available to another partition"
date: 2015-10-14
forum: Server Platforms
---

### Post by patrickdappollonio on 2015-10-14
Hello,

N00b here. I have this setup currently in an Ubuntu server it was given to me as payment for services. I setup a website there with a fairly good amount of visitors but sadly, I'm running out of space. This is the space distribution:


```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        21G  2.5G   17G  13% /
devtmpfs        8.5G  4.1k  8.5G   1% /dev
none            4.1k     0  4.1k   0% /sys/fs/cgroup
none            1.7G  746k  1.7G   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            8.5G     0  8.5G   0% /run/shm
none            105M     0  105M   0% /run/user
/dev/sda3       2.0T   71M  1.9T   1% /home
```

Now, I'm running a web project in /srv/php, with Nginx and other stuff there. So the root is filling up with data (my project weights about 100 mb but those are thousands of files). I honestly have no idea on how to repartition this without loosing any data and move that space from `/home` to `/`.

Any help?

---

### Post by volkswagner on 2015-10-14
If you site is only 100MB and you have 17Gig available, I would not consider that running out of space.

With that said, I would not recommend messing with partitions. Since you have a large space available in /home, you can move websites
and other files to /home/yourusername.

This would involve simply editing your site info in Nginx and point to where you copied files to in /home/user.

---

### Post by TheFu on 2015-10-15
volkswagner  is  correct. Nothing to worry about immediately. You have time - perhaps 10 years.

However, you could shrink /home. There are a few ways to do that. 
a) backup, delete, create smaller, create new, mount
b) backup, shrink, create new, mount

The easiest is to backup everything on /home, delete the partition and recreate it with the new size.  This is a basic task. Use a live-boot with Ubuntu to do it.

It may be possible to reduce the size of /home using file system tools, but that depends on the file system being used and whether it supports that mode.  This is dangerous. Do not attempt it without having a backup first.

After /home is smaller, you can make a new partition for /var, mount the new storage somewhere temporarily, copy everything in /var over, after that completes, remove everything under /var/*, mount the new storage to /var - don't forget to update the fstab so the new mount will happen at every reboot.

It is harder to write all of this than to actually do it.

If you don't know how to accomplish any specific task, 
a) the **ubuntu server guide** has lots of info.
b) ask here, but please show what you've tried first - the full command and output. 

I would not put websites under any user $HOME. That raises permissions and possibly some security considerations that would need to be addressed. Websites belong in /srv, /opt, or /var for a reason - based on the linux file system hierarchy standard.

BTW, I have a webapp server with only 7.1G total storage. It has been running since 2002 with only a few app  changes over that time. Clearly, the web server has been moved over that time, but the storage required hasn't changed much. Storage-sucking apps and files generally don't happen much on Linux when there is not a GUI involved.
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       7.1G  3.8G  3.0G  57% /
```
See?
Your system is using even less today.

---

### Post by patrickdappollonio on 2015-10-15
Thank you guys, I actually did worry because I hit that problem already. Not even tab autocompletion worked because it said I was running out of space. What I did was I deleted several Nginx log files to clean up space. I will probably do what Volkswagner suggest and move everything to `/home` but I would strongly prefer to reduce the space for `/home` and gave it to something else like TheFu says, like /opt or similar.

Now, regarding the server, it's running at Hetzner, so probably a live CD won't work. The server is also using a Redis database with millions of records (that was probably important to mention earlier, silly me!) so I'm thinking about moving it out of `/` too. The website itself is just a cache for a third party service, so technically, data is not important (the code will get every record eventually once again) and all the million of Redis records are expired in 24 hours (Redis is even set up to not save records to a file, a la memcache). The source code is published with a git hook so the source code is currently backed up and no "critical" data will be lost if the server burns to hell in any scenario. So I just want to reduce the odds of being offline for too long.

I will do what Volkswagner told me and move everything to /home but eventually I would definitely like to get rid of that and gave all to / or to another partition to store stuff. Any final thoughts will be very appreciated! :)

---

### Post by TheFu on 2015-10-15
Don't know what Hetzner is. If it is linux, then almost any live boot can be used ...  until systemd becomes more used and forces everyone to binary logging. Linux is Linux. If it is some sort of distro thingy - they may screw with some settings, but the file system is the file system. If it is a live-boot + configure thing that doesn't ask questions, may not be much you can do.

When building high volume servers, there are many steps to laying out an efficient storage arrangement. Most of those can be  handled by using LVM so that future changes are minor impacts. There are performance and backup reasons to use LVM too. The easiest way to deal with this today is by using SSDs in a RAID10 config.

LVs
* /
* /boot
* /var
* /home
and don't allocate more than you require to each. With LVM, it is trivial to add more space later even to an online file system.  Probably more than you want today, since using LVM is major surgery to an existing system.  I only use LVM on physical servers, not virtual machines.

Log files should never cause a full file system. Fix the log file settings to prevent that. You can limit the size, decrease the rotation period, reduce the number of log files retained. Lots of options there.

---

### Post by volkswagner on 2015-10-15
I have used theses steps to manipulate filesystems and mount points.

tar is your friend, and you can switch user to root with su or allow root login temporarily.
Since root user does not rely on /home you can do this on a live system. As TheFu mentions.... BACKUP if you care about your current state.

These instructions are adapted from [this post]("http://www.webdt.org/forum/viewtopic.php?f=3&t=106&p=479&hilit=%2Fusr#p479") (for creating symbolic links to external storage device).

Login as root or switch to root, create temporary /home directory for mounting later, change to /home dir:
```
sudo su
mkdir /homeTmp
cd /home

```
Use tar to create exact duplicate of all folders inside /home, the change to temp home and untar
```
tar cf - ./* | (cd /homeTmp && tar xfp - )
```
Change to /, unmount /home, rename /home to /home.old and rename /homeTmp to /home
```
cd /
umount /home
mv /home /home.old
mv /homeTmp /home
```
You'll then want to backup and edit /etc/fstab to comment out your mount point for /home before you reboot to test functionality.
```
cp /etc/fstab /etc/fstab.orig
nano /etc/fstab
```

You can also temporarily mount /dev/sda to /home.old and compare directories if you like.

This should allow you to delete partition /dev/sda and repartition from it's free space.
You can then use tar magic above to create and move additional mount points for existing directories like /var, /usr, /home, etc. etc.

As already mentioned using a live CD may be safer, but if the server is located remotely without monitor and keyboard, using the above
method should work just fine.

---

### Post by TheFu on 2015-10-16
**rsync** can be used instead of tar with a much simpler command. Besides that slight difference, I've done similar tasks many times.
The general form for an rsync command to create a mirror is:```

# rsync -avz  source target
```

---

