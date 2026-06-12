---
title: "Samba users and group"
date: 2008-07-19
forum: Server Platforms
---

### Post by rgotten on 2008-07-19
I have my Ubuntu server conected to my 4 windows client and use samba. i use webmin  to manage the server, When i see the vie conection thru webmin, i see: connected from: the window client: ie: windowes computer1, but the user and group is empty. How do i assing diferent windows computer, diferent users and groups? Or if somebody can explain this to me since i am new to linux. What i want to do is that some computers have only read access, while the other are read/write

Thanks

rgotten

---

### Post by HermanAB on 2008-07-19
Yes it can be done, but configuring Samba is difficult.  The problem is that Microsoft turned the IBM SMB protocol into a monster.

The configuration is in file /etc/samba/smb.conf.  Have a look at that file and also go to the Samba project page and start reading.  I recommend that you buy the Samba book too.
[http://us1.samba.org/samba/](http://us1.samba.org/samba/)

Cheers,

Herman

---

