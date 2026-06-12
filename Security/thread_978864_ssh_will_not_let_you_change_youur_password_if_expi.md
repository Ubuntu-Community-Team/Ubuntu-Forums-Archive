---
title: "ssh will not let you change youur password if expired"
date: 2008-11-11
forum: Security
---

### Post by davidmarkey on 2008-11-11
If my password is expired i cannot change it via ssh.

Example:

test@192.168.50.100's password:
You are required to change your password immediately (root enforced)
Connection closed by 192.168.50.100


This is a server so this needs to work. On intrepid.

---

### Post by davidmarkey on 2008-11-12
Anyone? If i cant get this fixed i'll have to use debian or centos

---

### Post by d_kramer on 2009-03-11
Hi, 

I had the same problem and could trace it down to a config problem in PAM.

Changing
account [success=1 default=ignore]        pam_unix.so

to
account [success=1 new_authtok_reqd=done default=ignore]        pam_unix.so

in /etc/pam.d/common-account helped for me.

Cheers,
Denis

---

