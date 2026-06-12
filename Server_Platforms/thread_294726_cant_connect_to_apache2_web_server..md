---
title: "cant connect to apache2 web server."
date: 2006-11-07
forum: Server Platforms
---

### Post by twigboy on 2006-11-07
I finally setup my webserver and using dyndns I can access [www.mysite.com](www.mysite.com) from the computer running apache2.  
If I try to access [www.mysite.com](www.mysite.com) from anohter computer on the lan it pulls up my router setup page.  
If I try to access [www.mysite.com](www.mysite.com) from an external computer I get a connection timeout.
I have setup my dyndns account and cofigured my router correctly(atleast it says it can resolve my domain).  I have added the server ip domain and comp hostname to the /etc/hosts file, changed the listening port and added the correct servername to the httpd.conf file.
Any ideas whats goin on?
Thanx

---

### Post by tomBorgia on 2006-11-07
As your getting your router's page I'd have thought that you have not set up port 80 to be forwarded to your webserver - ther should be a option on your router's page to forward all port 80 requests to a specific IP address (the address of your server) - this should sort out external access as well :D

---

### Post by kidders on 2006-11-07
Hi there,

It doesn't look as though your router is forwarding packets destined for port 80 to the right place. At any rate, imo your LAN shouldn't really be using external DNS servers to resolve your hostname.

If it were me, I'd ...

[LIST]
[*]Set up a local DNS server to resolve local names. This will also avoid potential confusion at your router over what to do with packets arriving from local addresses for port 80.
[*]Double-check the router's packet-forwarding configuration. You should bear in mind that, if your apache is running on a computer with a DHCP-assigned address, your port forwarding config will most likely break from time to time, whenever its address changes.
[/LIST]

**Edit:** NB: If you configure your router to forward local packets on port 80 to your apache server, you will probably lose access to your web-based router config.

---

### Post by twigboy on 2006-11-07
Thanx for all the help.
Sorry I forgot to mention I have apache listening on port 8080.  I believe I have this set in httpd.conf or apache2.conf.
Also I have a statice internal ip for my comp and have packet forwarding set up to forward to this address on 8080.  Do I need to forward to 80?

Kidders what do you mean by setting up a local DNS server?

---

### Post by kidders on 2006-11-07
Hey again,

> **twigboy said:**
> Sorry I forgot to mention I have apache listening on port 8080.
In that case, the address you should be requesting is [http://www.whatever.tld:8080/](http://www.whatever.tld:8080/) ... just in case!

> **twigboy said:**
> Kidders what do you mean by setting up a local DNS server?
I was referring to the idea that when you need an address for a local computer, the last thing you should ask is an *external* DNS server. On most configurations, that would lead to unexpected behaviour anyway. Ideally, internal packets for your apache server should be addressed to its internal IP, not the entire network's public IP. Running a local DNS server is one way of creating this effect ... in other words, your network would operate the way you imagine it should (for lack of a better way of putting it hehe).

You don't *have* to run a DNS server, but it's often sensible ... especially if you have more than one or two computers. Constantly fiddling with /etc/hosts can get a bit tedious!

---

### Post by twigboy on 2006-11-07
Hah adding the 8080 to the website fixed the problem.  I didnt know I would need that.  Thanx Kidders.

btw do you know of a tutorial on setting up a local dns server?

---

### Post by pppetter on 2006-11-07
Hmmz. Are you sure you forwarded port 80 to port 8080 on your server? If you haven't you will, as someone mentioned, type [www.yoursite.com:8080](www.yoursite.com:8080)

---

### Post by kidders on 2006-11-07
Hey again,

Yeah, port 80 is the default for the HTTP protocol, just as 443 is for HTTPS. If you're using something different, you need to say so. May I ask why you chose port 8080? (It's just that if it's an attempt to prevent your web server being bombarded by malicious users, you should probably opt for a less commonly used one.)

If you want to play with DNS, the app you're looking for is called "bind". There are lots of HOWTOs ... once you've done the apt-get, they should all be more or less the same as each other :-)

If you choose to try it out, it will give you the added advantage of (very slightly) speeding up your web browsing, by caching DNS information for you.

---

### Post by twigboy on 2006-11-08
Thanx for the info kidders.
I chose 8080 just for testing, so far I think Ill change it to 80 if my ISP allows.

---

