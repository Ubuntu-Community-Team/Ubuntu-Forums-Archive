---
title: "Need some help with setting up virtual hosts"
date: 2009-08-13
forum: Server Platforms
---

### Post by jclb111181 on 2009-08-13
First of all, thanks for reading and hopefully helping.  

I am fairly comfortable with Ubuntu having used it for years.  Last year I set up a Lamp server and have been using it to host my own website.  A friend recently asked if I could host his site.  I know it can be done and have made it work somehow.  I only have one problem:

I use no-ip.com to forward requests for my address to my ip.  The address shows up as it is typed in.  

I set up the virtual host to run on another port. It works.  

However I have to set up no-ip to forward the website to the new port.  I can't simply just set up a dns host.  I have to use a port forward setup. The problem is that when I type in the address <website.no-ip.org> the browser goes to the new page but it shows the ip address of the website in the address bar. 

I have been all up in the config files trying to name virtual hosts but to no avail.  

This is what I get when I try to restart Appache:

john@ubuntu:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                       [Thu Aug 13 20:49:48 2009] [error] VirtualHost *:8080 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 13 20:49:48 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Thu Aug 13 20:49:49 2009] [error] VirtualHost *:8080 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Aug 13 20:49:49 2009] [warn] NameVirtualHost *:80 has no VirtualHosts


Let me know what other info I can provide to help out.  Once again, thank you for reading.  

John

---

### Post by confusedstingray on 2009-08-14
here is a link from apache that seems to do what you want

[http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html)

---

### Post by Iowan on 2009-08-15
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") might help. [Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is another (hopefully not the same) name-based How-To.

---

