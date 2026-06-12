---
title: "Ubuntu Server - Times Out - SOMETIMES Can't Access Domains"
date: 2006-06-26
forum: Server Platforms
---

### Post by ShawnHunt on 2006-06-26
I am having a problem with my Ubuntu Web Server.  I have it hosting a number of personal domains.  Everything works fine, and I am able to see the domains from outside the network....  most of the time.  After about 5 minutes or so, the server seems to...  time out i'll have to do an /etc/init.d/networking restart and everything works again, for another 5 minutes or so.

I thought that it might have been because of IPv6 but I disabled that and it didn't solve the problems.  Has anyone else had this problem?  I've searched the forums and haven't found anything to point me in the right direction.

---

### Post by Iowan on 2006-06-27
Static IP address? (AKA bump)

---

### Post by ShawnHunt on 2006-06-27
Yep, it's a static IP.  I setup my machine almost exactly how they suggested in the LAMP server guide on howtosourceforge (or whatever it's called), if that helps at all.

---

### Post by ShawnHunt on 2006-06-28
Any suggestions?  I started fresh and reinstalled everything but am still having the same exact problem.  I'm very new to Ubuntu and have made it this far through the skin of my teeth.  Any help pointing me in the right direction on this issue would be much appreciated.

Here's a recap of my problem again:

My Ubuntu Server (Dapper Drake) is running ISPConfig along with all the services required to run it (apache2, php5, etc., etc.).  My server seems to time out though.  I won't be able to ssh, ftp, telnet, vsit a hosted domain, etc., on the server until I do a /etc/init.d/networking restart.  After that, it will work fine for a bit (the time varies) and I will no longer be able to access the server again until I do another /etc/init.d/networking restart.  And on and on and on.

I disabled IPv6, but have re-enabled it because it turned out to not be the problem.

Save me Ubuntu people, you're my only hope.

Again, sorry if I seem very n00bish, I'm just pretty much stumped.

---

### Post by Iowan on 2006-06-28
Is the server directly connected to the net - or is there a router/firewall in between?  If you can get to them, do the network configuration files (ifconfig, interfaces, etc.) change between a working machine and a locked one?  If there is one, I'm wondering if the gateway address is getting reassigned.

(Warning - I could be going in entirely the wrong direction)

---

### Post by ShawnHunt on 2006-06-28
You definitely put me in the right direction.  The server was behind one of my routers and was getting routed the traffic through there.  I took it off and set it up with it's own direct IP address and everything is working fine.  It must have been something on the router end.

Thanks!  :)

---

