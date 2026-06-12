---
title: "PHPMyAdmin Not Loading on my Domain"
date: 2006-07-23
forum: Server Platforms
---

### Post by jscrilla on 2006-07-23
I just reinstalled my server, with the server only install, as I'm fairly comfortable in the terminal window now. I'm having trouble though. I've set up my virtual host and that shows up and all remotely in a web browser. I've installed PHP4 and Mysql as well, but cannot access PHPMYADMIN from my browser window. It worked perfectly on my old install, but now I only see a page does not exist error message. 

What am I not doing right to get this to view? Any help would be much appreciated.

---

### Post by jscrilla on 2006-07-23
I fixed it...i had conflicting virtual host entries. one in httpd.conf and the other as the site enabled file under /etc/apache2/sites-enabled. I removed the httpd.conf references and everything works now.

---

