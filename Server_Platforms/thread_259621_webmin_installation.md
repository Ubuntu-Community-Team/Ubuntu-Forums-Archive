---
title: "webmin installation"
date: 2006-09-17
forum: Server Platforms
---

### Post by kpm on 2006-09-17
I am getting a strange error while attempting to install WebMin on the Ubuntu LAMP server...
```

sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.300_all.deb
 - 13:26:38 (111.26 KB/s) - `webmin_1.300_all.deb' saved [11654]
sudo dpkg --install webmin_1.300_all.deb
dpkg-deb: `webmin_1.300_all.deb' is not a debian format archive
dpkg: error processing webmin_1.300_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing: webmin_1.300_all.deb

```

Does anyone know of another web front end for managing a server that can be had with apt-get??

Thanks

---

### Post by bluefrog on 2006-09-18
If you really want webmin, enable universe in your sources.list and install webmin from there (doesn't come as a whole, have to select whatever module(s)s you want)


James

---

### Post by etcpool on 2006-09-18
get the source package from webmin.com

then better install it from the terminal ;).

---

### Post by SlowYaRoll on 2006-09-19
Try using the most recent version of webmin from Webmin.com.  Previous versions of webmin gave Ubuntu users a hard time because it relied on the root password.  Since in the typical Ubuntu install, you don't set the root password, you'd be unable to login to webmin unless you followed instructions I posted a while back.

[http://ubuntuforums.org/showthread.php?t=195093&page=4](http://ubuntuforums.org/showthread.php?t=195093&page=4) 

The new version of webmin allows you to login using a user account with sudo root privs.

---

