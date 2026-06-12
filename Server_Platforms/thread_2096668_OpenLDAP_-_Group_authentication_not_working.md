---
title: "OpenLDAP - Group authentication not working"
date: 2012-12-20
forum: Server Platforms
---

### Post by fabykarim on 2012-12-20
Hello,
 
Group authentication is not working in my openLDAP setup. I mean, I cannot restirct users based on groups. All the ldap users can login to all servers even if they are not the member of the group.

---

### Post by sandyd on 2012-12-20
Try restricting logins to the group using pam

```

sudo nano /etc/pam.d/login

```
add
```

-:*yourgroupnamehere*:ALL

```

you might have to add it to the sshd pam

---

### Post by Philip Colmer on 2013-01-09
I've solved this by adding the following line to the end of /etc/security/access.conf:

-:ALL EXCEPT root sysadmin (groupname):ALL

and then uncommented "account required pam_access.so" in /etc/pam.d/sshd.

The line in access.conf essentially allows you to specify some local accounts (your mileage may vary) that are always allowed to log in, plus the membership of the group you've specified.

---

