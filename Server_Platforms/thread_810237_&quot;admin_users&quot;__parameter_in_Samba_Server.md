---
title: "&quot;admin users&quot;  parameter in Samba Server"
date: 2008-05-28
forum: Server Platforms
---

### Post by kantha on 2008-05-28
Hi All,

In my Samba Server's configuration file (/etc/samba/smb.conf), for a particular share, I would like to allow full rights to certain users who belong to the group named "Full Access". I would like to know how to assign this group name to the "admin users" parameter of Samba.

The following doesn't work:

[Trainee]
 browseable = yes 
 admin users = @Full Access
 

Please help.

Regards,
George

---

### Post by windependence on 2008-05-28
not sure if you can use spaces in your group names.

-Tim

---

