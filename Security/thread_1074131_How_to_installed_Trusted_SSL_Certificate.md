---
title: "How to installed Trusted SSL Certificate?"
date: 2009-02-18
forum: Security
---

### Post by chsmith700 on 2009-02-18
Hello,

The time has come that I need a trusted SSL certificate. Basically I dont want any exceptions, or validations on my customers browser. Want them to be able to go into their secure page and buy products.

So, I was thinking about getting the Godaddy SSL certificate, is there a how to on installing this onto a Ubuntu server?

---

### Post by xTourniquet on 2009-04-16
I'm trying to tackle this as well. I found a decent write up that may help you. 

Creating a Ubuntu CSR for Go Daddy
[http://www.mygeekproject.com/?p=8](http://www.mygeekproject.com/?p=8)

> 
I had to get a SSL certificate for a web site of mine yesterday. I decided to get another SSL certificate from GoDaddy. Here are my notes for getting the certificate.

I went ahead and created a folder to make all of my work in so that I could zip it up later or have the Rsync server grab it and save it in the main infrastructure.

```
mkdir /root/certificate_godaddy
```
This will generate the randomized string create the csr.

```
openssl genrsa -out domain_name.key 1024
```
This will create the CSR for GoDaddy which will you will need to copy and paste into their site. If you are going to be requesting a Wild Card SSL make sure that the NAME is *.domain_name.com

```
openssl req -new -key domain_name.key -out domain_name.csr
```
Now log into the GoDaddy site and paste the contents from the above CSR into their site. When you get the email back I suggest putting the 2 files they give you in the same location as you created the above. You will most likely have the following files.

[I]domain_name.com.crt
gd_bundle.crt
[/I]
With those files you will need to setup the SSL virtual host like the below:
```

<VirtualHost *:443>
        ServerName subdomain.domain_name.com
        ServerAdmin user@domain.com
        DocumentRoot "/home/user/vhosts/site_down"
        DirectoryIndex index.html index.php
        ErrorLog /var/log/apache2/secure_domain_name_error.log
        <IfModule mod_ssl.c>
                SSLEngine On
                [B]SSLCertificateFile "/home/user/csr/_.domain_name.com.crt"
                SSLCertificateKeyFile "/home/user/csr/domain_name.com.key"
                SSLCertificateChainFile "/home/user/csr/gd_bundle.crt"[/B]
        </IfModule>
        .. The rest of your config file
</VirtualHost>

```
From here you should have no problems with the GoDaddy certificate. Hope this helps everyone.


---

