---
title: "HTTPS and IP based VirtualHosts"
date: 2008-02-25
forum: Server Platforms
---

### Post by wesblake on 2008-02-25
Hello all. Our company recently started moving some servers to Ubuntu due to poor upgrade systems in CentOS. So far, so good, accept for one thing. Initially I moved a bunch of site over to the new Ubuntu box and commented out the VirtualHost configs we had until I could get the certificate re-issued for the new box. We have 3 ips on the box x.x.x.10-12, and multiple sites on each ip. We also have some sites that could run both with or without https (e.g., one site runs in http, but when you go to the cart it redirected to https).
Now, the configs below are exactly as we had them in CentOS, but when I uncomment the portion for ssl, apache2 fails to start. Comment them again, and it starts fine.

At the end of apache2.conf (was at the end of httpd.conf in CentOS):
NameVirtualHost x.x.x.10:80
NameVirtualHost x.x.x.11:80
NameVirtualHost x.x.x.11:443
NameVirtualHost x.x.x.12:80

And in a file /etc/apache2/sites-available/sitename.com (was also at the end of httpd.conf in CentOS):
<VirtualHost x.x.x.11:80>
  DocumentRoot /var/www/sitename.com/docroot/
  ErrorLog /var/www/sitename.com/logs/error_log
  CustomLog /var/www/sitename.com/logs/access_log combined
  <Directory "/var/www/sitename.com/docroot/">
  AllowOverride All
  </Directory>
</VirtualHost>
#<VirtualHost x.x.x.11:443>
#  DocumentRoot /var/www/go.sitename.com/docroot
#  ServerName go.sitename.com
#  ErrorLog /var/www/go.sitename.com/logs/error_log
#  CustomLog /var/www/go.sitename.com/logs/access_log combined
#  SSLEngine on
#  SSLCertificateFile /etc/apache2/ssl/certs/sitename.com.crt
#  SSLCertificateKeyFile /etc/apache2/ssl/keys/sitename.com.key
#  <Directory "/var/www/go.sitename.com/docroot/">
#  allow from all
#  Options +Indexes
#  </Directory>
#</VirtualHost>
<VirtualHost x.x.x.11:80>
  DocumentRoot /var/www/go.sitename.com/docroot
  ServerName go.sitename.com
  ErrorLog /var/www/go.sitename.com/logs/error_log
  CustomLog /var/www/go.sitename.com/logs/access_log combined
  <Directory "/var/www/go.sitename.com/docroot/">
  allow from all
  Options +Indexes
  </Directory>
</VirtualHost>

Of course, x.x.x is actually the first 3 octets of the ip addresses and sitename is the actual domain name.
Any ideas? This worked perfectly before on CentOS and now I'm going nuts trying different combinations of how to declare NameVirtualHost(s) and VirtualHost(s) to get this working again. Oh, and I did a2dissite default since all the sites are on 1 of these 3 ip addresses, but I believe I tried using https before that too.
Thanks.

---

### Post by OffAxis on 2008-02-25
you didn't mention this so it's gotta be asked;
do you have the ssl mod enabled?

```
sudo a2enmod
ssl
```

---

### Post by wesblake on 2008-02-25
Sorry, yes I did.

---

### Post by rapiscan on 2008-02-25
Is there any useful output when it fails to start or from a configtest?
```
sudo apache2ctl configtest 
```

---

### Post by wesblake on 2008-02-26
All I get from sudo apache2ctl configtest is "Syntax OK", and the error logs I know of (the one specified in the virtual host, and /var/log/apache2/error.log) give me nothing. I even tried to clear both logs, then uncomment the virtual host again and restart apache2. The restart fails as usual, and there is nothing in the logs, empty.
Thanks again.

---

### Post by rapiscan on 2008-02-26
Here is someone with the same symptoms, perhaps this is also your problem?

[http://www.nabble.com/After-replacing-ssl-certificate,-apache-fails-to-start-but-gives-no-error-td14381126.html](http://www.nabble.com/After-replacing-ssl-certificate,-apache-fails-to-start-but-gives-no-error-td14381126.html)

---

### Post by MJN on 2008-02-26
You say 'failed to start', can you be a but more specific? Any errors? Anything in the error log?

Without further info we'd be doing little more than guessing (and hence it's not worth going through your config just yet).

Mathew

---

### Post by wesblake on 2008-02-26
By failing to start I mean that when I run either:
sudo /etc/init.d/apache2 restart
or
sudo /etc/init.d/apache2 start I get a message "fail" at the end of the output line rather than the usual [OK]
I check that link posted earlier, thanks. However, the is currently the only key we've put on this server so far, so it can't be the wrong csr. It's a rapidssl cert, so per their instructions I generated a csr, then a key file with openssl, then we sent that csr to them and got back a cert.

---

### Post by MJN on 2008-02-26
Check your error log. There must be a clue somewhere!

Mathew

---

### Post by Collino on 2008-02-26
I had terrible problems with apache when trying to get several sites up and running (name based vhosts). One would work but the others wouldnt, but on disabling the working one the non working sites worked. I'm not entirely sure how I solved it, but it had me pulling my hair out.

One thing to try is to comment out the working site and uncomment the "non working" site - hence swapping them over and see what happens. If it works, then bring them back up 1 by 1.

Hope this makes sense!

p.s. my sites are configured in their own file within sites-available, and enabled using a2ensite yoursiteconfigfile. They then show up in sites-enabled

---

### Post by wesblake on 2008-02-27
Well, as mentioned earlier, there is absolutely nothing in the error.log files
I tried that last suggestion, to turn working sites off (turned off the V host for port 80 for go.sitename.com and turned on that for 443), still no go.
Any more ideas? I'm about to go back to CentOS, unfortunately.

....Ok, I've narrowed things down which might help, If I uncomment the 443 section but leave just the 3 SSL lines commented out, like this:

<VirtualHost x.x.x.11:80>
DocumentRoot /var/www/sitename.com/docroot/
ErrorLog /var/www/sitename.com/logs/error_log
CustomLog /var/www/sitename.com/logs/access_log combined
<Directory "/var/www/sitename.com/docroot/">
AllowOverride All
</Directory>
</VirtualHost>
<VirtualHost x.x.x.11:443>
 DocumentRoot /var/www/go.sitename.com/docroot
 ServerName go.sitename.com
 ErrorLog /var/www/go.sitename.com/logs/error_log
 CustomLog /var/www/go.sitename.com/logs/access_log combined
# SSLEngine on
# SSLCertificateFile /etc/apache2/ssl/certs/sitename.com.crt
# SSLCertificateKeyFile /etc/apache2/ssl/keys/sitename.com.key
 <Directory "/var/www/go.sitename.com/docroot/">
 allow from all
 Options +Indexes
 </Directory>
</VirtualHost>
<VirtualHost x.x.x.11:80>
DocumentRoot /var/www/go.sitename.com/docroot
ServerName go.sitename.com
ErrorLog /var/www/go.sitename.com/logs/error_log
CustomLog /var/www/go.sitename.com/logs/access_log combined
<Directory "/var/www/go.sitename.com/docroot/">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

Apache2 starts and runs fine. I know the ssl mod is installed/working, but it still seems like ssl is not working. Does this shed any light?

---

### Post by wesblake on 2008-02-27
PROBLEM SOLVED!

Ok, so it looks like in the confusion of the server move we pasted the incorrect cert into the crt file. Doh!

Thanks.

---

