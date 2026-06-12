---
title: "ubuntu server 16.04.3 IP Address  Resolves Correctly but Webpage Does Not"
date: 2017-09-11
forum: Server Platforms
---

### Post by dmcgettigan on 2017-09-11
My apologies in advance, I am by no means an IT guy, I know just enough to be dangerous....

I helped my work create a wordpress site on ubuntu server; we installed and set it up out side of our server room, it had an IP address of 192.168.4.176.  Once we got it up an running and we were happy with it, we moved it to our server room, it now has an IP address of 10.11.79.3.  

Now this is where the rub happens, when I enter 10.11.79.3 in Chrome, it forwards to 192.168.4.17.

I can ping 10.11.79.3 and I can ping the ubuntu server name with no problems.  My corporate IT dept can see the server and they ping it as well, but they do not know anything about linux.  I have searched through the server networking files, that I know of, and I do not see the 192.168.4.176 IP address in any of the files.

Any help you provide is appreciated!

Darren

---

### Post by darkod on 2017-09-11
Post the output of:
```
cat /etc/network/interfaces
ifconfig
ls /etc/apache2/sites-available
```

Put the results in CODE tags so that they are with better formatting and more readable.

---

### Post by dmcgettigan on 2017-09-11
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface


auto enp0s25
iface enp0s25 inet dhcp
```

```
enp0s25   Link encap:Ethernet  HWaddr 00:1e:67:12:82:14
          inet addr:10.11.79.3  Bcast:10.11.79.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:67ff:fe12:8214/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:104471 (104.4 KB)  TX bytes:41613 (41.6 KB)
          Interrupt:20 Memory:b1b00000-b1b20000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

```
000-default.conf  default-ssl.conf

```

---

### Post by dmcgettigan on 2017-09-11
Update:

I just powered off the server, cleared my browser cache and tried 10.11.79.3 again and it is still going to 192.168.4.176, so it would seem it is a network issue, right??

---

### Post by darkod on 2017-09-11
1. Server should have static IP. You have it set to dhcp. It can work with dhcp reservations, but still.... I always stick to static IP outside of any dhcp range.

2. To see the apache2 virtual host config post the output of:
```
cat /etc/apache2/sites-available/000-default.conf
```

3. Did you change any other apache files or you were only working on 000-default.conf?

---

### Post by dmcgettigan on 2017-09-11
```
<VirtualHost *:80>        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com


        ServerAdmin webmaster@localhost
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
```

I do not believe there were any changes to the apache files

---

### Post by darkod on 2017-09-11
Usually you would use the virtual host conf file to set the domain name, etc. For example, you would use:
```
   ServerName   www.example.com
   ServerAlias   example.com
```

Then in your LAN internal DNS you will have to create the necessary A records so that [www.example.com](www.example.com) and example.com point to the server LAN IP.

You plan to reach it only by IP? No opening by URL?

Also, how did you install apache2, during the ubuntu install process in the task selector, or you added it with apt-get install later on?

---

### Post by dmcgettigan on 2017-09-11
I was only connecting by IP to test after we moved into the server room, I am waiting on our corporate IT dept to give me an external IP address still.

I used the apt-get to install apache2.

---

### Post by darkod on 2017-09-11
Waiting for external IP changes nothing. Set up the site (virtual host) with the correct ServerName as it should be (the URL you will use in production), and test that it opens like that.

Internally it will resolve using internal DNS servers, externally it will resolve using public servers and will point to the public IP once you have it.

In fact using ServerName might "solve" your current question because in that case it should not show any IP in the browser address line. It should show the URL.

---

### Post by Hugo_Serrano on 2017-09-13
Hello,

you may need to change something on Wordpress. 

See if this helps:
[https://wordpress.stackexchange.com/questions/155471/when-moving-a-wp-site-why-does-wp-admin-redirect-to-old-site](https://wordpress.stackexchange.com/questions/155471/when-moving-a-wp-site-why-does-wp-admin-redirect-to-old-site)

This happened to me before. I have used phpmyadmin to change the IP value in the DB.

Cheers,
Hugo.

---

### Post by dmcgettigan on 2017-09-13
So we cheated... we changed the IP address to 192.168.4.176 and now it works.  I don't what the issue was but I got to my end result, thanks for the effort!

---

### Post by Habitual on 2017-09-13
Cheating is "creative" and +1
Issue was posts in table wp_posts has stored content pointing to [http://192.168.4.176](http://192.168.4.176)

WP_SITEURL and WP_HOME variables in db.
can be "cheated" also using 
```
define('WP_HOME','http://domain.tld');
define('WP_SITEURL','http://domain.tld');
``` can be utilized in wp-config.php. negating the "reason" to alter another table.

wp_posts table has all the posted content still pointing to 192.168.4.176

something like export db > database.sql
```
cat database.sql | sed 's#http://192.168.4.176#http://10.11.79.3#g' > database2.sql
```
would "sanitize" the inplace data. You'd have to re-import database2.sql into the wordpress db and you should be golden.

[https://codex.wordpress.org/Changing_The_Site_URL](https://codex.wordpress.org/Changing_The_Site_URL)
and
[https://codex.wordpress.org/Moving_WordPress](https://codex.wordpress.org/Moving_WordPress)

---

