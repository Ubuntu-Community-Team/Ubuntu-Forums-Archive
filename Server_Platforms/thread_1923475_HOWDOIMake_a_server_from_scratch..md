---
title: "HOWDOI:Make a server from scratch."
date: 2012-02-10
forum: Server Platforms
---

### Post by 128keaton on 2012-02-10
Hello all, this is my first post on ubuntu forums. I want to setup a web server, with domain name, on one computer. I don't want to use a 3rd party service, just linux packages and such. So far i have Apache2 and the basic LAMP necessities.
How would i go about setting up a DNS server?

---

### Post by memilanuk on 2012-02-10
By one of our forum members...

[http://woodel.com/](http://woodel.com/)

---

### Post by TheFu on 2012-02-10
> **128keaton said:**
> Hello all, this is my first post on ubuntu forums. I want to setup a web server, with domain name, on one computer. I don't want to use a 3rd party service, just linux packages and such. So far i have Apache2 and the basic LAMP necessities.
How would i go about setting up a DNS server?

Welcome to the forums. I hope you find all the answers you need by searching first and asking second.

First, you must understand that for a web server to be "seen" on the internet, you **must** use an external provider for 
* Domain Name Registration
and you SHOULD use an external provider for
* DNS

Without those 2 items, nobody will be able to find your server.  If your that you setup and run DNS fails (or gets hacked), then you want an external DNS provider.  It is true, you don't **need** an external DNS provider, but DNS is the 2nd most likely service to be hacked on the internet.  If you are just a month behind on patches, you can be hacked.

DNS is usually provided by a program called BIND. [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) O'Reily sells a book about it.  When I setup my first DNS server, I was unable to succeed until reading a few pages from that book, so either it is the greatest book ever written or was a complete waste of money. I lean towards the former.
You can cheat and not have an internal DNS server by editing the /etc/hosts files on all the PCs for your network.  That's true for http and most other protocols, but for an email server, you must have an MX DNS record.

* [http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) explains the 4 things you need for an internet website and why you might **not** want to get the necessary services from a single provider.
* I've made DNS mistakes too [http://blog.jdpfu.com/2010/03/03/oops-bad-dns-update](http://blog.jdpfu.com/2010/03/03/oops-bad-dns-update)

If you choose to use a webGUI to help setup and admin a server, please, please, please be certain you properly secure access to those tools.  If you make them available on the internet and they aren't secured, then someone will own your server pretty quickly.  I see constant attempts to access webmin and phpadmin and mysqladmin and about 10 other variants on my websites.  I don't use any of those tools, so blocking them at the reverse proxy makes the most sense. If you must make them available on the internet, try to prevent outside IPs except from your main subnet AND have a very long and secure password - 25+ characters and never access the control panel from a wifi or public network.

There's a security methodology that says internet facing services should each be run on a single, specific server.  That would mean you 1 server for DNS, another for reverse proxy, and another for your web server and a final server for your RDBMS.  In this way you can ensure only the necessary public services are available publicly.  Ubuntu servers may run services that you didn't know you asked for, so be certain to use nmap to check your servers for undesired listeners from both inside and outside the network.

Falco is known for his how-to guides. He has one on [http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3)  He will help you get things working, but often security best practices can't be included in the guides.

You are going to have lots of fun with this!  Enjoy.

---

