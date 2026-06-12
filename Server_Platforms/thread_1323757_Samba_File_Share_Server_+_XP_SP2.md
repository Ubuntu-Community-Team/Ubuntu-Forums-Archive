---
title: "Samba File Share Server + XP SP2"
date: 2009-11-12
forum: Server Platforms
---

### Post by yameen101 on 2009-11-12
We have recently migrated to samba share server from Windows server 2003. We do have a xp with service pack 2 at our clients pc. We have map drives at client pc for share folders. At samba we have created users and assign passwords for users. However we are now facing problem when user try to access share folder through map drive.
 
The following error is appearing when user double click on map drive.
 
*"An error occured while reconnecting Z: to *[*\\192.168.1.200\share-data*]("file://\\192.168.1.200\share-data")
 
*Microsoft Windows Network: Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.*
 
*This connection has not been restored"*
 
This problem we do not face, if we allow share folder to all user by checking option "allow to all user" in samba. Whenever we restrict it some user the error become.
 
We use "net use" command at client system to delete all map drives and then to reconnect it. Then it works ok.
 
Kindly have your comments.

---

### Post by yameen101 on 2009-11-12
Still i am waiting for some response....

---

