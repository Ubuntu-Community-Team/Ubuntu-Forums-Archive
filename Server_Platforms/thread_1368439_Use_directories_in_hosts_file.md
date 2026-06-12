---
title: "Use directories in hosts file"
date: 2009-12-30
forum: Server Platforms
---

### Post by MadnessRed on 2009-12-30
I have a couple of sites that I need to be in the root directory. Obviously I can only have 1 at a time so its a bit of a pain moving various sites to the root.

Looks in /etc/hosts there is
127.0.0.1	    localhost
if I add
127.0.0.1	    site1

I can get to my localhost via [http://site1/](http://site1/)
Is it possible to do something like
127.0.0.1/site1	    site1
127.0.0.1/site2	    site2

So that I can access [http://localhost/site1](http://localhost/site1) from [http://site1/](http://site1/)
[http://localhost/site](http://localhost/site) 2 from [http://site2/](http://site2/)
etc.

Thanks,

---

### Post by falconindy on 2009-12-30
You can't do this.

Instead, make VirtualHosts in your Apache config.

---

### Post by BkkBonanza on 2009-12-30
That's correct. the hosts file is only for DNS (name to IP) lookup.

What you are needing is handled via VirtualHosts on the server or via "Frame Redirects" on (some) DNS servers. 

A frame redirect can also be set up if you don't have use of virtual hosting. But frame redirects are a bit nasty really - used to be common but are kind of frowned upon nowadays. Still, it is one way to do that. But it's easier and  preferable to use virtual hosts.

Read apache docs for VirtualHost directive and samples on how to use.

---

### Post by Lars Noodén on 2009-12-31
As @ BkkBonaza points out, Apache's VirtualHost directive is the way to set up different root directories.  More specifically, one way to play would be to use [IP-Based Virtual Hosts](http://httpd.apache.org/docs/2.2/vhosts/ip-based.html).  Your machine will respond to 127.0.0.2 just as easily as to 127.0.0.1 or anything up to 127.254.254.254.  

Here are some examples, but plenty more can be found on the net in the forms of articles, guides and HOWTOs: 
[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

---

### Post by MadnessRed on 2009-12-31
I found a sollution which is I installed lighttpd aswell, set it to port 81 and then mapped site1 to 127.0.0.1:81 which worked, but thanks for the info on virtual hosts, as it will be very useful if I need to setup any more sites

---

### Post by Lars Noodén on 2009-12-31
> **MadnessRed said:**
> I found a sollution which is I installed lighttpd aswell, set it to port 81 and then mapped site1 to 127.0.0.1:81 which worked, but thanks for the info on virtual hosts, as it will be very useful if I need to setup any more sites

That would be the same as running a pair of [port-based virtual hosts in Apache](http://httpd.apache.org/docs/2.2/vhosts/examples.html#port) or else [port-based virtual hosts in Lighttpd](http://redmine.lighttpd.net/wiki/1/Docs:Configuration).

Lighttpd is fine, as is Apache, but it would save resources to run only one web server and set it to serve the different sites via different ports.  There are a lot of tutorials available.  I've used port-based virtualhosts a lot myself at work for many years, usually as a means to have a staging area for changes to a production site.  The production site on one port, the preview of the new site on the other port.

---

### Post by MadnessRed on 2009-12-31
> **Lars Noodén said:**
> That would be the same as running a pair of [port-based virtual hosts in Apache](http://httpd.apache.org/docs/2.2/vhosts/examples.html#port) or else [port-based virtual hosts in Lighttpd](http://redmine.lighttpd.net/wiki/1/Docs:Configuration).

Lighttpd is fine, as is Apache, but it would save resources to run only one web server and set it to serve the different sites via different ports.  There are a lot of tutorials available.  I've used port-based virtualhosts a lot myself at work for many years, usually as a means to have a staging area for changes to a production site.  The production site on one port, the preview of the new site on the other port.

That could/will be very useful. Many thanks.

---

