---
title: "Apache and file permissions"
date: 2008-08-04
forum: Server Platforms
---

### Post by lincolnlad on 2008-08-04
Hello,

I've been running a single user LAMP server running Wordpress blogs for a while and everything has been straightforward.

I am now hosting a vhost and I'd like the new user to have full read-write file permissions over his directory as well as allow apache full permissions over the directory so that both SFTP and browser-side uploading works, too.  I can only seem to get either browser/apache permissions or user/SFTP permissions working but not both.

So, in essence I need:

apache rwx site A
apache rwx site B
user2 rwx site B

Any ideas? I'm assuming that this is a common requirement in a multi-user server environment.

Thanks very much

---

### Post by hvc123 on 2008-08-04
try chown -R www-data:www-data /var/www/site1
then chmod -R 775 /var/www/site1

if thats where te sites are located

---

### Post by lincolnlad on 2008-08-05
Hi,

Thanks for your reply.  I can see how that works when I add user1 to the www-data group, but this is pretty insecure as then any file that apache owns is rwx by that user.

I'm looking for a way for user1 to only have permissions over his own /home files and his /var/www/siteA while apache has full rwx permissions over all sites system wide.

Any ideas?

Thank you

---

### Post by StickyStyle on 2008-08-05
First off, I personally have not seen a web application that requires the apache user full +rwx across everything in /var/www or even full +rwx throughout an individual web applicatoin folder.  Often there are very specfic locations that require write access such as a temp, log, or upload folder.  Giving the the apache user full access across everything is asking for trouble.

For your setup i can recomend this...

admin@web1:/var/www# ls -la
drwxr-xr-x  4 root root  112 2007-10-30 16:22 .
drwxr-xr-x 18 root root  416 2007-12-10 09:19 ..
drwxr-xr-x  2 root www-data 1352 2008-03-31 08:53 SITEA
drwxr-xr-x  2 user2 www-data 1352 2008-03-31 08:53 SITEB

Then in the directories that require the apache process to write to you can do this (SITEB)...

/var/www/SITEB/WRITE_TO_DIR

drwxrwxr-x  2 user2 www-data 1352 2008-03-31 08:53 WRITE_TO_DIR

and SITEA
/var/www/SITEA/WRITE_TO_DIR

drwxrwxr-x  2 root www-data 1352 2008-03-31 08:53 WRITE_TO_DIR

---

### Post by 2smooth on 2008-08-17
> **StickyStyle said:**
> 
drwxr-xr-x  2 root www-data 1352 2008-03-31 08:53 SITEA
drwxr-xr-x  2 user2 www-data 1352 2008-03-31 08:53 SITEB


Why is SITEA owned by root and not www-data?

---

