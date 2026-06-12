---
title: "pureftpd mysql (ftp configuration)"
date: 2006-02-14
forum: Server Platforms
---

### Post by Virogenesis on 2006-02-14
I've used a guide taken from [HowToForge]("http://www.howtoforge.com/pureftpd_mysql_virtual_hosting") 

The server will be configured like this using mysql with pureftpd.
Now I've created a folder inside home called ftpusers and within that I have a folder called download and another called upload.
The upload will set be set so a user can make a folder and write to.
Download will be read only.

This is the part I do not understand is this.... 
MYSQLGetDir     SELECT Dir FROM ftpd WHERE User="\L"AND status="1" AND (ipaccess = "*" OR ipaccess LIKE "\R") 

Now that selects the dir from the username but the problem is I wish for all the users to share the same dir.

---

