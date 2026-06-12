---
title: "lighttpd + php5 + mysql"
date: 2006-06-19
forum: Server Platforms
---

### Post by starmonkey on 2006-06-19
Hey fellahs,

I'm currently running lighttpd (from synaptic) + php5, which I compiled from source as fast-cgi. MySQL was installed via synaptic also. For mysql support in php, I need the mysql headers, but I kinda fudged it and compiled against mysql-standard-5.0.22-linux-i686-glibc23 source that I downloaded from mysql's site. 

```
./configure --prefix=/usr/lib/php5 --enable-fastcgi --enable-force-cgi-redirect \
--with-mysql=/home/blah/files/mysql-standard-5.0.22-linux-i686-glibc23 \
--with-mysql-sock=/var/run/mysqld/mysqld.sock \
--with-pdo-mysql=/home/blah/files/mysql-standard-5.0.22-linux-i686-glibc23 \
--with-zlib --with-gd --with-pear \
--with-curl
```

This seems to work fine for phpMyAdmin (tested this morning against MySQL - 5.0.22-Debian_0ubuntu6.06-log) but bombs out on a web-application that I'm running. Lighttpd's error log reports the following:

```
2006-06-20 12:11:59: (mod_fastcgi.c.2430) unexpected end-of-file (perhaps the fastcgi process died): pid: 4536 socket: unix:/tmp/php5-fastcgi.socket-3
2006-06-20 12:11:59: (mod_fastcgi.c.3215) response not received, request sent: 913 on socket: unix:/tmp/php5-fastcgi.socket-3 for /path/to/webapp/index.php , closing connection
```

The php error log shows nothing. 

I read [lighttpd's fastcgi troubleshooting docco]("http://www.lighttpd.net/documentation/fastcgi.html#troubleshooting") but it didn't really enlighten me. I'm getting lighttpd to spawn the php children internally.

I deduce that my dodgy method of compiling mysql support into php5 is to blame - but in turn I blame synaptic for not having a mysql-dev or mysql-server-dev package that will give me the header files!!!!!

So - am I blind? What's the best way to handle this kind of thing? I don't want to use apache/php from syn - I want to use lighttpd.

cheers,
sm

---

### Post by starmonkey on 2006-06-24
*bump* any tips on working out what's causing php to crash? note that php doesn't always crash, but it _always_ crashes on one particular webapp (that's using PDO/MySQL) - I found the line that it crashes on:

[PHP]
/**
 * open the connection, or bomb out :)
 */
function connectDB() {
	try {
		$this->dbh = new PDO('mysql:host='.$this->cfg['db_host'].';dbname='.$this->cfg['db_name'], 
									$this->cfg['db_user'], 
									$this->cfg['db_pass']);
		$this->dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);	
                // crashes here
		$this->dbh->setAttribute(PDO::MYSQL_ATTR_USE_BUFFERED_QUERY, TRUE);
	} catch(PDOException $e) {
		print "<div class=\"error\">Error: " . $e->getMessage() . "</div>";
		die();
	}
}
[/PHP]

Note that the line before is fine:

[PHP]$this->dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);[/PHP]

Note that this webapp works fine on my win32 machine with MySQL 4.1.14-nt and Apache/1.3.34 (Win32) PHP/5.1.2 It also runs on a linux box with 5.1.4-pl0-gentoo and MySQL - 4.0.27 with no errors.

Should I install mysql from source instead and compile php against its headers?

thanks,
SM

---

