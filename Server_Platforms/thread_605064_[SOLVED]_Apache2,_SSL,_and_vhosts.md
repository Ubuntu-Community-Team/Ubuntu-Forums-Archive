---
title: "[SOLVED] Apache2, SSL, and vhosts"
date: 2007-11-06
forum: Server Platforms
---

### Post by alimadzi on 2007-11-06
I was hoping to get everything working without starting my own discussion thread.  However, I'm still having problems even after reading about five different sources of documentation and at least 20 existing forum threads on this site.

I'm using Ubuntu 6.06 LTS server with Apache2.  I've enabled SSL (a2enmod ssl) and added "Listen 443" to ports.conf.  I'm trying to generate and install a self-signed certificate on a site.

One point of confusion is PEM files vs CRT files.  Here's one of my sources that uses PEM:

[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

And here's one that uses CRT:

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

So let's start there.  Which cert file type should i use or does it matter?  Why can we just have a PEM file without a key file, but CRT files always have KEY files associated with them?

Thanks in advance.  I'll post my vhosts files, but I want to try to get on the right track first.

---

### Post by MJN on 2007-11-06
Don't be confused by the differing .extensions - remember the extension bears no meaning other than human friendliness - changing the extension doesn't change the file type.

PEM is simply the *encoding* of the file hence a certificate can be PEM encoded and be called .crt or .pem or .anything.

The issues of keys and certificate is that a certificate may or may not include the private key - if the file contains both then it is referenced in Apache using the SSLCertificateFile directive, if you've got a seperate key and certificate then you must use the SSLCertificateFile AND SSLCertificateKeyFile directives.

If you are going to follow HowTo's then follow just the one as this is one area where there are many ways to skin the cat!

Does that make any more sense?

Mathew

---

### Post by alimadzi on 2007-11-06
Yeah, that makes more sense.

Now I have a question about what's possible with Apache2.  I'm planning to serve at least eight sites using one Apache2 install.  Most of them will be HTTP and use named vhosts on the same IP address.  At least two will have dedicated IP addresses and be served via HTTPS (one w/ a trusted cert and the other with a self-signed cert since it's for internal use only).   So can this work with Apache2?

I haven't read anything that says I can't do this, but I also haven't found any tutorials detailing exactly what I have in mind either.  Every tutorial I've seen about SSL and Apache2 uses "*:443" and not an IP address or hostname.

Thanks in advance.

-Patrick

---

### Post by MJN on 2007-11-06
As long as you have a unique IP per site then you'll be okay.

The 'problem' with SSL is that you are unable to use name-based virtual hosting (i.e. multiple names, single IP). This is because the SSL connection is established between the client and server *before* the HTTP protocol is underway. Hence Apache does not know what site is being asked for (using the HTTP_HOST header) by the client until after the encrypted tunnel is established, yet it needs to know which site is being asked for in order to serve the right certificate/key (issuing the wrong credentials will cause the client to throw a warning). Chicked and egg situation.

You are fortunate that you have multiple IPs available so each site can reside on its own IP. The DNS then dictates which name goes to which address hence Apache then knows which site is being requested and can set up the tunnel accordingly.

You will need to substitute your IP for the * in *:443 for your HTTPS sites.

Mathew

---

### Post by alimadzi on 2007-11-06
OK, good.  I feel better now.  I've read all the official vhosts documentation on the Apache site and I was pretty sure that what I wanted to do could actually work.  And I was careful to assign a unique IP to each HTTPS site.  I just hadn't seen a complete working example config anywhere.

So now that I know it's possible, I'll clean up my vhosts files and post them for review.  At this point I really don't know where the problem lies, but it's probably something simple (I hope).

Config files to be posted shortly...

---

### Post by alimadzi on 2007-11-06
OK, I'm using the following tutorial since it's been referenced in many other threads on this site (usually followed by "Yay, thanks!  Worked perfectly..."):

[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

I've taken care of all the obvious stuff like enabling the site, enabling SSL, adding "Listen 443" to ports.conf, and restarting Apache.  I also set the common name on the self-signed cert to match the ServerName in the vhost.  Here's my vhosts file:

```

NameVirtualHost 69.55.238.170:80
<VirtualHost 69.55.238.170:80>
        ServerName tools.idahostatesman.com
        ServerAlias *.tools.idahostatesman.com
        DocumentRoot /var/www/tools.idahostatesman.com/public_html

        CustomLog /var/log/apache2/tools.idahostatesman.com:80-access.log combined
        ErrorLog /var/log/apache2/tools.idahostatesman.com:80-error.log
        LogLevel warn
</VirtualHost>

NameVirtualHost 69.55.238.170:443
<VirtualHost 69.55.238.170:443>
        ServerName tools.idahostatesman.com
        ServerAlias *.tools.idahostatesman.com
        DocumentRoot /var/www/tools.idahostatesman.com/public_html

        CustomLog /var/log/apache2/tools.idahostatesman.com-access.log combined
        ErrorLog /var/log/apache2/tools.idahostatesman.com-error.log
        LogLevel warn

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.pem
</VirtualHost>

```

So right now I'm just trying to make the same site available with and without SSL.  Step two will be to force SSL and step three will be to restrict access just to our company's IP address (since this will eventually be for internal use only).  But for now I just want to get SSL working properly.

The site is available without SSL using either the hostname or the IP:

[http://tools.idahostatesman.com/](http://tools.idahostatesman.com/)
[http://69.55.238.170/](http://69.55.238.170/)

You should simply see the word 'tools' in the browser window for both of those links.

Trying SSL with either the hostname or the IP results in Firefox timing out.  No error message other than "Problem loading page":

[https://tools.idahostatesman.com/](https://tools.idahostatesman.com/)
[https://69.55.238.170/](https://69.55.238.170/)

The log files show hits on port 80, but none on 443.

Any ideas?  Any obvious mistakes I'm making in my vhosts file?  Any other info you need to figure this out?  Thanks in advance.  I really appreciate it.

---

### Post by MJN on 2007-11-07
Is there a firewall/router blocking port 443? Also, how did you create the certificates?

I am curious as to why the logs are showing nothing (try upping the log level) - this leads me to think requests aren't even getting as far as your server.

Mathew

---

### Post by alimadzi on 2007-11-07
The web host tells me there's nothing blocking port 443, but I'm starting to have my doubts.  How can I know for sure?

To generate the certificate, I used the following command:

```
apache2-ssl-certificate -days 365
```

I changed the log level to 'debug', restarted Apache, and got these items in the error log:

```

root@idahostatesman:/var/log/apache2# cat tools.idahostatesman.com-error.log 
[Wed Nov 07 07:56:06 2007] [info] Loading certificate & private key of SSL-aware server
[Wed Nov 07 07:56:06 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_pphrase.c(469): unencrypted RSA private key - pass phrase not required
[Wed Nov 07 07:56:06 2007] [info] Configuring server for SSL protocol
[Wed Nov 07 07:56:06 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_init.c(405): Creating new SSL context (protocols: SSLv2, SSLv3, TLSv1)
[Wed Nov 07 07:56:06 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_init.c(588): Configuring permitted SSL ciphers [ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL]
[Wed Nov 07 07:56:06 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_init.c(716): Configuring RSA server certificate
[Wed Nov 07 07:56:06 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_init.c(755): Configuring RSA server private key
[Wed Nov 07 07:56:07 2007] [info] Loading certificate & private key of SSL-aware server
[Wed Nov 07 07:56:07 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_pphrase.c(469): unencrypted RSA private key - pass phrase not required
[Wed Nov 07 07:56:07 2007] [info] Configuring server for SSL protocol
[Wed Nov 07 07:56:07 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_init.c(405): Creating new SSL context (protocols: SSLv2, SSLv3, TLSv1)
[Wed Nov 07 07:56:07 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_init.c(588): Configuring permitted SSL ciphers [ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL]
[Wed Nov 07 07:56:07 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_init.c(716): Configuring RSA server certificate
[Wed Nov 07 07:56:07 2007] [debug] /build/buildd/apache2-2.0.55/build-tree/apache2/modules/ssl/ssl_engine_init.c(755): Configuring RSA server private key
```

Does this help at all in isolating the problem?  Thanks.

---

### Post by MJN on 2007-11-07
Can you connect to the https site **from the server**?
 
Alternatively, you could try commenting out the port 80 vhost stuff, and changing the port 443 to 80. Hence now you'd be running HTTPS over port (hopefully avoiding any potential port blocking) but note that you'd need to specify the address as [https://69.55.238.170:443/](https://69.55.238.170:443/)
 
Mathew

---

### Post by alimadzi on 2007-11-07
I don't have a GUI installed on the server, so I can't use a browser locally.  Not really sure how to attempt a secure connection to a local site from the command line?  Which command would I use?

Didn't quite follow the part about changing port 443 to 80, but that's all right.  I really need to make sure port 443 is accessible anyway.

Thanks.

---

### Post by alimadzi on 2007-11-07
I got it working and I feel dumb.  It was iptables... which in my defense, I know nearly nothing about.  As soon as I ran 'iptables -F', I lost the connection and had to restart the VPS, but as soon as it came back up, I could connect via HTTPS without any problem or delay.

I've restored the original set of rules and figured out how to open port 443 with the following reference:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Thanks again for your help.  I'll probably have more questions to post later on, but I think I'm in good shape on this for now.  Just need to read everything I can about iptables to make sure I configure the firewall properly.

---

### Post by MJN on 2007-11-08
That's great news - good to hear you've got it working.
 
I'll keep an eye out for the inevitable subsequent posts, although it has to be said you're over the worst of it now!
 
Mathew

---

### Post by MJN on 2007-11-08
> **alimadzi said:**
> I don't have a GUI installed on the server, so I can't use a browser locally. Not really sure how to attempt a secure connection to a local site from the command line? Which command would I use?
 
I forgot to answer this bit but it might be useful for you to know for the future...
 
If you issue the command **openssl s_client localhost:443** and then **GET** then you will see the low-level SSL handshaking and the tunneled HTTP traffic.
 
Mathew

---

### Post by alimadzi on 2007-11-08
That's a very informative command, but I had to tweak it a little bit to get it to execute properly.  Here's what I used:

```
openssl s_client -connect tools.idahostatesman.com:443
```

I've also made the changes needed to force SSL and restrict access just to our corporate IP address, so the links aren't going to work any more.

Thanks again for your help.  I definitely feel like I'm over the worst of it now and I have a better grasp of how to troubleshoot this sort of thing in the future.  And I love all the little Apache utilities baked into Ubuntu like a2enmod, a2ensite, etc.  Makes web server admin work a lot easier.  Ubuntu rocks!

---

### Post by MJN on 2007-11-08
Ah yes, you spotted my deliberate mistake... ;)

---

