---
title: "Apache won't stop"
date: 2008-05-06
forum: Server Platforms
---

### Post by Colhost on 2008-05-06
Hey,

I'm creating an adminpanel for my Ubuntu Server. At the moment I'm busy making a PHP script to start, stop and restart services on this server. It works fine, except for Apache.

After a reboot I can use my script to stop and start Apache 1 time. If I want to stop Apache again, it won't react on anything. I can't stop it with my script, I can't stop it with Webmin and in the shell it doesn't work neither. But Apache keeps on running.

If I use the shell after rebooting, it just works fine with the same shell-commands (/etc/init.d/apache2 start/stop/restart) as I used in my script.

This is the Apache-part of my script```
$server = $_GET['server'];
$action = $_GET['action'];

switch($server)
{
case HTTP:

$response = shell_exec("sudo /etc/init.d/apache2 ".$action."");
echo $response;
break;
```

Can anyone tell me why Apache is acting this strange? Thanks :D

Edit: I'm using Apache 2.2.4 on Ubuntu Server 7.10

---

### Post by windependence on 2008-05-06
Have you tried apachectl stop?

-Tim

---

### Post by Colhost on 2008-05-06
Won't work at all. ```
-bash: apachectl: command not found
```
apache2ctl stop does work, but does not stop Apache.

---

### Post by windependence on 2008-05-06
> **Colhost said:**
> Won't work at all. ```
-bash: apachectl: command not found
```
apache2ctl stop does work, but does not stop Apache.

Yep, sorry, I forgot you were using Apache 2. 

-Tim

---

