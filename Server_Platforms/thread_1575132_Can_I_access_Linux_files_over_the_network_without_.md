---
title: "Can I access Linux files over the network without using FTP?"
date: 2010-09-15
forum: Server Platforms
---

### Post by crayonfingers on 2010-09-15
Hi there

I've setup a webserver with LAMP and wondered if it was possible to edit the files without having to login through FTP, as would be the case if I was editing on an IIS server?

Thank you

Simon

---

### Post by arrrghhh on 2010-09-15
SSH...

Unless you're on a LAN, then I'd use NFS if it was Linux-to-Linux, or Samba if it's Linux-to-Windows...

---

### Post by gmanigault on 2010-09-15
You could also use Webmin.  It is and awesome piece of software that will let you manager every aspect of your server using your browser.  Go to [www.webmin.com](www.webmin.com) and check it out. 

GWShark

---

