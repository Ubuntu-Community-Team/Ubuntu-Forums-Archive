---
title: "Restricting Domain users"
date: 2008-11-12
forum: Security
---

### Post by minus89 on 2008-11-12
My ubuntu 8.04 box is connected to a windows active directory domain using Winbind. User authentication is working fine, but I have one problem. I need to stop certain domain users from logging into the linux box. I believe I should be using Samba Authentication but I am not sure. If anyone could help me it would be greatly appreciated.

If you need any more information please feel free to ask.

---

### Post by koenn on 2008-11-12
how do they log in ?  ssh ?

---

### Post by minus89 on 2008-11-12
> **koenn said:**
> how do they log in ?  ssh ?

It is a local login directly to the computer. SSH and RDC will be setup but i don't need to worry about restricting login at that point.

---

### Post by oSourceM on 2008-11-13
> **minus89 said:**
> It is a local login directly to the computer. SSH and RDC will be setup but i don't need to worry about restricting login at that point.
While they login threw the samba (as i understand - simple file sharing), for sure You have to manage samba authentification

---

### Post by minus89 on 2008-11-13
> **oSourceM said:**
> While they login threw the samba (as i understand - simple file sharing), for sure You have to manage samba authentification

I was pretty sure it had to be done through samba authentication but I don't know exactly how, can  someone point me to a tutorial or somewhere that might be able to help me with that.

---

### Post by {}dif{} on 2008-11-14
You could put the pam_access.so module in /etc/pam.d/gdm and /etc/pam.d/login before @include common-account like so:

> account required pam_access.so
@include common-account

Then just specify the specific groups/users that should have access in the /etc/security/access.conf file, like so:

> + : ITAdmins : ALL
- : ALL : ALL

If ITAdmins was the group that should have access to the computer via gdm and login (or kdm or any other service to login locally) then that grants that group access and the second line denies all others access.  Anyway, read the manpage for pam_access.so and /etc/security/access.conf, I think they should be able to help you with this.

---

