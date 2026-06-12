---
title: "Where is Apache Located?"
date: 2005-12-12
forum: Server Platforms
---

### Post by Liberteh on 2005-12-12
Hai, I just installed Apache, and WebMin.
Now WebMin gives this error while entering the Apache Directory:

The Apache server executable /etc/apache/httpd does not exist. If you have Apache installed, adjust the module configuration to use the correct path.

Does anyone know where its located when you download it via the package manager?

Many Thanks,

Liberty

---

### Post by Hube on 2005-12-12
You will find all the configuration files in /etc/apache2

Note that the httpd.conf file is deprecated, I believe that apache.conf replaces it, however httpd.conf still exists in the directory mentioned above and is referenced from apache.conf (meaning you can add stuff to httpd.conf if you really want to).

Don't know much about webmin but wonder what it's looking for and whether you can somehow fake a symbolic link or whether it has a configuration file of it's own?

---

### Post by exkalibur on 2005-12-12
When you set up the apache2 module in Webmin, you have to redirect the paths of a few files, to their correct locations. Apache2 for Debian/Ubuntu has changed certain files purposes and locations. If you need more help I'll be watching this thread for a few days. I went thru the same thing as you, not so long ago.
 
Regards

---

### Post by Liberteh on 2005-12-13
Yea, I found it, but the big problem is, I installed and compiled most of the programs that webmin uses, but they are all on other places. So I have to change all modules to the right dir's. Thats a shitty job :P

---

