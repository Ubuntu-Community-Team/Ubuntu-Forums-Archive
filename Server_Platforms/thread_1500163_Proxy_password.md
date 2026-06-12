---
title: "Proxy password?"
date: 2010-06-02
forum: Server Platforms
---

### Post by Vrekk on 2010-06-02
I recently set up a transparent squid proxy server with dansguardian on my home linux gateway and I love it.  What I would like to be able to do is use this proxyed connection anywhere.  My first though was just to open up port 8080 and have the computer do the rest, and that works pretty well.  But the problem is, I don't want any random person who port scans my ip to see that I have a free proxy server they can use :mad:

So my question is this, how can I set up my gateway so that a user name and password is required to use it BUT ONLY if the request is coming from the internet.  I would still like to have the computers on my local network proxy-ed without having to go type a user name and password on each and every one of them 

FYI. My gateway is currently set up in this manner: Port 80 iptables -> Port 127.0.0.1:8080 -> dansguardian does its stuff -> Port ->127.0.0.1:3128 -> Squid does its stuff

My though process was that I could make it so dansguardian also listens to port 8081 (which would be open from internet side) and would ask for auth info on that port and not on 8080, but I don't know if it is even possible, let alone how to do it.

So my Linux loving friends, any ideas?

---

