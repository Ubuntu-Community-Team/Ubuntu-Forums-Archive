---
title: "Mysql in Ubuntu Server 12.04 innodb disabled?"
date: 2012-06-17
forum: Server Platforms
---

### Post by echo15 on 2012-06-17
Hi!
I hope someone could help me.  I have a home server running Ubuntu Server 12.04 and it's been running okay for a couple of days.  I turned the server off one night and when I turned it back on, I noticed Gallery3 was not working anymore.  When I checked the database all tables kept returning:
"#1286 - Unknown storage engine 'InnoDB' "

In phpmyadmin when I check the engines it says:
"This MySQL server does not support the InnoDB storage engine. "

Is there a way to reinstall or re-enable InnoDB?

Thanks!

---

### Post by biocyberman on 2012-08-16
Hi, 
Maybe you changed something in /etc/mysql/my.cnf ?

I changed innodb_log_file_size and that cause my trouble, I found my fix thanks to "Tero" suggestion here:
[http://ubuntuforums.org/showpost.php?p=10501109&postcount=4](http://ubuntuforums.org/showpost.php?p=10501109&postcount=4)

---

