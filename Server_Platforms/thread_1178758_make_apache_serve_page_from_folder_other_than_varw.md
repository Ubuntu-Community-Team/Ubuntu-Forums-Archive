---
title: "make apache serve page from folder other than /var/www?"
date: 2009-06-04
forum: Server Platforms
---

### Post by jeremy1138 on 2009-06-04
Here's the problem I have.  I'm trying to use wordpress to set up a blog on a server that I'm running at home.  I've got wordpress installed and running for the most part but I'm having some problems.  The problems are many but the one I'm concerned with at the moment is that I'm trying to install plugins for wordpress but the installation process requires the use of ftp to install said plugins.  

I have ftp working fine and all that but the problem is that the way I have vsftpd set up (which is the way it came out of the box) is that my username and password only gives me access to my home directory.  Here's my question: Is there a way to make apache point at a different folder other than /var/www?  I'd like it to point to something like home/myusername/www or something like that.  If this isn't possible or if this is really difficult to accomplish, it would be equally useful if there was a way to make /var/www accessible (read and write) via ftp somehow.

I'm sorry if this has come up a million times but I searched everywhere I could think of and I just don't know what else to do.  I would really appreciate any help.  Thanks!

---

### Post by Iowan on 2009-06-04
Check [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") one...

---

