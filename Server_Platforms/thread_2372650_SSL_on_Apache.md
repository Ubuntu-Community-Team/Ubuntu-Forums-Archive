---
title: "SSL on Apache"
date: 2017-09-27
forum: Server Platforms
---

### Post by fernandoch on 2017-09-27
Hello,

I have my apache running perfectly but would like to convert my sites to https://

What would be the proper way to do it?

Do I have to buy a certificate for each website?

Thank you

---

### Post by SeijiSensei on 2017-09-27
You'll need at least one certificate for every domain you host.

If you have multiple hosts in the same domain, you can buy a "wildcard" certificate that matches all hosts in the domain.

---

### Post by fernandoch on 2017-09-27
What are the certificates that I have in my cert folder for?

---

### Post by mastablasta on 2017-09-28
you may not need to buy it. depending on why you need the website for.

have a look at this: [https://letsencrypt.org/](https://letsencrypt.org/)

for 14.04 but it likely still valid for 16.04: [https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-14-04)
edit: certbot ppa: [https://launchpad.net/~certbot/+archive/ubuntu/certbot](https://launchpad.net/~certbot/+archive/ubuntu/certbot)
certbot guide (official): [https://certbot.eff.org/](https://certbot.eff.org/)

---

### Post by darkod on 2017-09-28
Which ever you choose to use, make sure first it is trusted and the visitors will not receive a warning when visiting the site. If that is not important to you or the visitors, you can even use your self-signed certs (the one you say are in the cert folder probably).

If your visitors expect trusted communication start to end, they wouldn't like it when a warning pops up saying the cert is not trusted. So, have that in mind...

Otherwise, setting up https in apache is real easy, plenty tutorials around.

---

### Post by fernandoch on 2017-09-28
Just some blogs.

Do they get a warning with the let's encrypt ssl certificate?

---

### Post by SeijiSensei on 2017-09-28
The certificates that come with Apache are "self-signed."  Using them will generate a warning in browsers.

I don't know about "let's encrypt".

---

### Post by mastablasta on 2017-09-29
no, the "let's encrypt certificate" is certified. it shouldn't give out any warnings. the FAQ on their site shoudl tell you more. 

although i have to say i am not sure what is the exact difference between theirs or for example the one from Comodo or other certificate authority.

it's the self signed ones that give out the warings. warnings are ok, if the users know about them (e.g. home use, company use), but are not suitable for public sites.

---

### Post by ecrosby on 2017-10-03
I've used this guide in the past to setup LAMP and generate a certificate using Lets Encrypt. It's a good guide. 

[https://www.howtoforge.com/tutorial/install-apache-with-php-and-mysql-on-ubuntu-16-04-lamp/](https://www.howtoforge.com/tutorial/install-apache-with-php-and-mysql-on-ubuntu-16-04-lamp/)

Once you've configured you can use this site to test the cert:

[https://www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/)

---

