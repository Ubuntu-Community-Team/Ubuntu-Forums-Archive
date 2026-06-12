---
title: "Apache:   Web clents can't see virtual host. Only default host."
date: 2008-07-19
forum: Server Platforms
---

### Post by bobdobbs on 2008-07-19
Hi all.

I'm setting up an environment for web development. My main workstation, which runs Heron, is hosting apache.

I created the conf file for my vhost, (basically editing the conf the default), created the log files using touch, and put the conf in  /etc/apache2/sites-available

I created a dir 'hosts' under /var/www , edited the conf files for both the default site and the vhost accordingly, and put an index file at both locations.
I made sure apache wasn't running and ran a2ensite to enable my new site.

I then edited the hosts file on both the web host itself and my laptop.

Alas, I can't see my vhost!
What is going on, I wondered to myself.


When I type in "myserver" (the name of my vhost)  in the browser nav bar, the browser gets my default host.

I assume that I'm doing something wrong here, but I can't figure out what it is.

Does anyone have any suggestions?

Thanks

---

### Post by RealPSL on 2008-07-19
Did you modify the ServerName directive to match what is in the hosts file?

---

