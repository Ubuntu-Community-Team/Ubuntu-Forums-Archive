---
title: "Setting up an Intranet"
date: 2011-09-22
forum: Server Platforms
---

### Post by teejay17 on 2011-09-22
Hello all, 
I would like to set up an internal server for my company that will run Ubuntu and also have 
[LIST]
[*]a wiki
[*]a forum
[*]and an internal blog/news site
[/LIST]
Caveat: I'm not an IT person, so I'm looking for a simple way to install/get running rather quickly. Also, if I can get it to run with my limited skills, that should help persuade IT that it's not that bad. 
Also, I'm doing this as a side project within my department as a test-run, on a test machine (my manager said go for it!), to prove that we don't need to purchase expensive MS SharePoint software and licences for this. 
If I can do a good job with this, we'll be able to re-allocate resources to something more useful. 
I'm not afraid to dig in; however, I'd like the set up to be as easy as possible for the end users to use/navigate. Internally, some of our testers are already having a very difficult time testing SharePoint.
I'm looking forward everyone's responses.
Cheers!

---

### Post by SeijiSensei on 2011-09-22
[Ubuntu Server Guide](https://help.ubuntu.com/10.04/serverguide/C/index.html) is a good starting point.  Here are a couple of topics you should read carefully:

[Apache2 Web Server](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)
[PHP5 Scriping](https://help.ubuntu.com/10.04/serverguide/C/php5.html)
[Installing the "LAMP" stack of Apache, PHP, and the MySQL database server](https://help.ubuntu.com/community/ApacheMySQLPHP)

Most of the software you will want to install will require LAMP as the platform.  For blogging, you can install [WordPress]("http://wordpress.org/"). For forums, the gold standard is vBulletin, which this site uses, but it's now commercial.  [Simple Machines](http://www.simplemachines.org/) is a nice alternative.  I can't help with wikis.

I'd also suggest you enable "[webdav]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html")" on the server which facilitates sharing files.  Windows users can have a desktop folder that points to the webdav share.  The other obvious filesharing alternative is to run [Samba]("https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html") which provides Windows-style sharing.

---

### Post by teejay17 on 2011-09-22
> **SeijiSensei said:**
> [Ubuntu Server Guide](https://help.ubuntu.com/10.04/serverguide/C/index.html) is a good starting point.  Here are a couple of topics you should read carefully:

[Apache2 Web Server](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)
[PHP5 Scriping](https://help.ubuntu.com/10.04/serverguide/C/php5.html)
[Installing the "LAMP" stack of Apache, PHP, and the MySQL database server](https://help.ubuntu.com/community/ApacheMySQLPHP)

Most of the software you will want to install will require LAMP as the platform.  For blogging, you can install [WordPress]("http://wordpress.org/"). For forums, the gold standard is vBulletin, which this site uses, but it's now commercial.  [Simple Machines](http://www.simplemachines.org/) is a nice alternative.  I can't help with wikis.

I'd also suggest you enable "[webdav]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html")" on the server which facilitates sharing files.  Windows users can have a desktop folder that points to the webdav share.  The other obvious filesharing alternative is to run [Samba]("https://help.ubuntu.com/10.04/serverguide/C/windows-networking.html") which provides Windows-style sharing.
Thanks for the info. Great starting point.

---

### Post by patryk77 on 2011-09-22
I would recommend a CMS like [Drupal](http://www.drupal.org).

It contains support for forums, wikis, blogs and news, with a nice permissions system.

It requires a bit of customization, but it's not really daunting. I use it to run a small social networking site and am quite happy with it.

Edit: Oh, and MySQL/PHP/Apache are the requirements, so you still need to install those.

---

