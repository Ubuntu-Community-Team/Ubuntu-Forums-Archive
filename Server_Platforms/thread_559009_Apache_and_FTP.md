---
title: "Apache and FTP"
date: 2007-09-24
forum: Server Platforms
---

### Post by Stormspace on 2007-09-24
OK. I installed vsftp so that I could transfer files to my webserver. Thing is think I might have screwed up the ownership of the web directory on the server. Ok, I know I did, I just need to know how to fix it. 

Currently I can chown the web folder to www-data and the web pages display fine, but i can't ftp using the administrator account. If I chown the folder as administrator, the web pages won't display, but the ftp goes through fine. Obviously I've done something to the default settings since it was working earlier today. 

Anyone want to walk me through this? Thx in advance.

---

### Post by cookfromfrozen on 2007-09-25
/var/www needs to be owned by root, not www-data.  

```

chown root /var/www
chgrp root /var/www
chown 755 /var/www
chmod -R 644 /var/www/*

```

all files in /var/www should be owned by root too, they just need to allow read access to others so www-data can read them.  if you want people to upload by ftp then you'll need to allow write access to a certain directory to whatever user logs in through ftp or whatever account the ftp daemon runs as

that should help

---

