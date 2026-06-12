---
title: "problems with apache2: SNI &amp; virtual hosts"
date: 2011-01-17
forum: Server Platforms
---

### Post by lowrider2025 on 2011-01-17
Situation:
server running as a virtual machine
Ubuntu 10.04.1
Apache 2.2.16
OpenSSL 0.9.8k (library: OpenSSL 0.9.8o 01 Jun 2010)

What I want: multiple virtual hosts with ssl and only 1 ip address:

In my example: server = 192.168.227.129

What I did so far:
cd /var
mkdir sslsite1
mkdir sslsite1
chmod 755 sslsite1
chmod 755 sslsite2
chown root:root sslsite1
chown root:root sslsite2

cd sslsite1
touch index.html
nano index.html: <h2>SSL Site 1</h2>
cp index.html /var/sslsite2
nano index.html: <h2>SSL Site 2</h2>

cd /etc/apache2/sites-available
touch sslsnihosts
nano sslsnihosts

sslsnihosts:
<VirtualHost *:443>
   ServerName test1.domain.com

   SSLEngine On
   SSLCertificateFile /etc/apache2/ssl/server.crt
   SSLCertificateKeyFile /etc/apache2/ssl/server.key
  
   DocumentRoot /var/sslsite1
</VirtualHost>
<VirtualHost *:443>
   ServerName test2.domain.com

   SSLEngine On
   SSLCertificateFile /etc/apache2/ssl/server.crt
   SSLCertificateKeyFile /etc/apache2/ssl/server.key
  
   DocumentRoot /var/sslsite2
</VirtualHost>

a2ensite sslsnihosts

/etc/apache2/ports.conf
added:
NameVirtualHost *:443

already in the file:
<IfModule mod_ssl.c>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

/etc/init.d/apache2 restart (gives no errors)

on host OS:
windows/system32/drivers/etc/hosts
192.168.227.129 test1.domain.com
192.168.227.129 test2.domain.com

