---
title: "Ports via SSL"
date: 2009-03-11
forum: Server Platforms
---

### Post by freefly on 2009-03-11
I have an Ubuntu server with webfusion and have some problems configuring an SSL enabled domain to listen to 3 specific ports. I need this for communication with an external server using those 3 ports.

I was hoping you bright guys could help me - I am stuck.

(Below I have replaced IP addresses and domain names for privacy).

In /etc/apache2/sites-available/default I had this:

```
Listen 111.111.111.111:80
Listen 111.111.111.111:443

<VirtualHost 111.111.111.111:443>
ServerName www.mydomain.co.uk
ServerAlias mydomain.co.uk

DocumentRoot /home/m/d/mydomain/public_html

SSLEngine on
SSLCertificateKeyFile /etc/ssl.key/www.mydomain.co.uk.key
SSLCertificateFile /etc/ssl.crt/www.mydomain.co.uk.crt

CustomLog /var/log/apache2/ssl_access_log ssl

LogLevel warn
ErrorLog /var/log/apache2/error_log

</VirtualHost>
```

I then added:
```
Listen 111.111.111.111:5559
Listen 111.111.111.111:6559
Listen 111.111.111.111:7559
```

and for all 3 ports I added one of these (a copy of the standard 443 one):
```
<VirtualHost 111.111.111.111:5559>
ServerName www.mydomain.co.uk
ServerAlias mydomain.co.uk

DocumentRoot /home/m/d/mydomain/public_html

SSLEngine on
SSLCertificateKeyFile /etc/ssl.key/www.mydomain.co.uk.key
SSLCertificateFile /etc/ssl.crt/www.mydomain.co.uk.crt

CustomLog /var/log/apache2/ssl_access_log ssl

LogLevel warn
ErrorLog /var/log/apache2/error_log

</VirtualHost>
```
I then did a sudo /etc/init.d/apache2 reload

I have not edited ports.conf

I would have thought that was it, but it doesn't do the trick. 
Also, I will need to do this to several domains on the server and am wondering if there is a better way.

I am pretty new to this and any help would be appreciated. Not sure if I need to provide more information.

Cheers

---

### Post by askreet on 2009-03-17
I'm 99.97% sure a 'reload' isn't sufficient to listen on new ports.

Check the output of:
netstat -anp|grep LISTEN

to see if you're actually listening on those ports (probably not).  If not, do /etc/init.d/apache2 **restart**

Hope this helps,
Kyle

---

