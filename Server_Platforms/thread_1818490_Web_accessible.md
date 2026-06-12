---
title: "Web accessible"
date: 2011-08-04
forum: Server Platforms
---

### Post by mbw290 on 2011-08-04
I am trying to write a script that users can use to make a directory that would be accessible from the web browser.  Any ideas?

---

### Post by thomasw_lrd on 2011-08-04
I'm just going to throw it out there.  I think more details are needed.  Is this a webserver you are running?  On your machine, in the cloud?

---

### Post by fdrake on 2011-08-04
what kind of server ? apache? which user will you allow? more details will be appreciated,we don't read minds yet ...  :)

---

### Post by mbw290 on 2011-08-04
Sorry guys!  I am running a web server with apache everything works fine so far in terms of I can access the it works! page

---

### Post by fdrake on 2011-08-04
> **mbw290 said:**
> Sorry guys!  I am running a web server with apache everything works fine so far in terms of I can access the it works! page

go to 
/var/www/ 
and you can put anything you want and everyone on you local net will be able to access. i don;t quite get what you want to do...

---

### Post by Wim Sturkenboom on 2011-08-04
On the question to create a directory

use e.g. PHP and [http://www.php.net/mkdir](http://www.php.net/mkdir)

As you don't provide any details how you visualize this (basically a specification), there is not much that we can advise in my opinion.

---

### Post by mbw290 on 2011-08-04
Sorry guys I am very new to this.  I want a user to login run a script then have a directory where they can put a website rather than having to manually make a directory for them.

---

### Post by fdrake on 2011-08-04
> **mbw290 said:**
> Sorry guys I am very new to this.  I want a user to login run a script then have a directory where they can put a website rather than having to manually make a directory for them.
you are looking definitively for PHP. you can start looking around for some tutorials. What you are asking is not a 1 step script. . .
[http://www.phpeasystep.com/phptu/6.html](http://www.phpeasystep.com/phptu/6.html)

---

### Post by volkswagner on 2011-08-05
Are the users in question actual system users?   If they are, Apache [mod_userdir]("http://httpd.apache.org/docs/2.0/mod/mod_userdir.html") may be an option.

---

