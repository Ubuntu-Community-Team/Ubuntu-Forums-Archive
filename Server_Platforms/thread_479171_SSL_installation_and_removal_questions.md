---
title: "SSL installation and removal questions"
date: 2007-06-20
forum: Server Platforms
---

### Post by dfreer on 2007-06-20
Hey everyone,

 Ok, so on my test server I am wanting to try and use SSL to encrypt user logins, using HTML forms to get the login info, posting it to a PHP script that checks whether to the login is valid or not, then return them to the site.

Question number (1): can just the PHP login script use SSL? 
(example, login.html has the HTML forms, which posts the results to login_user.php, which then redirects the user to home.html if they login successfully. can I just make the link to [https://localhost/login_user.php](https://localhost/login_user.php) be the only part that uses SSL and still have the user info encrypted, or does login.html need to use SSL as well?)



  I already have a SSL certificate /etc/apache2/apache.pem, and SSL works fine. However, when it asked for the "common name (YOUR name)" when issuing the certificate, I put my real name instead of the FQDN, so now IE7 brings up this huge nasty warning saying the certificate is for "My Real name, but the site is http://localhost.localdomain"

Question number (2): Can I change this to the FQDN, or since I probably can't how do I "revoke" the certificate? is simply deleting apache.pem enough?

Question number (3): Since I will most likely need to create a new certificate (self-signed), can anyone point me to a guide or tell me the command to do so again (somehow I didn't bookmark the guide I followed, and I don't quite remember how I did so)?

---

### Post by dfreer on 2007-06-22
*bump* anyone?

---

