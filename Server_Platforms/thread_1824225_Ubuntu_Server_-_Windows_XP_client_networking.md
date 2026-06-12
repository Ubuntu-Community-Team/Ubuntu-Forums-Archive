---
title: "Ubuntu Server - Windows XP client networking"
date: 2011-08-13
forum: Server Platforms
---

### Post by galtech-server on 2011-08-13
We are having a web development firm with 15 employees. Now we are planning to networking Ubuntu Server with Windows XP client systems. Our plan is to make the network act same as Windows Networks.

Sometime like, all the Windows machines will be client system and have guest accounts with limited privileges. The web development files will be stored in the server and accessed using svn.

Can anyone please help me ?

Since I am new to Linux, hope I can get a newbie like help.

---

### Post by Lars Noodén on 2011-08-13
It sounds like [Samba](https://help.ubuntu.com/community/Samba) might be what you want, if you want to access things as files.

Or you can just work through SVN over SSH.

---

### Post by galtech-server on 2011-08-13
So I can use Samba for doing this ?
So will it work like this ?

-> I can create guest accounts in Windows and set privileges (can I do it from Linux server itself ?) 

->  Map this accounts with the server

->  So each time when a user logs in he will be logged in from the linux server and use its resources ? 


Please help me with a good tutorial to do it.

---

### Post by Lars Noodén on 2011-08-14
See the links on these pages:

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

---

