---
title: "Setting up Apache in 10.10"
date: 2010-12-07
forum: Server Platforms
---

### Post by ingeva on 2010-12-07
When starting Apache I get this error in 10.10 (not in 9.10):

[Fri Dec 03 21:14:22 2010] [error] (2)No such file or directory: could not open transfer log file /etc/apache2/${APACHE_LOG_DIR}/other_vhosts_access.log.
Unable to open logs

So where do I define APACHE_LOG_DIR ?

---

### Post by windependence on 2010-12-07
By default, the server writes the transfer log to the file /var/log/apache2/access.log. You can change this on a per-site basis in your virtual host configuration files with the *CustomLog* directive, or omit it to accept the default, specified in /etc/apache2/apache2.conf. You may also specify the file to which errors are logged, via the *ErrorLog* directive, whose default is /var/log/apache2/error.log. These are kept separate from the transfer logs to aid in troubleshooting problems with your Apache2 server. You may also specify the *LogLevel* (the default value is "warn") and the *LogFormat* (see /etc/apache2/apache2.conf for the default value). 
 
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)
 
You may want to check to see if the log exists and if it does, check ownership and permissiions.
 
-Tim

---

### Post by windependence on 2010-12-07
May also want to try adding a line in /etc/apache2/envvars:
export APACHE_LOG_DIR=/var/log/apache2
 
 
-Tim

---

### Post by ingeva on 2010-12-07
> **windependence said:**
> May also want to try adding a line in /etc/apache2/envvars:
export APACHE_LOG_DIR=/var/log/apache2
 -Tim
THAT WORKED!  Thank you!

I must have modified the file somehow, because the
first time I loaded Apache it worked just fine! :)

inge

---

### Post by windependence on 2010-12-07
Your welcome! :-)
 
-Tim

---

