---
title: "Apache web server behind router"
date: 2006-08-13
forum: Server Platforms
---

### Post by jhop on 2006-08-13
I have an apache web server set up, and it works.  I can log into it from within my local network (ie the machines plugged into the same router).
However, when I try to get to it from outside my router (Through teh adsl connection)  I start having issues.  In the router logs, can see the request hitting my router, and being forwarded to my web server.  However I can't see it hitting the web server, and I am not getting the page back.

Is there anyway I can get UBUNTU to log all the requests, so that I can see the request getting to it?  the router says it is forwarding it, but maybe it isn't.  Or is there some reason that apache might not reply to requests from cirtain domains?

---

### Post by stormblue on 2006-08-13
You wouldn't happen to be running DHCP on your server would you?  If you are that would cause the router to forward it to an IP address that isn't currently in use.

---

### Post by slakkie on 2006-08-13
> **jhop said:**
> I have an apache web server set up, and it works.  I can log into it from within my local network (ie the machines plugged into the same router).
However, when I try to get to it from outside my router (Through teh adsl connection)  I start having issues.  In the router logs, can see the request hitting my router, and being forwarded to my web server.  However I can't see it hitting the web server, and I am not getting the page back.

Is there anyway I can get UBUNTU to log all the requests, so that I can see the request getting to it?  the router says it is forwarding it, but maybe it isn't.  Or is there some reason that apache might not reply to requests from cirtain domains?

Check wheter it actually listens on the interface:
'netstat -na'

Check your ports.conf in /etc/apache2 (I assume you work with Apache 2), check the docs at: [http://httpd.apache.org/docs/2.0/bind.html](http://httpd.apache.org/docs/2.0/bind.html)

Try running tcpdump (as root): 'tcpdump port 80' and check wheter you see requests coming in from the client. If the client also allows to sniff the network, do it on that hosts as well.

If you have iptables running, check wheter it allows connections from the outside world to your machine, 'iptables -L' (as root).

Check your apache logs (check the Apache config to see where they are located).

Happy hunting.

---

### Post by az on 2006-08-13
It sounds like your ISP is blocking port 80.

---

### Post by stormblue on 2006-08-13
Azz,

I have a question about ISP's blocking port 80.  It would seem to me that they would drop all traffic to port 80 coming in at their location.  I don't see how they could be blocking port 80 and the packets still hitting the router, but not the server behind it.

Can you please shed some light on this.  Thanks!

---

### Post by jhop on 2006-08-13
OK, So I have sorted it now.

The issue was that I din't have the default gateway on the web server set to be the router (it wasn't set at all)  So the web server couldn't talk back.

I used route to set it up, and all was good.

I am not cirtain that it will come back when I restart, but that is a problem for another day

---

### Post by az on 2006-08-13
> **stormblue said:**
> Azz,

I have a question about ISP's blocking port 80.  It would seem to me that they would drop all traffic to port 80 coming in at their location.  I don't see how they could be blocking port 80 and the packets still hitting the router, but not the server behind it.

Can you please shed some light on this.  Thanks!

I can't say whether they block inbound and outbound trafic, or just outbound traffic.  I have never checked, to be honest.  I dunno.

---

