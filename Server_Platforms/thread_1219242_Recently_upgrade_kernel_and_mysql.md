---
title: "Recently upgrade kernel and mysql"
date: 2009-07-21
forum: Server Platforms
---

### Post by RickSimnett on 2009-07-21
Hello,
I recently updated my ubuntu 7.04 server and its mysql packages. Since the upgrade the servers performance has dropped dramatically, and I noticed that klogd and dd are running CONSTANTLY in the background. After investigating the kern.log I find it is FULL of these:

Jul 21 14:07:41 mpd1 kernel: [2821954.705571] audit(1248199661.601:4166852242): type=1502 operation="file_permission" requested_mask="w::" denied_mask="w::" name="/mysql/mailpro/cl06042009125043811.MYI" pid=28717 profile="/usr/sbin/mysqld" namespace="default"

and these:

Jul 21 14:13:54 mpd1 kernel: :::: :: :: ::: :::: :: :: ::: :: ::: :: :::: : : :: :::: : :: ::: :::: :: :::::: :::: : : :: : : :: : :: ::::::::::: : : : : : : : ::::: : : : : : : ::::: :: :: :::: : : :: ::: : : : : : : : : : :::: : : :: :::: :: :::: :: : : : : : :: :: :: ::::: : : : : : : :: : :: : : ::::::: : : : : : : : : : : : : : ::::::: ::::: : : : : :: : : : : : : : : : : : ::::::: ::: :: :: :: : : : : : : : : : :::: : :: : : : : : ::: : : : : : : : : :::::: : : : : : : : : : :::::: :: t:: : ::: ::::::::: :: : : :: :: : : :::: :: : : :: : : :::: : : :: :::: :::: :::: :: :::: : : : : :: : : :: :: : : : : : : :::: :: : : :: : : :: : : :: : : :: : :: :: : : : : : ::: : : : : : : : : : : : : : : : : : : : :: : : : : : : : : t: : : : : t: :: : : :: : : t: : : : t:: :: :: : : :: :: : : :: :: :: : : ty: : t: : t: : :: :: :: :: : : : : :: :: : : :: :::: :: :::: :: :: : : : : : : : :: : : :: :: :: :: : : :: :: : : :: ::: : : : : :: :: :: :: :: : : :: : : : : :: : : : : :: : : : : : : : : : : :: : : :: : : :: : : 

and things like this:

Jul 21 14:14:05 mpd1 kernel: 22>[<5"

I assume these errors are causing the performance issues.

Can someone tell me how to correct these issues, the databases belong to mysql:mysql, the /mysql partition is on a hardware raid 6 running XFS. These issues occurred after upgrading the kernel to:

root@mpd1:/var/log# cat /proc/version
Linux version 2.6.24-24-server (buildd@yellow) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Apr 15 15:41:09 UTC 2009


and mysql to:

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 671796
Server version: 5.0.51a-3ubuntu5.4-log (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.


This is a real problem as this is a production server. Worst case I'd like to just rollback the upgrade if thats possible.

Thanks in advance,
Rick

---

### Post by tommcd on 2009-07-21
Ubuntu 7.04 reached end of life a long time ago, and is no longer supported. This is a big problem if your server is connected to the internet.
 You should do clean install of Ubuntu 8.04, which will be supported for a few more years.

---

### Post by RickSimnett on 2009-07-22
I know 7.04 isnt supported anymore. That is why I upgraded the os and mysql. Since the upgrade, I have been having these issues... Do you really think just doing a clean reinstall will fix things?

Thanks,
Rick

---

### Post by RickSimnett on 2009-07-22
Sorry if I havent been clear. I upgraded using apt from 7.04 to 8.04, in the process teh kernel, AND mysql were updated. Thats when the trouble began. I just applied another upgrade to kernel 24-24.56 hopefully this resolves my issue. I will post back after I've made that determination.

Thanks,
Rick

---

### Post by Vegan on 2009-07-22
I am using 2.6.30 with Ubuntu 9.04 and its good for my basic LAMP stack. No problems.

---

### Post by RickSimnett on 2009-07-22
Looks like the dist-upgrade that I applied this time fixed the dd, and klogd issues. Server performance is back to normal.

Thanks!

---

