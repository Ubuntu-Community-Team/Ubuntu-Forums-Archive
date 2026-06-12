---
title: "Installing an SSL certificate from a vendor"
date: 2013-11-18
forum: Server Platforms
---

### Post by aysiu on 2013-11-18
Does anyone have a good tutorial for dummies on using commercial SSL certificates on a Ubuntu server?

I see a lot of tutorials for self-signed certificates, but not a lot for commercial ones.

I guess something like [this](http://blogs.reliablepenguin.com/2012/12/18/install-ssl-certificate-apache-centos-rhel), except for Ubuntu, instead of CentOS.

Thanks in advance!

---

### Post by koenn on 2013-11-18
as for a webserver, to run a  https site?  or more general than that ?

---

### Post by aysiu on 2013-11-18
Yes, for https

---

### Post by sandyd on 2013-11-18
> **aysiu said:**
> Yes, for https

What server software and SSL Certificate provider
Some have intermediary certificates (e.x. Globalsign AlphaSSL) that you have to combine, depending on what webserver software you are using

---

### Post by CharlesA on 2013-11-18
> **sandyd said:**
> What server software and SSL Certificate provider
Some have intermediary certificates (e.x. Globalsign AlphaSSL) that you have to combine, depending on what webserver software you are using

In addition to this, the CA I use offers some excellent instructions for both Apache and Nginx.
[http://www.startssl.com/?app=20](http://www.startssl.com/?app=20)

But yeah, it would help to know what web server you are running and which CA (mine needs to have an intermediary cert added to the public one).

---

### Post by aysiu on 2013-11-19
Ubuntu Server 13.10 and Network Solutions. I don't really need a lot of hand-holding... just a solid tutorial you can link me to. Thanks!

---

### Post by CharlesA on 2013-11-19
> **aysiu said:**
> Ubuntu Server 13.10 and Network Solutions. I don't really need a lot of hand-holding... just a solid tutorial you can link me to. Thanks!

Are you using Apache on this box?

If so they have some instructions [here]("http://www.networksolutions.com/support/installation-of-an-ev-ssl-certificate-on-apache-mod-ssl-openssl/"), but they are kinda lacking.

The procedure is similar to the link I posted above from startssl, but I find their documentation easier to understand.

check this page out too:
[http://www.unixmen.com/install-apache-ssl-ubuntu-13-10/](http://www.unixmen.com/install-apache-ssl-ubuntu-13-10/)

---

### Post by aysiu on 2013-11-19
Unfortunately, neither of those works. I did check out the official Network Solutions instructions, but they didn't seem to work. The second link seems to be just a self-signed non-commercial certificate. Thanks, though.

---

### Post by CharlesA on 2013-11-19
What error were you getting when you tried using the official documentation?

---

### Post by koenn on 2013-11-19
> **aysiu said:**
> Ubuntu Server 13.10 and Network Solutions. I don't really need a lot of hand-holding... just a solid tutorial you can link me to. Thanks!

I don't have a tutorial handy, but maybe you can write one afterwards :-)
Essentially, it's the same as the tutorials you find about https with self-signed certs/private PKI, minus all the hasle to create the certificates. It's just that you have to know where the PKI stuff ends and the webserver config begins. I think that's your problem. 

Mostly from memory so possibly incomplete but it'll get you started and there's bound to be people here who can fill in the gaps :

Asuming Ubuntu server and apache :

- enable apache ssl  module ```
a2enmod ssl
```

- get certificates from a CA
- copy the certificates to your webserver.
where should you put them ? I've seen documentation that says /etc/ssl/certs and /etc/ssl/private  or something, and other that says /etc/apache2/ssl
if you're just doing web, I'd go with /etc/apache2/ssl

- create a suitable virtual host definition, eg by editing /etc/apache2/sites-available/default-ssl
comment out or delete the part that references the certificates, and replace those with the paths and filenames of your certs (the ones you copied in the previous step)

```

        SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key

```

This is the tricky part :  depending on what certificates you got, you may also need to describe tho whole "chain of trust" with 
```
SSLCertificateChainFile      /etc/ ... /some_intermediate_cert
``` 
It's likely the CA that supplied your certificates has more detailed instructions on this. 
The Centos tutorial may be of help too - this is not going to differ significantly between distros, it's just a matter telling apache where to find the files


-enable the default https site (or the one you created) : ```
 a2ensite default-ssl 
```
- restart apache ```
service apache2 restart
```

obviously, all of this is work for root, so you need to "sudo" all the commands.

---

### Post by aysiu on 2013-11-19
CharlesA, no error on the server side, but the client side still throws up errors about a mismatched certificate.

koenn, thanks for that breakdown. I'll give that a shot and try to piece it all together.

---

### Post by koenn on 2013-11-19
> **aysiu said:**
>  the client side still throws up errors about a mismatched certificate.
.

have a close look at that error. 

The certificate on your server is supposed to identify/authenticate your server, for the beneifit of the clients (eg so that users don't send their credentials to a rogue server). That's the primary purpose of those certs. So the server cert will contain the FQDN of the server (in principle; there exist "wildcard" certs), and the clients have to approach it using that same FQDN. If they don't, they'll get a security warning about a name mismatch, telling them "this may not be the server you think it is, are you sure you want to go there ?"

So if your server is certified 'www.orangecat.com' but you test it with  URLs like  'localhost' or an IP address or anything that is not that specific name , you'll get that warning.

---

### Post by CharlesA on 2013-11-20
If this is a public site, you can always check the SSL stuff with SSL labs:
[https://www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/)

---

### Post by aysiu on 2013-11-20
Thanks for all the help and suggestions. A lot of stuff to work on and test, so I don't know when I'll be posting back on this thread again, but I do very much appreciate the help.

---

