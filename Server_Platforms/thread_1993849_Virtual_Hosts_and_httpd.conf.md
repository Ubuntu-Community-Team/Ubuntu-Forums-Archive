---
title: "Virtual Hosts and httpd.conf"
date: 2012-06-02
forum: Server Platforms
---

### Post by supportsbt on 2012-06-02
How the  virtual hosts and httpd.conf file are related? 

if  i want to run two domain , how can i do that .Each domain require httpd.conf or just one is enough

---

### Post by Ms. Daisy on 2012-06-04
Let's start with the virtualization software you're using. Virtualbox? VMware?

I take it you're installing a web server?

---

### Post by Iowan on 2012-06-04
Moved to Virtualization.

---

### Post by stmiller on 2012-06-05
virtual hosts is an apache web server thing - not a virtualization thing. :)

Can someone move this to the server section?

---

### Post by SeijiSensei on 2012-06-06
Here's a quick overview of the process of creating virtual hosts in Ubuntu:
[http://ubuntuforums.org/showpost.php?p=11922324&postcount=2](http://ubuntuforums.org/showpost.php?p=11922324&postcount=2)

The httpd.conf file is deprecated in Ubuntu.  The main Apache configuration is in /etc/apache2/apache2.conf and ports.conf.  The virtual hosts are placed in separate files in /etc/apache2/sites-available as I describe in the posting linked above.

---

