---
title: "Setting up openLDAP"
date: 2011-03-02
forum: Server Platforms
---

### Post by miketoasty on 2011-03-02
Hello All!

I am new to Linux Ubuntu servers and just needed a little help getting started off. I am currently an IT employee at a company and I have been gifted with the task of switching our current windows domain, to a Ubuntu domain. So far I have the server set up with a GUI enviroment but little past that. Right now I am just trying to get openLDAP setup and be able to add users and connect local computers to it. I have been using various guides from accross the internet but none have seemed to work. I am using Ubuntu Server 10.10, fresh installation and was wandering if someone can point me to an "Noob" friendly step by step process for getting LDAP setup.

Thanks in advance.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-02
Screw OpenLDAP, Kerberos and Samba. On ubuntu theyre hell to work with, especially to get any security. If your any good with Linux, I would strongly recommend the alpha versions of Samba4. I find that it tends to be faster, have more features, and (I find) that its a fair amount more secure than windows :) 
heres the address:

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

Unlike Samba, this can properly replicate a Server 2008_R2 domain, not just NT4 :)

---

