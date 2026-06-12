---
title: "servers certificates"
date: 2012-03-24
forum: Security
---

### Post by eawz9999 on 2012-03-24
I have an Ubuntu 11.04 server running on a dynamic IP. The server is only open on port 447 (ssl). 
Using Dyndns I created several DNSs that default on my actual IP address and are updated with ddclient. 
I have the same DNS as name-based virtualhosts defined in apache2 sites-enabled. Each VirtualHost has its own server certificate. **The default** virtual host (for anything that does not match any of my DNSs, including my actual IP) leads to a dead-end directory.
This setup works fine with **one exception**. I used ssl-cert-snakeoil.pem for the default site to avoid disclosing my information on the https page. Every time someone accesses my server with an incorrect DNS I get an error on my logs stating “certificate does not match server’s name”. _Snakeoil.pem_ is issued to ‘ubuntu’ and it could never match a request. On the other hand I cannot create a certificate that will cover any DNS but the ones I defined (or can I?).
This problem does not interfere with the operation of the server, it’s just **annoying**.
Thank you for any suggestions, Enrique

---

### Post by eawz9999 on 2012-03-26
If I list my  apache2 VirtualHosts the default server is localhost.localdomain.
I assume that any connection not matching my defined VirtualHosts would go to this virtual server.
If I replace my snakeoil.pem by a self-signed certificate under the name 'localhost.localdomain' may work (?). I'll try.

---

### Post by CharlesA on 2012-03-26
The default port for SSL is 443.

You would need to issue a certificate to each domain name individually.

---

### Post by eawz9999 on 2012-03-27
Thank you for your help.
In *:443 I have 5 namevhosts, each one with a certificate, and have no problems with this.
The first namevhost is default, catching anything that does not match anything else, including my real IP address. This is the one giving warnings since the default certificate does not match the URL.
I tried signing a certificate as **localhost.localdomain.crt** This eliminates the warnings in apache2 logs, however, when I send a URL request there is still a warning on my browser: "Certificate does not match URL".
It works anyway, my only question is **why**.

---

### Post by CharlesA on 2012-03-27
How are you accessing the "default" site?

---

### Post by eawz9999 on 2012-03-27
[https://myIP](https://myIP)

If I request 'debug' on my log the 'vservername' is listed as localhost.localdomain
I took this 1 step further.
I added to my default the following lines:

# DEFAULT FOR PORT 443

NameVirtualHost *:443
<IfModule mod_ssl.c>
<VirtualHost *:443>
	ServerAdmin webmaster@localhost
	
[B]RewriteEngine on
RewriteRule . - [R=403][/B]

Now if I request [https://myIP](https://myIP) it does not take me to /var/www but it just says "Forbidden"

---

### Post by CharlesA on 2012-03-27
Certificates cannot be signed with the IP of the machine, they are signed using the domain name. You'd need to sign it using the domain name of the machine, which wouldn't be localhost.localdomain.

---

### Post by eawz9999 on 2012-03-27
My hostname is 'enrique-64' (the name of my machine).
When I get a chance I will issue a certificate under that name.
Will let you know, thank you.
Enrique

---

### Post by eawz9999 on 2012-03-27
Sorry but I still get this error:
_[warn] RSA server certificate CommonName (CN) `enrique-64' does NOT match server name_
'enrique-64' IS the name of my machine.
There is something I just don't fully understand.

---

### Post by CharlesA on 2012-03-27
Here you go:
[http://serverfault.com/questions/120889/apache-config-rsa-server-certificate-commonname-cn-not-match-server-name](http://serverfault.com/questions/120889/apache-config-rsa-server-certificate-commonname-cn-not-match-server-name)

---

### Post by eawz9999 on 2012-03-27
I defined ServerName in default vhost configuration.
As it happened when I signed the certificate localhost.localdomain the error is not longer in the apache log.
The only error I see is on the browser "Server Certificate does not match the **URL**", (not the servername).
It's not really that important since it does not affect apache or my virtual hosts. What bothers me is not to understand why this is happening.

To complete my information, this is the **/etc/hosts** file as written during ubuntu installation:

127.0.0.1	localhost.localdomain	localhost
::1	enrique-64	localhost6.localdomain6	localhost6
127.0.1.1	enrique-64


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I assume 'enrique-64' or 'localhost.localdomain' would have the same result as long as there is a 'server name' and a certificate that matches it.

---

### Post by eawz9999 on 2012-03-27
After studying this matter for a while, I decided to go back using ubuntu's generic certificate for my default vhost. Beside the certificate, I just had to change the ServerName to 'ubuntu'. In this way I do not disclose any unnecessary information in my certificate.
_No errors_ in apache2 logs. 
That_ it warns the user_ about not matching the URL... well, that's the way it is. To match the URL I would have to issue the certificate in my IP name (which you said is not possible) and been a dynamic IP it would have to be change every day.

---

### Post by eawz9999 on 2012-03-29
Thank you very much CharlesA for your help.
Enrique

---

