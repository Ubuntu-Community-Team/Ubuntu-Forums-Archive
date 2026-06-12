---
title: "Apache Permissions"
date: 2010-12-12
forum: Server Platforms
---

### Post by blakep2 on 2010-12-12
I would like to change the permissions for a directory and all files inside the directory how do I do this?  The website is located only on my local network so I am not worried about security.

Also what would be the optimal permissions for running wordpress.

---

### Post by chrislynch8 on 2010-12-13
chmod -R (your-permissions) /var/www/some-directory


As for the permissions I assume so long as files are read/write-able by the web server user www-data you'll be OK

---

