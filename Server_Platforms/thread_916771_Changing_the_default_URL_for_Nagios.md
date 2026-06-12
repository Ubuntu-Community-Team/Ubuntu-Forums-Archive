---
title: "Changing the default URL for Nagios"
date: 2008-09-11
forum: Server Platforms
---

### Post by supersk on 2008-09-11
Hello,

This is a noob question. I would like to change the default URL for Nagios from [http://localhost/nagios](http://localhost/nagios) to simply [http://localhost](http://localhost)

In cgi.cfg, I edited I set the variable url_html_path to blank (e.g. url_html_path=).

Is this correct? And are there any other steps I need to configure in Nagios? In Apache, what do I need to change?

Thanks for the assistance.

---

### Post by inphektion on 2008-09-11
Yea apache config.  but I think nagios drops its apache config in the conf.d directory under /etc/apache2
In that file you'll see where is specifies /nagios

---

### Post by supersk on 2008-09-19
thanks, but what would i need to edit in the /etc/conf.d/apache2.conf file?

---

