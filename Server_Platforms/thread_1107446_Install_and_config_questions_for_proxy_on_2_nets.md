---
title: "Install and config questions for proxy on 2 nets"
date: 2009-03-26
forum: Server Platforms
---

### Post by cackles on 2009-03-26
Before I start to instal squid I just want to check it will do what I want it to and see if there's a tut on what I'm after. I cant find a tut specifically for my needs or I missed it, or its easier than I think (wishful thinking).

My server is on my network currently but Im going to add in another card with another inet connection and set it up from scratch again using 8.10.

The 'idea' is that I can use a second connection Im getting, for almost free because they are kindly throwing it into my phone package, to offload some traffic.

Sooooo ... I'd like my server with one card on the net and the other on the router.

I'd like my local machines to connect to the server when I want them and surf etc. via it when I need them to (ie when Im gaming online) to take the strain off of the connection I currently have.

I can configure the local machines to use either connection when I need them to.

What I dont know is:

Is this easy enough to do?

Will all my machines going through the server look like the server? Which is what I want, I dont want anyone to be able to tell the difference if its the server requesting or someone connecting through it.

Should I allow the router to connect to the server or just the localhosts? 192.168.0.1 is my router and 100-200 the range - acl 192.168.0.1/200 or 192.168.0.100/200 or 192.168.0.1 then 192.168.0.100/200?

Can I take off all caching so that the server holds nothing and it all goes direct to the machine wanting it? I dont think I need that feature - 'cache deny'?

Will all applications I setup for using a proxy go through one port I can choose on my server or do I need to config it for everything, like choose a port for every application and give it rules? Id like http, https, ftp and well actually I want all the messaging clients and any other unforseen traffic to work. Im guessing thats either saving or making a lot of allows or denies.

Is squid the best for this?

Ive probably forgotten something but if I can get the basics up and then work out the rest Id appreciate it, thanks.

---

### Post by BkkBonanza on 2009-03-26
I'm sorry - I can't figure out what you are doing. Maybe that's why no one has replied.
Sounds like you have a network going through a router to the internet now. 
And you want to add a nic to one machine so that you can gain access to a second internet connection. 

Is that connection going to be through a modem or will it have a router as well?
Or are you planning to have everything go to the server and then it routes it through either connection?

How you do this really depends very much on how you connect the pieces. It doesn't sound like you need a proxy at all though. A few routing commands for load balancing ought to work depending on how things are connected.

---

