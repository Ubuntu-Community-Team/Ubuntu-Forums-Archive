---
title: "SAMBA File Sharing works with a User Logged In"
date: 2006-01-02
forum: Server Platforms
---

### Post by ztrek7 on 2006-01-02
I have setup SAMBA, thanks to the might Webmin. I have one user on this box, administrator. If I log into this box as administrator, I can access the files from any windows machine using administrator as user name. If I log off the box, I get access denied.

Any ideas?

---

### Post by alamba on 2006-01-02
administrator as a user on your ubuntu box?

Akshay

---

### Post by harisund on 2006-01-04
I do not know how to do it through webmin, but to enable Samba access for any user I do 
sudo smbpasswd -a username
After that the Windows machine on the network can see it, using the appropriate username/password and on the appropriate WorkGroup of course.

---

### Post by ztrek7 on 2006-01-05
[QUOTE=alamba]administrator as a user on your ubuntu box?

Akshay[/QUOTE]


Just something I saw somewhere. Create a user named Administrator. Still use sudo and su, just log in as administrator.

---

