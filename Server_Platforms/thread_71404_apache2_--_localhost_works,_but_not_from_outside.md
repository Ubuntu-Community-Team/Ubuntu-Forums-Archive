---
title: "apache2 -- localhost works, but not from outside"
date: 2005-10-03
forum: Server Platforms
---

### Post by shreevatsa on 2005-10-03
I'm using Hoary 5.04; and did apt-get install apache2 (and apt-get install apache2-doc).
Also, I changed the "Listen 80" line in /etc/apache2/ports.conf to "Listen 4242".
I can now do [http://localhost:4242/](http://localhost:4242/) and access the page, but I get "connection refused" when I access it from outside.
I've enabled port forwarding for port 4242 on my router, both TCP and UDP (and canyouseeme.org confirms that the port is open. In fact, the only open ports are those I've portforwarded through my router settings -- 22 for ssh, 4242 for http, and a couple of ports that a couple of programs open up through UPnP). 
So is there something I need to do? My /etc/hosts.allow is empty (that is, all lines are commented out. This was the default), and I have no problems with ssh. 
About my connection:
I'm using an ADSL connection, and the way it works (quoted from somewhere else) is this:
"The modem/router device acts as a gateway and my computer is just a LAN device with a LAN ip (192.168.1.xx) and the ip of the gateway is set up as 192.168.1.1. I can configure my router settings, etc by connecting to 192.168.1.1 (As in connecting to the gateway inside the LAN). So, my computer's identity to the outside world is resolved through the gateway, whenever I connect or download to/from the internet...."
It does not give me a static IP address, but I can ssh to my computer by finding out the IP address it currently has. (E.g, through dynDNS.org, or by typing the address manually). Just typing my address takes me to my modem/router settings page, and I didn't want to change that, so I gave it a different port 4242.

P.S: The *Before you post* sticky thread above mentions a "HOWTO's forum", but I couldn't find it. Maybe it would be good idea to link to it....

---

### Post by Tinwood on 2005-10-06
> **shreevatsa]I'm using Hoary 5.04 said:**
> http://localhost:4242/[/URL] and access the page, but I get "connection refused" when I access it from outside.
I've enabled port forwarding for port 4242 on my router, both TCP and UDP (and canyouseeme.org confirms that the port is open. In fact, the only open ports are those I've portforwarded through my router settings -- 22 for ssh, 4242 for http, and a couple of ports that a couple of programs open up through UPnP). 
So is there something I need to do? My /etc/hosts.allow is empty (that is, all lines are commented out. This was the default), and I have no problems with ssh.  
Did you actually forward port 4242 to the computer with the server on it?  Is the port open (can you telnet to it for example?)

Or it could be your firewall blocking incoming connections to port 4242?  i.e. the firewall on the computer that hosts apache not necessarily the router.  
--
Alex

---

### Post by diebels on 2005-10-07
Ok, so you get a web page with "Connection refused", and an ubuntu server signature?

Tried editing the /etc/apache2/sites-enabled/000-default file?

---

### Post by shreevatsa on 2005-10-09
The port *is* open; I can telnet to it. In fact, the strange thing I just noticed that when I telnet to port 4242 from outside, and type GET, I actually do get the index.html that I have in /var/www on my computer. But when I type the address ("http://xx.xx.xxx.xxx:4242") in my browser, I get an error message ("The connection was refused when attempting to contact..." in Firefox, and "Could not connect to remote server..." in Opera, and similar things in lynx). Oh, and I have no firewall running on this computer.

Edit: Hmm, looks like I *can* access it from outside, just not from my browser when I'm here. It's not really a problem then. I can just use  localhost when I want to see it from here. Sorry for the trouble.

---

