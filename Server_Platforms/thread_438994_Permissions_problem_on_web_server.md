---
title: "Permissions problem on web server"
date: 2007-05-10
forum: Server Platforms
---

### Post by raddevon on 2007-05-10
I'm running Apache and proftpd on Fiesty Fawn. I've got my DocumentRoot in Apache and my FTP server root set to /etc/apache2/htdocs. I created this folder, but, when I log into the FTP, I can't transfer files due to a permissions problem. I tried chmod a=rw /etc/apache2/htdocs to set the permissions. Once I do this, I can no longer login to the FTP server. It says my password is incorrect. I created the folder and set the permissions while logged in as root. I have a feeling I'm just missing a step. Any help is greatly appreciated.

---

### Post by masmad on 2007-05-10
I think it's a problem with the permissions you gave the directory. Try sudo chmod a+x /etc/apache2/htdocs.

(and you should really consider using something else than giving everyone read/write-access)

---

### Post by raddevon on 2007-05-10
I tried that, and, although I can still login to the FTP server, I cannot transfer files up. My server returns this message:
550 index.html: Permission denied

I just chose to do it this way because I'm a noob and figured it would be the easiest way. What alternate method would you suggest?

---

### Post by raddevon on 2007-05-10
So, does anyone else have any suggestions?

---

