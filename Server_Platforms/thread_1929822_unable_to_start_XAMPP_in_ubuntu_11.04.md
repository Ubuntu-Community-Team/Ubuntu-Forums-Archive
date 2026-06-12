---
title: "unable to start XAMPP in ubuntu 11.04"
date: 2012-02-22
forum: Server Platforms
---

### Post by lamiya on 2012-02-22
When I try to start XAMPP with /opt/lampp/lampp start command it gives me a message like this.
 Starting XAMPP for Linux 1.7.7...  XAMPP: Another web server daemon is already running.  XAMPP: XAMPP-MySQL is already running.  XAMPP: XAMPP-ProFTPD is already running.  XAMPP for Linux started. Then I type this on terminal :
sudo netstat -pant | egrep ":80 .* LISTEN" Then message show as like as :
tcp6 0 0 :::80 :::* LISTEN 1117/apache2  Then assume that I have another apache that have to uninstall. Then try this one:
sudo aptitude remove apache2  Then message show on terminal as like as ::
sudo: aptitude: command not found  What can i do?

---

### Post by lisati on 2012-02-22
*Thread moved to **Server Platforms**.*

---

