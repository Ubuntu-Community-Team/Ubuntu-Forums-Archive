---
title: "ispconfig subdomains (perfect server)"
date: 2009-01-19
forum: Server Platforms
---

### Post by specail on 2009-01-19
I went through the perfect server guide to set up my webserver, and it has worked fine for months. I even had a subdomain set up, but all this has come crashing down over the past few days.

I had a subdomain set up [http://frank.tier7.net](http://frank.tier7.net) as a Co-Domain under ispconfig, so I tried to add a new one [http://benkyou.tier7.net](http://benkyou.tier7.net) and now neither work. 

At first, they worked, and then they simply didn't... After spending a few days messing with ip addresses in the A records, I am at a loss.

I even tried using godaddy's subdomain system to no avail.

I created about a dozen subdomains with slightly different methods hoping I'd find one that would work. Most of them work LOCALLY, within my LAN, but none of them work outside of my network.

I usually search google and this forum to find answers, but for this I can find none.

---

### Post by windependence on 2009-01-19
Your problem is not external, and in fact you probably have your setup messed up now with your external DNS.

When using named based virtual hosts (which is what ISPconfig does) you should have just one IP pointing to your server. Apache figures out where each request goes and uses different document routes for different web sites. Your problem is most likely in your apache configuration. Unfortunately, control panels like this usually make it more difficult to fix these things as they tend to overwrite any config changes you make. The control panel is just a fancy GUI front end for the real configuration files. 

Do some reading on named virtual hosts, and you may be able to fix this by editing the config files yourself. You will need to make sure you put everytyhing back the way it was with Godaddy, that means an A record pointing to your server, and no configured subdomains at the external DNS level.

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

[http://www.cahilig.org/apache2-name-based-virtual-hosting-debianubuntu](http://www.cahilig.org/apache2-name-based-virtual-hosting-debianubuntu)

[http://www.ubuntugeek.com/howto-create-name-based-and-ip-based-virtual-hosts-in-apache.html](http://www.ubuntugeek.com/howto-create-name-based-and-ip-based-virtual-hosts-in-apache.html)

-Tim

---

