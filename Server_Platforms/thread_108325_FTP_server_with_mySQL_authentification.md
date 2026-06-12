---
title: "FTP server with mySQL authentification"
date: 2005-12-25
forum: Server Platforms
---

### Post by djvishnu on 2005-12-25
I am having a really hard time finding a ftp daemon that can authenticate users from an mysql database.

I looked at pureFTPd, which can do exactly this, but it still requires users mapped to system users, witch i dont want.

glFTPd i almost perfect, it uses a userdb that is independent of system users, and i can define directory rules in a conf file instead of using system ownership and permissions. The only problem is that i cant cannot figure out how to make it authenticate throuh a sqldb

Anyone got some tips for me? I cant imagine that im the first one to want this..

---

### Post by chrigu on 2005-12-27
Hi,
I use pure-ftpd-mysql! IMHO, you must map a ftp-user to a system user.. Otherwise you get troubles with the permissions?!
All my ftp-users have the rights of the system-user www-data. So there is no problem to create/edit files in /var/www, because all modification are made under the rights oh www-data..

bye,
chrigu

---

### Post by djvishnu on 2005-12-29
I c, but my problem is that if i map the sql users to the same system user they can delete eachothers files (my server has homefolders +  a shared folder). And i cant create one systemuser for each user. (then i wouldnt need sql auth..)

What i really need is a sql-auth like pureFTPd and a permissionsconfiguration of glftpd. (the server runs as a user that has full access to the files, and sets permissions itself)

any hints?

---

