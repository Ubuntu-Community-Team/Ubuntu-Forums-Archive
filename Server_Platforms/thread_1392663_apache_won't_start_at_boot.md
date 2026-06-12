---
title: "apache won't start at boot"
date: 2010-01-28
forum: Server Platforms
---

### Post by knichel on 2010-01-28
I just completed a fresh install and apache will not start at boot time.  It starts fine manually with apache2ctl start 

I tried sudo update-rc.d apache2 defaults but no joy.

If you can help, please do.

--
Mike

---

### Post by kamaji792 on 2010-01-28
> I tried sudo update-rc.d apache2 defaults but no joy.

[s]The start command you are using looks like it is for a Red Hat based system.[/s] [edit]Obviously a load of rubbish, will try and pay more attention in the future[/edit]

Try:
```
sudo /etc/init.d/apache2 start
```

That would be good to check because if that does not work then I don't think it will run at boot.

If that does work I am at a loss as to why it will not start at boot.

[edit]
A quick scan around and I found this:
```
sudo update-rc.d <file name> defaults
```

So assuming my original suggestion worked:
```
sudo update-rd.d /etc/init.d/apache2 defaults
```

Also check **man update-rd.d**.

And [www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

All the best

---

### Post by lykwydchykyn on 2010-01-29
The output from these commands would be most helpful in diagnosing the problem:

```

ls /etc/rc$(runlevel|cut -d " " -f 2).d |grep apache

sudo tail /var/log/apache2/error.log

/etc/init.d/apache2 restart

```

---

### Post by knichel on 2010-01-29
OK, here goes...
ls /etc/rc$(runlevel|cut -d " " -f 2).d | grep apache
```

S91apache2

```
sudo tail /var/log/apache2/error.log
```

[Thu Jan 28 11:31:52 2010] [warn] RSA server certificate CommonName (CN) `q3ait.org' does NOT match server name!?
[Thu Jan 28 11:31:52 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g configured -- resuming normal operations
[Thu Jan 28 11:38:23 2010] [notice] caught SIGWINCH, shutting down gracefully
[Thu Jan 28 11:38:33 2010] [warn] RSA server certificate CommonName (CN) `q3ait.org' does NOT match server name!?
[Thu Jan 28 11:38:33 2010] [warn] RSA server certificate CommonName (CN) `q3ait.org' does NOT match server name!?
[Thu Jan 28 11:38:33 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g configured -- resuming normal operations
[Thu Jan 28 15:46:59 2010] [error] [client 66.249.71.22] File does not exist: /var/www/robots.txt
[Thu Jan 28 23:17:44 2010] [error] [client 208.76.172.54] script '/var/www/mirror.php' not found or unable to stat
[Fri Jan 29 00:35:14 2010] [error] [client 61.183.15.9] script '/var/www/prx2.php' not found or unable to stat
[Fri Jan 29 01:47:12 2010] [error] [client 66.249.71.117] File does not exist: /var/www-ssl/robots.txt

```
/etc/init.d/apache2 restart
```

 * Restarting web server apache2                                                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 5723?) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                                                                                                        [fail]

```
Iam not sure if you wanted me to use sudo, so here goes w/ sudo...
sudo /etc/init.d/apache2 restart
```
 * Restarting web server apache2 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                                                        [ OK ]

```

So, one thing I noticed was the warnings about the SSL certificate.  I am not an expert with SSL by any means, but it seems I need to re-install the Cert?

Thanks in advance for the assistance.

---

### Post by lykwydchykyn on 2010-01-30
> **knichel said:**
> OK, here goes...
ls /etc/rc$(runlevel|cut -d " " -f 2).d | grep apache
```

S91apache2

```

That's as it should be
> 
sudo tail /var/log/apache2/error.log
```

[Thu Jan 28 11:31:52 2010] [warn] RSA server certificate CommonName (CN) `q3ait.org' does NOT match server name!?
[Thu Jan 28 11:31:52 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g configured -- resuming normal operations
[Thu Jan 28 11:38:23 2010] [notice] caught SIGWINCH, shutting down gracefully
[Thu Jan 28 11:38:33 2010] [warn] RSA server certificate CommonName (CN) `q3ait.org' does NOT match server name!?
[Thu Jan 28 11:38:33 2010] [warn] RSA server certificate CommonName (CN) `q3ait.org' does NOT match server name!?
[Thu Jan 28 11:38:33 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g configured -- resuming normal operations
[Thu Jan 28 15:46:59 2010] [error] [client 66.249.71.22] File does not exist: /var/www/robots.txt
[Thu Jan 28 23:17:44 2010] [error] [client 208.76.172.54] script '/var/www/mirror.php' not found or unable to stat
[Fri Jan 29 00:35:14 2010] [error] [client 61.183.15.9] script '/var/www/prx2.php' not found or unable to stat
[Fri Jan 29 01:47:12 2010] [error] [client 66.249.71.117] File does not exist: /var/www-ssl/robots.txt

```

How long after you rebooted the machine was this run?  Sorry, I should have said to run that one RIGHT AFTER restarting, so we can maybe find the error it's failing on.
> 
/etc/init.d/apache2 restart
```

 * Restarting web server apache2                                                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 5723?) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                                                                                                        [fail]

```
Iam not sure if you wanted me to use sudo, so here goes w/ sudo...

Yeah sorry, I forget that bit sometimes.  Ignore those errors.
> 
sudo /etc/init.d/apache2 restart
```
 * Restarting web server apache2 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                                                        [ OK ]

```

That's as it should be.
> 
So, one thing I noticed was the warnings about the SSL certificate.  I am not an expert with SSL by any means, but it seems I need to re-install the Cert?

Thanks in advance for the assistance.

I don't know what those mean, but you probably want to look into it.  I doubt it's what's stopping it from starting on boot, because I would think it would also stop you from starting it manually.

Does your certificate use a passphrase?  I mean, if you restart it manually you don't need to enter a passphrase do you?

---

### Post by knichel on 2010-01-30
Well,
I did a sudo apt-get --reinstall install apache2 and now it starts on reboot.  Thanks for your help.

---

