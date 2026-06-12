---
title: "File Browsing In Server Edition"
date: 2009-01-08
forum: Server Platforms
---

### Post by jairom70 on 2009-01-08
How or what do can I use to view my system files in the Ubuntu Server 
Edition. 

Also if im viewing a folder. And want to copy the file im currently 
viewin is that possible to then go to a diff Directory and pasting. 
ratther then doing

-cp 

Ty  :D

---

### Post by netztier on 2009-01-08
> **jairom70 said:**
> How or what do can I use to view my system files in the Ubuntu Server 
Edition. 

Also if im viewing a folder. And want to copy the file im currently 
viewin is that possible to then go to a diff Directory and pasting. 
ratther then doing 

If you're old enough *grin* to remember Norton Commander from the DOS age, you might like the Midnight Commander, aka **mc**. Get it with

```
sudo aptitude install mc
```

after having enabled the "universe" repositories (see [https://help.ubuntu.com/8.10/serverguide/C/configuration.html](https://help.ubuntu.com/8.10/serverguide/C/configuration.html) for instructions how to do this on Ubuntu server).

regards

Marc

---

### Post by volkswagner on 2009-01-08
[Webmin]("http://www.webmin.com/") has a FileManager.  It is Java based so you need Java on the client machine web browser.

---

### Post by Dr Small on 2009-01-08
My filemanager concists of the commandline and the following commands:
```
ls mv cp mkdir rm chown chmod
```

---

### Post by soldersplash on 2009-01-08
I use Webmin to admin my headless (media) ubuntu server.
Recommend it.
:)

---

