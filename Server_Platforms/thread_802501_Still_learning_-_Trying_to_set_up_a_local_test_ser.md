---
title: "Still learning - Trying to set up a local test server"
date: 2008-05-21
forum: Server Platforms
---

### Post by indianajones123 on 2008-05-21
Hi everyone,

I'm looking to set up a local test server on an Ubuntu Linux machine we have here in the office.  I've been doing good so far... I have the whole LAMP setup installed, I'm using Webmin, and I have ProFTPD installed.

I want this to be a staging server, accessible only by those connected to our LAN, definitely not externally available.

Following some recommendations, I created a new user on the linux box representing a site.  I.E. if my production site is [www.awesome.com](www.awesome.com), my new user is "awesome".  The idea behind this is to have the document root as /home/awesome/public_html.

We're connected to a router, so I feel that the dynamic IP address is a problem.  Plain and simple, I want my coworkers to be able to navigate to something like "staging.awesome.com", which would be a mirror of [www.awesome.com](www.awesome.com), only completely internal.

Is this possible?  I'm having a difficult time setting up my virtual host, and I'm wondering if this is more trouble than its worth if my IP address changes every day.  Am I going about this the wrong way?

I apologize for the long email, but it's my first time doing something like this, and I don't even know if what I want is possible or worth it.

Just so you all know, I've been following [http://www.webmasterworld.com/forum48/2432.htm](http://www.webmasterworld.com/forum48/2432.htm) pretty closely.

---

### Post by indianajones123 on 2008-05-21
Sorry posted too soon on the IP issue... I forgot I can just go into the router and "assign" my linux box to always have a certain IP address.

Still though... I'm a newbie when it comes to setting this stuff up, so if I have a bunch of different sites, will my coworkers be able to view it like:

ip.add.re.ss/staging.site1.com
ip.add.re.ss/staging.site2.com
etc.

I think I'm just confusing myself...

---

### Post by Dr Small on 2008-05-21
If you setup BIND DNS server from Webmin, and setup a domain for the network to point to the system's IP, you can setup Apache VirtualHosts to point to specific directories on the system.

Of course, every computer on the network would need to use this system's DNS server as theirs in order to access the domain.

Dr Small

---

