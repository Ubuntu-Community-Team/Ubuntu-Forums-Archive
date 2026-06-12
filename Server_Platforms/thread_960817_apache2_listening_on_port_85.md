---
title: "apache2 listening on port 85"
date: 2008-10-27
forum: Server Platforms
---

### Post by dcroxton on 2008-10-27
I'm trying to get apache2 to listen on port 85.  It works fine in my lan, but when I make a request via my wan ip, the request is refused.  The server is in a DMZ, so I don't think a firewall or NAT is the issue.  When I go to Shields Up, it shows port 85 as open, so I know that somehow packets can get through.  The same with telnet:  I can get to port 85 from inside my lan, but if I use the wan ip, I get a "Connection refused" error.

I'm at a loss how to proceed.  Any suggestions would be welcomed.

Sincerely,
Derek

---

### Post by bettlebrox on 2008-10-27
U probably have the hostname in the httpd.conf file set to localhost (the loopback internet address). Try setting it to the hostname or IP address of the system.

---

### Post by dcroxton on 2008-10-27
My httpd.conf is empty.  In sites-available, I have a virtual server set up.  I left the name empty so it would listen for all requests, but I've tried changing it to the ip or the fqdn, without any help.

The weird thing I'm noticing is that if I browse to my ip address, it shows my router's home page!  This suggests that the modem is passing through port 80 requests to the router, but I don't see why they wouldn't continue on to my server, which I have put in a dmz.  (I tried taking it out of the dmz and forwarding the ports I needed, but that didn't help either.)

There must be something going on with the cable modem they installed, an Arris TM502G.  It doesn't seem like I can configure anything on it myself, it is all done remotely.  This is a depressing turn of events.

Sincerely,
Derek

---

### Post by cariboo on 2008-10-27
Are you trying to reach from your internal network, or from outside your internal network. Apparently some routers will not allow you to loop around the router so that you can access the external ip address. 

Get one of your friends to try and access your web site.

A better site to check which ports you've got open is [canyouseeme]("http://www.canyouseeme.org/"), at least you won't be bombarded by requests to purchase Spinrite and other products GRC is trying to sell.


Jim

---

### Post by dcroxton on 2008-10-28
Wow, thanks, that was helpful.  I was trying to see if the site would be accessible from outside my network, but I've had this problem before (with other ISPs); I didn't realize it was potentially a router issue.  Kind of a bother to test whether I'm getting through NAT, but at least if I know it won't work, I can try other methods.

Sincerely,
Derek

---

