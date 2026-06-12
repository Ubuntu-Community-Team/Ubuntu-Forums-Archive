---
title: "&lt;VirtualHost ????:?????&gt;"
date: 2010-05-14
forum: Server Platforms
---

### Post by ihaveshoes on 2010-05-14
Can someone help me out? I've been trying to understand the first line of the virtual host configuration in Apache for a very long time. The documentation says that it should be an IP address or a FQDN. But I've also seen it in several different formats from tutorial sites:

<VirtualHost domain.com:80>
<VirtualHost *:*>
<VirtualHost domain.com:*>

Which one is correct? What is it fighting with in my config file? (I edit this in sites-available individually for each site.)

Currently, my server has two sites-available's set up and enabled, but both sites pull up the same site, regardless of what I have specified in the definition.

I'm in the middle of an OS reboot on my VPS right now and I'd really love to set this up correctly for once! 

Thank you! :)

---

### Post by cdenley on 2010-05-14
Unless you want that vhost to respond to only a particular network interface, just use "*:80", which would respond to requests on any interface using port 80. It should match a NameVirtualHost entry somewhere in your configuration, which is in /etc/apache2/ports.conf on recent ubuntu releases. If you don't specify the port, I believe 80 is assumed. If you use "*" for the port, the vhost will be served for connections on any port apache is configured to listen on.

---

