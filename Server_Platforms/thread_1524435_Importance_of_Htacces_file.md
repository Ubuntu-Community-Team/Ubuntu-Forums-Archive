---
title: "Importance of Htacces file"
date: 2010-07-05
forum: Server Platforms
---

### Post by divya101101 on 2010-07-05
Can anyone let me know that why htaccess file is created? And what is important of it in dynamic website development.

---

### Post by koenn on 2010-07-05
[http://www.debianhelp.co.uk/htaccess.htm](http://www.debianhelp.co.uk/htaccess.htm)

---

### Post by bodhi.zazen on 2010-07-05
> **divya101101 said:**
> Can anyone let me know that why htaccess file is created? And what is important of it in dynamic website development.

a .htaccess file is used when one does not have access to the main apache configuration file.

You then use a htaccess file to modify a directory and you may do many things from a url re-write to password protect a directory.

In general, it is better to configure the main apache config file .

---

### Post by Bachstelze on 2010-07-06
> **bodhi.zazen said:**
> 
In general, it is better to configure the main apache config file .

Disagreed. If you have a lot of directories with per-directory configuration and you put all of it in your Apache config file, it will become unmanageable very quickly. Not to mention that you will have to SSH into your server and reload the config for every small change.

---

### Post by robowen on 2010-07-06
I agree with having .htaccess for each site if lots of sites / virtual hosts, makes it much easier to manage.

But it is also a performance hit as apache has to read the .htaccess files for each request

if you're programming with php then you may be able to put some directives in the php.ini file instead, depending on what you're trying to control

as for its importance, unless you are doing very basic web development then you should find it useful in pretty much all of your projects

---

### Post by janderson101101 on 2010-07-14
> **divya101101 said:**
> Can anyone let me know that why htaccess file is created? And what is important of it in dynamic website development.


You can use htaccess file to told google that the index page and home page is not canonical. In short htacces file solve canonical issue, It also helps for redirction of old pages to new domain.

---

