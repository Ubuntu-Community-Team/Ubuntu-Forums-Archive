---
title: "Can only access webserver from localhost"
date: 2022-01-27
forum: Ubuntu, Linux and OS Chat
---

### Post by digitalis492 on 2022-01-27
**Really need some help here PLEASE. **[B]==============================
**Fi**rst off - I am NOT an experienced Linus person but I can follow clear instructions.
[/B]
I have a dedicated home/office PC running Ubuntu 20.04 + LAMP + Joomla.

 Have not, as yes, installed Letsencrypt SSL - but will do so asap.

I have a registered domain with Godaddy.com - Let's call it "myweb.com".

 
I have a static public IP address - used in Godaddy's DNS A & CNAME records - IP address provided by my ISP.

 
Ubuntu network settings are IPv4 Auto DHCP & auto Routes. No IPv6.

 --------------------------------------------------------
/etc/hostname = myweb

 ---------------------------------------------------------
/etc/hosts = 
192.168.0.137   myweb.com myweb 
127.0.0.1         localhost localhost.localdomain

 ------------------------------------------------------------
/etc/apache2/sites-enabled = 
VirtualHost *:80> 
ServerName myweb.com 
ServerAlias [www.myweb.com]("http://www.myweb.com") 
ServerAdmin [email]admin@myweb.com[/email] 
DocumentRoot /var/www/html/joomla

 ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

<Directory /var/www/html/joomla>
     Options FollowSymlinks
     Allowoverride all
     Require all granted
---------------------------------
      [h=1]ISSUE:[/h] I can only access my Joomla website using my local IP address or localhost. 
Using a computer external to my network to access my site gives me a timeout or connection refused message.

 
I have searched the net for likely causes for several weeks but have not resolved this issue.

 
PLEASE, I would really appreciate some advice from this very learned community.

 Am happy to provide more info as needed - naturally!

Thank you.
Andreas.

---

### Post by jeremy31 on 2022-01-27
Dupe of [https://ubuntuforums.org/showthread.php?t=2471340](https://ubuntuforums.org/showthread.php?t=2471340)
Closed as this forum is not for support issues

---

