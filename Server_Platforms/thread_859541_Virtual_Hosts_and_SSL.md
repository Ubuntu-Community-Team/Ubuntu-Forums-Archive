---
title: "Virtual Hosts and SSL"
date: 2008-07-14
forum: Server Platforms
---

### Post by Jerim on 2008-07-14
I am running Ubuntu Server 8.04 with Apache. I am hosting several virtual hosts. I am trying to install SSL for one of those virtual hosts. I have gone through several guides. Most are outdated mentioning httpd.conf when apache2.conf is all that is needed. 

I have "Listen 443" in apache2.conf. I have SSLEngineOn in the /etc/apache2/sites-enabled/www.domain.com.conf file. I have created the .crt and .key files. I have loaded them in the [www.domain.com.conf](www.domain.com.conf) file.

However, when I try to go to [https://www.domain.com](https://www.domain.com), it just tells me the page can not be display. I can access it with [http://www.domain.com](http://www.domain.com). Is there current guide out there anywhere that works?

---

### Post by skunkbad on 2008-07-14
If you are trying to use SSL with name based virtual hosts, it can't be done according to Apache. If you are using IP based virtual hosts, then somebody else will have to chime in.

---

### Post by windependence on 2008-07-14
Well you can do it, but you can only have one SSL virtual host enabled. You can have as many others as you want but they can't be defined using a blanket directive:

<virtual host *80>

> **Why can't I use SSL with name-based/non-IP-based virtual hosts?**
The reason is very technical, and a somewhat "chicken and egg" problem. The SSL protocol layer stays below the HTTP protocol layer and encapsulates HTTP. When an SSL connection (HTTPS) is established Apache/mod_ssl has to negotiate the SSL protocol parameters with the client. For this, mod_ssl has to consult the configuration of the virtual server (for instance it has to look for the cipher suite, the server certificate, etc.). But in order to go to the correct virtual server Apache has to know the Host HTTP header field. To do this, the HTTP request header has to be read. This cannot be done before the SSL handshake is finished, but the information is needed in order to complete the SSL handshake phase. Bingo!

**Why is it not possible to use Name-Based Virtual Hosting to identify different SSL virtual hosts?**
Name-Based Virtual Hosting is a very popular method of identifying different virtual hosts. It allows you to use the same IP address and the same port number for many different sites. When people move on to SSL, it seems natural to assume that the same method can be used to have lots of different SSL virtual hosts on the same server.

It comes as rather a shock to learn that it is impossible.

The reason is that the SSL protocol is a separate layer which encapsulates the HTTP protocol. So the SSL session is a separate transaction, that takes place before the HTTP session has begun. The server receives an SSL request on IP address X and port Y (usually 443). Since the SSL request does not contain any Host: field, the server has no way to decide which SSL virtual host to use. Usually, it will just use the first one it finds, which matches the port and IP address specified.

[I]You can, of course, use Name-Based Virtual Hosting to identify many non-SSL virtual hosts (all on port 80, for example) and then have a single SSL virtual host (on port 443). But if you do this, you must make sure to put the non-SSL port number on the NameVirtualHost directive, e.g.

NameVirtualHost 192.168.1.1:80[/I] 

[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#vhosts](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#vhosts) 

-Tim

---

### Post by skunkbad on 2008-07-15
Hey Jerim,
Can you please share links to the tutorials you were looking at?

---

### Post by Jerim on 2008-07-15
Thanks, that honestly helps me a lot. I have never setup SSL before so I wasn't aware of that. So right now I am targeting my efforts on setting up only one domain with SSL. I am wondering if my thinking is off though. Instead of setting up the domain with SSL, is the concept more related to setting up the server with SSL?

I took over a server from someone else. The server has about 40 virtual hosts, each a seperate domain. One domain was used as the SSL domain and all sites needing SSL were funneled to it. For instance, let's say the SSL domain is ssl.domain.com. Then there are a few sites such as [www.foo.com](www.foo.com) and [www.bar.com](www.bar.com). On each site is an order link which takes you to ssl.domain.com for the actual ordering. 

We had a server attack a while back, and I have been trying to get the SSL set back up on ssl.domain.com. But to be honest, I just haven't been able to get anything to work.

---

### Post by Jerim on 2008-07-15
> **skunkbad said:**
> Hey Jerim,
Can you please share links to the tutorials you were looking at?

[http://www.debian-administration.org/articles/349](http://www.debian-administration.org/articles/349)
[http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu](http://www.linode.com/wiki/index.php/Apache2_SSL_in_Ubuntu)
[http://ubuntuforums.org/archive/index.php/t-4466.html](http://ubuntuforums.org/archive/index.php/t-4466.html)
[http://www.securityfocus.com/infocus/1818](http://www.securityfocus.com/infocus/1818)
[http://www.ornl.gov/~jar/Apache/SSL_in_Apache_2.html](http://www.ornl.gov/~jar/Apache/SSL_in_Apache_2.html)

I also have used the texts Apache2 Bible, and Pro Apache Pro Edition. 

I believe my main issue is that I am not quite sure how to setup a virtualhost. I had been using the syntax <VirtualHost *:*>, then I tried <VirtualHost *:80> and right now I am on <VirtualHost www.domain.com>. Please keep in mind that I have a [www.domain.com.conf](www.domain.com.conf) file for each virtual host, so I start each [www.domain.com.conf](www.domain.com.conf) file off with <VirtualHost www.domain.com>

---

### Post by Jerim on 2008-07-17
Anyone have any ideas? I am willing to post my apache2.conf file as well as an exampled [www.domain.com.conf](www.domain.com.conf) file if anyone feels that will help. I have been working on this issue a little at a time for a couple of months. 

Can someone who has SSL working show me your apache2.conf file and an example [www.domain.com.conf](www.domain.com.conf) file? I just want to take a look at a working system.

I can give SSH access to anyone who wants to look or if someone has a test system up and running, I would like to SSH in and just take a look at the settings. I feel that there is some crucial, yet easily overlooked step that I am missing.

---

### Post by Kolipoki on 2008-07-17
This is a mighty interesting topic (also noob here). I wonder how hosting companies do it, as it seems they can host multiple HTTPS sites in a physical server. There must be some kind of workaround.

---

### Post by Jerim on 2008-07-17
I agree, there has to be a way to do it, but I just haven't found anything that works. My experience is that there are usually multiple ways of setting things like SSL up, but the procedure for setting it up one way versus the other requires changes to a handfull of files instead of just the ones mentioned. I have found guides that explain how to setup SSL but they don't seem to take into account the way all the settings need to be setup in multiple files. They usually just focus on setting it up in apache2.conf but not how to set it up in [www.domain.com.conf](www.domain.com.conf) for instance. This has lead to me trying one thing but it not working because the guide didn't explain that another file has to be setup another way.

Also, most of the guides I have seen for SSL on apache2 talk about editing httpd.conf, however httpd.conf is no longer used from what I understand. You can still use httpd.conf for some settings as you wish, but most of the configuration takes place in apache2.conf and [www.domain.com.conf](www.domain.com.conf) from what I have gathered. I am looking for a guide that covers all settings for apache2.

---

### Post by amenszer on 2008-07-17
Here is my vhost file that uses an SSL certificate. This works. Hope it helps you out.

```

NameVirtualHost *:443
<VirtualHost *:443>
        ServerName companyname.com
        ServerAlias www.companyname.com
#        UseCanonicalName On
        ServerAdmin webmaster@localhost

        RewriteEngine on

        RewriteCond %{SERVER_NAME} ^www.companyname.com* [NC]
        RewriteRule ^.*$ https://companyname.com%{REQUEST_URI} [L,R]


        SSLEngine On
        SSLCertificateFile /etc/ssl/certs/companyname.com.crt
        SSLCertificateKeyFile /etc/ssl/certs/companyname.com.key
        SSLCACertificateFile /etc/ssl/certs/intermediate.crt

        ErrorLog /var/log/apache2/zeus-www.companyname.com.error.ssl.log
        CustomLog /var/log/apache2/zeus-www.companyname.com.access.ssl.log combined
        ProxyRequests Off
        ProxyVia Off

        <proxy *>
                Order deny,allow
                Deny from all
                Allow from all
        </proxy>

                ProxyPass / http://companyname.com/
                ProxyPassReverse / http://companyname.com/

</VirtualHost>

```

---

### Post by windependence on 2008-07-17
This will work, but will be the ONLY doamin able to do ssl access. I think the OP wants to do this on all his domains, and unfortunately with named based virtual hosting, I don't think this is possible.

-Tim

---

### Post by amenszer on 2008-07-17
Yes, you're right. However, the OP only mentions trying to do it with one vhost...if that is not the case, he can disregard my post. 

Thanks.

---

