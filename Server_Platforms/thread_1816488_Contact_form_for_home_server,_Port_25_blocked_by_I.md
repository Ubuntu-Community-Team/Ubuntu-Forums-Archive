---
title: "Contact form for home server, Port 25 blocked by ISP"
date: 2011-08-02
forum: Server Platforms
---

### Post by frenchtoast747 on 2011-08-02
I have been searching for an answer through several forums, google searches, etc for a week and I cannot find the answer I am looking for. 

In order for the PHP mail() function to work with Ubuntu I have read that you have to set up an SMTP server. So, I set up Postfix and after spending 3 days finally figured out that Sendmail wasn't completely uninstalled and was in fact still running and hogging port 25. 

After finally getting Postfix to work locally, I have come to find out that my ISP (att.net) has blocked port 25. I have tested this by trying to telnet into GoDaddy's and Yahoo's SMTP servers. I am getting a "connection timed out error" when trying to send mail via my PHP script.

My big question is this: is there any way that can easily enable me to have a contact form on my home server? I have been trying to learn how to relay to GoDaddy's server (how I registered my domain and email plan), but everything I try is not working. I have messed with so many settings that I am unsure that even if I get advice on how to correctly configure Postfix that it will work, so does "sudo apt-get --purge autoremove postfix" completely remove Postfix (including all added settings and files) so I can start out fresh?

Please forgive any bad syntax and/or semantics in this post. I am new to Ubuntu and this is my first post on a forum, normally google solves everything. ;)

Thanks in advance to any replies!

---

### Post by haqking on 2011-08-02
try port 587 instead, 25 is used for relaying more than anything.

---

### Post by frenchtoast747 on 2011-08-02
Well for my purpose, I finally got PEAR Mail to work. With GoDaddy at least, I didn't use their "relay-hosting.secureserver.net" ports 25, 465, or 587. 

What ended up working is "smtpout.secureserver.net" port 80 (with my GoDaddy login as authentication). I followed this tutorial using the "SSL" script (without the ssl:// prefix to GoDaddy's server) to get the php script: 
[URL="http://email.about.com/od/emailprogrammingtips/qt/PHP_Email_SMTP_Authentication.htm"]
http://email.about.com/od/emailprogrammingtips/qt/PHP_Email_SMTP_Authentication.htm[/URL]

A fix for some of my noobish mistakes in installing and using the PEAR php script:

```
sudo apt-get install pear-php
sudo pear install Mail
```Make sure to also install Net_SMTP
```

sudo pear install Net_SMTP
```After everything is installed, edit php.ini (at /etc/php5/apache2/php.ini) be sure to remove the semi-colon as well as be sure the path is correct:

```
; UNIX: "/path1:/path2"
include_path = *.:/usr/share/php"
```

Thanks for help!

---

