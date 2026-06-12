---
title: "File Permissions"
date: 2012-05-31
forum: Server Platforms
---

### Post by tynen on 2012-05-31
Hello everyone! First off I'd like to say thanks! :)

Okay so here it goes:

I'm running Ubuntu Server 12.04. I have SAMBA running and configured with a share /srv/samba/share and that's working great

My question is, is there a way to have different permissions for different groups on folders. Like can I have group @sysadmin have RWX for folder /srv/samba/share/files and have @sales have RW permissions for /srv/samba/share/files and @graphics have R permissions for /srv/samba/share/files?? 

Thanks guys! :) :KS

---

### Post by papibe on 2012-05-31
Hi tynen.

Take a look at this online book: [Using Samba]("http://oreilly.com/openbook/samba/book/index.html"). This chapter: ["Users, Security, and Domains"]("http://oreilly.com/openbook/samba/book/ch06_01.html") has useful information regarding user and group permissions.

I hope that points you in the right direction.
Regards.

---

