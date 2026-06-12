---
title: "how to make subdomain secure?"
date: 2008-12-16
forum: Server Platforms
---

### Post by kustomjs on 2008-12-16
Hi Guys
I just want to know how can I make the subdomain secure? like [https://secure.jbodyconnection.com](https://secure.jbodyconnection.com)

---

### Post by kustomjs on 2008-12-17
anybody?

---

### Post by HermanAB on 2008-12-17
Enable SSL in Apache (needs a fixed IP address) and create a redirect from http to https.

Hope that helps!

Herman

---

### Post by kustomjs on 2008-12-17
well I got 2 domains needs to be secured.

---

### Post by kustomjs on 2008-12-18
can i use virtual host or what?

---

### Post by kustomjs on 2008-12-18
I guess I wount get that much help I guess.

---

### Post by kustomjs on 2008-12-19
can somebody please help that would be really great. Thanks

---

### Post by martien on 2008-12-19
> **kustomjs said:**
> can somebody please help that would be really great. Thanks
First create ssl certificate using openssl or buy one (if you want). Then move the files to folder, that apache user has access to. Make sure you have mod_ssl enabled for apache. Then in your configuration add something like this:
```

NameVirtualHost [your ip_or_*_for_everything]:443
<VirtualHost [the value of the previous line]>
ServerAdmin someone@somedomain.com
ServerName [yourdomain/subdomainname]
DocumentRoot /path/to/www/dir
SSLEngine On
SSLCertificateKeyFile /path/to/key/file.key
SSLCertificateFile /path/to/cert/file.cert  
SSLCACertificateFile /path/to/ca/cert/file.cert
</VirtualHost>

``` 
If you want to have a SSL log file add something like this:
```
SSLLogFile /path/to/logs/ssl.log
```
The only thing you have to do is to search for Self signed certificates over the internet. (to be able to create the certificate. It's important to create Self signed cert, cause in other case apache could not be able to start).
Basic thats all. Good luck.

---

### Post by kustomjs on 2008-12-19
thanks martien for your help.

---

### Post by kustomjs on 2008-12-20
I got a other question how would I do 2 different SSL's and they are on different domain names?

like say [https://secure.yourdomain1.com](https://secure.yourdomain1.com)
then other on [https://secure.yourdomain2.com](https://secure.yourdomain2.com) 

would I just do the same steps over or not to create the SSL?

and here what I want to use:[http://www.startssl.com/?app=21](http://www.startssl.com/?app=21)

---

### Post by killerdragon on 2008-12-21
> **kustomjs said:**
> I got a other question how would I do 2 different SSL's and they are on different domain names?

like say [https://secure.yourdomain1.com](https://secure.yourdomain1.com)
then other on [https://secure.yourdomain2.com](https://secure.yourdomain2.com) 

would I just do the same steps over or not to create the SSL?

and here what I want to use:[http://www.startssl.com/?app=21](http://www.startssl.com/?app=21)

Simple answer, you can't. Chicken and the egg problem, basically the packet comes encrypted to mod_ssl, and since it doesn't know which SSL cert to use..it just uses the first one it knows about.

But there must be a way right?
Yes, 3 options:
Use a static IP address for each secure site (they must be publicly accessible!):
200.x.x.x = [https://site1.com](https://site1.com)
201.x.x.x = [https://site2.com](https://site2.com)

Second option is to run multiple Apache instances (who would do that?). And each Apache instance would use its own SSL cert.

Last option is to run each vhost on a different port, but use mod_proxy to proxy them from port 443 (in theory this would work, but never tried it).

However, for some serious $$$, some cert signers will allow you to put multiple domains in one cert. Even though really it doesn't cost them any extra...eh I'll leave my opinions out of this thread :).

---

