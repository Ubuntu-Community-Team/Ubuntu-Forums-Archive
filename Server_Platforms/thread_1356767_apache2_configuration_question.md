---
title: "apache2 configuration question"
date: 2009-12-16
forum: Server Platforms
---

### Post by josh6847 on 2009-12-16
I just have a couple general question about apache2. I starting digging back into it because I am configuring SSL, so I would like to understand a couple things:

1. What is the difference between having your virtualhost configs in httpd.conf vs sites-enabled/? Is it just that for certain things the virtualhost's should be in sites-enabled? I run 4 sites off of one apache2 server with everything in httpd.conf. Is this ok?

2. For SSL, does creating your own certificates using a passphrase allow for many more vulnerabilities? From my understanding you can go through a certificate agency or do it through Ubuntu.

Thanks in advance.

Josh

---

### Post by cdenley on 2009-12-16
1. You shouldn't use httpd.conf. It will work fine, but if you have configuration problems, it will be more difficult for anyone to help you. Also, the ubuntu configuration is made to be modular, so you can enable/disable vhosts/modules without editing files.

2. If you use self-signed certificates, then visitors will be given a warning about it, and required to make an exception. They cannot verify that the certificate they are accepting is authenticated since it hasn't been signed by a trusted third party (certificate authority). This means that the server may be spoofed, and the visitor may be sending sensitive data to the wrong server.

---

### Post by HighCommander540 on 2009-12-17
1. Yup, seriously just use sites-enabled.

2. Also, just don't use a passphrase. It makes it harder to boot. You have to be at the computer for every boot, to enter the passphrase.

---

### Post by josh6847 on 2009-12-17
Great, thanks for the advice. I have one follow up question to that. If I have 4 domains, with 1 or more subdomains for each domain, should I then create 4 different files in sites-enabled/ with the necessary virtual host configs? Apache must be reading all of those files on load then?

Thanks,

Josh

---

### Post by oneloveamaru on 2009-12-17
Yes and Yes.

Create the sites in sites-available and then do an "a2ensite sitefilename" which will create a sym link over to sites-enabled. 

Then you can just do a /etc/init.d/apache restart and you should be good to go.

---

### Post by cdenley on 2009-12-17
> **josh6847 said:**
> Great, thanks for the advice. I have one follow up question to that. If I have 4 domains, with 1 or more subdomains for each domain, should I then create 4 different files in sites-enabled/ with the necessary virtual host configs? Apache must be reading all of those files on load then?

Thanks,

Josh

If you want 4 different vhost/site configurations with those domains/subdomains. You can also have multiple domains/subdomains for a single vhost/site. It all depends on how you want to configure your site(s).

---

### Post by oneloveamaru on 2009-12-17
> **cdenley said:**
> If you want 4 different vhost/site configurations with those domains/subdomains. You can also have multiple domains/subdomains for a single vhost/site. It all depends on how you want to configure your site(s).

If the sub-domains are separate sites(different content), then you will need a vhost for them.

---

### Post by josh6847 on 2009-12-17
Great, very helpful.

---

