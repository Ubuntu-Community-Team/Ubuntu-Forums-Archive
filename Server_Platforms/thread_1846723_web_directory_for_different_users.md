---
title: "web directory for different users"
date: 2011-09-19
forum: Server Platforms
---

### Post by allegrauser on 2011-09-19
I am ignorant and trying to learn this, but searching the internet does not work so well because I am not sure what I am looking for. Here is what I need to understand and how to accomplish it. I have Ubuntu Server 11 running fine with Apache and SMB. The default directory for web is var. I have several sites that I work on for development purposes. So essentially it needs to act like shared web server. My hosting company gives me a directory that has a private & www directory. In the www directory I can have sub domains directory and the default www directory. I need to mimic this some how.

Do I have to setup a DNS server or do I use SAMBA domain controller to do this? In other words how can I create a directory structure for different sites and then have my url in the browser fine that directory?

---

### Post by i.r.id10t on 2011-09-19
You want name based virtual hosts on the apache side, and either DNS entries or entries in your /etc/hosts files for the domain names pointing to the proper IP.

---

### Post by allegrauser on 2011-09-19
Thanks for pointing me in the right direction. I think I found a tutorial that works. However the thing I am not quite clear on is how to access these virtual host on my local network. my server ip is 192.168.1.28. If I type that into the browser it just goes to the default directory. How do I use the point to my virtual host.

On the internet my domain name points to a named server, when that server gets the request it send the browsers to the virtual host directory. However on my local network typing in a name does nothing but point to the internet. I have OpenDNS that just says the site cannot be found.

---

