---
title: "HTTP-based File Manager"
date: 2007-06-08
forum: Server Platforms
---

### Post by dasunst3r on 2007-06-08
Does anybody know how one would go about implementing web-based home directory access?  The user must be able to type in their user name and password and be able to manipulate files (download, upload, delete, etc.).  Thanks!

---

### Post by turinglabs on 2007-06-08
webmin has a browser-based file manager that allows you to restrict access to home directories, but it seems there are no official webmin packages anymore (not since breezy). You can get upstream debian packages at webmin.com, they might work.

---

### Post by piers on 2007-06-08
Webmin source is a piece of cake to get going (probably easier than using the deb), also look at Virtualmin

---

