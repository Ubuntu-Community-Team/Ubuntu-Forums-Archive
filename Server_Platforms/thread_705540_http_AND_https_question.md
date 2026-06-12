---
title: "http AND https question"
date: 2008-02-23
forum: Server Platforms
---

### Post by Hopworks on 2008-02-23
Greets all!

Quick question if I may...

It's been awhile since I set it up, but on my Feisty 7.04 server (LAMP config), I set up SSH and can't remember all that I did. It works though, but now everything I access on my LAMP from remote (on my local network) has to be https:// and was wondering where I should look to configure to be able to have http AND https served up.

For example, I have a folder on my LAMP that is the root of all things I access via my browser from remote, say, '/home/public/lanserver/'.  If I place a folder in there, say called 'test', I can go to it via browser at address [https://mydomain/test/index.php](https://mydomain/test/index.php). I like the https for some subfolders of that root folder, but not all. Is it possible via a config file somewhere for SSH to have some subfolders flagged for SSH and some not?

I hope I gave enough info for an answer.

Thank you for your time!

Hop

---

### Post by HermanAB on 2008-02-23
Here you go:
[http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html](http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html)

---

### Post by k_grdn on 2008-02-23
Hi,

Think you mean ssl not ssh, anyway I suggest you do some googling and review the link kindly provided but briefly.

For http sites set your Virtualhost directive to listen port :80 for ssl sites :443.


State both these directives in the same vhost file for your site.

NameVirtualHost *:443
<Virtualhost *:443>
ServerName MyDomain
DocumentRoot /home/public/lanserver

  <IfModule mod_ssl.c>
      SSLEngine on
      SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
      SSLCertificateFile /etc/apache2/ssl/server.crt
      SSLCertificateKeyFile /etc/apache2/ssl/server.key
  </IfModule>

(Not required if you use rewrites, dir specific)
   <Directory /home/public/lanserver/test>
      SSLVerifyClient require
      SSLVerifyDepth 1
  </Directory>


<VirtualHost *>
ServerName MyDomain
DocumentRoot /home/public/lanserver/

Use rewrites to https specific dirs, also you need to generate certs with openssl and place keys in dirs (Do a recap on your initial SSL config).

Regards,

k_grdn

---

### Post by Hopworks on 2008-02-27
Thank you two for the help. I have some reading to do so I can better understand what you provided, but it is something I want to know and definitely worth it.

That's exactly what I want though, ssl and non-ssl on the same virtual host.

I said SSH, because I thought they were related. In my Webmin, I see a SSH Server and I thought I used that somewhere in the process when I created my local ssl certificates.

It's frustrating being a newbie at anything worth learning.

Hop

---

