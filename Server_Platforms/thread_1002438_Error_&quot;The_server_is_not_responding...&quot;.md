---
title: "Error &quot;The server is not responding...&quot;???"
date: 2008-12-05
forum: Server Platforms
---

### Post by quangtrung1789 on 2008-12-05
I have just installed Lamp on ubuntu, but when i go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin), i meet a error is "The server is not responding..."
Can you help me???:confused:

---

### Post by utnubuuser on 2008-12-05
have you tried > sudo /etc/init.d/apache2 restart

---

### Post by quangtrung1789 on 2008-12-05
> **utnubuuser said:**
> have you tried

oh, this is the result:

> * Restarting web server apache2                                                .: 197: Can't open /etc/apache2/envvars
ERROR: APACHE_PID_FILE needs to be defined in /etc/apache2/envvars
apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory


---

### Post by utnubuuser on 2008-12-05
have you actually gotten to use this server since you installed it? And if not, have you tried just re-installing,  sometimes that's the quickest fix.

---

### Post by quangtrung1789 on 2008-12-05
> **utnubuuser said:**
> have you actually gotten to use this server since you installed it? And if not, have you tried just re-installing,  sometimes that's the quickest fix.

ok, i have re-installed xampp. But it still has that error:confused:

---

### Post by lykwydchykyn on 2008-12-05
> **quangtrung1789 said:**
> ok, i have re-installed xampp. But it still has that error:confused:

OK, just FYI... if you're installing xampp, please say you're using xampp and don't just say "LAMP".  LAMP is a generic acronym for Linux Apache MySQL and PHP (with variations, yes).  If you just say "i've installed LAMP" everyone will assume you installed apache, mysql, and php out of the repositories and try to troubleshoot from that angle. 

xampp is a specific bundled version of all this stuff.  The commands and file locations are different.

Try /opt/lampp/lampp_stop && /opt/lampp/lampp_start

---

