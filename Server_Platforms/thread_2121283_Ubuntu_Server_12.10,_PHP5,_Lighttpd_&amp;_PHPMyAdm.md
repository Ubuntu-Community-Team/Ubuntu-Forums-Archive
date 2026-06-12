---
title: "Ubuntu Server 12.10, PHP5, Lighttpd &amp; PHPMyAdmin"
date: 2013-03-01
forum: Server Platforms
---

### Post by daz1uk on 2013-03-01
Hi,

I'm urgently trying to set up a dev environment for a Sugar job I'm doing, the problem is I can't get PHPMyAdmin to restore the backup databases I have. It is not displaying any error messages, just linking me to an article on edititing the PHP.ini. I have editied my PHP.ini with 100M upload size and /tmp as the temp directory. I have made these changes @ both locations of /etc/php5/cgi/php.ini and /etc/php5/cli/php.ini. 

I'm stumped, please help.

Thanks.

Edit: This is the error message from phpMyAdmin "You probably tried to upload too large file. Please refer to documentation for ways to workaround this limit."

---

### Post by tgalati4 on 2013-03-01
How large is your primary database?  Perhaps 100MB is not large enough for PHP to handle, try 256MB, then reduce after restoration.

---

### Post by daz1uk on 2013-03-01
Cheers for the response,

The file I'm trying to restore is 82MB, yeah I've already set it 256MB in case that was the issue. Any other ideas? Any ideas how to show the actual error in PHPMyAdmin?

---

### Post by tgalati4 on 2013-03-02
I would ssh into the server and look at the log files in /var/log/apache2 or in /var/log/mysql.  PHP is simply handling the html and mysql requests so errors will get dumped in /var/log.  PHPMyAdmin will let you look at the database and fields, and overall schema, but the errors are probably happening with PHP execution of mysql queries.

I was under the impression that SugarCRM had an administration page that allowed migration and restoration of sugar databases?  Is there a reason that you are not using the tools within SugarCRM?

A simple google search on *sugarcrm database migration* gives a lot of hits with procedures.  Have you tried any of those?

---

### Post by daz1uk on 2013-03-03
Thanks for the help, I ended up re-installing Ubuntu Server 12.04, set all the php.ini settings as I needed them and it all worked fine, don't know what the issue was in 12.10 mind.

---

### Post by hydn79 on 2013-03-04
While your at this. Consider replacing lighttpd ([pretty dead now]("http://redmine.lighttpd.net/boards/3/topics/3845")) with [Nginx]("http://nginx.com/").

---

