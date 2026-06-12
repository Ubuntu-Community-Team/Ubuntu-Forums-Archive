---
title: "Recommended &quot;/&quot; Root Partition Size for Server"
date: 2007-04-18
forum: Server Platforms
---

### Post by thornomad on 2007-04-18
Hello - I want to separate my hard drive into / "root" and /home partitions (so I can have an easier time of reinstalling the base server system without having to remove all my data files).  

Anyhow, my question is: how big of a partition does ubuntu server need at / ?  I will be running a file server: ssh, afp (netatalk), and nfs.  That's pretty much it.  Some cron jobs for backup scripts and the like.  At the most, I may install slimserver for music later.  

Do I need more than 2 GB ?  5 GB ?  I have a 320 GB disk (RAID 1) but don't want to waste any more than is necessary.

Thoughts ?

Thanks,
Damon

---

### Post by jtc on 2007-04-18
If I understand your correctly there will only be two partion, / and /home?
(and then swap, of course)

What might vary most on a server is probably /var, which in your case would be the / partion. Planing on having many users with mailboxes? Expecting any heavy trafic, impacting your log files?

---

### Post by az on 2007-04-18
I think it will be far easier for you to back up your home folder when you need to reinstall than to create a seperate partition for it.  Just leave your home in /

If this will be a production server (you won't be using it as a desktop) you won't even be using the home folder.

---

### Post by Brazen on 2007-04-18
You'll want a minimum of 3 GB for your root partition.

Personally though, I set all mine up like this:

1.7 GB / partition, 1.4 GB /var partition, 102MB /boot partition, and then a big partition mounted whever the main service stores its files (ie, 20GB /var/lib/mysql for the MySQL server or 20 GB /var/www for the Apache web server).

For a file server, I mount my big partition at /export and then put all my shares in there.

---

### Post by thornomad on 2007-04-19
Sorry I took so long to reply ... yea I am just using a file server (no mail clients and no mysql or anything else).  I could just leave it as one large partition and not worry about backup, however, I think I would like to keep them separate if I could.  

But seems like around 5 GB for / would do it.

Thanks.

---

