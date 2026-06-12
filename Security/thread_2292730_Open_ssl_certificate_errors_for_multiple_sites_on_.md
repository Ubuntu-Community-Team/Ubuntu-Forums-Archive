---
title: "Open ssl certificate errors for multiple sites on server - Invalid Certificate"
date: 2015-08-30
forum: Security
---

### Post by shawnblanchette on 2015-08-30
I used a (in my opinion) fantastic tutorial to help me set up a web/mail hosting server on Amazon EC2. I would definitely use it again and again because I don't forget anything! I always forget something.
[https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3](https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3)

So, as you can see from the URL the server is:
-Ubuntu 14.04
-PHP5
-MySQL
-phpMYAdmin
-Bind
-Dovecot
-Squirrelmail
-ISPConfig 3


I am hosting four web sites with different domains. There will be more as time goes on and business expands to new areas. The issue is simple. Anything using SSL shows an invalid certificate. I'm talking phpMYAdmin, ISPConfig 3, Squirrelmail, phpBB (for partner communications)... Anything. It doesn't matter what domain I use to log in to ISPConfig, phpMYAdmin, or Squirrelmail (the BB is tied to a domain), I still get the errors, even if I use the IP address. All domains will allow phpMYAdmin, Squirrelmail, and ISPConfig access.

If the above doesn't make sense it's because I am on about 20 hrs of sleep in the last 3 weeks. My apologies.

Can someone help me with stopping the annoying certificate errors?

Thanks!

---

### Post by SeijiSensei on 2015-08-30
Did you buy SSL certificates for each domain?  Self-signed certificates will always produce those errors since their authenticity cannot be validated by a trusted third party.  Do a Google search for "how ssl certificates work" and read some of the articles the search returns.

Certificates are usually assigned to a specific hostname like "www.example.com," but it's possible to buy "wildcard" certificates that match any hostname within the domain.  That means the same certificate can be used for "www.example.com" and "mail.example.com".

---

