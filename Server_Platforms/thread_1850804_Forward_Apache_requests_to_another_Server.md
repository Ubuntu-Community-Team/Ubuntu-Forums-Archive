---
title: "Forward Apache requests to another Server"
date: 2011-09-27
forum: Server Platforms
---

### Post by chrislynch8 on 2011-09-27
Hi,

I am moving a Database application from one server (server01) to another server (server02) on the same LAN. Server01 is my main Apache server and is configured to redirect external request to use Https. Internally, I am just chanign my DNS to point to the IP address of the new server02 for access to the application and this is working fine, just configure apache to match the servername nad document root.

How do I configure Apache on server01 and 02 to allow access to the application on server02 via an External IP and force access over https.

Rgds
Chris

---

### Post by Ryan Dwyer on 2011-09-27
What's stopping you from changing the port forwarding rule in your router so requests go straight to server02?

---

### Post by chrislynch8 on 2011-09-27
Hi,

Server01 is my Router, Firewall etc. and that will still have one small internal web application.

Rgds
Chris

---

### Post by Ryan Dwyer on 2011-09-27
I'm not an iptables guru, but surely it's possible to add a rule that forwards incoming port 80 requests on the external interface to server02. Internally you'd access both servers directly on port 80.

---

### Post by SeijiSensei on 2011-09-27
Run Apache in [reverse proxy mode]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") on server 1.  You can selectively forward requests for some virtual hosts while answering requests for other virtuals on the same machine.

---

### Post by chrislynch8 on 2011-09-27
The Reverse Proxy worked a threat.

Rgds
Chris

---

### Post by chrislynch8 on 2011-09-27
One final question, to handle the forced redirection over https which server would this be handled on?

The server that is acting as the reverse proxy or the apache server that is getting forwarded to?

Rgds
Chris

---

### Post by SeijiSensei on 2011-09-27
I've never used a proxy with https.  It might look like a "man-in-the-middle" attack to the browser since it's going to try and set up an SSL connection to the proxy, but the real SSL connection needs to be with the actual server.

You might consider using either iptables or an application-level TCP proxy.  I use the hoary "[tcpproxy]("http://www.sourcefiles.org/System/Daemons/Proxy/tcpproxy-1.1.9.tar.gz")" program in a number of situations like this.  You'd have to compile it from source, but it should compile cleanly if you first run "sudo apt-get build-essential" to install gcc and associated programs.

---

### Post by HermanAB on 2011-09-28
I have found that Socat is easiest for forwarding random stuff from one machine to another.

---

