---
title: "Apache/MultiDomains/SingleIP/Vhost nightmare"
date: 2008-05-02
forum: Server Platforms
---

### Post by digitalfrog on 2008-05-02
Okay, I'm loosing sleep on this one.

- I'm hosting my webserver at home, and I have a dedicated IP address from my provider. 
- I have 3 domains registered (2 from one provider, the last one from another).
- all 3 domains point to the same IP address, NAT'd to my webserver.

Without virtualhosts, all domains work ok and can access a same webpage.

I've been playing with virtual hosts configuration and it somewhat works:

domain a.nl works ok -> points to content for a.nl (with or without www prefix)
domain b.info works ok -> points to content for b.info (with or without www prefix)
domain c.com does not work as planned:
     [www.c.com](www.c.com) points to a.nl
     c.com points to b.info 

This is driving me crazy, I ended up with the most minimalistic vhosts file I could think off, and the 10's of changes I've made lead to the same result.

The log files for c.com are always empty, which makes me think that apache never receives the info for that domain. 

Any help is welcome.

I have 3 files, one for each domain:

<VirtualHost 192.168.1.8:80>
        ServerAdmin [email]digitalfrog@gmail.com[/email]
        ServerName [www.domainX.com](www.domainX.com)
        ServerAlias *.domainX.com
        DocumentRoot /var/www/domainX
</VirtualHost>

        ErrorLog /var/log/apache2/DomainX.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog /var/log/apache2/DomainX_access.log combined


hostname -a gives me all the alternatives FQDN (c.com [www.c.com](www.c.com) a.nl [www.a.nl](www.a.nl) etc....)

Help :-) !

---

### Post by windependence on 2008-05-02
I'm pretty sure your vhost IP does not need the port number after it.

