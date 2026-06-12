---
title: "SFTP (FTP over SSH2) Shows ALL Hidden Files"
date: 2007-05-29
forum: Server Platforms
---

### Post by Dark Elitist on 2007-05-29
Hello,

Does anybody happen to know how to make it so that when connecting to a proftpd server using SFTP (FTP over SSH2) that all hidden files (files beginning with .) are not displayed?  

Regular FTP works fine in this regard and only displays files not beginning with . but SFTP shows all the hidden files in the home directory.

If anybody has a fix for this, it would be much appreciated!

Dark Elitist

---

### Post by TKRL2 on 2007-05-30
When I was useing proftpd with my fedora core server... I had to go in and edit the proftpd.conf file located in the /etc directory..... and in the file, I needed to comment out the "show .a files" or something to that effect.... which solved the problem.... hopefully this helps

---

### Post by obimeister on 2007-05-31
Are you you don't have openshs server running? because it has sftp protocol too and uses same port.

---

