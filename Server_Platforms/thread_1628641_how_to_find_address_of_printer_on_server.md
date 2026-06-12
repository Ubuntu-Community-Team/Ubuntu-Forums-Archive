---
title: "how to find address of printer on server"
date: 2010-11-22
forum: Server Platforms
---

### Post by raymondvillain on 2010-11-22
I have a printer on a server running Ubuntu 10.04 Server.  This was upgraded from a much earlier version of Ubuntu Server.  Before the upgrade my printer was accessible from every machine on the small home network (2 Ubuntu machines and a Windows XP machine).

Now I'm unable to set up the printer.

I've opened a browser window (Firefox) and navigated to the printer administration page ([http://localhost:631/printer/](http://localhost:631/printer/)).  From this I added my printer.  But I can't print to it from the server, nor can I add this printer to any of the other machines on the network.

How do I find the IP address of the printer?  How do I allow applications on the server to print?

---

### Post by HermanAB on 2010-11-23
The IP address is the same as the IP address of the server:
$ /sbin/ifconfig

Note that you need to open port 631 for CUPS if you are running some sort of a firewall.

The name of the printer will be named whatever you named it as during setup.  Therefore I always use simple old fashinoned UNIX printer names like lp0.

See this:
[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

---

