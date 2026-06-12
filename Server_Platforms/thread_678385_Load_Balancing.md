---
title: "Load Balancing"
date: 2008-01-25
forum: Server Platforms
---

### Post by etechship on 2008-01-25
I have read alot about having two internet connections, but I am trying to do it backwards.

I want to have a network set up like this:
[http://ucstreaming.net/img/load_pic.jpg](http://ucstreaming.net/img/load_pic.jpg)

Server 1: Load Balancer (get's requests)
Server 2: Copy One
Server 3: Copy Two
Server 4: NAS Server

I am using a network like this to do red5 flash video streaming. The NAS server stores the videos, server 2 and 3 stream them.

How to I tell server 1 to send every other request to server 2 or server 3?

I have tried balance, but I get an  error. I think there is a easier way to do this.

thanks

---

### Post by HermanAB on 2008-01-25
Read the Advanced Routing Howto on tldp.org.

Cheers,

Herman

---

