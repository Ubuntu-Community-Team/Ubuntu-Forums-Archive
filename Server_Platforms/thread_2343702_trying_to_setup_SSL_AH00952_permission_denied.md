---
title: "trying to setup SSL: AH00952 permission denied"
date: 2016-11-18
forum: Server Platforms
---

### Post by kyosaku on 2016-11-18
Hi there, 
 
I am trying to setup HTTPS access to a seafile server, following instructions on [https://manual.seafile.com/deploy/deploy_with_apache.html](https://manual.seafile.com/deploy/deploy_with_apache.html) & [https://manual.seafile.com/deploy/https_with_apache.html](https://manual.seafile.com/deploy/https_with_apache.html) - when I try to access my https server-address from WAN I get 
 
[TABLE="width: 90%, align: center"]
[TR]
[TD]**Quote:**[/TD]
[/TR]
[TR]
[TD="class: quote"]Service Unavailable 
The server is temporarily unable to service your 
request due to maintenance downtime or capacity 
problems. Please try again later. 
Apache/2.4.7 (Ubuntu) Server at xx.xx-xx.xx Port 443[/TD]
[/TR]
[/TABLE]
 
 
OS is Ubuntu 14.04 running via chroot/Deploy Linux on Android. 
 
SELinux is permissive & no apparmor installed. 
 
Seafile & Seahub Server/fast-cgi are running. 
 
 
apache.log file says 
[TABLE="width: 90%, align: center"]
[TR]
[TD]**Quote:**[/TD]
[/TR]
[TR]
[TD="class: quote"][Fri  Nov 11 17:38:48.627827 2016] [proxy:error] pid 12721:tid  2934961200Permission denied: AH00952: FCGI: error creating fam 2 socket  for target 127.0.0.1 
    [Fri Nov 11 17:38:48.628010 2016] [proxy:error] [pid 12721:tid  2934961200] AH00959: ap_proxy_connect_backend disabling worker for  (127.0.0.1) for 60s 
    [Fri Nov 11 17:38:48.628041 2016] [proxy_fcgi:error] [pid 12721:tid  2934961200] [client 192.168.20.21:56429] AH01079: failed to make  connection to backend: 127.0.0.1 
    [Fri Nov 11 17:38:49.208150 2016] [proxy:error] [pid 12721:tid  3044013104] AH00940: FCGI: disabled connection for (127.0.0.1)[/TD]
[/TR]
[/TABLE]
 
 
  Where to start for debugging ?  I have no experience whatsoever with Apache, but am willing to follow anyones suggestions.

---

### Post by kyosaku on 2016-11-26
Update:

changing /etc/apache2/envvars solves the problem:

change www-data > seafile

APACHE_RUN_USER=seafile
APACHE_RUN_GROUP=seafile

Seahub works with https now: but is this safe?

---

### Post by Habitual on 2016-11-27
Good job and well done!

---

