---
title: "trying to configure virtualhosts with webmin on ubuntu 9.10 karmic koala"
date: 2010-09-16
forum: Server Platforms
---

### Post by dionp2 on 2010-09-16
Hi,

Could somebody please help me?

I'm a bit of a Nooob to Virtual hosting.

On my internal network 192.168.1.x I have a dns server running bind9

My DNS / web server is 192.168.1.3

I have succeeded in getting ice.7rocks.com to resolve and it goes to my web page in /var/www/

Now I want to get say 

music.7rocks.com

to go to  /var/www/music/

1. What's the best way to go about this?

2. Can I configure it using webmin or do I just do it the old fashioned way through a terminal?

3. I tried virtual hosts via the following method

Added to /etc/apache2/sites-available/default

NameVirtualHost 192.168.1.3:80

Then created

/etc/apache2/sites-available/music.7rocks.com

<VirtualHost 192.168.1.3:80>
ServerName music.7rocks.com
ServerAlias music.7rocks.com
ServerAdmin [email]dion@7rocks.com[/email]
DocumentRoot /var/www/music/
</VirtualHost>


Then 

a2ensite music.7rocks.com 

Restarted apache

root@ice:/etc/apache2/sites-available# /etc/init.d/apache2 restart
 * Restarting web server apache2
[Fri Sep 17 08:08:09 2010] [warn] The Alias directive in /etc/apache2/conf.d/phpmyadmin.conf at line 3 will probably never match because it overlaps an earlier Alias.
 ... waiting [Fri Sep 17 08:08:11 2010] [warn] The Alias directive in /etc/apache2/conf.d/phpmyadmin.conf at line 3 will probably never match because it overlaps an earlier Alias.
   ...done.

root@ice:/etc/apache2/sites-available# ping music.7rocks.com
ping: unknown host music.7rocks.com

I'm not sure which logs to tail to see what's happening.

Cheers,

D

---

### Post by Fafler on 2010-09-17
Ping uses ICMP, not HTTP, so whether or not you're able to ping our virtual host or not has nothing to do with Apache, you have to look at your DNS configuration instead.

---

### Post by dionp2 on 2010-09-17
Cheers Fafler,

This is my forward lookup file /etc/bind/zones/7rocks.com.db

------------------------------------------------
$TTL 86400

7rocks.com.     IN      SOA     ice.7rocks.com. dion.7rocks.com. (
10118 ; Serial
43200 ; Refresh
3600 ; Retry
3600000 ; Expire
2592000 ) ; Minimum

7rocks.com.                 IN      NS              ice.7rocks.com.
7rocks.com.                 IN      MX     10       mail.7rocks.com.

mail             IN      A       82.98.86.173
ice              IN      A       192.168.1.3
------------------------------------------------

And my reverse lookup file /etc/bind/zones/rev.1.168.192.in-addr.arpa

------------------------------------------------
$TTL 86400

@       IN      SOA     ice.7rocks.com. dion.7rocks.com. (
                        2006081402
                        28800
                        604800
                        604800
                        86400 )

        IN      NS      ice.7rocks.com.
3.1.168.192.in-addr.arpa.       IN      PTR     ice.7rocks.com.

------------------------------------------------


I'm not sure what I should be looking for here.

Cheers,

D

---

### Post by Fafler on 2010-09-17
I'm not really that much into bind configurations,  but i don't see music.7rocks.com anywhere in the configuration. I guess it should be

music IN      A       192.168.1.3

Also, i see you use DNAT. Some routers have difficulties with these kind of configurations. You should really test things out on both sides of the router to make sure. Use a proxy or another internet connection.

---

### Post by dionp2 on 2010-09-17
I think I did that last night and it worked to get to /var/www

What I really want to do is redirect music.7rocks.com to the /var/www/music/ subdirectory.

music.7rocks.com already works from the outside world as I have got the DNS managed with dyndns.com

Dyndns.com allows you to do what is called a Webhop redirection.

So at dyndns.com I have got
music.7rocks.com pointing to [http://ice.7rocks.com:81/music/](http://ice.7rocks.com:81/music/)
and it works great.

I don't know how DNAT works and will look into it later tonight. 

Thank you again.

---

