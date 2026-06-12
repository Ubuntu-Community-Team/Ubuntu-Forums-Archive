---
title: "Setting up a Web Server"
date: 2009-09-10
forum: Server Platforms
---

### Post by Garebear.Shields on 2009-09-10
Hello everyone. Were trying to setup a new web server, and it's running Ubuntu Server Edition X64.

We have absolutely no idea how to install a control panel on it, (we're thinking either CubePanel or Webmin). 

Do we first need to install things like Perl and PHP? And if so, how do we install them?

---

### Post by wojox on 2009-09-10
If you didn't install LAMP on installation you can do so here:

```
sudo tasksel install lamp-server
```

That will install PHP, Apache2, Mysql.

Look at this link:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Garebear.Shields on 2009-09-10
> **wojox said:**
> If you didn't install LAMP on installation you can do so here:

```
sudo tasksel install lamp-server
```

That will install PHP, Apache2, Mysql.

Look at this link:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Thanks for the speedy reply. 
Since the server is being hosted by a company, I do not have direct access to it, do you know how I would access the console?

EDIT: Thank's everyone, this issue has been resolved. :)

---

