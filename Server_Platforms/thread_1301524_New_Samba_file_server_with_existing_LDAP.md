---
title: "New Samba file server with existing LDAP"
date: 2009-10-26
forum: Server Platforms
---

### Post by jap1968 on 2009-10-26
Hello there,

After having read many tutorials and how-to I can not find a tutorial for my particular scenario:

My company already uses an LDAP server for several tasks. This is regularly maintained, so every employee in the company is properly registered there.

I want to create a new service: Just a Samba file server (no domain controller nor anything more advanced in this moment) offering personal folder for every user. I want that every existing user on the LDAP (about 600) has its own storage space on a centralized file server based on Samba.

Almost all tutorials that I have read so far involve modifications on the LDAP or cover the toppic of setting up your own LDAP sever. This is not possible in this case. I just can access to the LDAP server in read mode. I am not allowed to modify the LDAP structure in any way.

How should I configure the samba file server in order to authenticate with such LDAP server?

---

### Post by koenn on 2009-10-26
here's a start :

[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

---

