---
title: "https:// leads to another site on my server"
date: 2010-07-12
forum: Server Platforms
---

### Post by rand486 on 2010-07-12
Hi everyone,

A while back, I put a site up under a LAMP setup, and followed a guide from ubuntuforums that I googled to set up SSL encryption for the site.

That site works great, but since then, I've added some other sites to the same LAMP server.  They load fine as well, but if I type in https:// before going to the latter sites, the browser attempts to redirect to the first, and warns that it is a fraudulent certificate, and that I'm at risk by going to the site.

Obviously, it isn't an attack site, the certificate is just set up for only one domain.  How do I prevent my non-SSL sites from redirecting to the SSL-encrypted site?

Thanks!

---

### Post by dapperdanny77 on 2010-07-12
do you have a officially signed certificate ? - if not the browser cannot guarantee that the correctness of the certificate and warns about possible harm.

there are several certification authorities out there, where you can get a certificate - if you use your server just for private activities you can ignore the browser message

---

### Post by rand486 on 2010-07-12
Yes, it is an officially signed certificate.

The site was built with Joomla, and I asked first on the Joomla forums.  The response was a confident reply that it has to do with my SSL configuration.  That's why I came here for more help.

---

### Post by dapperdanny77 on 2010-07-12
check your apache config - there should be at least one seperate virtual host for https. if you want the same result for http and https the virtual host configurations for http and httpshave to point to the same directories.

On Ubuntu/Debian based systems the config directory for the vhosts should be located at /etc/apache2/sites-enabled

---

### Post by rand486 on 2010-07-13
Maybe I'm not explaining myself properly.  SSL DOES work.  https:// does indeed lead to the SSL-encrypted site.
ie: [http://www.site1.com](http://www.site1.com) automatically becomes [https://www.site1.com](https://www.site1.com), and [https://www.site1.com](https://www.site1.com) works perfectly.

The problem is that the other NON-SSL encrypted sites on the same apache2 server redirect to my SSL-encrypted site.
ie: [https://www.site2.com](https://www.site2.com) stays in the location bar, but actually loads the SSL encrypted site1.

The certificate throws the web browsers into panic mode, since the certificate is for site1, and the domain typed in is for site2.

If I type <VirtualHost *:443> into the non-SSL site configs, it reloads with no errors, but the site still redirects to a panicky "This is a falsified certificate" SSL encrypted version of site 1.

What I want is for the non-encrypted sites to just redirect https:// to http://
Can this be done with .htaccess, or something?  Or is this still an apache2 setup problem?

---

### Post by dapperdanny77 on 2010-07-13
> **rand486 said:**
> 
The problem is that the other NON-SSL encrypted sites on the same apache2 server redirect to my SSL-encrypted site.
ie: [https://www.site2.com](https://www.site2.com) stays in the location bar, but actually loads the SSL encrypted site1.


this could point to a vhost configuration issue - do you have a NameVirtualHost ?
please post your vhost config. 

> 
The certificate throws the web browsers into panic mode, since the certificate is for site1, and the domain typed in is for site2.


you can have only 1 ssl cert per IP address if you have only 1 IP then your cert has to include the site2 hostname

> 
If I type <VirtualHost *:443> into the non-SSL site configs, it reloads with no errors, but the site still redirects to a panicky "This is a falsified certificate" SSL encrypted version of site 1.


non ssl http usually runs on port 80 - ssl enabled hosts on 443 - it seems a bit conflicting having a port 443 vhost in your non ssl config ... 

> 
What I want is for the non-encrypted sites to just redirect https:// to http://
Can this be done with .htaccess, or something?  Or is this still an apache2 setup problem?

you can do this via .htaccess if allowed or directly in the apache config with Redirect 
[http://httpd.apache.org/docs/2.1/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.1/mod/mod_alias.html#redirect)

---

### Post by rand486 on 2010-07-13
I was well aware that the SSL certificate is only for the site1.com domain, and one ip address.  I have been trying to find a way to prevent the other addresses going to that ip address from redirecting to the SSL-encrypted site if someone types in https://

It seems there is no great answer, as I've noticed even huge sites will produce error messages when someone does that.

I'll take a close look at the apache redirect link shortly, and see if I can work out a satisfactory solution that way.  All I really need is for each of the non-encrypted domains to just redirect to the http:// version if htts:// is being used.

---

