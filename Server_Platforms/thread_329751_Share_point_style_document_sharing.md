---
title: "Share point style document sharing"
date: 2007-01-02
forum: Server Platforms
---

### Post by ikonia on 2007-01-02
A small workgroup server is running on the internet with ubuntu 6.0.6.

I am currently running a samba network share for windows clients to share information.

I was wondering if there was anything similar to a sharepoint portal - something that can use /etc/password or other libc authenciation methods to share documents. Currently I'm just mapping the samba share to the a web directory and trying to get htaccess to auth against /etc/password, as a poor mans portal.

---

### Post by pmasiar on 2007-01-02
some wiki? like moinmoin wiki? web pages editing using browser? 

edgewall's TRAC has all what small workgroup needs: svn repository and code viewer, bug tracker, and wiki for docs, all integrated.

There is also application where you can start editor server and multiple people can (using special client) edit the same file, but I forgot the name - starts with G :-)

---

