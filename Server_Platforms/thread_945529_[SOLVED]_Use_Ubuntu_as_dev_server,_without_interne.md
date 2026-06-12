---
title: "[SOLVED] Use Ubuntu as dev server, without internet connection"
date: 2008-10-12
forum: Server Platforms
---

### Post by scribu on 2008-10-12
Hi, I'm trying to use my box as a local development server. I am using Ubuntu Hardy and XAMPP.

I want to be able to access [http://localhost](http://localhost) in Firefox without having an internet connection available. How can I do that? Do I also have to install a local DNS server, or what?

(I have tried using LAMP or XAMPP default setups, but due to my internet connection I cannot acces localhost.)

---

### Post by cariboo on 2008-10-12
I'm not sure what your problem is, but are you saying that can connect to localhost when you're on the internet?

If you can't connect at all, then either apache2 isn't running of you have some sort of misconfiguration. to check if apache2 is running in a terminal type:

```
ps ax grep apache
```

you should get an output something like this:

```
ps ax | grep apache
 5314 ?        Ss     0:10 /usr/sbin/apache2 -k start
20341 pts/0    R+     0:00 grep apache
23579 ?        S      0:00 /usr/sbin/apache2 -k start
23580 ?        S      0:00 /usr/sbin/apache2 -k start
23581 ?        S      0:00 /usr/sbin/apache2 -k start
23582 ?        S      0:00 /usr/sbin/apache2 -k start
23583 ?        S      0:00 /usr/sbin/apache2 -k start
```

If it isn't running start apache from the management console.

Jim

---

### Post by scribu on 2008-10-12
I did

```

$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.6.8a...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

```

then

```
$ ps ax | grep apache
6510 pts/0    R+     0:00 grep apache

```

By the way, while trying to do the "LAMP Server" routine from the package manager, it stalls at "Installing mysql-server", just after it asks me to set a mysql root password.

I also can't remove residual config from mysql-server-5.0 package!

---

### Post by scribu on 2008-10-12
The XAMPP processes seem to be there:

```

$ ps ax | grep lampp
 7100 ?        Ss     0:00 /opt/lampp/bin/httpd -k start -DPHP5
 7132 ?        S      0:00 /bin/sh /opt/lampp/bin/mysqld_safe --datadir=/opt/lampp/var/mysql --pid-file=/opt/lampp/var/mysql/cristi-laptop.pid
 7135 ?        S      0:00 /opt/lampp/bin/httpd -k start -DPHP5
 7160 ?        Sl     0:00 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var/mysql --user=nobody --pid-file=/opt/lampp/var/mysql/cristi-laptop.pid --skip-external-locking --port=3306 --socket=/opt/lampp/var/mysql/mysql.sock
 7161 ?        S      0:00 /opt/lampp/bin/httpd -k start -DPHP5
 7162 ?        S      0:00 /opt/lampp/bin/httpd -k start -DPHP5
 7163 ?        S      0:00 /opt/lampp/bin/httpd -k start -DPHP5
 7164 ?        S      0:00 /opt/lampp/bin/httpd -k start -DPHP5
 7165 ?        S      0:00 /opt/lampp/bin/httpd -k start -DPHP5
 7228 pts/0    S+     0:00 grep lampp

```

I still think it has something to do with my internet connection.

---

### Post by lykwydchykyn on 2008-10-12
"localhost" resolves (thanks to /etc/hosts) to 127.0.0.1, the loopback address.  As long as "lo" is up, you should be able to hit localhost.  You can verify this with:
```

ifconfig lo

```

Can you check to see which address your apache is listening on?  This command should show you:
```

sudo netstat -tunap |grep apache

```

---

### Post by cariboo on 2008-10-13
THe left over mysql config shouldn't make any differece, as if I remember correctly Xampp is installed in /opt, including th config files, whereas a lamp servers's config files are all in /etc

If you are worried about them you could always use the purge option with apt-get or aptitude.

Jim

---

### Post by scribu on 2008-10-13
```
$ ifconfig lo
lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
$ sudo netstat -tunap |grep apache
``` (nothing, probably because I have XAMPP)

```
$ sudo netstat -tunap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      6390/mysqld     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      6392/proftpd: (acce
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5072/cupsd      
tcp        0      0 172.16.5.232:41153      208.43.202.9:80         ESTABLISHED 5846/dropboxd   
tcp       38      0 172.16.5.232:33984      67.228.78.114:443       CLOSE_WAIT  5846/dropboxd   
tcp        0      1 172.16.5.232:49704      127.0.0.1:80            SYN_SENT    6022/firefox    
tcp        0      0 172.16.5.232:52376      74.125.39.17:443        ESTABLISHED 6022/firefox    
tcp       38      0 172.16.5.232:33987      67.228.78.114:443       CLOSE_WAIT  5846/dropboxd   
tcp6       0      0 :::80                   :::*                    LISTEN      6338/httpd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           5893/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5023/avahi-daemon: 
udp        0      0 0.0.0.0:41335           0.0.0.0:*                           5023/avahi-daemon: 

```

I installed Windows XP over Ubuntu (via qEmu) and put XAMPP on it and localhost works ok.

---

### Post by lykwydchykyn on 2008-10-13
It shows up as httpd, not apache.  My mistake.  It appears to be listening, at least on ipv6.  I don't know if that will cause problems with browsers, I haven't worked much with ipv6.

I also haven't worked much with XAMPP (I prefer just to install from the repos).  Maybe you need to try to set the virtual host to 127.0.0.1 directly?

---

### Post by scribu on 2008-10-13
> **lykwydchykyn said:**
> Maybe you need to try to set the virtual host to 127.0.0.1 directly?

How do I do that?

---

### Post by lykwydchykyn on 2008-10-13
I don't use XAMPP, so I can't give you line-by-line instructions.  But in your config file, you'd change this part:
```

NameVirtualHost *:80
<VirtualHost *:80>
...

```

To this:
```

NameVirtualHost 127.0.0.1:80
<VirtualHost 127.0.0.1:80>
...

```

Though that may not help.  Have you checked your log files for errors?

---

### Post by scribu on 2008-10-13
Playing with virtual hosts doesn't help. The access_log is empty and there are only some ssl notices in the error_log. I'll upgrade to intrepid and see what happens.

---

### Post by scribu on 2008-10-14
I installed Intrepid beta - couldn's use mouse and keyboard, switched back to Hardy and localhost works now, using XAMPP for linux. Thanks to all those who tried to help.

---

