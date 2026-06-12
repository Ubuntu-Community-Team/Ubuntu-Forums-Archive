---
title: "Help with installing server, with DNS, DHCP and webserver"
date: 2010-09-09
forum: Server Platforms
---

### Post by ctidk on 2010-09-09
Hi

I&#8217;am completely new to Linux server, but I know my way around computers, I hope that helps me. And then I hope that all of you on this forum can help me too.

The problem:
I have about ten IP-phones that are locked by the original service provider, I need to unlock them, that is why I need the linux server. The original service provider has goon out of business, which is why I can&#8217;t get the password form them.

I need to do these tasks:
-- Install a server with DNS and DHCP enabled &#8211; I have installed a server with DNS and DHCP, but they are not enabled yet.
-- This step depends on the phones, and if they are setup to use TFTP or HTTP to access the configuration file -- Either download and install a version of TFTP, configure it and point it to to a directory. Or install a web server and configure it with the correct name and point to the necessary directory.

If they use TFTP then I need to do these tasks as well:
-- ad a "bootp" (option 66) to DHCP and point the "TFTP" server to this server by name.
-- On the Server: enabled detailed logging for DNS and cleared the cache.
-- Using a network switch (but not connected to any other network) attach the phone and the server.
-- After attaching the phone and waiting, examin the DNS log to see what names the phone is looking for.
-- Then add those names to DNS and point it to the server's IP address.
-- Power cycle the phone and watch the logging for the TFTP service.
-- At that point I should be able to see what config files the phone is looking for. 
-- Create a flat config file for the phone, with a new password, and unlock them that way.

Basically I need your help with almost all the above, And I really hope that you can help me.

I have installed the 32 bit version of Ubuntu Server 10.04.1 I downloaded it and installed it today. During the installation I installed DNS and after I have installed DHCP server, following the server manual.
The next step is to install a Web server, I think I can do that reading the documentation. But I do not know anything about a TFTP server, I hope that I can also install that.

It is mostly setting up DNS and enabling detailed logging, and maybe DHCP where I will really need help. After that I will need help with the TFTP and or the web server. All help to accomplish the above will be greatly appreciated! :)

---

