---
title: "Cannot manage to get apache2 listening to port 8082"
date: 2016-12-15
forum: Server Platforms
---

### Post by anthony-tb on 2016-12-15
Hi everyone,
I am having issues trying to get apache to listen on port 8082, when I set apache to listen to 80 and 8082 it redirect to port 80 (which won't work for my purpose). When I set apache to listen only to 8082 then my website doesn't work at all.
Any idea? also my ubuntu firewall is disabled right now for troubleshooting purpose

Here are a few config file samples:
**Ports.conf:**
Listen 8082

**Sites-enabled 000-default.conf:**
<VirtualHost *:8082>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName landlordexchange.ca


        ServerAdmin [email]anthony.tb@gmail.com[/email]
        DocumentRoot /var/www/html


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
[B]

Sites-available 000-default.conf:
[/B]<VirtualHost *:8082>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName landlordexchange.ca


        ServerAdmin [email]anthony.tb@gmail.com[/email]
        DocumentRoot /var/www/html


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

---

### Post by darkod on 2016-12-15
When you are saying it doesn't work with 8082 you are adding :8082 at the end of the url when trying the site right?
To check if apache is correctly listening on 8082 try:
```
sudo netstat -plunt
```

---

### Post by anthony-tb on 2016-12-15
Yes correct i'm adding :8082 at the end of the url, if i'm listening to both 80 and 8082 then then my browser removes the :8082 and it works, if i'm listening only to 8082 then it just doesn't work

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1337/mysqld
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      1678/master
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      1364/dovecot
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      1364/dovecot
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1725/perl
tcp        0      0 192.168.1.60:53         0.0.0.0:*               LISTEN      1309/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1309/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1307/sshd
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      1193/postgres
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1678/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1309/named
tcp        0      0 0.0.0.0:20000           0.0.0.0:*               LISTEN      1723/perl
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      1548/python
tcp6       0      0 :::587                  :::*                    LISTEN      1678/master
tcp6       0      0 :::110                  :::*                    LISTEN      1364/dovecot
tcp6       0      0 :::143                  :::*                    LISTEN      1364/dovecot
tcp6       0      0 :::10000                :::*                    LISTEN      1725/perl
tcp6       0      0 :::8082                 :::*                    LISTEN      1521/apache2
tcp6       0      0 :::21                   :::*                    LISTEN      1800/proftpd: (acce
tcp6       0      0 :::53                   :::*                    LISTEN      1309/named
tcp6       0      0 :::22                   :::*                    LISTEN      1307/sshd
tcp6       0      0 ::1:5432                :::*                    LISTEN      1193/postgres
tcp6       0      0 :::25                   :::*                    LISTEN      1678/master
tcp6       0      0 ::1:953                 :::*                    LISTEN      1309/named
tcp6       0      0 :::443                  :::*                    LISTEN      1521/apache2
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           1725/perl
udp        0      0 0.0.0.0:20000           0.0.0.0:*                           1723/perl
udp        0      0 192.168.1.60:53         0.0.0.0:*                           1309/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1309/named
udp6       0      0 :::53                   :::*                                1309/named
```

---

### Post by SeijiSensei on 2016-12-15
According that result, Apache is only listening on port 8082 for IPv6.  I don't use IPv6 at all, so I can't tell why that would be.

---

### Post by darkod on 2016-12-15
Please post file content and output inside CODE tags. It keeps the formatting better.

From the above it looks configured correctly and apache is listening on 8082. If you try it from a computer on the same network http://<serverIP>:8082 what does it say? Post the exact error message pls. Also check the apache error.log in /var/log/apache2 on the server. It might give you more info.

---

### Post by darkod on 2016-12-15
> **SeijiSensei said:**
> According that result, Apache is only listening on port 8082 for IPv6.  I don't use IPv6 at all, so I can't tell why that would be.

I wasn't sure if that's correct myself so I checked one server and it says the same in netstat but I know for sure it works for ipv4 too. So that should not be an issue.

---

### Post by anthony-tb on 2016-12-15
So the error I get when I try to access it from chrome using [http://192.168.1.60:8082](http://192.168.1.60:8082) is [COLOR=#696969][FONT=&quot]ERR_CONNECTION_REFUSED[/FONT][/COLOR]

---

### Post by anthony-tb on 2016-12-15
[IMG]http://i1148.photobucket.com/albums/o574/Anthony_Therrien_Bernard/Capture_zpselngq6c6.png[/IMG]

---

### Post by Graham_Willis on 2016-12-15
What's the result of **telnet 127.0.0.1 8082** from the server itself? I'd also recommend that you try to reload Apache and check then, if it hasn't already been done. The logs that you showed were generated by attempts to reach 192.168.1.60:8082? And you can grep Apache configuration files for strings '80' and 'ports', perhaps it'll bring something useful. I have just switched Apache to listen on the port 8082 and it works fine, although I tried to connect to it only from the machine on which it's running.

Well, and I just noticed that it returns 301.... do you indeed have a redirection? If yes, try removing it and check if it changes something.

---

### Post by anthony-tb on 2016-12-15
Correct these logs were generated from 192.168.1.50 (client) trying to reach 192.168.1.60(server). I don't think I have a redirection setup, I have not setup one anyway.

```

anthony@linux-server:~$ telnet 127.0.0.1
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
anthony@linux-server:~$ telnet 127.0.0.1:8082
telnet: could not resolve 127.0.0.1:8082/telnet: Name or service not known
anthony@linux-server:~$

```

---

### Post by Graham_Willis on 2016-12-15
It's not how you should connect to the machine using telnet. Use:

[B]telnet 127.0.0.1 8082
[/B]
as I explicitly wrote earlier, not

[COLOR=#ff0000]**telnet 127.0.0.1:8082**[/COLOR]

---

### Post by anthony-tb on 2016-12-16
I apologize for the missread, I used telnet 127.0.0.1 8082 now and it worked
```

anthony@linux-server:~$ telnet 127.0.0.1 8082
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

```

---

### Post by Graham_Willis on 2016-12-16
OK, install **links** browser on the server, and open your site using it (links 127.0.0.1). Check if it looks reasonably. If yes, the best way to proceed'd be to compare the raw outputs of the three connections (from the server to 127.0.0.1, from the server to 192.168.1.60, from the second machine to 192.168.1.60) - it can reveal valuable information.

If the page doesn't look reasonably, it can mean that there's something bad about the page itself.

In any case, please report back what you established.

---

### Post by anthony-tb on 2016-12-16
I get a connection refused error using: links 127.0.0.1:8082

---

### Post by darkod on 2016-12-16
Hmmm it seems it is refusing connections. Did you perform any type of security setup or similar? Is the apache config the standard?

What you can also try is leave the Listen 80 in ports.conf but configure 8082 for the specific website in it's .conf file in sites-available. Then restart apache. I think it allows the general port to be 80 but websites to have specific port binding different from 80.

---

### Post by anthony-tb on 2016-12-16
No I even disabled the firewall as of right now. I've tried to leave apache listening on port 80 but somehow when I do this it redirect from 8082 to port 80

---

### Post by darkod on 2016-12-17
Just to confirm, you did modify 000-default.conf in sites-available and restarted apache service after that right?

Is this a default apache installation or you already did many modifications? Because except for port modifications I can't see any major changes in the files you posted in your first post. In such case if you can't make it to work I suggest purging apache (to delete the config files too) and reinstalling it again.

But before that try the following one last time:
1. In /etc/apache2/ports.conf there should be lines like
Listen 80 (for the http traffic)
Listen 443 (for the https traffic)

2. In /etc/apache2/sites-available/000-default.conf on the top there should be lines like
Listen 8082
<VirtualHost *:8082>

3. Restart apache
```
sudo systemctl restart apache2.service   (if this is 16.04 LTS)
sudo service apache2 restart (for 14.04 LTS or earlier)
```

4. Check listening ports
```
sudo netstat -plunt | grep apache
```

5. Check from browser on the same LAN http://<serverIP>:8082

If that still doesn't work, purge and reinstall apache if there is nothing important to lose in the current configuration.

PS. You mentioned disabling the firewall but you also mentioned the server has a private LAN IP. Why do you need a firewall at all???

---

### Post by Graham_Willis on 2016-12-17
**anthony-tb, PLEASE DO NOT REMOVE APACHE YET! IT SEEMS THAT THERE'S SOMETHING WEIRD GOING ON AND IT'S BETTER KNOW WHAT.**

Just to be sure: you issued links 127.0.0.1 from the server itself, yes? If nothing changed up to that moment from the time when you logged in to the port 8082 using telnet, there's something weird going on. Please return the configuration in which the port 8082 is specified in both files ports.conf and 000-default.conf. Then restart apache and do the following (on the server, of course) - replace ZZZZ with HTTP, I typed ZZZZ due to the forum posting issues:

netstat -av | grep 8082
telnet 127.0.0.1 8082
GET / ZZZZ/1.1<ENTER><ENTER>
Host: 127.0.0.1<ENTER>

Then quit telnet with Ctrl-] and:

netstat -av | grep 8082 (must be issued reasonably fast after quitting the previous telnet session, let's say within a minute)
telnet 127.0.0.1 8082
GET / ZZZZ/1.1<ENTER><ENTER>
Host: localhost<ENTER>

Quit telnet as above.

netstat -av | grep 8082
telnet 127.0.0.1 8082
GET / ZZZZ/1.1<ENTER><ENTER>

Quit telnet once again.

Copy all the output and save it, issue links 127.0.0.1:8082 again and issue links localhost:8082.
Then please provide us with output of all of this commands and report what links returned. 
Also, please post the output of **apachectl -V** and Apache's error.log.
If you can, please also put the contents of your index.html or index.php document.

If you go for purging and reinstalling apache, please at lease save all the current configuration files and compare them once you make things work correctly so you'd know what was causing the problem and we could learn something. 

From what I can say, it looks a bit as you perhaps have a kind of interference on the port 8082. Have you something listening on it earlier? If yes, reboot can help.

@darkod: 
> 
Hmmm it seems it is refusing connections. Did you perform any type of security setup or similar? Is the apache config the standard?


But note that he said that he was able to log in to the port 8082 using telnet. There's something deeper than just simple connection refusal.

> 
PS. You mentioned disabling the firewall but you also mentioned the server has a private LAN IP. Why do you need a firewall at all???


I don't get you (taking the three question marks into account). It's perfectly conceivable that one has a private network and yet doesn't want to grant all the computers within that network constraints full access to the other ones (especially servers). In fact it's much more likely that such a configuration's desired than that it isn't.

---

### Post by darkod on 2016-12-17
Rereading the whole thread I think it might be best to take a step back... Your question was directly for apache port and we all started looking into that specifically. But seeing that you have many other roles on this server (mail, DB, DNS, etc), it would be nice if you explain to us what this server is being used for, and how it was deployed. For example, there are online tutorials and scripts that "install" all those roles for you, and the server works in specific designed way, so changing ports might not be supported. It makes a difference if you installed mail, db, dns, apache one by one by hand, or were using some sort of script/tutorial...

Also please show us the content of /etc/apache2/sites-available and /etc/apache2/sites-enabled. If you have another site in there that is the primary, changing options on 000-default.conf is not really necessary.

Is the server on a home LAN, or business LAN?

---

### Post by anthony-tb on 2016-12-17
Yes I did restarted the apache service after. So I tried again to put listen 80 in prots.conf and the proper 8082 port config in sites-available and all it does is I can access the site with :8082 but it still redirects to port 80
Here is the output of netstat:
```

anthony@linux-server:/etc/apache2/sites-available$ sudo netstat -plunt | grep apache
tcp6       0      0 :::8082                 :::*                    LISTEN      25214/apache2
tcp6       0      0 :::443                  :::*                    LISTEN      25214/apache2

```


> **darkod said:**
> Just to confirm, you did modify 000-default.conf in sites-available and restarted apache service after that right?

Is this a default apache installation or you already did many modifications? Because except for port modifications I can't see any major changes in the files you posted in your first post. In such case if you can't make it to work I suggest purging apache (to delete the config files too) and reinstalling it again.

But before that try the following one last time:
1. In /etc/apache2/ports.conf there should be lines like
Listen 80 (for the http traffic)
Listen 443 (for the https traffic)

2. In /etc/apache2/sites-available/000-default.conf on the top there should be lines like
Listen 8082
<VirtualHost *:8082>

3. Restart apache
```
sudo systemctl restart apache2.service   (if this is 16.04 LTS)
sudo service apache2 restart (for 14.04 LTS or earlier)
```

4. Check listening ports
```
sudo netstat -plunt | grep apache
```

5. Check from browser on the same LAN http://<serverIP>:8082

If that still doesn't work, purge and reinstall apache if there is nothing important to lose in the current configuration.

PS. You mentioned disabling the firewall but you also mentioned the server has a private LAN IP. Why do you need a firewall at all???

---

### Post by anthony-tb on 2016-12-17
This server has an SSH server and the LAMP package and that's about it (and now ajenti but the problem started before). It's used for a wordpress site, I didn't use a script for apache but just used the lamp install instructions using apt-get install.
Output of sites-available:
```

anthony@linux-server:/etc/apache2/sites-available$ ls
000-default.conf  default-ssl.conf

```
Sites enabled:
```

anthony@linux-server:/etc/apache2/sites-enabled$ ls
000-default.conf

```




> **darkod said:**
> Rereading the whole thread I think it might be best to take a step back... Your question was directly for apache port and we all started looking into that specifically. But seeing that you have many other roles on this server (mail, DB, DNS, etc), it would be nice if you explain to us what this server is being used for, and how it was deployed. For example, there are online tutorials and scripts that "install" all those roles for you, and the server works in specific designed way, so changing ports might not be supported. It makes a difference if you installed mail, db, dns, apache one by one by hand, or were using some sort of script/tutorial...

Also please show us the content of /etc/apache2/sites-available and /etc/apache2/sites-enabled. If you have another site in there that is the primary, changing options on 000-default.conf is not really necessary.

Is the server on a home LAN, or business LAN?

---

### Post by Graham_Willis on 2016-12-17
> **"anthony-tb"]**It's used for a wordpress site**[/quote][COLOR=#000000]
[/COLOR]Ah, OK, all of that makes perfect sense now. You won't make WordPress work on non-default Apache ports so easily.

The source of the problem:

[http://marvintam.com/2009/05/wordpress-on-localhost-port-number/](http://marvintam.com/2009/05/wordpress-on-localhost-port-number/) :

> On a new WordPress installation, if I hit [http://localhost:8080/](http://localhost:8080/) on a browser, I will get a HTTP 301 redirect to [http://localhost/](http://localhost/) (sans port number) because of the built-in Canonical URLs feature.

The solution to the problem:

[https://wordpress.org/support/topic/localhost8080-this-page-cant-be-displayed/](https://wordpress.org/support/topic/localhost8080-this-page-cant-be-displayed/)

[quote][FONT=&amp]Using WAMP&#8217 said:**
> http://localhost:8080[FONT=&amp]Once that is done, you will be able to log into the dashboard. Once there, install and run this plugin to update the rest of the site&#8217;s URLs:[/FONT]
[FONT=&amp][https://wordpress.org/plugins/better-search-replace](https://wordpress.org/plugins/better-search-replace)[/FONT]
[FONT=&amp]After that is done, go to Settings > Permalinks and just click &#8216;Save&#8217;; this rebuilds the .htaccess file for the site.[/FONT]

---

### Post by anthony-tb on 2017-01-30
I am very sorry for the extremely late reply but things have been very busy for me lately. Thank you very much this worked like a charm!

> **Graham_Willis said:**
> [COLOR=#000000]
[/COLOR]Ah, OK, all of that makes perfect sense now. You won't make WordPress work on non-default Apache ports so easily.

The source of the problem:

[http://marvintam.com/2009/05/wordpress-on-localhost-port-number/](http://marvintam.com/2009/05/wordpress-on-localhost-port-number/) :



The solution to the problem:

[https://wordpress.org/support/topic/localhost8080-this-page-cant-be-displayed/](https://wordpress.org/support/topic/localhost8080-this-page-cant-be-displayed/)

---

### Post by darkod on 2017-01-31
If you are happy with the solution please mark the thread as solved. You can do that in Thread Tools above the first post.

---

