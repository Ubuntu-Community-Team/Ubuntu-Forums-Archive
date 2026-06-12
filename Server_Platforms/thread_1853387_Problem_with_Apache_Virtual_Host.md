---
title: "Problem with Apache Virtual Host"
date: 2011-10-02
forum: Server Platforms
---

### Post by RideTheWave on 2011-10-02
Hello! It's my first post here :)

I installed Apache like it is described here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Apache works but the steps described under "Virtual Hosts" cause a 403 error in my browser. Ho can I change the DocumentRoot to /home/user/public_html/ ?

Thanks in advance.

---

### Post by Lars Noodén on 2011-10-02
> **RideTheWave said:**
> Ho can I change the DocumentRoot to /home/user/public_html/ ?

Look at the module [UserDir](http://httpd.apache.org/docs/2.3/mod/mod_userdir.html).  That will enable user-specific directories so that you don't need to change the document root.

---

### Post by volkswagner on 2011-10-02
If you followed the how to, your docRoot should already be set.  That is why you are getting the error.

You need to change the permissions for the directory.

You can:

```
sudo chown -R yourusername:www-data /home/username/public_html
```

Also check the individual file permissions.

```
ls -alt /home/user/public_html
```

Typically they should be read only for group and everyone and read/write for owner.

---

