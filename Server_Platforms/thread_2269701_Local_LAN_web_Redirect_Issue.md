---
title: "Local LAN web Redirect Issue"
date: 2015-03-17
forum: Server Platforms
---

### Post by scott.bouch on 2015-03-17
Hi all,

After setting my server up to redirect requests of [www.scottbouch.com]("http://www.scottbouch.com") and [http://www.scottbouch.com](http://www.scottbouch.com) to [https://www.scottbouch.com](https://www.scottbouch.com), I'm now experiencing an anoying bug when I'm at home trying to view my site locally.

I followed [this guidance]("https://www.digitalocean.com/community/tutorials/how-to-create-temporary-and-permanent-redirects-with-apache-and-nginx") and documented it in [this thread]("http://ubuntuforums.org/showthread.php?t=2261688&page=2#18"). 

I'm pretty sure this worked immediately after setting up the redirect, but has now stopped (possibly since an update perhaps??).

When I use my servers IP address in a browser to locally view my site, it gets redirected to [https://www.scottbouch.com](https://www.scottbouch.com), which fails as my router can't do loopback.

Not only can I not see my website locally, I also can't access my Zoneminder CCTV webpages, or PLEX media server webpage either (all hosted from teh same machine), but I can when I'm not at home.

Any tips on how to allow local lan browser requests to access the servers pages without redirects?

Here's the contents of my etc/apache2/sites-available/**000-default.conf** file:

```

<VirtualHost _default_:80>
    ServerName www.scottbouch.com
    Redirect / https://www.scottbouch.com/
</VirtualHost>

<VirtualHost _default_:443>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.

    ServerName www.scottbouch.com

ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html
    SSLEngine on
    SSLCertificateFile /etc/apache2/sites-enabled/6e1709ae5902a152.crt
    SSLCertificateKeyFile /etc/apache2/scottbouch.key
    SSLCACertificateFile /etc/apache2/sites-enabled/gd_bundle-g2-g1.crt
    SSLProtocol All -SSLv2 -SSLv3

    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet


```

Any help is much appreciated... 
Many thanks, Scott.

---

### Post by volkswagner on 2015-03-17
This is a router problem, as you say it does not allow loopback.
Does your router allow local DNS entries or host entries? If so add the local ip and domain name.
Perhaps you can add a local DNS server and point your router to it, so you can add local hostnames.
You can edit local /etc/hosts files on your machine, which you'd have to comment out while away from home,
or more simply, I suggest getting a different router.

---

### Post by scott.bouch on 2015-03-18
Hi, thanks for having a look at my issue!

I do hate to come back with a question,  but all that's configured in my router is port forwarding to the server for web, ssh, and plex.

My router isn't aware of my domain name, so why would it redirect requests of the IP address to the domain name?

This is why I thought it would be to do with the server's redirect config file, as that does redirect requests to the domain name.

I like the idea of a local LAN DNS, as I could also use it to easily access my raspberry pi xbmc media player's web remote controls.

---

### Post by volkswagner on 2015-03-18
Yes this is normal. For proper https the domain url must match the certificate domain name.
Your redirect is working correctly. If you redirect to [https://mypublicIP](https://mypublicIP) then you'll get a warning of 
suspicious site.


Does your router have host file or or dns settings? What model router do you have?

Your domain has public dns records, so your router is "aware" of your domain name, and as 
far as your router is concerned, your domain name points to the router itself ;)

---

### Post by scott.bouch on 2015-03-20
Oh, thanks, I see now how the router could be causing the issue ... it's funny, as I'm convinced it used to work, and I;ve not changed anything. Maybe an automatic firmware update perhaps?

My router was provided by my ISP, TalkTalk. It's a Huawei HG533 router.

Thanks, Scott

---

### Post by scott.bouch on 2015-03-28
Hi - I've found a solution!!

From within my LAN If I use the computer name instead of the IP address it works a treat!!

Tip about using compuerName.local came from [here]("http://community.talktalk.co.uk/t5/Computers-Gaming/Can-the-HG533-resolve-internal-IP-addresses-from-machine-names/td-p/1410443").

I've had to add a security exemption to Firefox as the computer name is different to the domain name on the SSL certificate.

It's nice to have a fix, maybe it's to be considered a workaround, but hey, it works!

Thanks again, Scott.

---

