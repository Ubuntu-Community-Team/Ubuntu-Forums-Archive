---
title: "Apache2, vsftpd + user permissions"
date: 2008-06-17
forum: Server Platforms
---

### Post by Poleh on 2008-06-17
Hi folks

I have an interesting problem that I haven't been able to fix (being a relative Linux n00b with a working server install for 4 months now).

**So setting the scene:**

Ubuntu Gutsy Server
Apache2 running as www-data
vsftpd running as vsftpd which is a no-priv user
Some regular system users with FTP login capability

Websites (vhosts) in 
/var/www/www.domain1.com/public_html
/var/www/www.domain1.com/logs

/var/www/www.domain2.com/public_html
/var/www/www.domain2.com/logs

/var/www owned by root:root

/var/www/www.domain1.com/public_html owned by user1:www-data with permissions of 750
/var/www/www.domain1.com/logs owned by user1:www-data with permissions of 770
etc.

**So, the explanation:**
I have set the ownership to the ftpuser:www-data so that apache can read/write to those web files, this seemed to be the only way I could get it to work.

I have set the permissions on the folders to full access for the user, and read/execute for the group. Again, this seemed to be the only way I could get apache to work.

An issue I have encountered is that new files created by uploading them via FTP have a default ownership of the FTP user, i.e. user:user - this means that because the group ownership isn't user:www-data apache can't access the files to serve them.

So the question: is this a suitable set of ownership and permissions on the website folders? Obviously the problem I am encountering is allowing apache access to the files/folders, while still allowing the ftp users to access those same files/folders to upload/alter/delete etc.

I read somewhere that umask would be my solution, i.e. setting the default cascading ownership/permissions on the folders, but haven't a clue where to start with it.

Any help/hints appreciated (and well done if u read this far!)

---

### Post by Poleh on 2008-06-19
*bump* anyone? :(

---

