---
title: "Backup and Restore of Apache &amp; MySQL"
date: 2012-02-17
forum: Server Platforms
---

### Post by tsubakaran on 2012-02-17
I have setup the Ubuntu server in new hardware and already have Ubuntu server in old hardware where I am running Apache and MySQL. how to backup and restore the Apache and MySQL databases from old hardware to new server. I have already installed webmin but I don't know how to backup and restore to new Ubuntu server. help me please.

---

### Post by TheFu on 2012-02-17
Use mysqldump to export any DBs.
Copy the files below /etc/apache2/ (careful about links) and where ever you keep any php or static HTML files over. You probably want to put them in the same place.

Be certain Apache is not running on the target system.  This may not be that important.

Import the DB(s), double check any settings, restart apache.

---

### Post by tsubakaran on 2012-03-06
Thanks for your reply, I have done the job with your suggestion as well. In addition, I used webmin to do the job simply.

---

