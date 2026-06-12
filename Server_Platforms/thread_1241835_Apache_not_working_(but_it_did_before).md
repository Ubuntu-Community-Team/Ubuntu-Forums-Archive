---
title: "Apache not working (but it did before)"
date: 2009-08-16
forum: Server Platforms
---

### Post by vikketorr on 2009-08-16
Have been using Apache2, php and mysql for making a wordpress theme and until recently it have been working out great but now apache seems to have broken somehow. Because when i try to access [http://localhost](http://localhost) with Firefox i get a page load error.

Have recently installed Windows 7 but seem odd if that has anything to to with this problem, but can't come up with something else that might broken apache.

sudo netstat -tulpn returns

```
Aktiva internetanslutningar (endast servrar)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      2525/mysqld     
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN      3054/hddtemp    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2424/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3543/cupsd      
tcp6       0      0 :::139                  :::*                    LISTEN      3120/smbd       
tcp6       0      0 :::22                   :::*                    LISTEN      2424/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      3543/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      3120/smbd       
udp        0      0 192.168.1.123:137       0.0.0.0:*                           3113/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           3113/nmbd       
udp        0      0 192.168.1.123:138       0.0.0.0:*                           3113/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           3113/nmbd      
```

My /etc/apache2/ports.conf:

```
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```

I've tried to restart apache but i doesn't help.

Any help, suggestions, etc. will be greatly appreciated.

Thanks,
Viktor

---

### Post by Waappu on 2009-08-16
Hi

If you type to terminal
```

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

```

does it give some errors ?

---

### Post by vikketorr on 2009-08-17
sudo /etc/init.d/apache2 start returns

```
* Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

But I'm quite sure that I had that error when apache was working as well, so I don't think it got anything to do with my problem.

---

### Post by Waappu on 2009-08-17
Hi

Check do you have file /etc/apache2/httpd.conf

If not then
```
sudo nano /etc/apache2/httpd.conf
```
and add line 
```
ServerName localhost
```
and save file ctrl+x then y and press enter

then
```
sudo /etc/init.d/apache2 restart
```
post result

---

### Post by vikketorr on 2009-08-17
Added the line to the file (the file was there but it was empty) and now there's no error from apache. But the i still can't access it through firefox :(

---

### Post by Waappu on 2009-08-17
Hi

If you go /var/log/apache2 and check file error.log
Can you see any helpful from there ?

If you type to terminal```
top
```
then press u
type www-data
can you see any running processes for apache ?


Edit:

Check that you have some site configuration on /etc/apache2/sites-available (by default there is file default)
Does that folder still exists on file system what are defined there (default is /var/www/ if I'm not wrong)

Also you could try 
1. clear FF cache and try again [http://localhost](http://localhost)
2. Try address [http://127.0.0.1](http://127.0.0.1) and [http://127.0.1.1](http://127.0.1.1)
3. Try your local are ip
Change FF preferences->advanced->settings to "no proxy" and try steps 1-3 again

---

### Post by vikketorr on 2009-08-17
Checked the error.log file and found some interesting stuff:
```
icecpp: can't open `/usr/share/slice/Murmur.ice' for reading
PHP Fatal error:  Unable to start ice module in Unknown on line 0
```
I now recall that I quite recently installed mumble-server (aka. murmur), but I removed it because i didn't need it.
I checked /usr/share/slice/Murmur.ice and the file wasn't there...

Restarted Apache and yet another entery of the same error appeared, so the problem probably got something to to with that.

And about the processes from user www-data, nope not a single process from that user.

/etc/apache2/sites-available/default still exists.

Got any suggestions?

BTW can i backup the mysql database somehow and reinstall the whole php apache mysql stack?

---

### Post by Waappu on 2009-08-17
Hi

Sorry, I do not have any idea :(
Never used php or mysql database

---

### Post by vikketorr on 2009-08-17
Got it to work :D.

This  is what i did:

First i removed the whole apache, MySQL and PHP stack with:
```
sudo apt-get remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

```
Then installed it again:
```
sudo tasksel install lamp-server
```
Cleared the browser cache and then everything worked, the database and www catalog where still intact :D

---

### Post by Waappu on 2009-08-17
Hi

Great =)
Maybe you check how backup that setup. Next time before install new features you take backup just in case.

---

### Post by linfidel on 2009-08-23
The exact thing happened to me yesterday - everything was working fine, then suddenly, Apache no longer listened.  Nothing listening on port 80, it starts with no error, nothing in the error logs that should make a difference.

I had some anomaly with MySQL around that time, but I don't see how that should make a difference, since I don't think apache depends on MySQL to run.

I'd like to figure out the solution (to me, reinstalling is a fix, not a solution - Linux is supposed to be more robust than Windows, isn't it?), and if I do, I'll post back.  But, like the OP, I don't really want to spend too much time on this stupid issue.

I just found out a new troubleshooting method, which isolated the problem.  in the apache2 server directory (/etc/apache2), there are two directories - mods-enabled and mods-available.  This controls the modules loaded by Apache; the mods-enabled one contains links to the mods-available.  So, it's easy to disable modules one-by-one, then put them back.  Since there was only one that I had messed with at all, PHP, I picked that first, and apache began working after a restart.

Now, I just have to fix PHP.  I had just gotten Smarty to work, and it may have something to do with the problem.  But I also noticed some errors loading xdebug, which I may have tried to add at some point.

Hope this helps someone.

---

### Post by ostaja on 2010-01-06
Had exaxtly same problem, solution was that PHP cant find mumble server "ice" module and because that, apache wont "work", it's starting and running, but you just cant connect to localhost etc..

So solution was to reinstall mumble server, or disable PHP as at previous post, or fix that entry on PHP.

Thx to linfidel post to find this out. :)

---

### Post by linfidel on 2010-01-07
> **ostaja said:**
> Had exaxtly same problem, solution was that PHP cant find mumble server "ice" module and because that, apache wont "work", it's starting and running, but you just cant connect to localhost etc..

So solution was to reinstall mumble server, or disable PHP as at previous post, or fix that entry on PHP.

Thx to linfidel post to find this out. :)
Glad I was helpful, and thx for letting me know. :)

---

