---
title: "Samba 4.0.14 AD DC"
date: 2014-01-23
forum: Server Platforms
---

### Post by access1denied on 2014-01-23
I have installed Samba 4.0.14 and I am able to share two folders and created a user account on AD using a windows xp PC.  I have also connected two computers to the DC, Windows XP and Windows 7.

I have created and shared the two folders:
Users
Data

The challenge I am having has to do with the sharing... if I try to access either of the shared folder from windows XP or 7, login as the Administrator, using the UNC path \\domain.lan\Users\, I am not able to access the folders.  if I use the \\domain.lan\ I can see shared folders, i just cannot access them.  However, if I use the unc address \\hostname.domain.lan\Users\ I am able to access the folder. However, this will be available to all users.  

So my problem is this... I cannot lock down the shared folder when using the unc path \\hostname.domain.lan\User to prevent other users from accessing the folder.  and I need to allow access via AD to both shared folder when using the \\domain.lan\Users path.

---

### Post by JnPson on 2014-01-24
This might help
[http://ubuntuforums.org/showthread.php?t=2191980](http://ubuntuforums.org/showthread.php?t=2191980)

---

### Post by access1denied on 2014-03-04
JnPson... that worked... thanks for the help!!

---

