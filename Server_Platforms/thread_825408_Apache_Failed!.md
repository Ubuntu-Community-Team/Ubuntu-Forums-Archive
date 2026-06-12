---
title: "Apache Failed!??"
date: 2008-06-10
forum: Server Platforms
---

### Post by subzero06 on 2008-06-10
Hello,

i am having problems with Apache version 2.2.8 my websites work fine, but i want to run a website using SSL, i got the key and certificate from godaddy. 
So i have to create a virtual host mydomain.com using the default port 80 and create another virtual domain using port 443. They create successfully but when i got to SSL option in the virtual host thats using port 443 and enable the ssl with the certificate and key, apache stops working and when i apply changes appears
---------------------------------------
* Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.6 for ServerName
   ...fail!
----------------------------------------
so when i delete the virtual host thats using the port 443 the problem goes away and apache starts workin....
what could be wrong? i know the SSL is enabled in my server and working using the default site, like when i go to [https://myip.com](https://myip.com) it works.

i am using Ubuntu Linux 8.04

---

### Post by MJN on 2008-06-11
Post your sites-enabled config then we can take a look.

It is difficult to diagnose without knowing the configuration.

Incidentally, the error message you are seeing is just a warning that you haven't set a ServerName hence it is having make assumptions on what this is (this is useful to maintain control of certain redirects etc).

Mathew

---

### Post by subzero06 on 2008-06-11
> **MJN said:**
> Post your sites-enabled config then we can take a look.

It is difficult to diagnose without knowing the configuration.

Incidentally, the error message you are seeing is just a warning that you haven't set a ServerName hence it is having make assumptions on what this is (this is useful to maintain control of certain redirects etc).

Mathew

Yes here.

<VirtualHost *:443>
DocumentRoot "/home/coolcomputers"
ServerName myweb.com
<Directory "/home/coolcomputers">
allow from all
Options +Indexes
</Directory>
ServerAlias *.myweb.com
SSLEngine on
SSLCertificateFile /home/coolcomputers/ssl/www.myweb.com.crt
SSLCertificateKeyFile /home/coolcomputers/ssl/www.myweb.com.key
</VirtualHost>
<VirtualHost *>
DocumentRoot "/home/coolcomputers/"
ServerName myweb.com
<Directory "/home/coolcomputers/">
allow from all
Options +Indexes
</Directory>
ServerAlias *.myweb.com
</VirtualHost>

---

### Post by molotov00 on 2008-06-11
Is your server actually the one I'm going to when I go to myweb.com?

I'm sceptical that's you... it's a Windows box, according to nmap at least.

If you are coolcomputers.myweb.com then Apache needs to know that.

---

### Post by subzero06 on 2008-06-11
Nah, let me explain, iam using a new a new hard drive, so i installed ubuntu server 8.04 in my new hard drive. My other hard drive came pre configured with ubuntu 7.10... so i have installed ubuntu8.04 on a new hard drive. So my ssl was working fine with my other hard drive. So what i think i did wrong was use the same ssl certificate from my other hard drive with different settings but for the same domain but in my new hard drive. I was looking in apache error logs and i found this

----------------------------------------------------

apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.6 for ServerName
[Wed Jun 11 19:47:57 2008] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Wed Jun 11 19:47:57 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Wed Jun 11 19:48:19 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.6 for ServerName
[Wed Jun 11 19:48:19 2008] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Wed Jun 11 19:48:19 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g configured -- resuming normal operations
[Wed Jun 11 19:49:10 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.6 for ServerName
[Wed Jun 11 19:49:10 2008] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Wed Jun 11 19:49:10 2008] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Wed Jun 11 19:49:10 2008] [warn] RSA server certificate CommonName (CN) `Go Daddy Secure Certification Authority' does NOT match server name!?
[Wed Jun 11 19:49:10 2008] [error] Unable to configure RSA server private key
[Wed Jun 11 19:49:10 2008] [error] SSL Library Error: 185073780 error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
[Wed Jun 11 19:49:22 2008] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
[Wed Jun 11 19:49:22 2008] [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Wed Jun 11 19:49:22 2008] [warn] RSA server certificate CommonName (CN) `Go Daddy Secure Certification Authority' does NOT match server name!?
[Wed Jun 11 19:49:22 2008] [error] Unable to configure RSA server private key
[Wed Jun 11 19:49:22 2008] [error] SSL Library Error: 185073780 error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
-------------------------------------------------------------------

So this means i have to create/regenerate a new SSL for my new ubuntu installation?

---

### Post by quelx on 2008-06-11
> **subzero06 said:**
> apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.6 for ServerName
to get rid of this echo your FQDN into */etc/hostname*; eg. ```
sudo echo myweb.com | sudo tee -a /etc/hostname
```

---

### Post by subzero06 on 2008-06-11
crap i just created a new one with godaddy and im getting same error....:confused::confused:

---

### Post by quelx on 2008-06-11
> **subzero06 said:**
> crap i just created a new one with godaddy and im getting same error....:confused::confused:

Pretty sure **CommonName (CN)** should be your FQDN
```
[Wed Jun 11 19:49:10 2008] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
```
Are you creating the signing request yourself or is all of the certificate creation done on their site?  If they have the option to sign a certificate request I'd make your own cert for submission.
[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)

---

### Post by subzero06 on 2008-06-11
> **quelx said:**
> Pretty sure **CommonName (CN)** should be your FQDN
```
[Wed Jun 11 19:49:10 2008] [warn] RSA server certificate CommonName (CN) `localhost' does NOT match server name!?
```
Are you creating the signing request yourself or is all of the certificate creation done on their site?  If they have the option to sign a certificate request I'd make your own cert for submission.
[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)

and how do i fix it? by the way, i created the CSR in my server and the SSL certificate crt in godaddy
what do i have to change? etc/hosts  or /etc/hostname
right now my /etc/hostname files says:
Ubuntu

and my etc/hosts says :
127.0.0.1	localhost
192.168.1.6	ubuntu
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

------------------------------------

i have two domains hosting in my server, one is computertechforum.net and coolcomputers.info
and i only need coolcomputers for ssl

---

