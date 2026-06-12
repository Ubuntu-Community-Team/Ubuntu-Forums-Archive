---
title: "Samba forgetting my password"
date: 2009-04-23
forum: Server Platforms
---

### Post by jammeri on 2009-04-23
I'm running Samba server on my Ubuntu 9.04, but every time I reboot it seems to forget the user's samba password and I need to do "smbpasswd <user>" to fix it. 

Does Samba save the user database? Where?
What could cause this problem and how should I attempt to fix it?

---

### Post by jammeri on 2009-04-30
Apparently Ubuntu synchronizes the passwords with user's system password with libpam-smbpass

I figured this wouldn't be the case because help says in 8.2.3. Accessing shared folders via Windows:

> 
If you would like to access a shared folder hosted on an Ubuntu computer by using computers running Windows, you may have to perform some additional steps:
1. Press ... to open a Terminal
2. Type sudo smbpasswd -a username ...
3. Enter your password ...
4. When prompted with "New SMB password:", **enter the password that you would like to use to access the shared folder** and the press Enter. ...


Anyway this is solved now as using the user's system password works.

---

