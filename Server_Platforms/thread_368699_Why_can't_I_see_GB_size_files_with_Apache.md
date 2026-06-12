---
title: "Why can't I see GB size files with Apache?"
date: 2007-02-23
forum: Server Platforms
---

### Post by caffienda on 2007-02-23
I just setup 6.10 server and have copied a lot of ISO's to the /var/www/ directory.  Some of these files are between 1-5GB (DVD ISO's).  

Why do these not show up when looking at the directory in the web browser?

---

### Post by GoBieN on 2007-02-23
do they have read permissions set for everyone ?

Just try a "sudo CHMOD 644 *" in that directory and look again.

---

### Post by caffienda on 2007-02-23
I tried setting the permissions to 777 even! All the files in the directory are have the same permissions and owner.    The only two files that can't bee seen are > 1GB.  

BTW, thanks for helping, I saw that you posted on the Apache, PHP, MySQL install too!

---

### Post by GoBieN on 2007-02-24
hmm strange, and what are the filenames of these files ? Because Apache is standard set to not list everything that starts with a . (aka hidden files).

---

### Post by drakkan on 2007-02-24
apache <2.2 can handle filesize <2GB, for big file you have to upgrade to apache 2.2.x or use an ftp server, pure-ftpd is fine,

regards
drakkan

---

