---
title: "Virtual hosts with two SSL certs, but only one works"
date: 2009-12-07
forum: Server Platforms
---

### Post by mrgordonz on 2009-12-07
Hi experts,

I have set up a relatively simple LAMP server (Ubuntu 8.04) which is used to host two Named Virtual Hosts (let's say they are mydomain.com and myotherdomain.net).  The server has a single public (ie: internet facing) IP address.  I don't own or manage the domains - they belong to my client.  My client provided me with an SSL certificate and a private key for each domain.  The certs are signed by VeriSign.

I have configured the virtual hosts as follows:

```
#
#  mydomain.com:80
#
<VirtualHost 123.123.123.123:80>
        ServerAdmin some.email@mydomain.com
        ServerName  mydomain.com
        ServerAlias www.mydomain.com

        # Indexes + Directory Root.
        DirectoryIndex index.php index.html
        DocumentRoot /home/myaccount/mydomain.com/

        # Logfiles
        ErrorLog  /home/myaccount/mydomain.com/logs/error.log
        CustomLog /home/myaccount/mydomain.com/logs/access.log combined
</VirtualHost>

#
#  mydomain.com:443
#
<VirtualHost 123.123.123.123:443>
        ServerAdmin some.email@mydomain.com
        ServerName  mydomain.com:443
        ServerAlias www.mydomain.com

        # Indexes + Directory Root.
        DirectoryIndex index.php index.html
        DocumentRoot /home/myaccount/mydomain.com/

        # SSL Config
        SSLEngine on
        SSLOptions +StrictRequire
        SSLCertificateFile /etc/ssl/certs/mydomain.com.crt
        SSLCertificateKeyFile /etc/ssl/private/mydomain.com.key

        # Logfiles
        ErrorLog  /home/myaccount/mydomain.com/logs/error.log
        CustomLog /home/myaccount/mydomain.com/logs/access.log combined
</VirtualHost>

#
#  myotherdomain.net:80
#
<VirtualHost 123.123.123.123:80>
        ServerAdmin some.email@mydomain.com
        ServerName  myotherdomain.net
        ServerAlias www.myotherdomain.net

        # Indexes + Directory Root.
        DirectoryIndex index.php index.html
        DocumentRoot /home/myaccount/myotherdomain.net/

        # Logfiles
        ErrorLog  /home/myaccount/myotherdomain.net/logs/error.log
        CustomLog /home/myaccount/myotherdomain.net/logs/access.log combined
</VirtualHost>

#
#  myotherdomain.net:443
#
<VirtualHost 123.123.123.123:443>
        ServerAdmin some.email@mydomain.com
        ServerName  myotherdomain.net:443
        ServerAlias www.myotherdomain.net

        # Indexes + Directory Root.
        DirectoryIndex index.php index.html
        DocumentRoot /home/myaccount/myotherdomain.net/

        # SSL Config
        SSLEngine on
        SSLOptions +StrictRequire
        SSLCertificateFile /etc/ssl/certs/myotherdomain.net.crt
        SSLCertificateKeyFile /etc/ssl/private/myotherdomain.net.key

        # Logfiles
        ErrorLog  /home/myaccount/myotherdomain.net/logs/error.log
        CustomLog /home/myaccount/myotherdomain.net/logs/access.log combined
</VirtualHost>

```

The problem I am experiencing is that when I browse to [https://www.mydomain.com](https://www.mydomain.com) SSL works fine, but when I browse to [https://www.myotherdomain.net](https://www.myotherdomain.net) I get the following certificate error:

```
www.myotherdomain.net uses an invalid security certificate.

The certificate is only valid for mydomain.com.

(Error code: ssl_error_bad_cert_domain)

```

I have double-checked the actual certificates and they are the correct certificates for each domain.

Any ideas why the certificate for myotherdomain.net is being ignored?

Cheers,

Paul

---

### Post by windependence on 2009-12-07
Unfortunately, SSL only works for one host when using named virtual hosts.

[http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html](http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html)

> **Why can't I use SSL with name-based/non-IP-based virtual hosts?**

 The reason is very technical, and a somewhat "chicken and egg" problem.      The SSL protocol layer stays below the HTTP protocol layer and      encapsulates HTTP. When an SSL connection (HTTPS) is established     Apache/mod_ssl has to negotiate the SSL protocol parameters with the     client. For this, mod_ssl has to consult the configuration of the virtual     server (for instance it has to look for the cipher suite, the server     certificate, etc.). But in order to go to the correct virtual server     Apache has to know the Host HTTP header field. To do this, the     HTTP request header has to be read. This cannot be done before the SSL     handshake is finished, but the information is needed in order to      complete the SSL handshake phase. Bingo!
   **Why is it not possible to use Name-Based Virtual Hosting to identify different SSL virtual hosts?**

     Name-Based Virtual Hosting is a very popular method of identifying     different virtual hosts. It allows you to use the same IP address and     the same port number for many different sites. When people move on to     SSL, it seems natural to assume that the same method can be used to have     lots of different SSL virtual hosts on the same server.
      It is possible, but only if using a 2.2.12 or later web server,     built with 0.9.8j or later OpenSSL.  This is because it requires a     feature that only the most recent revisions of the SSL     specification added, called Server Name Indication (SNI).
      The reason is that the SSL protocol is a separate layer which     encapsulates the HTTP protocol. So the SSL session is a separate      transaction, that takes place before the HTTP session has begun.      The server receives an SSL request on IP address X and port Y      (usually 443). Since the SSL request did not contain any Host:      field, the server had no way to decide which SSL virtual host to use.     Usually, it just used the first one it found which matched the      port and IP address specified.
      If you are using a version of the web server and OpenSSL that     support SNI, though, and the client's browser also supports SNI,     then the hostname is included in the original SSL request, and the     web server can select the correct SSL virtual host.
      You can, of course, use Name-Based Virtual Hosting to identify many     non-SSL virtual hosts (all on port 80, for example) and then      have a single SSL virtual host (on port 443). But if you do this,     you must make sure to put the non-SSL port number on the NameVirtualHost     directive, e.g.
              NameVirtualHost 192.168.1.1:80     

          Other workaround solutions include: 
      Using separate IP addresses for different SSL hosts.      Using different port numbers for different SSL hosts.


-Tim

---

### Post by mrgordonz on 2009-12-07
> **windependence said:**
> Unfortunately, SSL only works for one host when using named virtual hosts.

[http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html](http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html)



-Tim

Hmmm - that is a real poo poo.  I have checked my server and I am running Apache 2.2.8.  Is it a simple process to upgrade to 2.2.12 (or later)?  I'm not sure how to determine the version of OpenSSL - how do I find out and can this also be upgraded if necessary?

Cheers,

Paul

UPDATE:  I have just identified the version of OpenSSL: 0.9.8g.  How do I upgrade this?

---

### Post by windependence on 2009-12-07
If there isn't a later version in the repositories, you'll have to compile it from source. It's not hard, the instructions are on the OpenSSL site:

[http://www.openssl.org/source/](http://www.openssl.org/source/)

-Tim

---

### Post by HighCommander540 on 2009-12-07
> **windependence said:**
> If there isn't a later version in the repositories, you'll have to compile it from source. It's not hard, the instructions are on the OpenSSL site:

[http://www.openssl.org/source/](http://www.openssl.org/source/)

-Tim
Also, like the tutorial says. The browser you are using would have to support it as well. That is one of the things, I don't like about the Ubuntu repository. It is always way behind. I know its supposed to rely on stable versions, but there are stables versions that are so far behind.

---

### Post by windependence on 2009-12-07
I know what you mean, but you should see how far Debian is behind. Therein lies the problem. The Red Hat based distros are much further ahead  because of this. Personally, I use BSD for that reason also. Ubuntu goes on all my Zimbra servers, but FreeBSD on everything else.

-Tim

---

### Post by mrgordonz on 2009-12-07
Hi Tim,

Thanks for your help - I think I will go with different port numbers.

Cheers,

Paul

---

