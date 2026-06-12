---
title: "Make web app files owned by user not www-data?"
date: 2009-06-21
forum: Server Platforms
---

### Post by betarobot on 2009-06-21
Hey guys, 

What would you recommend to setup web server to make web app files to be owned by user not www-data?

So currently when my Drupal install generates folders or files it is owned by www-data. This way normal user can't modify / delete those files via ftp/sftp. 

Thanks for any tips!

---

### Post by Kareeser on 2009-06-21
I personally do not see any problem with it. I myself have multiple folders in /var/www owned by the individual users, so they can FTP and SSH changes easily. As long as "others" (as in ug**o**) have read access to the file, www-data can still serve them properly.

---

