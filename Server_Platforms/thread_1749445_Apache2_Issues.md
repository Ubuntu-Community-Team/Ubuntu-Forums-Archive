---
title: "Apache2 Issues"
date: 2011-05-04
forum: Server Platforms
---

### Post by gtmtnbiker98 on 2011-05-04
This is strange. Currently running a Web server on Ubuntu 10 LTS. Current Web site is *.htm file extensions. The new site that I'm trying to put in place is running *.html extensions. I don't feel that this is a directory index issue since the index page properly displays along with 85% of the linked pages.

When I copy and paste the new HTML in to /var/www some of the Web pages will display and other's cannot be found. In the browser I receive a page load error. The pages are on the server; however, for whatever reason, Apache2 is not finding them. I have stopped and restarted the Apache2 Daemon and for the life of me, cannot figure this one out.

I have placed the new site on a development Apache Server on a Mac Snow Leopard Apache instance and it runs fine. I'm at a loss, any ideas?

As soon as I delete and replace the contents of /var/www with the old site, it runs just fine. It's been awhile since I've messed with this box and cannot seem to even locate the Directory Index in /etc/apache2/apache2.conf.

---

### Post by falko on 2011-05-05
Not sure, but did you clear your browser cache?

---

### Post by hawk2010 on 2011-05-05
Can you check the file/ directory permissions?

> **gtmtnbiker98 said:**
> This is strange. Currently running a Web server on Ubuntu 10 LTS. Current Web site is *.htm file extensions. The new site that I'm trying to put in place is running *.html extensions. I don't feel that this is a directory index issue since the index page properly displays along with 85% of the linked pages.

When I copy and paste the new HTML in to /var/www some of the Web pages will display and other's cannot be found. In the browser I receive a page load error. The pages are on the server; however, for whatever reason, Apache2 is not finding them. I have stopped and restarted the Apache2 Daemon and for the life of me, cannot figure this one out.

I have placed the new site on a development Apache Server on a Mac Snow Leopard Apache instance and it runs fine. I'm at a loss, any ideas?

As soon as I delete and replace the contents of /var/www with the old site, it runs just fine. It's been awhile since I've messed with this box and cannot seem to even locate the Directory Index in /etc/apache2/apache2.conf.

---

### Post by gtmtnbiker98 on 2011-05-05
Dumped cache, flushed DNS, checked ownerships, no good.  Beginning to think the Apache2 install is corrupted.  Currently running the site on a Mac OS Apache instance without issue until I can gut and redo the main Web server.  Oh well, it's a computer.

---

