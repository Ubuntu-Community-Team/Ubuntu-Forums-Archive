---
title: "Getting things straight: Apache, SSL, Multiple External IPs / Internal IPs"
date: 2007-07-01
forum: Server Platforms
---

### Post by robin.com.au on 2007-07-01
I've been spending days to get my head around apache+ssl and im still left with uncertainties.
Just wanna get things straight. Here's what I've gathered. Correct me if I'm wrong.

For a **PROPER** Apache+SSL configuration with **multiple** websites:
Each site must have a unique **external-IP** and a unique **internal-IP**.

[COLOR="Gray"]External-IP as in 220.245.32.14 , outside the router, provided by the ISP.
Internal-IP as in 192.168.0.2 or 10.1.1.2 , behind the router, inside a LAN network.[/COLOR]

For example:
[http**s**://www.aaa.com](http**s**://www.aaa.com) goes to 215.323.24.54 which goes into my router which forwards to 192.168.0.2
[http**s**://www.bbb.com](http**s**://www.bbb.com) goes to 223.436.34.57 which goes into my router which forwards to 192.168.0.3  
which probably means these URLs are going to 2 different computers and 2 different routers.

Whereas the following example is **not** correct:
[http**s**://www.aaa.com](http**s**://www.aaa.com) goes to [COLOR="Red"]215.323.24.54[/COLOR] which goes into my router which forwards to 192.168.0.2 
[http**s**://www.bbb.com](http**s**://www.bbb.com) goes to [COLOR="Red"]215.323.24.54[/COLOR] which goes into my router which forwards to 192.168.0.3
Because the [COLOR="Red"]External-IPs[/COLOR] are not unique.

Am I correct? Or greatly confused?

Still talking about SSL, I know that you can use namevirtualhost in /etc/apache2/httpd.conf that allows one external-IP and one internal-IP, and it works but I gathered that it is not the 'proper' way.


Thank you in advance.

---

### Post by Maxtorm on 2007-07-03
You are correct with respect to external IPs.  They must be unique for SSL purposes because SSL is bound to IP rather than host name (I believe this is because host headers are not in the SSL specification, but don't quote me).  With respect to internal IPs, I expect most environments would use at least one internal IP per external IP, so it would not be an issue.  However, if there was some reason for mapping many external IPs to one internal IP (bandwidth sharing perhaps?), I don't think that would be a problem for SSL.  You might have to get tricky with they way SSL is configured on the server.  That is, serve SSL to incoming requests from external IP address A on port 443 and SSL requests from external IP address B on port 444.

---

