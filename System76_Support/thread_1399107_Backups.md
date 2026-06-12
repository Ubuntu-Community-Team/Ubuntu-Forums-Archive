---
title: "Backups"
date: 2010-02-05
forum: System76 Support
---

### Post by jdb on 2010-02-05
This forum is loaded with posts about broken computers due to bad updates or upgrades, failed attempts at some configuration change or application install, etc., etc.

If you just do a backup every once in a while when the thing is working good, you can always get back to that point, even without a network connection.


jdb

---

### Post by gamerchick02 on 2010-02-05
I agree.

What do you use for such backups, jdb?

I like Back In Time, which is available in the repos.  I backup to an external drive every week, and it's worked well for me.

Amy

---

### Post by thomasaaron on 2010-02-05
I wrote a little script that backs up all my important files to dropbox and ubuntu one. Not only does that back it up, but I have access to my stuff from anywhere / any computer. I have multimedia junk backed up on an external drive.

---

### Post by samalex on 2010-02-05
When I ran a desktop computer and still on my server I have a script that mounts a physical drive, backs-up data (normally compressed with tar), then unmounts the drive.  I've always been paranoid about commands like 'rm -rf /' which won't affect the backup drive if it's not mounted.

Now that my wife and I use laptops exclusively we have a 1TB external drive I use for backups.  My goal is to setup network backups, but I just haven't gotten around to it yet.

When Ubuntu 10.4 Lucid comes out in April my plan is to backup everything and repartition the drives so /home is separate from / (root).  This has normally been my best practice so I could reinstall the OS without affecting my data.  The stock install from System76 though left everything on one partition.  I know I could use tools to change this, but I've always been squeamish about shrinking partitions with data.

Sam

---

### Post by jdb on 2010-02-05
> **gamerchick02 said:**
> I agree.

What do you use for such backups, jdb?

I like Back In Time, which is available in the repos.  I backup to an external drive every week, and it's worked well for me.

Amy

I just use tar.

The most foolproof way is to boot to a different partition or a CD or a USB.
Then mount the partition to backup & cd to the mount point.
Then tar to an external device or another partition.
For instance if I'm booted to /dev/sda2 and want to backup /dev/sda1 to /dev/sda3 I would do the following as root:
```
mkdir /ubuntu
mount /dev/sda1 /ubuntu
mkdir /backup
mount /dev/sda3 /backup
cd /ubuntu
tar czf /backup/ubuntu_2010_02_05.tgz .
```

You can also use tar on the partition you are booted to but when you restore you have to add a few /dev directories that will be missing.
I keep a dummy /dev handy to copy to a newly restored partition.
```
11:06:46 boota ls -l dev
total 0
crw------- 1 root root 5, 1 2009-04-17 10:15 console
crw-r--r-- 1 root root 1, 3 2009-04-17 10:15 null
crw-r--r-- 1 root root 1, 5 2009-04-17 10:15 zero
```

In this case you also need the --one-file-system option
```
cd /
tar czf /backup/ubuntu_2010_02_05.tgz --one-file-system .
```

I'm sure almost any backup application does as well or better, this is just what I'm used to.
Old habits are hare to break :)

Besides, I've written scripts to do it all for me so all I have to do is type one command.

jdb

---

