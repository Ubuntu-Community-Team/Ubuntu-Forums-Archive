---
title: "SSL on PHPMyAdmin - Ubuntu Server 6.10"
date: 2007-04-17
forum: Server Platforms
---

### Post by 7echno7im on 2007-04-17
Hello,

First off I have only been using 'nix systems for about 6 months, and only as a hobby.  I have recently built a text only ubuntu server for my webserver and I am loving the perfomance, reliability, and stability.  I have a few questions.   If I need to post separate ones I will.

I use phpmyadmin to manage my databases.  I used the apt-get to install it after unlocking some of the repositories.  It is installed and working just fine, except for the fact that it is running on http rather than https.  I have followed some things on google, where people were saying to add a line to the config.inc.php file to indicate the https path, but that is not working.  Out of the box, after installing Ubuntu 6.10 server + LAMP option, then unlocking the repos and updating, upgrading, and using apt-get phpyadmin, it installs and configures phpmyadmin without SSL, any ideas?


My second question was that once I get SSL working, i want to restrict that page to my local subnet only.  Any help is appreciated.  I know all of his can be done, but I have seached google many times and have not been able to yeild the results I am looking for.

---

### Post by astrogazer on 2007-04-18
That what you are looking for is not phpMyAdmin related-you need to setup Apache to use SSL.
To do so you need to have a SSL certificate, either self-sign (free) one or buy one (15-20 Euros).
Both offer exactly the same level of protection. The only difference is that your browser will ask
you if you trust your self signed certificate since it has not been issued by a registered Certificate
Authority (CA).

---

### Post by 7echno7im on 2007-04-18
OK well I have SSL working fine for webmin, so how do I get it to work with phpmyadmin?  Why doesn't the apt-get install phpmyadmin config for SSL by default?  Can you help me get SSL on my phpmyadmin site?  I understand SSL is to be configured for Apache, does Webmin install and configure SSL for webmin only and not for apache?   If so then I need to install and configure SSL for apache2 and it will automatically use SSL if pointed to do so in browswer?  Thank you so much foryou responses.

---

### Post by astrogazer on 2007-04-19
Webmin does not use Apache at all. It has its own web server that is also SSL capable.

SSL for Apache cannot be installed and run out of the box. There are some changes/additions 
that need to be made in the config files. You will need to create a virtual host that will listen to
port 443 using SSL and set its home directory to the directory where the "secure" webpages
are located.

---

### Post by 7echno7im on 2007-04-19
Thank you very much.  I thought that this is what was going on because you can start and stop the apache service from webmin and still have access to webmin's console.  Awesome!  So do you recommned and SSL in particular?  Should it be OpenSSL?  Is there one SSL in particular I should use or a standard that everyone goes by?  Thanks again!

---

### Post by 7echno7im on 2007-04-22
Can anyone post a step by step guide on how to setup SSL and configure apache to serve my phpmyadmin site using this?  Thanks for all of your help.

---

