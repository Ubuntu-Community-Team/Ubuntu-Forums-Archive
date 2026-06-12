---
title: "proxy-http install issue"
date: 2007-08-16
forum: Server Platforms
---

### Post by jones28s on 2007-08-16
I'm trying to setup a reverse-proxy on my server to an old web server that I have my email setup on.  I need to be able to access the webmail interface from this system.

I installed the proxy-http module for apache2 on my system using a2enmod, which seemed to install fine.  However, when I reloaded apache, I got this error:

[INDENT]patrick@ubuntu:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of apache 2.0 web server... Syntax error on line 1 of /etc/apache2/mods-enabled/proxy_http.load:
Cannot load /usr/lib/apache2/modules/mod_proxy_http.so into server: /usr/lib/apache2/modules/mod_proxy_http.so: undefined symbol: ap_proxy_ssl_enable[/INDENT]

I had to uninstall the module in order to get my server running again.  Does anyone have any ideas as to what is going on?  Any help would be appreciated.

---

### Post by jones28s on 2007-08-23
OK.  I think I got the issue above fixed.  However, when I try to connect to the webmail server, which is where the reverse proxy points to, I'm getting a 403 Forbidden message.  I've verified I have the proxy and the proxy_http modules running.  It's pointing to a login page which is publicly accessible (when this server is open to port 80, that is).

The mail server is on a Windows XP box running Sambar server.  Is there an issue with reverse procying to a windows system?  CHMOD perhaps?  I hope someone can help.

Thanks.

---

### Post by twistedtwig on 2007-08-26
I had that error code when setting up a virtual host had /var/www/sub1 as a sub domain and /var/www/root/ as the default / root domain.  When I put Indexes in:

Options FollowSymLinks Indexes

it seemed to work.. to be honest I don't know why though.

---

