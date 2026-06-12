---
title: "Server Root Partition"
date: 2009-03-08
forum: Server Platforms
---

### Post by MrWES on 2009-03-08
What are the recommended partition sizes for a server? I have a 160GB drive to dice up?

Bill

---

### Post by mrsteveman1 on 2009-03-08
What is it going to be used for? There aren't many good reasons to separate out individual filesystems, even boot. I typically just make one big ext3 partition.

There are people who like to set quotas on specific filesystems or restrict execution of binaries, or make sure one directory doesn't fill up the entire filesystem but there are probably better ways to deal with those problems.

---

### Post by Iowan on 2009-03-08
I have the same questions... Fortunately, I found a guide (of sorts) in the Apress book by Sander van Vugt titled _Pro Ubuntu Server Administration_:> /boot   100 MB (50 MB)
/      20 GB (5 GB)
/var   5 GB (1 GB)
/tmp   1 GB (1 GB)
/srv   (50 GB (1 GB)
/home   50 GB (1 GB)
Where numbers in Parentheses are for VMware test environment - or other limited-space environment.  He also uses different file systems on different partitions, but the entire exercise is for an enterprise level server.

For the sake of discussion, the author also has an Apress book titled _Beginning Ubuntu LTS Server Administration_ that recommends the following partitions/sizes:> /boot   100MB
/var   4GB
/home   200 GB
/      50 GB
swap   1 GB

---

### Post by hyper_ch on 2009-03-09
I did setup two fully encrypted server (each one has 1 TB storage) according to this:

/boot --> 500 MB
swap --> 4GB
/ --> 20 GB
/data --> rest

I also did move the various "data" folders under data so

/home symlinks to /data/home
/var/lib/mysql symlinks to /data/mysql
/var/www symlinks to /data/www

---

### Post by MrWES on 2009-03-09
> **mrsteveman1 said:**
> What is it going to be used for? There aren't many good reasons to separate out individual filesystems, even boot. I typically just make one big ext3 partition.

There are people who like to set quotas on specific filesystems or restrict execution of binaries, or make sure one directory doesn't fill up the entire filesystem but there are probably better ways to deal with those problems.


Basic home file and print server. I'm might go with this;

/  - 10gb
/swap - 512mb (I have 2gb ram memory)
/data - the rest (for data storage on the server -- shared with windows xp machines and Ubuntu)

Bill

---

