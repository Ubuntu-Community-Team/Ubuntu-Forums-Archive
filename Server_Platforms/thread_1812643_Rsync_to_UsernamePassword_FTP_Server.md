---
title: "Rsync to Username/Password FTP Server"
date: 2011-07-26
forum: Server Platforms
---

### Post by techanalyst on 2011-07-26
Im reading a lot on how to rync to an ftp server but none of the steps are telling me how to do it on servers that use normal authentication

Example I want to keep /var/www in sync with a folder on an ftp server in a folder called /cdn/

Id like to see all files and folders in sync, not just a compressed file etc

---

### Post by koenn on 2011-07-26
your question does not make much sense.

to an FTP server, you'd use ftp, not rsync
if you want to do rsync, you'd do it towards either an rsync server, or a system where you have shell access


if you rsync to a server that uses username/password authentication, you include the username in the rsync command, and gibve the password when prompted. Why is that a problem for you ? 

rsync doesn't n,ormally limit itself to compressed files. What gave you that idea ?

---

### Post by techanalyst on 2011-07-27
Im just trying to figure out the best way to do it.  I tried ftp and ive run into two things, one it either moved all the files or two it copied only the files and not the subfolders.

My understanding is rsync and do the samething, this is for a CDN Service

---

