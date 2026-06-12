---
title: "howto dotProject 2.x with gantt in ubuntu server"
date: 2007-09-19
forum: Server Platforms
---

### Post by artfutura on 2007-09-19
How to install dotProject in Ubuntu 7.04 with gantt graphics chart support

We start with a Ubuntu LAMP server as a base, so make sure apache2, mysql and php are installed.

if in doubt or running a desktop version of ubuntu (possibly debian as well)

```
sudo apt-get install mysql-server mysql-client php5 
```

we download dotProject from

[http://sourceforge.net/projects/dotproject]("http://sourceforge.net/projects/dotproject")

move it to /var/www
and uncompress it there 

if we don´t have unzip then run

```
apt-get install unzip
```


if you want gantt graphs support

```
sudo apt-get install libphp-jpgraph libgd-tools 
```

Now we need to create a mysql user 

Run the following command:

```
mysqladmin -u root password ChooseApassword
```

and 

```
mysql -u root -p
```

(where you enter the password you chose in the previous step)

now we need to make dotProject available to apache2 so:

```
sudo chown www-data.www-data /var/www/dotproject -Rf
```

and 

```
sudo chmod 755 /var/www/dotproject  -Rf
```

time to edit php.ini to enable session autostart

```
sudo vim /etc/php5/apache2/php.ini
```

find:
```
; Initialize session on request startup.
session.auto_start = 0
```

and replace with:
```
; Initialize session on request startup.
session.auto_start = 1
```


and finally we restart apache to enable these changes

```
sudo /etc/init.d/apache2 restart
```

at this point open a web browser (firefox or opera will do)

and enter

[http://192.168.X.Y/dotproject/](http://192.168.X.Y/dotproject/)

where 192.168.X.Y is the ip address of the Ubuntu server that is going to host dotProject

follow the wizard there replacing the user user_dp with root and the password you chose earlier on.

That should be it!

login with admin and passwd

---

### Post by stunder on 2008-01-23
Thanks for the install tips... For my install it wouldn't work unless I included the php5-mysql connector. 

sudo apt-get php5-mysql

---

### Post by chan1 on 2008-03-03
Dear artfutura and stunder

Hi, I am a new user of Ubuntu and currently I am using Gutsy. I hope to explore dotproject and found (i) your steps and others (ii) at the web page on how to install the LAMP at [http://www.foogazi.com/2007/01/03/howto-setup-a-debianubuntu-lamp-server/](http://www.foogazi.com/2007/01/03/howto-setup-a-debianubuntu-lamp-server/).

1) I first set up the LAMP according to (ii) but can not open restart the apache as mentioned there. The terminal gave me a lots of error as follow:
-------------------------------
chan123@chan123-desktop:/var/www$ /etc/init.d/apache2 restart
open: Permission denied
 * Restarting web server apache2                                              [Tue Mar 04 01:54:58 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: apr_sockaddr_info_get() failed for chan123-desktop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (pid 9714?) not running
install: cannot change owner and/or group of `/var/lock/apache2': Operation not permitted
[Tue Mar 04 01:55:08 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: apr_sockaddr_info_get() failed for chan123-desktop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied
                                                                       [fail]
chan123@chan123-desktop:/var/www$ 
---------------------------------
and I suspect that there are something very wrong about the network thingy in my Ubuntu Gutsy installed in a Virtual Machine. And I forgot what is the domain name or pc name I used or did not specified during the installation of Ubuntu at the VM.

2) Then I followed steps detailed in (i). Everything went well until teh step when I tried teh command 
mysqladmin -u root password ChooseApassword
and it gave me errors as follow:
------------------------------
chan123@chan123-desktop:/var/www$ mysqladmin -u root password ChooseApassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
---------------------
followed by the command
mysql -u root -p
and it also gave me errors as follow:
--------------------
chan123@chan123-desktop:/var/www$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
--------------------

what follows next are urgly :-(

Are you guys able to help? 

Regards,
Chan

---

### Post by citybird on 2008-03-06
i fixed the localhost problem by giving the machine name in the hosts file:

```
127.0.0.1       mymachine.mydomain.com     mymachine
```

That part is simple.

---

