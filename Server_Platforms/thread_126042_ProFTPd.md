---
title: "ProFTPd"
date: 2006-02-05
forum: Server Platforms
---

### Post by justin.tyler on 2006-02-05
I'm having some trouble with ProFTPD. How does one create a user and a password for that user?

---

### Post by anodizer on 2006-02-05
Via the "Users and Groups" menu (it is located in system -> administration).
You must create a new user there, and a folder for the new user will be created in the /home directory. When someone logs in your ftp server he will be able to see only the contents of this folder.

---

### Post by justin.tyler on 2006-02-05
well then how would one upload files to the web server?

---

### Post by anodizer on 2006-02-05
He can upload normally, assuming he has write permission in that specific folder.

---

### Post by justin.tyler on 2006-02-05
Ok, but I can't login using an FTP program, regardless of which account on the machine I try to use...

---

### Post by anodizer on 2006-02-05
It doesn't login ori it doesn't connect at all? Cause if it cannot connect you should check your ports. Proftpd uses the default port for ftp, which is 21, so you should check if it is forwarded to your ip through your router. You can change the port the program uses with editing /etc/proftpd.conf.
Also keep in mind that if you chose the standalone mode you must execute the program first.

---

