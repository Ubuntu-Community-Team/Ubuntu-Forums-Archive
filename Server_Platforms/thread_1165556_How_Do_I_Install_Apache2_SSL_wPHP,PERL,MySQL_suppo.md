---
title: "How Do I Install: Apache2 SSL w/PHP,PERL,MySQL support"
date: 2009-05-20
forum: Server Platforms
---

### Post by starr0stealer on 2009-05-20
I have recently found information that states (apache2-ssl-certificate) is no long found in the apache2 package.

I am trying to setup a server that will run any page under both Port 80 or 443. HTTP or HTTPS.

I am also wanting to make sure I can run PHP and Perl script inside any directory of the server.


These are the commands I have done so far. (i removed commands ran to edit conf files and restart services)

apt-get install mysql-server
apt-get install apache2
apt-get install php5 libapache2-mod-php5
a2enmod php5
apt-get install libapache2-mod-perl2
a2enmod perl
mkdir /var/www/cgi-bin
a2enmod ssl



PHP is working. Perl is working but only under CGI-bin. Which I dont want it to just work under that.

---

### Post by Aeonsies on 2009-05-20
[http://ubuntuforums.org/archive/index.php/t-4466.html](http://ubuntuforums.org/archive/index.php/t-4466.html)

This should get you started a bit.  I'd like to be more explanatory but I'm dashing out the door right now.  If your still confused later I'll try and help you comb through a bunch of the garbage in the above archive.

---

### Post by starr0stealer on 2009-05-20
I actually tried to use that article, I used these two..
[http://ubuntuforums.org/showthread.php?t=4466](http://ubuntuforums.org/showthread.php?t=4466)
AND
[http://ubuntuforums.org/showthread.php?t=51753](http://ubuntuforums.org/showthread.php?t=51753)

But since (apache2-ssl-certificate) is spitting out (command not found), I wasnt able to get very far with the CERT setup. I didnt have to setup a .CA or .KEY?
_____________________

I have ran these other commands in addtion to

apt-get install ssl-cert
mkdir /etc/apache2/ssl
make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl
ln -s /etc/apache2/sites-available/ssl /etc/apache2/sites-enabled/ssl



HTTPS is working, I get that Certificate error, can have that removed?

Is this the most secure I can get,
This is going to contain a portal for our clients, with confidential data
________

In, /etc/apache2/sites-available/ssl

Can I just set it to
```
<VirtualHost localhost:443>
        DocumentRoot /var/www/
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem
</VirtualHost>
```


And Can I just merge what is in default and SSL to one file. like

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

	AND ALL THAT JAZZ

</VirtualHost>
<VirtualHost localhost:443>
        DocumentRoot /var/www/
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem
</VirtualHost>
```

---

### Post by apel_2804 on 2009-05-21
Maybe you find this usefull:

[http://www.tbaumi.de/blog/?p=60](http://www.tbaumi.de/blog/?p=60)

You get the certificate error in firefox because it is self signed.

---

### Post by starr0stealer on 2009-05-22
Ok, I have been able to get HTTPS working..

I ended up removing everything this did.. 
```
apt-get install ssl-cert
mkdir /etc/apache2/ssl
make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl
ln -s /etc/apache2/sites-available/ssl /etc/apache2/sites-enabled/ssl
```

And used these commands instead...
```
apt-get install openssl ssl-cert libssl0.9.8 libssl-dev ca-certificates
mkdir /etc/apache2/ssl
a2ensite default-ssl
openssl genrsa -des3 -out /etc/ssl/private/inapps-s-tech.server.key 4096
openssl req -new -key /etc/ssl/private/inapps-s-tech.server.key -out /etc/ssl/inapps-s-tech.server.csr
openssl x509 -req -days 3650 -in /etc/ssl/inapps-s-tech.server.csr -signkey /etc/ssl/private/inapps-s-tech.server.key -out /etc/ssl/certs/inapps-s-tech.server.crt
cp /etc/ssl/private/inapps-s-tech.server.key /etc/apache2/ssl/inapps-s-tech.server.key
cp /etc/ssl/certs/inapps-s-tech.server.crt /etc/apache2/ssl/inapps-s-tech.server.crt
cp /etc/apache2/ssl/inapps-s-tech.server.crt /var/www/inapps-s-tech.server.crt
```



So my last question... 
Using the .crt and .key files, I have to put in the pass phrase on every reboot.
Before when I used the .pem single file, when I reboot i wouldnt get prompts for the pass phrase.

Which is BETTER to use, if its more secure I can put up with the password deal. Other wise I rather not have it.

---

