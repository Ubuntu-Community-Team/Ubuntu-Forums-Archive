---
title: "Apache2 fails to start"
date: 2008-05-29
forum: Server Platforms
---

### Post by satimis on 2008-05-29
Hi folks,


Ubuntu 6.05 drake amd64

$ sudo /etc/init.d/apache2 start```
* Starting apache 2.0 web server...                                            
(98)Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs                                           [fail]

```


$ tail /var/log/apache2/error.log ```

[Thu May 29 23:05:26 2008] [warn] RSA server certificate CommonName (CN) `SMSL' does NOT match server name!?
[Thu May 29 23:05:26 2008] [notice] Apache/2.0.55 (Ubuntu) DAV/2 SVN/1.3.1 PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Thu May 29 23:06:01 2008] [error] [client 192.168.0.10] File does not exist: /var/www/favicon.ico
[Thu May 29 23:20:15 2008] [notice] Graceful restart requested, doing restart
[Thu May 29 23:20:15 2008] [warn] RSA server certificate CommonName (CN) `SMSL' does NOT match server name!?
[Thu May 29 23:20:15 2008] [notice] Apache/2.0.55 (Ubuntu) DAV/2 SVN/1.3.1 PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Thu May 29 23:43:28 2008] [notice] Graceful restart requested, doing restart
[Thu May 29 23:43:28 2008] [warn] RSA server certificate CommonName (CN) `SMSL' does NOT match server name!?
[Thu May 29 23:43:28 2008] [notice] Apache/2.0.55 (Ubuntu) DAV/2 SVN/1.3.1 PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Thu May 29 23:58:55 2008] [notice] caught SIGTERM, shutting down

```
Please advise how to fix the problem.  TIA


B.R.
satimis

---

### Post by quelx on 2008-05-29
It's telling you some other service is already on port 80, perhaps it's apache

try ```
sudo /etc/init.d/apache2 stop
``` followed by ```
sudo killall apache2
``` then make sure no services are running on port 80 ```
sudo netstat -l|grep www
``` then (re)start apache ```
sudo /etc/init.d/apache2 restart
```

---

### Post by satimis on 2008-05-29
> **quelx said:**
> It's telling you some other service is already on port 80, perhaps it's apache

try ```
sudo /etc/init.d/apache2 stop
``` followed by ```
sudo killall apache2
``` then make sure no services are running on port 80 ```
sudo netstat -l|grep www
``` then (re)start apache ```
sudo /etc/init.d/apache2 restart
```
Thanks for your advice.


$ sudo /etc/init.d/apache2 stop```

 * Stopping apache 2.0 web server...                                         [ ok ] 

```

$ sudo killall apache2
No complaint

$ sudo netstat -l | grep www
No printout


$ sudo /etc/init.d/apache2 restart```

 * Forcing reload of apache 2.0 web server...                                       Apache/2.0.55 mod_ssl/2.0.55 (Pass Phrase Dialog)
Some of your private key files are encrypted for security reasons.
In order to read them you have to provide us with the pass phrases.

Server lampserver:443 (RSA)
Enter pass phrase:

Ok: Pass Phrase Dialog successful.
                                                                             [ ok ]

```
$ netstat -l | grep www```

tcp6       0      0 *:www                   *:*                     LISTEN     

```

It is OK now.


Previously I ran 
/etc/init.d/apache2 stop

it prompted OK.  Why it is still running?  TIA


B.R.
satimis

---

