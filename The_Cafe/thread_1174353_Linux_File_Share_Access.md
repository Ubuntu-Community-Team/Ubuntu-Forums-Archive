---
title: "Linux File Share Access"
date: 2009-05-30
forum: The Cafe
---

### Post by cdanik on 2009-05-30
Does anyone know of a free desktop application for the windows platform that works similarly to a mapped drive in My Computer? 

I am looking for a desktop application that a user would login and using Linux based access control, would have a list of "mapped drives". Based on groups, the system would deny users from certain shares.

I am looking for something similar to [Magellan Desktop]("http://www.ezbluesoftware.com/magellan.php") from EzBlue, but something free.

Thanks,
Chris

---

### Post by Ocxic on 2009-05-30
That can be done with samba, allowing only certain users/groups to access certain shares.  That way you don't need to configure every windows box you need to access your shares.

When you map the drive make sure the "re-connect at login" option is selected, then that user will automatically connect to the appropriate share(s) automatically.

---

