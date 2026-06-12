---
title: "webadmin on server 8.04"
date: 2008-07-28
forum: Server Platforms
---

### Post by amai on 2008-07-28
Any work around on installing webadmin on Ubuntu server8.04.
No matter what version I am in install i get the following error.

# sudo dpkg -i webmin_1.420_all.deb
dpkg: error processing webmin_1.420_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 webmin_1.420_all.deb

---

### Post by Separ on 2008-07-28
Are you sure that you are in the same directory as the .deb package?

Try specifying the path to the file.
```
sudo dpkg -i /full/path/to/deb/file.deb
```

---

### Post by brocky102 on 2008-07-29
check out this page. it tells you all the required files needed [http://www.webmin.com/deb.html]("http://www.webmin.com/deb.html")

---

### Post by cariboo on 2008-07-29
if you are in the same directory as your webmin deb you have to use a dot slash eg:

```
dpkg -i ./webmin_1.420_all.deb
```

Instead of installing it manually you can always double click the .deb and let gdebi install it, it will download any dependencies it needs.

Jim

---

