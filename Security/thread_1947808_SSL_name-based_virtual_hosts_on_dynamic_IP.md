---
title: "SSL name-based virtual hosts on dynamic IP"
date: 2012-03-27
forum: Security
---

### Post by eawz9999 on 2012-03-27
SSL Name-based virtual hosts on dynamic IP. 
**Setup**:
5 DNS defined in dyndns.com, updated by ddclient to current IP, (example.com, secondexample.net, etc).
**Apache2** sites-available:
# DEFAULT PORT 443
NameVirtualHost *:443
<IfModule mod_ssl.c>
<VirtualHost *:443>
DocumentRoot /var/www/dead-end
........
SSLCertificateFile    /etc/apache2/ssl/localhost.localdomain.crt

-----------------------------------------------------------------
# example.com CONFIGURATION
<IfModule mod_ssl.c>
<VirtualHost *:443>
ServerName example.com
DocumentRoot /var/www/dead-end
Alias /complexalias /home/example.com/mypage1
.......
SSLCertificateFile    /etc/apache2/ssl/example.com.crt

------------------------------------------------------------------
# secondexample.net CONFIGURATION
<IfModule mod_ssl.c>
<VirtualHost *:443>
ServerName secondexample.net
DocumentRoot /var/www/dead-end
Alias /complexalias1	/home/secondexample.net/mypage2
......
SSLCertificateFile    /etc/apache2/ssl/secondexample.net.crt
etc

1-	Any request not matching the DNS/alias is directed to /var/www/dead-end.
2-	Request to my IP is handled by DEFAULT.
3-	This home server is used for sharing genealogy information with a large family in 3 Continents.
4-	I used to have more than 200 attacks on my server every day. They once got access to my database. I had to reinstall everything.
5-	Since this new setup, no unauthorized person access my server anymore.
This seems to work fine with the exception of a ‘warn’ on apache log when using Default vhost that ‘certificate does not match URL’.
My questions are: Is there a way to make this simpler? Am I missing something?
Thank you for your input,
Enrique

---

### Post by eawz9999 on 2012-03-27
The warning on apache2 log was corrected by using sneakoil.crt and adding 'ServerName ubuntu' in default vhost configuration.

---

