---
title: "Permissions"
date: 2009-05-01
forum: Security
---

### Post by pavsid on 2009-05-01
Hi,

I've set up an FTP server on my home machine and a new user to connect to it through.

However, any folders i create at home (under my normal login) are created with permissions rw-r-r- as are any files i create over the FTP connection.  The result is that i can't amend those files if logged in as the other user.

What can be done to prevent this from happening? Can you set default permissions on the FTP home directory so that no matter what user creates files there they will always be rw-rw-rw-?

Thanks

---

### Post by pavsid on 2009-05-01
OK, i've done a bit more reading and i think ACL is the solution to my problem

Does anyone know the whereabouts of guide or options list for ACL?

Thanks

---