in firefox 3.6.13
[https://test1.domein.com](https://test1.domein.com)

=> Connection was interupted

[http://test1.domain.com:443/](http://test1.domain.com:443/)
=>Bad Request

Your browser sent a request that this server could not understand.
Reason: You're speaking plain HTTP to an SSL-enabled server port.
Instead use the HTTPS scheme to access this URL, please.

Hint: [https://test1.domain.com/](https://test1.domain.com/)

Does someone have a clue ?

Thanks for reading

---

### Post by SeijiSensei on 2011-01-17
> **lowrider2025 said:**
> What I want: multiple virtual hosts with ssl and only 1 ip address:

From the [Apache docs](http://httpd.apache.org/docs/2.2/vhosts/name-based.html):

"Name-based virtual hosting cannot be used with SSL secure servers because of the nature of the SSL protocol."

---

### Post by lowrider2025 on 2011-01-17
> **SeijiSensei said:**
> From the [Apache docs](http://httpd.apache.org/docs/2.2/vhosts/name-based.html):

"Name-based virtual hosting cannot be used with SSL secure servers because of the nature of the SSL protocol."

=> [http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI]("http://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI")

I think I do meet the requirements:
minimum apache 2.2.12 - me:2.2.16 > check
minimum openssl 0.9.8j - me:0.9.8k > check

---

### Post by lowrider2025 on 2011-01-18
Did some research with: openssl s_client -connect 192.168.227.129:443
output a.o.: SSL23_WRITE:ssl handshake failure:s23_lib.c:188

Where could I find what the reason is for this error ? In what log files would I have to look ? Problably in /var/log ?

openssl.cnf: 
added serveral common names just to be sure:
localhost
127.0.0.1
192.168.227.129
*.domain.com
hostname

---

### Post by James78 on 2011-01-18
@lowrider: If SNI is working, you should be seeing this in your default apache error log. By default, Ubuntu Apache and OpenSSL already work with SNI. I did absolutely no configuring on my server for this, except for in Apache, adding multiple SSL Vhosts on the same port and IP. It all works perfectly. :) 10.04.1 of course. Honestly, I don't see any reason this shouldn't work for you.
```
[warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
```
Are there any interesting errors in your default error log?
> **lowrider2025 said:**
> Where could I find what the reason is for this error ? **In what log files would I have to look ?** Problably in /var/log ?
/var/log/apache2/error.log
> **SeijiSensei said:**
> From the [Apache docs](http://httpd.apache.org/docs/2.2/vhosts/name-based.html):

"Name-based virtual hosting cannot be used with SSL secure servers because of the nature of the SSL protocol."
Actually, on 10.04.1 I am hosting multiple SSL Vhosts on the same port and IP and it's working perfectly. :)

---

### Post by lowrider2025 on 2011-01-18
> **James78 said:**
> @lowrider: If SNI is working, you should be seeing this in your default apache error log. By default, Ubuntu Apache and OpenSSL already work with SNI. I did absolutely no configuring on my server for this, except for in Apache, adding multiple SSL Vhosts on the same port and IP. It all works perfectly. :) 10.04.1 of course. Honestly, I don't see any reason this shouldn't work for you.
```
[warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
```
Are there any interesting errors in your default error log?

/var/log/apache2/error.log

Actually, on 10.04.1 I am hosting multiple SSL Vhosts on the same port and IP and it's working perfectly. :)

I found a warning about an ip address that I added to the CN list(for future use). 
=> [warn] RSA server certificate CommonName (CN) `ip address' does NOT match server name!?
=> Will this be fatal to ssl function ? 

I also found that testing with ```
openssl s_client -connect ip:port
```
does not work => [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
***=> edit: OK, apparently it should be a sign SNI is working. So far so good for this warning then :)***

But still the browser from host os does not let me connect.

---

### Post by lowrider2025 on 2011-01-18
Maybe it's time to test this out on a 'real' server instead of a VM. I find it strange that webmin did work from host os browser.

Do the warnings prevent ssl from working or is is just informing the user ? (the commonname not matching the server name)

---

### Post by lowrider2025 on 2011-01-18
is there a way of letting apache show warnings and errors on restart(= /etc/init.d/apache2 restart) ?

---

### Post by lowrider2025 on 2011-01-19
What would have to be used as CN when creating the self-signed certificate ?

1) *hostname*
2) localhost
3) 127.0.0.1
4) external ip address
5) fqdn (in my example: test1.domain.com & test2.domain.com)

What would apply ? If fqdn would be used then does one use 
1) test1.domain.com
2) [https://test1.domain.com](https://test1.domain.com)

virtual hosts file:
ServerName would be:
1) [https://test1.domain.com](https://test1.domain.com)
2) test1.domain.com
3) test1.domain.com:443

Which one to use ?
What entries would /etc/hosts (on ubuntu) have to contain)?

---

### Post by James78 on 2011-01-19
> **lowrider2025 said:**
> I found a warning about an ip address that I added to the CN list(for future use). 
=> [warn] RSA server certificate CommonName (CN) `ip address' does NOT match server name!?
=> _Will this be fatal to ssl function ?_

I also found that testing with ```
openssl s_client -connect ip:port
```
does not work => [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
***=> edit: OK, apparently it should be a sign SNI is working. So far so good for this warning then :)***

But still the browser from host os does not let me connect.
It is not fatal, but I find it strange connecting doesn't work.. Something's wrong somewhere.. The question is where that is...
> **lowrider2025 said:**
> Maybe it's time to test this out on a 'real' server instead of a VM. I find it strange that webmin did work from host os browser.

_Do the warnings prevent ssl from working or is is just informing the user ? (the commonname not matching the server name)_
Nope, all it will do is popup a security warning on your browser that the certificate doesn't match.
> **lowrider2025 said:**
> is there a way of letting apache show warnings and errors on restart(= /etc/init.d/apache2 restart) ?
Error will be shown automatically because it'll fail to restart (if not fatal, it'll be in the error log). As for warnings, some of those also get shown, but the rest of them will be in the default error log. If there's any configuration errors, starting/restarting will almost always show them, however there is a utility to check for problems..
```
sudo apache2ctl configtest
```
> **lowrider2025 said:**
> What would have to be used as CN when creating the self-signed certificate ?

1) *hostname*
2) localhost
3) 127.0.0.1
4) external ip address
5) fqdn (in my example: test1.domain.com & test2.domain.com)

What would apply ? If fqdn would be used then does one use 
1) test1.domain.com
2) [https://test1.domain.com](https://test1.domain.com)

virtual hosts file:
ServerName would be:
1) [https://test1.domain.com](https://test1.domain.com)
2) test1.domain.com
3) test1.domain.com:443

