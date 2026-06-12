---
title: "Ubuntu server 22.04 after koha install none of the LAMP applications work"
date: 2022-06-08
forum: Server Platforms
---

### Post by deepakdeshp on 2022-06-08
I installed drupal, Joomla and Wordpress on Ubuntu server 22.04. All were working fine. Then I installed Koha library usin [http://kohageek.blogspot.com/2015/05/install-koha-on-ubuntu-1404.htmlg](http://kohageek.blogspot.com/2015/05/install-koha-on-ubuntu-1404.htmlg)  Koha install was successful. Now when I try running drupal, joomla or wordpress it redirects me to koha page with the message the wordpress page file not found. What am I missing?

---

### Post by TheFu on 2022-06-08
I'd guess that the Koha installation scripts don't play well with others.  Maybe ask on their forum for people more familiar with it?

It is very common for webapps to need manual configuration.  Very few "just work" - none that I've ever installed besides extremely trivial CGI scripts "just work" post-install.  If you want things that don't need any setup and integration, perhaps using docker containers for each would be a better idea?  Just, please, please, please, be careful where you get the container from.  When we install webapps under the same web server instance, it is up to us to setup virtual URLs for each that don't conflict.  A common method is to have
1) different directories for each webapp under /var/www/
2) different web-server config files under /etc/nginx/sites-available/
3) setup different virtual hostnames for each web-app.  So  using koha.domain.net, drupal.domain.net, joomla.domain.net and wp.domain.net would be a common set of virtual websites to use.  This will allow clients to request those directly and SSI in the web server will redirect to the correct web-app.  It is possible to setup a reverse proxy on a system that clients connect into, but have the back-end running in a container or on a different system entirely.  I use this for about 20 domains.  Simple static websites are hosted on the reverse-proxy server, but full webapps run in containers or inside virtual machines which may run on the same or different physical hardware.  Running in containers and VMs means that as workload increases, scaling up is easier.

I'd get a drupal container from the drupal project, not some random package from docker-hub.
I'd get wordpress from the official wordpress guys, not some random docker or snap package from docker-hub or the Canonical snap store.  Anyone can post and name code whatever they want to those places.

Another thing to try is to change the order of the installs.  Do Koha first, then the others.

---

### Post by deepakdeshp on 2022-06-08
> **TheFu said:**
> I'd guess that the Koha installation scripts don't play well with others.  Maybe ask on their forum for people more familiar with it?

It is very common for webapps to need manual configuration.  Very few "just work" - none that I've ever installed besides extremely trivial CGI scripts "just work" post-install.  If you want things that don't need any setup and integration, perhaps using docker containers for each would be a better idea?  Just, please, please, please, be careful where you get the container from.  When we install webapps under the same web server instance, it is up to us to setup virtual URLs for each that don't conflict.  A common method is to have
1) different directories for each webapp under /var/www/
2) different web-server config files under /etc/nginx/sites-available/
3) setup different virtual hostnames for each web-app.  So  using koha.domain.net, drupal.domain.net, joomla.domain.net and wp.domain.net would be a common set of virtual websites to use.  This will allow clients to request those directly and SSI in the web server will redirect to the correct web-app.  It is possible to setup a reverse proxy on a system that clients connect into, but have the back-end running in a container or on a different system entirely.  I use this for about 20 domains.  Simple static websites are hosted on the reverse-proxy server, but full webapps run in containers or inside virtual machines which may run on the same or different physical hardware.  Running in containers and VMs means that as workload increases, scaling up is easier.

I'd get a drupal container from the drupal project, not some random package from docker-hub.
I'd get wordpress from the official wordpress guys, not some random docker or snap package from docker-hub or the Canonical snap store.  Anyone can post and name code whatever they want to those places.

Another thing to try is to change the order of the installs.  Do Koha first, then the others.

Thank you for your reply.  I had ifaced this problem some years ago and the solution came back to me.
While installing Koha I had done

```
 [COLOR=#000000][FONT=&amp]sudo a2dissite 000-default[/FONT][/COLOR] 
```
Then I just reversed it with 
```
 [COLOR=#000000][FONT=&amp]sudo a2ensite 000-default[/FONT][/COLOR] 
``` Then restarted Apache. Now all the web apps and Koha are working!
I am not sure if the [COLOR=#000000]sudo a2dissite 000-default command while installing Koha was actually required [/COLOR]

---

### Post by TheFu on 2022-06-08
Those commands just setup or remove symlinks that make the config file for a virtualhost that is  enabled from the available subdirectory.  Nothing more.  In the old days, we didn't have scripts to do it and just manually created the symlinks. No magic in those commands.

---

### Post by deepakdeshp on 2022-06-08
Yet magically it worked. Thanks for your inputs

---

