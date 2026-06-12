---
title: "PHP: Call to undefined function mysql_connect()"
date: 2008-10-13
forum: Server Platforms
---

### Post by Jesdisciple on 2008-10-13
I'm supposed to have a LAMP stack installed from the repository, but the PHP package apparently wasn't compiled [--with-mysql]("http://www.php.net/manual/en/mysql.installation.php").  Is compiling PHP myself the only way to fix this?```
<?php
mysql_connect('localhost', 'root', 'abc123') or die(mysql_error());
?>
```

> **Fatal error:** Call to undefined function mysql_connect() in **/home/chris/www/projects/testConnection/testConnection.php** on line **2**

Thanks!

---

### Post by lykwydchykyn on 2008-10-13
If you have the php5-mysql package installed, it should work.  You shouldn't need to compile anything.

See if you have it installed:
```

sudo aptitude install php5-mysql

```

---

### Post by Jesdisciple on 2008-10-13
No, it wasn't installed.  But I'm apparently still not using that package because I still get the error.```
$ sudo netstat -atp
[sudo] password for chris: 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      5191/mysqld     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      5349/smbd       
tcp        0      0 localhost:ipp           *:*                     LISTEN      5113/cupsd      
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      5349/smbd       
tcp        0      0 Jesdisciple-lapto:56079 ag-in-f19.google.co:www ESTABLISHED 27995/firefox   
tcp        0      0 Jesdisciple-lapto:50423 an-in-f18.google.co:www ESTABLISHED 27995/firefox   
tcp6       0      0 [::]:8009               [::]:*                  LISTEN      5843/jsvc       
tcp6       0      0 [::]:www                [::]:*                  LISTEN      5876/apache2    
tcp6       0      0 [::]:8180               [::]:*                  LISTEN      5843/jsvc       
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      5040/sshd       
```

---

### Post by cdenley on 2008-10-13
```

sudo /etc/init.d/apache2 restart

```

---

### Post by Jesdisciple on 2008-10-13
That did it.  Thanks!  (Maybe if I see these commands enough I'll start to use them on my own.)

---

