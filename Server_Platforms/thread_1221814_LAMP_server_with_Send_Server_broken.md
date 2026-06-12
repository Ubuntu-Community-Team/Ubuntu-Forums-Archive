---
title: "LAMP server with Send Server broken"
date: 2009-07-24
forum: Server Platforms
---

### Post by velanse on 2009-07-24
Hello!
I had a LAMP server installed on my Ubuntu - everything worked fine!
But I decided to install Zend Server CE instead of my php. And I faced couple of problems:
1) I can not open [http://localhost](http://localhost) (or [http://127.0.0.1](http://127.0.0.1)) from my server. It's weird, But it works using a global ip from outside!!! 
2) So I'm testing my server using a outside ip - and i've got a second problem: Can't connect to local MySQL server through socket ```
'/tmp/mysql.sock'
```. Okay - I've checked all configuration data of MySQL(my.cnf) and PHP (php.ini) and the path of the socket is: ```
/var/run/mysqld/mysqld.sock
``` I have no idea why it searches socket file in tmp directory.
3) When I start using Zend Server admin panel I faced another error ```
"Failed to access Web server.  Please make sure that the Web server is running and listening to the correct port"
```Any suggestion of fixing this?

Thanx in advance!!!!!!

---

### Post by cdenley on 2009-07-24
1. What interface is your server binding to?
```
sudo netstat -tlnp
```

2. Try this (replacing your username and password).
[PHP]
<?php
$link = mysql_connect(':/var/run/mysqld/mysqld.sock', 'mysql_user', 'mysql_pass$
if (!$link) {
    die('Could not connect: ' . mysql_error());
}
echo 'Connected successfully';
mysql_close($link);
?>
[/PHP]

3. Sounds like the same problem as #1. Post this output:
```

cat /etc/apache2/ports.conf

```

---

### Post by velanse on 2009-07-24
Hoooray!!! I solved problem #1 and also #3. You was right - there was the same problem. The solution was changing /etc/network/interfaces by adding these lines: 
```
auto lo
iface lo inet loopback
```2) This code works fine and echos [COLOR=#000000][COLOR=#0000bb]Connected successfully! [/COLOR][/COLOR]still have no idea - why php sets /tmp/mysql.sock by default...

My phpinfo says this:
```
**mysql**
** MySQL Supportenabled**
 Active Persistent Links 0 
 Active Links 0
 Client API version 5.0.67
 MYSQL_MODULE_TYPE *no value*
 MYSQL_SOCKET /tmp/mysql.sock
 MYSQL_INCLUDE [I]no value
[/I] MYSQL_LIBS *no value*  

 **DirectiveLocal ValueMaster Value**
 mysql.allow_persistentOnOn
 mysql.connect_timeout6060
 mysql.default_host*no value**no value* 
 mysql.default_password*no value*[I]no value
[/I] mysql.default_port*no value*[I]no value
[/I] mysql.default_socket/var/run/mysqld/mysqld.sock/var/run/mysqld/mysqld.sock
 mysql.default_user*no value*[I]no value
[/I] mysql.max_linksUnlimitedUnlimited
 mysql.max_persistentUnlimitedUnlimited mysql.trace_modeOffOff
```[COLOR=#000000][COLOR=#0000bb]
[/COLOR][/COLOR]I tried to use a hack by creating a link-file in that tmp folder. That works but after rebooting i need to create this file again... And it does not look like a solution.

---

### Post by velanse on 2009-07-24
I wonder - where does php gets this path "/tmp/mysql.sock"...

---

