---
title: "Need Some Help Understanding and Configuring Apache"
date: 2018-09-13
forum: Server Platforms
---

### Post by Abdul_Hakim on 2018-09-13
Hello everyone,

Apologies if this is on the wrong subforum, wasn&#8217;t sure if I should post here on in Networking.

Also sorry for the weird formatting, I wrote this out in a Google Doc and then copy+pasted it over here.

I was hoping someone might be able to give me an in-depth explanation and/or walkthrough on how to get Apache on my home server configured the way I want. I have a basic grasp on this but I think there&#8217;s some pieces of the puzzle that I&#8217;m not understanding. I understand that I need to use Apache VirtualHosts, and I think I also need to have the sites listening on different port numbers? I&#8217;m just not sure how to get it all to fit together

Desired Results:
1. Nextcloud installed and accessible from Internet. So mydomain.ddns.net/nextcloud goes to my Nextcloud (unless it needs to be something like mydomain.ddns.net:portnumber)

2. A Wordpress site installed and accessible from Internet (which I know how to do assuming I can get Apache VirtualHosts to do what I&#8217;m wanting). So mydomain.ddns.net goes to my wordpress site, unless it needs to be something like mydomain.ddns.net:portnumber

3. Webmin installed and accessible from Internet (if applicable, can&#8217;t remember if Webmin is local only) (pretty sure I can get this working on my own once I understand VirtualHosts). So mydomain.ddns.net/webmin goes to Webmin for my server, unless it needs to be something like mydomain.ddns.net:portnumber

4. Have everything secured with HTTPS/SSL/TLS

Basically, I need to understand how to configure virutalhosts to all share my single DDNS domain for 3+ separate services (Nextcloud, Wordpress, Webmin). Assuming that that&#8217;s even possible in the first place.

If it is possible, I&#8217;m not sure if it will need to be setup like mydomain.ddns.net/page or mydomain.ddns.net:portnumber

My Setup:

[LIST=1]
[*]ASUS router running asuswrt-merlin 384.6 configured with my DDNS domain
[*]Ubuntu Server 18.04
[/LIST]

What I&#8217;ve Done So Far:


[LIST=1]
[*]1. Installed LAMP stack following this article:
[/LIST]

([https://www.ostechnix.com/install-apache-mariadb-php-lamp-stack-ubuntu-16-04/]("https://www.ostechnix.com/install-apache-mariadb-php-lamp-stack-ubuntu-16-04/"))

&#8220;Hardened&#8221; Apache installation following this article: 

([https://hostadvice.com/how-to/how-to-harden-your-apache-web-server-on-ubuntu-18-04/]("https://hostadvice.com/how-to/how-to-harden-your-apache-web-server-on-ubuntu-18-04/")


[LIST=1]
[*]Opened ports 80 and 443 on my server (along with 22 which was already open so I can SSH into my server remotely)
[*]Installed Nextcloud following this article: ([https://websiteforstudents.com/setup-nextcloud-on-ubuntu-18-04-lts-beta-with-apache2-mariadb-and-php-7-1-support/]("https://websiteforstudents.com/setup-nextcloud-on-ubuntu-18-04-lts-beta-with-apache2-mariadb-and-php-7-1-support/"))
[/LIST]


[LIST=1]
[*]In apache ports.conf, I have three Listen statements, listening on 80,443, and 10000. I think in order for this to work, each service/instance has to be on a separate port number? So I was going to run Nextcloud on 10000, and then Webmin on something else
[/LIST]


[LIST=1]
[*]I have a virtualhost file configured and enabled via a2ensite for nextcloud (configured as part of the aforementioned installation process), along with the default virtualhost files (000-default.conf and default-ssl.conf)
[/LIST]

The Problem(s):


[LIST=1]
[*]I don&#8217;t understand the difference between /var/www/html and /var/www/. I understand that /html is the &#8220;Apache Default site&#8221;, and I can reach the default apache page when I&#8217;m on my LAN. And I understand that additional websites should be created in www rather than www/html, but what&#8217;s confusing about this is that Nextcloud is installed in www/html/nextcloud. Shouldn&#8217;t it be www/nextcloud? Is www the &#8220;root&#8221; of the Apache server? If so, then do I even need the www/html folder? And can I just move the Nextcloud installation from www/html to www?
[/LIST]


[LIST=1]
[*]I can reach my Nextcloud via the Internet when I go to mydomain.ddns.net/nextcloud, however I would expect that mydomain.ddns.net by itself should show the default Apache page shouldn&#8217;t it? But instead I get &#8220;This site can&#8217;t provide a secure connection - mydomain.ddns.net sent an invalid response: &#8220;ERR_SSL_PROTOCOL_ERROR&#8221;. I don&#8217;t know what to do about this.
[/LIST]


[LIST=1]
[*]When going through the process to automatically obtain a Let&#8217;s Encrypt cert, do I need a separate cert for every site on the Apache server? Or can I just have one cert that applies to the entire apache server regardless of how many sites are on it?
[/LIST]


[LIST=1]
[*]I found this article on getting a Lets Encrypt cert, but part of the prerequisites include &#8220;Both of the following DNS records set up for your server...&#8221;, but, set up where? Whose DNS? Do I need to have a local DNS server running as well? My DDNS domain is registered with no-ip and is also configured on my router so the domain should always be pointing to my WAN IP. Is that sufficient or do I need something more?

([https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04]("https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04"))
[/LIST]


[LIST=1]
[*]In general I&#8217;m just having trouble wrapping my head around this, and I&#8217;m not sure if it even CAN work the way I want it to, and since I&#8217;m new to this I don&#8217;t know what I don&#8217;t know so I&#8217;m not entirely sure what I should be asking.
[/LIST]

Can someone tell me what I&#8217;m missing here or point me in the right direction to be able to accomplish my Desired Results. I&#8217;m brand new to Apache and web hosting in general so I&#8217;m kinda just learning this as I go along. Please don&#8217;t hesitate to point me to any relevant documentation although I may have to ask additional questions if I don&#8217;t understand it.

Thanks in advance!

---

### Post by wildmanne39 on 2018-09-13
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Yes this is the correct sub-forum for your topic.

---

### Post by LHammonds on 2018-09-14
You do not "have to" have multiple virtual hosts defined.  You could just use the default configs that already exist and install your software to sub-folders.

Example:

```

/var/www/html/nextcloud/
/var/www/html/wordpress/
/var/www/html/webmin/

```

You will likely need to add directory-specific directives though.

If you can use different hosts in your domain name, I would use those and create separate virtual hosts such as:

files.mydomain.ddns.net which points to /var/www/nextcloud
wordpress.mydomain.ddns.net which points to /var/www/wordpress
webmin.mydomain.ddns.net which points to /var/www/webmin

And have a separate .conf file for each site.

A single apache .conf for all sites means one SSL for all of them.  Separate apache .conf files means separate SSL for each site unless you use a wildcard certificate.

You probably do not want to use DNS authorization for LetsEncrypt (CertBot) and instead let it modify files directly on the websites which is should have access to.  I cannot give you any advice on CertBot since I am just now starting to figure out and document how to use it...but do not have it working just yet.  I am concentrating on creating a local certificate authority for internal services before tackling the external SSL.

LHammonds

---

### Post by Abdul_Hakim on 2018-09-17
> **wildmanne39 said:**
> Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Yes this is the correct sub-forum for your topic.

Is everything not regular black? It looks black to me?

---

### Post by Abdul_Hakim on 2018-09-17
> **LHammonds said:**
> You do not "have to" have multiple virtual hosts defined. You could just use the default configs that already exist and install your software to sub-folders.

Example:

```

/var/www/html/nextcloud/
/var/www/html/wordpress/
/var/www/html/webmin/

```

You will likely need to add directory-specific directives though.

If you can use different hosts in your domain name, I would use those and create separate virtual hosts such as:

files.mydomain.ddns.net which points to /var/www/nextcloud
wordpress.mydomain.ddns.net which points to /var/www/wordpress
webmin.mydomain.ddns.net which points to /var/www/webmin

And have a separate .conf file for each site.

A single apache .conf for all sites means one SSL for all of them. Separate apache .conf files means separate SSL for each site unless you use a wildcard certificate.

You probably do not want to use DNS authorization for LetsEncrypt (CertBot) and instead let it modify files directly on the websites which is should have access to. I cannot give you any advice on CertBot since I am just now starting to figure out and document how to use it...but do not have it working just yet. I am concentrating on creating a local certificate authority for internal services before tackling the external SSL.

LHammonds

Thanks man that really helps. Unfortunately no-ip doesn't enable subdomains for free, so I guess I gotta just cough up the $10 a year for a proper domain. Although I'm still not sure where potentially configuring DNS fits into the picture.

I may have to post additional questions in this thread down the road if I bump into any more obstacles (which is likely...lol)

---

### Post by LHammonds on 2018-09-18
> **Abdul_Hakim said:**
> Although I'm still not sure where potentially configuring DNS fits into the picture.
If you are talking about the Certbot method of domain validation, that just means adding a TXT record with a unique string provided by Certbot which will tell Certbot that you have control over the domain rather than some yahoo that is lying and trying to do something malicious.

If you are talking about DNS in terms of the Apache configuration, DNS is everything to do with it.  You typically get one IP address and a single server that needs to host multiple sites...even on different domains or sub-domains.  When an inbound web browser is hitting the server, Apache knows where to send the browser based on how it is getting to the server in the 1st place.  If the browser's URL has "mydomain.com" then Apache will look at your config files in "sites-enabled" to see if there are any matching definitions to that name and direct the browser to the correct website.  This is over-simplifying the process but it is the basics to understand what it is doing.

LHammonds

---