Which one to use ?
What entries would /etc/hosts (on ubuntu) have to contain)?
1) *hostname* - If you add the other machines hostname to your /etc/hosts and access it like that from the browser, that's fine.
2) and 3) If you're accessing it from localhost then sure. You generally shouldn't be putting IP's for the common name; the names should work fine. Because it's self signed though, you'll still have to accept a security warning.
5) Definitely. The very best choice there is. FQDN should always be the common name

You would use
1) test1.domain.com

ServerName would be 2) test1.domain.com. Like so...
```
<VirtualHost *:80>
ServerName test1.domain.com
...
```

/etc/hosts would contain something like this (assuming your test machine is on localhost)
```
127.0.0.1 test1.domain.com
```

Did this answer any of your questions?

---

### Post by lowrider2025 on 2011-01-19
> **James78 said:**
> 
You would use
1) test1.domain.com

ServerName would be 2) test1.domain.com. Like so...
```
<VirtualHost *:80>
ServerName test1.domain.com
...
```


Does this apply to ssl as well ? As we're talking about multiple ssl vhosts

Would you have to use:
```
<VirtualHost *:443>
ServerName test1.domain.com
...
```
I've seen an example where they use ServerName [https://test1.domain.com](https://test1.domain.com) . But it seems odd to me.

thanks for the answers btw !! It does help making it a bit more clear.

---

### Post by James78 on 2011-01-19
> **lowrider2025 said:**
> _Does this apply to ssl as well ? As we're talking about multiple ssl vhosts_

Would you have to use:
```
<VirtualHost *:443>
ServerName test1.domain.com
...
```
I've seen an example where they use ServerName [https://test1.domain.com](https://test1.domain.com) . But it seems odd to me.

thanks for the answers btw !! It does help making it a bit more clear.
Correct. For some reason port 80 was running through my head. :D

Yes, using [https://test1.domain.com](https://test1.domain.com) for a ServerName does seem odd. The reason for that is...
*"Sometimes, the server runs behind a device that processes SSL, such as a reverse proxy, load balancer or SSL offload appliance. When this is the case, specify the https:// scheme and the port number to which the clients connect in the ServerName directive to make sure that the server generates the correct self-referential URLs."*

So if you're not one of those exceptions, you shouldn't and don't need to do that. I certainly am not required to do that for my site. :)
[http://httpd.apache.org/docs/2.2/mod/core.html#servername](http://httpd.apache.org/docs/2.2/mod/core.html#servername)

---

### Post by lowrider2025 on 2011-01-20
I installed everything on a real server and tried to connect to the website through another pc in the network. Same problem as on the notebook with the virtual machine. Connection interrupted. 

@James: would you have a link to the howto you used? Or if you didn't use a tutorial post the rights/ownerships for /etc/apache2/ssl and the openssl.cnf & your virtual hosts file ?
Thanks beforehand.

ps: I do have to admit that I do run other versions of lamp and openssh than those that come with ubuntu 10.04.1. I changed the sources.list file to get lamp-server and openssh that come for natty.I don't know what versions come with 10.04.1.

---

### Post by James78 on 2011-01-20
My config isn't really that overly complex.

/etc/apache2/ports.conf
```
Listen 80
Listen 443
```

/etc/apache2/apache2.conf
```
...
NameVirtualHost <local-ip>:80
NameVirtualHost <local-ip>:443
```

/etc/apache2/sites-available
```
<VirtualHost [local-ip]:443>
ServerName ...
ServerAlias ...

...

SSLEngine on
SSLCertificateFile /home/user/ssl.cert
SSLCertificateKeyFile /home/user/ssl.key
SSLCACertificateFile /home/user/ssl.ca-bundle
</VirtualHost>
```

For the Virtualhosts, I simply just have multiple Virtualhosts on the same IP and port. This works perfectly for me, so your problem might be related to something else. Maybe if you just try to simply do a configuration like that above, with a fresh virtualmachine, and 10.04.1, maybe it will work. And, as for using Natty's LAMP, that probably didn't cause it to fail.

"I changed the sources.list file to get lamp-server and openssh that come for natty."
OpenSSH != OpenSSL (in case that's why you are using Natty's OpenSSH)

Try clearing your browsers cache however, that can cause many false positives (yes, even false positives with redirects).

---

### Post by lowrider2025 on 2011-01-20
Thanks James. 

My files were more or less the same.Just to be sure changed them so they matched yours...didn't change anything.

Found a ready made distro for joomla called "Turnkey Joomla" and I'm continuing from there.

Thanks for the effort you put in to help...it's much appreciated!!

---

