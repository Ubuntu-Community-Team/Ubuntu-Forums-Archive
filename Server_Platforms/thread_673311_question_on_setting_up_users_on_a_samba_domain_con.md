---
title: "question on setting up users on a samba domain controller"
date: 2008-01-20
forum: Server Platforms
---

### Post by beaker15 on 2008-01-20
I'm setting up a samba domain controller on Feisty serving about 10 Windows XP clients and wondering how best to go about setting up the users/groups i need. At the moment I was just going to create the users and groups in ubuntu and convert them to samba users through webmin.  Is this the best way or do i need to use openLDAP? In particular I'm looking at the "passdb backend" line in smb.conf. because i'm not sure what to put in there.

---

### Post by K.Mandla on 2008-01-22
Moved to Servers and Security.

---

### Post by freebeer on 2008-01-22
I use tdbsam myself.  You might want to have a look at [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/passdb.html]("http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/passdb.html") for some background info to help you make a choice.

---