Your vhost file is way bigger than it needs to be to get it working. Have you looked at the expamples on apache.org? There is a great Wiki here:
[http://wiki.apache.org/httpd/](http://wiki.apache.org/httpd/)

Don't quote me but I think your vhost section can be as lean as this:

<VirtualHost *>
  ServerName [www.example.net](www.example.net)
  ServerAlias example.net
  DocumentRoot /var/www/example
</VirtualHost>

-Tim

---

### Post by digitalfrog on 2008-05-02
Hi Tim, thanks for your reply.

I indeed tried the minimalistic apache wiki suggestion, also using wildcard rather than ip:80, same result.

It does work for 2 domains, not the 3d one. So I guess there must be something else around that makes that apache never get's the right domain info for that last domain and even not getting a chance to call the related vhost config file.

---

### Post by windependence on 2008-05-03
> **digitalfrog said:**
> Hi Tim, thanks for your reply.

I indeed tried the minimalistic apache wiki suggestion, also using wildcard rather than ip:80, same result.

It does work for 2 domains, not the 3d one. So I guess there must be something else around that makes that apache never get's the right domain info for that last domain and even not getting a chance to call the related vhost config file.

I just noticed Apache 2 is much different than what I am used to. I run my sites on 1.3 on FreeBSD.

Look at this:

[http://wiki.apache.org/httpd/DebianLikePlatform](http://wiki.apache.org/httpd/DebianLikePlatform)

Looks like you have to enable the vhosts like a kernel module kinda. I have never done one this way, always used vhost files which I believe is still supported but is deprecated.

-Tim

---

### Post by digitalfrog on 2008-05-03
Oh, I did not know about this.

I tested it, and guess what... same results :-(

---

### Post by andguent on 2008-05-03
I have a 2 site minimalistic setup that appears to do what you want. Maybe I'm missing something about your problem though.

head /etc/apache2/sites-enabled/*
```
==> 000-default <==
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName domainA
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

==> 001-domainB <==
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName domainB
	
	DocumentRoot /var/www/domainB/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/domainB/>
```

I don't know if that 'NameVirtualHost *' line at the beginning of mine makes a difference or not.

In /etc/apache2/apache2.conf, have you changed LogLevel to debug? It may give more info on why things are going where.

Do you mind posting 'cat /etc/apache2/sites-enabled/*' here?

---

### Post by ghostknife on 2008-05-03
OK. Firstly doing the following will work, I'm sure.

First make sure you delete any virtual host data you setup for previous ones, then put the following directly inside your httpd.conf.

There after if everything is working as intended you can move the 3 files. Make sure you copy/paste the following and modify as needed, instead of trying to see what the differences are. It's possible that you are missing something trivial, which a clean setup will help with.

Then make sure all the directories for document roots exist and that apache has read permissions. Easiest is to do is run the following commands for your web root parent directory.

```

find /var/www -type d -exec chmod 0755 {} \;
find /var/www -type f -exec chmod 0644 {} \;

```

Put the following inside httpd.conf
```

NameVirtualHost *
<VirtualHost *>
  ServerAdmin yourname@yourdomain.com
  DocumentRoot /var/www/a.nl
  ServerName a.nl
  ServerAlias www.a.nl 
  ErrorLog /var/log/apache2/a.nl-error_log
  CustomLog var/log/apache2/a.nl-access_log combined
</VirtualHost>

<VirtualHost *>
  ServerAdmin yourname@yourdomain.com
  DocumentRoot /var/www/b.info
  ServerName b.info
  ServerAlias www.b.info
  ErrorLog /var/log/apache2/b.info-error_log
  CustomLog var/log/apache2/b.info-access_log combined
</VirtualHost>

<VirtualHost *>
  ServerAdmin yourname@yourdomain.com
  DocumentRoot /var/www/c.com
  ServerName c.com
  ServerAlias www.c.com
  ErrorLog /var/log/apache2/c.com-error_log
  CustomLog var/log/apache2/c.com-access_log combined
</VirtualHost>

```

Then restart apache and see if it works now.

If it doesn't work, please do the following and paste the output:
```

 ping -c1 a.nl
 ping -c1 b.info
 ping -c1 c.com

```

---

### Post by digitalfrog on 2008-05-03
> **ghostknife said:**
> OK. Firstly doing the following will work, I'm sure.

First make sure you delete any virtual host data you setup for previous ones, then put the following directly inside your httpd.conf.

There after if everything is working as intended you can move the 3 files. Make sure you copy/paste the following and modify as needed, instead of trying to see what the differences are. It's possible that you are missing something trivial, which a clean setup will help with.

Then make sure all the directories for document roots exist and that apache has read permissions. Easiest is to do is run the following commands for your web root parent directory.

```

find /var/www -type d -exec chmod 0755 {} \;
find /var/www -type f -exec chmod 0644 {} \;

```

Put the following inside httpd.conf
```

NameVirtualHost *
<VirtualHost *>
  ServerAdmin yourname@yourdomain.com
  DocumentRoot /var/www/a.nl
  ServerName a.nl
  ServerAlias www.a.nl 
  ErrorLog /var/log/apache2/a.nl-error_log
  CustomLog var/log/apache2/a.nl-access_log combined
</VirtualHost>

<VirtualHost *>
  ServerAdmin yourname@yourdomain.com
  DocumentRoot /var/www/b.info
  ServerName b.info
  ServerAlias www.b.info
  ErrorLog /var/log/apache2/b.info-error_log
  CustomLog var/log/apache2/b.info-access_log combined
</VirtualHost>

<VirtualHost *>
  ServerAdmin yourname@yourdomain.com
  DocumentRoot /var/www/c.com
  ServerName c.com
  ServerAlias www.c.com
  ErrorLog /var/log/apache2/c.com-error_log
  CustomLog var/log/apache2/c.com-access_log combined
</VirtualHost>

```

Then restart apache and see if it works now.

If it doesn't work, please do the following and paste the output:
```

 ping -c1 a.nl
 ping -c1 b.info
 ping -c1 c.com

```
Hi ghostknife, thanks for your post.

I have done what you suggested, but sadly it did not fix it.
Here is the output of the ping commands...



Domain that works: (this is my public IP)

```

root@media:/var/log/apache2# ping -c1 a.nl
PING a.nl (85.145.238.25) 56(84) bytes of data.
64 bytes from xxx.xxx.xxx.nl (85.145.238.25): icmp_seq=1 ttl=63 time=5.98 ms

--- a.nl ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 5.983/5.983/5.983/0.000 ms

```

Second domain that works too:

```

root@media:/var/log/apache2# ping -c1 b.info
PING media (192.168.1.8) 56(84) bytes of data.
64 bytes from media (192.168.1.8): icmp_seq=1 ttl=64 time=0.013 ms

--- media ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.013/0.013/0.013/0.000 ms


```

And the domain that does not get redirected where it should be, but to a.nl instead:

```

root@media:/var/log/apache2# ping -c1 c.com
PING media (192.168.1.8) 56(84) bytes of data.
64 bytes from media (192.168.1.8): icmp_seq=1 ttl=64 time=0.013 ms

--- media ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.013/0.013/0.013/0.000 ms

```

one of the domain that works pings to the public ip adress
one of the domain that works pings to my localhost
the domain that does not work points to my locahost (but apache see's it as the first domain that pings to the public address)

I'm 99% sure this has to do with the way the domains are setup, resolved or whatever. But I can't demonstrate it.
Today, I tried to sniff my lan to detect what domain name was sent to apache when I pointed my webbrowser to the site that does not re-route, but never managed to get any meaningfull data.

---

### Post by ghostknife on 2008-05-04
Please paste your whole httpd.conf.

And make sure there are NO other <VirtualHost> tags in httpd.conf or any of the files it includes.

---

### Post by digitalfrog on 2008-05-04
Here we go:

```

NameVirtualHost *
<VirtualHost *>
 ServerAdmin digitalfrog@a.nl
 DocumentRoot /var/www/a.nl
 ServerName a.nl
 ServerAlias www.a.nl
 ErrorLog /var/log/apache2/a.nl-error_log
 CustomLog /var/log/apache2/a.nl-access_log combined
</VirtualHost>

<VirtualHost *>
 ServerAdmin digitalfrog@b.info
 DocumentRoot /var/www/b.info
 ServerName b.info
 ServerAlias www.b.info
 ErrorLog /var/log/apache2/b.info-error_log
 CustomLog /var/log/apache2/b.info-access_log combined
</VirtualHost>

<VirtualHost *>
 ServerAdmin digitalfrog@c.com
 DocumentRoot /var/www/c.com
 ServerName c.com
 ServerAlias www.c.com
 ErrorLog /var/log/apache2/c.com-error_log
 CustomLog /var/log/apache2/c.com-access_log combined
</VirtualHost>

```

---

### Post by ghostknife on 2008-05-04
Your whole httpd.conf. If you fear for privacy, post this sensitive information inside a private message to me, and we can discuss solutions in public.

It's most probably a problem with the configuration. It usually is something very small. As long as all directories for DocumentRoot exists, Apache can read them, and the names can be resolved to IPs everything is fine. If Apache still doesn't do them it means there is a configuration problem.

---

### Post by ghostknife on 2008-05-04
Do you have any files inside /etc/apache2/sites-enabled/?

If so, paste them all separately, with their names prefixing them.

---

### Post by digitalfrog on 2008-05-04
it's all empty now, I consolidated the 3 files I had there in one httpd.conf (the one I posted above)


> **ghostknife said:**
> Do you have any files inside /etc/apache2/sites-enabled/?

If so, paste them all separately, with their names prefixing them.

---

### Post by ghostknife on 2008-05-04
OK. Remove those lines from httpd.conf, and put in apache2.conf. And post the full file in private again.

---

### Post by digitalfrog on 2008-05-04
Good news: It's working now
Bad news: I don't know what was wrong.

I cleaned up things and reworte them several times without success. Or at least I though. I cleaned my cache and .... now it works.

So one of the changes I've done fixed it, and it's likely to be one of ghostknife sugegstions.

So many thanks !

Ralph

---

