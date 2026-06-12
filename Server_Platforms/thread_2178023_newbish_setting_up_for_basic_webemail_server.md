---
title: "newbish setting up for basic web/email server"
date: 2013-10-01
forum: Server Platforms
---

### Post by nobodyfamous on 2013-10-01
I am tired of problems with shared hosting, so I signed up for a VPS.  I also don't want to pay for cPanel, I also don't need to provide a control panel to my customers.  I fully manage their websites.  It would be nice if I could provide them with an interface to setup emails/forwarders/auto-responders themselves, but it is not necessary.

I am only a little familiar with installing and setting up things like Apache2, mySQL, PHP5, phpMyAdmin, etc.  I can make it work, but I need to do just a bit more than that.

Things I need;
[LIST=1]
[*]Apache2 w/PHP & mySQL (phpMyAdmin)
[LIST]
[*]I need to serve more than 1 website.  I think these are called virtual hosts (example.com points to var/www/example.com/html/ and website.com points to var/www/website.com/html/ etc.)
[/LIST]

[*]IMAP & POP3 email
[LIST]
[*]I also would like to be able to connect securely, so need an ssl certificate.  Can I generate a self signed one for this purpose?
[/LIST]
[/LIST]

I think thats really it.

How hard is it to do this via command line/ssh by just editing the config files?  Previously with cPanel, I would just add domains to my account, add emails to domains, and occasionally set MX records to point to Google.

Looking for some advice on how to proceed. (good how to articles etc) So far Google has not been much help, I may not have the terminology right.

---

### Post by Lars Noodén on 2013-10-01
> **nobodyfamous said:**
> Things I need;
Apache2 w/PHP & mySQL (phpMyAdmin)
[LIST]
[*]I need to serve more than 1 website.  I think these are called virtual hosts (example.com points to var/www/example.com/html/ and website.com points to var/www/website.com/html/ etc.)
[/LIST]

If you are running default Ubuntu, there is a default virtual host configuration file in /etc/apache2/sites-enabled/000-default.conf   It will point to /var/www/ as the DocumentRoot, but you can change that if you think you will have more than one virtual host.  Just add new directories and then point to them as DocumentRoot, making a new configuration file for each virtual host.

---

### Post by lingpanda on 2013-10-01
> **nobodyfamous said:**
> I am tired of problems with shared hosting, so I signed up for a VPS.  I also don't want to pay for cPanel, I also don't need to provide a control panel to my customers.  I fully manage their websites.  It would be nice if I could provide them with an interface to setup emails/forwarders/auto-responders themselves, but it is not necessary.

I am only a little familiar with installing and setting up things like Apache2, mySQL, PHP5, phpMyAdmin, etc.  I can make it work, but I need to do just a bit more than that.

Things I need;
[LIST=1]
[*]Apache2 w/PHP & mySQL (phpMyAdmin)
[LIST]
[*]I need to serve more than 1 website.  I think these are called virtual hosts (example.com points to var/www/example.com/html/ and website.com points to var/www/website.com/html/ etc.) 
[/LIST]
  
[*]IMAP & POP3 email
[LIST]
[*]I also would like to be able to connect securely, so need an ssl certificate.  Can I generate a self signed one for this purpose? 
[/LIST]
   
[/LIST]

I think thats really it.

How hard is it to do this via command line/ssh by just editing the config files?  Previously with cPanel, I would just add domains to my account, add emails to domains, and occasionally set MX records to point to Google.

Looking for some advice on how to proceed. (good how to articles etc) So far Google has not been much help, I may not have the terminology right.

I used this with nginx. This is for Apache. [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3)

---

### Post by nobodyfamous on 2013-10-01
I want to see about doing it without a "control panel"  I tried out zPanel, and it's not going so well.  I attempted to try ispConfig on a local virtual box without success, after all was said and done I could not access it due to some sort of ssl/https thing. it just never worked.  I may try it again, the demo looks promising.  The thing is, I don't need all the extra user/reseller stuff.  I will not be creating invoices or collecting money through the system either.

---

### Post by SeijiSensei on 2013-10-01
Have you read the [Server Guide]("https://help.ubuntu.com/lts/serverguide/") yet?

---

### Post by nerdtron on 2013-10-01
Full featured mail server that we use.
[http://www.iredmail.org/](http://www.iredmail.org/)
Installation in just a few minutes.
[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

---

### Post by sandyd on 2013-10-02
> **nobodyfamous said:**
> I want to see about doing it without a "control panel"  I tried out zPanel, and it's not going so well.  I attempted to try ispConfig on a local virtual box without success, after all was said and done I could not access it due to some sort of ssl/https thing. it just never worked.  I may try it again, the demo looks promising.  The thing is, I don't need all the extra user/reseller stuff.  I will not be creating invoices or collecting money through the system either.

Have you tried OpenLiteSpeed? - free and has web control panel that is easy to use. The web interface only has to do with the web server configuration itself, so you will have to use something like axigen, iredmail, or some other email system in addition to openlitespeed

Packages for openlitespeed can be found at [https://launchpad.net/~sandyd/+archive/openlitespeed-stable](https://launchpad.net/~sandyd/+archive/openlitespeed-stable)

---

### Post by nobodyfamous on 2013-10-03
thank for the info so far, I will be looking into it.  I have read the server guide, just not getting very far with it.  I think I will give ispConfig a go first since I never got it to work the first time around.

---

### Post by nobodyfamous on 2013-10-24
well, I gave ispConfig another whirl. I don't like the way it sets up so many folders and sym links.  It also was not a 1 shot deal to setup new virtual hosts, or emails.  I looked into webmin, and thats pretty close to just editing the files manually, which looks good to me, except I don't know what I am doing just yet.  On a similar note, virtualmin looks like 1 step closer to a WHM/cPanel simplicity in setup, yet functions on webmin, so I still have the basic control.  I think virtualmin is going to be the way I go.

---

