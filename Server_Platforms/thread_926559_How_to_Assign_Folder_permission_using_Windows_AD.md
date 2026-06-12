---
title: "How to Assign Folder permission using Windows AD?"
date: 2008-09-22
forum: Server Platforms
---

### Post by daveloh on 2008-09-22
I have one ubuntu machine will join Windows 2003 Domain.

And it will become a file server for certain department.

How I join Windows Domain and assign folder permission by Users Group or User?

Thank you.

---

### Post by gishaust on 2008-09-22
I don't know if this is what you are looking for exactly, and I have never done it. However samba will be the tool you will need to use, as it is for communicating to windows servers.

[https://help.ubuntu.com/8.04/serverguide/C/windows-networking-introduction.html](https://help.ubuntu.com/8.04/serverguide/C/windows-networking-introduction.html)

This is will help you get started but if you need more google samba with ubuntu and the version you are using.

---

### Post by koenn on 2008-09-22
I happened to be researching this last weekend, 
here are my notes:
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

Also look for "likewise-open" in the link gishaust posted

---

