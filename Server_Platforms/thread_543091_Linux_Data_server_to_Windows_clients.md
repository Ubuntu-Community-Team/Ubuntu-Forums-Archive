---
title: "Linux Data server to Windows clients"
date: 2007-09-04
forum: Server Platforms
---

### Post by jmvidalvia on 2007-09-04
I am sorry: I really tried to google it, but was not able to find what I need.:(
My company runs a Windows 2003 Server with 30 Windows clients.
I would like to add an extra box running linux in order to share files, rsync to an external box for backups, etc.)
I read about LDAP, but it seems too complicated for my possibilities.
I guess I can give some permissions to user and/or groups just with Samba, can't I?
Can anybody link me to a suitable howto?
Thanks a lot!:)

---

### Post by NewbieNik on 2007-09-05
there are some fine examples available in the ¨HOW TO By Example "section on samba.org
Join the ubuntu box to the domain and the allow permissions by adding YOURDOMAIN/DOMAIN USERS in the allow list. you&#314;l need to install smbfs and winbind (Sudo apt-get install winbind smbfs)
I would also use SWAT to configure Samba if you´re new to it (Sudo apt-get install swat), it&#347; perfect to learn with and gives a good GUI rather than editing files.

---

### Post by jmvidalvia on 2007-09-05
Thank's a lot: I didn't know swat.
Time to work now!

---

