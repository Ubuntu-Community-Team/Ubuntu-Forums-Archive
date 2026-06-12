---
title: "How do I make my Apache server viewable to everyone?"
date: 2010-01-28
forum: Server Platforms
---

### Post by SCTPenguin on 2010-01-28
I have it set up so when I go to [http://localhost.com](http://localhost.com) it shows my server. I'm not sure how I can make it viewable to everyone though. Thanks in advance.

---

### Post by pirateghost on 2010-01-28
who are you wanting to make it viewable to?
for other users on your LAN, just have them point to the IP address that the server is on.
for outside world to connect, you need to forward a port from your router to the machine that the server is on and give someone your IP address or use DYNDNS.org account to create a dynamic dns configuration.

---

### Post by SCTPenguin on 2010-01-28
> **pirateghost said:**
> who are you wanting to make it viewable to?
for other users on your LAN, just have them point to the IP address that the server is on.
for outside world to connect, you need to forward a port from your router to the machine that the server is on and give someone your IP address or use DYNDNS.org account to create a dynamic dns configuration.

Okay so I own a domain name - I guess my question is, how do I use my server to host my domain?

---

### Post by pirateghost on 2010-01-28
> **SCTPenguin said:**
> Okay so I own a domain name - I guess my question is, how do I use my server to host my domain?
point your domain name to your EXTERNAL ip address, and forward the port that you are hosting on to the local machine that is hosting it.  if you dont understand basic networking/security, i would suggest you do NOT host your own webserver and open up your machine to attack.

---

