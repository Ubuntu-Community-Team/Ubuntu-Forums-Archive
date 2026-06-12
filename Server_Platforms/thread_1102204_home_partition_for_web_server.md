---
title: "/home partition for web server"
date: 2009-03-21
forum: Server Platforms
---

### Post by rowan-jetboy on 2009-03-21
I'm trying my hand at setting up a Dell Poweredge 1850 as a production LAMP web server with Ubuntu Server. The specs are two 73GB drives in RAID 1 and 8GB RAM.

This will host less than a dozen sites, with a single FTP user for each. Apache and MySQL data will be on a /srv partition, and I also intend to run Postfix, although this isn't an app I've used before. The server won't be used for anything else beyond this, so I wouldn't expect to accumulate user data in the /home directory.

Provisional partitioning scheme is:

sda1	/	ext3	4GB

sda6	/srv	ext3	max	nosuid,nodev,noexec
sda7	/tmp	ext3	4GB	nosuid,nodev,noexec,noatime
sda8	/var	ext3	4GB	nosuid,nodev,noexec
sda5	/swap	swap	1GB

My main question is: In this configuration, what are the security implications of not having a separate /home partition, and if I do have to have one, should I lock it down with anything more than nosuid and nodev?

Secondarily, can I get away with a / partition of only 4GB?

Any general comments about my proposed partitioning scheme also welcome.

---

### Post by cariboo on 2009-03-21
You don't need a seperate /home partition, and I would sugest making /var the largest partition as that is where /var/www is located.

Jim

---

### Post by rowan-jetboy on 2009-03-21
Thanks for the help.

Going to sit /www on /srv as per the Filesystem Hierarchy Standard, but the idea's the same.

I figured that having /var set aside for spools and log files would mean that if I do manage to fill up /var at least Apache and MySQL wouldn't run out of disk space too.

---

### Post by hyper_ch on 2009-03-22
on my servers I created a /data partition and on there I have:

/etc --> /data/etc
/home --> /data/home
/var/www --> /data/www
/var/lib/mysql --> /data/mysql

That way I have all the configs and data on just one partition.

---

### Post by rowan-jetboy on 2009-03-25
Interesting. If you set /tmp and /var to be noexec on install, Ubuntu ignores the flag on /tmp and dpkg errors due to the flag on /var. Perhaps The Official Ubuntu Book should mention this when they recommend these setting for securing Ubuntu Server?

After doing a little research, it looks like dpkg (and apt-get) need to execute from both of these partitions on an Ubuntu installation. Presumably this isn't just restricted to installation, but potentially any use of apt-get?

I went down the route of setting the noexec flags in fstab, and creating /etc/apt/apt.conf with the following in:

DPkg::Pre-Invoke {"mount -o remount,exec /tmp";"mount -o remount,exec /var";};
DPkg::Post-Invoke {"mount -o remount /tmp";"mount -o remount /var";};

which will hopefully get around this issue.

---

