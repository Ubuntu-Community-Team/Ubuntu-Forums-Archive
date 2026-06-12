---
title: "[SOLVED] Ubuntu 7.10 Server wont access external sites"
date: 2007-10-29
forum: Server Platforms
---

### Post by andersdd on 2007-10-29
Hi,  I'm running a LAMP server for home use and accessible from the Internet.  I've been running Ubuntu 5.04 with no hassles for a couple of years and using the DynDNS to access my site from outside my home.  

I have just replaced my hardware and done a clean install of Ubuntu 7.10 server with its LAMP components.  Very easy install !!

I find my server now cannot access the Internet.  When I ping a website it will resolve the name but not return any packets.  The application ddclient cannot connect to the Internet to resolve my IP address and update the DynDNS service.  I can access my websites and other applications from within my network.  Some of my websites access external websites (such as Amazon.com) but these now cannot connect either.

I'm assuming that added security and/or firewalls are preventing these applications from working correctly.  I've tried adding entries to iptables to allow web traffic to my server but this has not worked (or I got it wrong).

I would appreciate if someone could give me tips on where to start looking to resolve this.  

Thanks

---

### Post by Peter Riche on 2007-10-29
what about your local network?

---

### Post by andersdd on 2007-10-29
Everything works fine within the local network.  I can access my website and the databases that are running on the server.

Other PCs can access the Internet with no problems.  As I said from the server I can ping an external web address and it resolves the IP address but I don't get any packets returned.  

I have set up port forwarding to this server which appears to be set up correctly (using port 80).

I would have thought that if I could get to my server from within the network I could get to it from anywhere.

Thanks

---

### Post by andersdd on 2007-10-30
Resolved the problem.  It was a network configuration problem.

---

