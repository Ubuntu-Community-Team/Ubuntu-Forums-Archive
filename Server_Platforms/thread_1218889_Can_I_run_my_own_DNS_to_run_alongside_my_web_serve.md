---
title: "Can I run my own DNS to run alongside my web server...lol"
date: 2009-07-21
forum: Server Platforms
---

### Post by strujillo.jr on 2009-07-21
Ok so I set up my site with the ubuntu server following the tutorial on [NetTuts]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/") and after spending for ever trying to do this darn DNS crap, I am curious if I could just run my own on the server that will update all my info right away thatway I dont have to deal with editDNS and other services? Is this possible? If so where should I start? Thanks in advanced :-)

---

### Post by NewbieNik on 2009-07-21
The Server you are asking about is BIND. You can install it by entering

sudo apt-get install bind9

This, however will only serve systems that are set to use your server as their DNS (So not any client accessing your web-site unless spefically told to)
It will help if you set your server to look at itself for DNS resolving, but I can't see how that would help you.
What are you trying to achieve as the end result?

---

### Post by strujillo.jr on 2009-07-21
Well, I am the kind of person that likes to do everything himself. So I have been using EditDNS for the last week but I dont trust its Dynamic DNS service. I dont know why, i am just like that. So I figured if I could just install a Dynamic DNS client thingy on my server and just run it from there it would be WAY easier. Now im not sure if thats possible...

---

### Post by NewbieNik on 2009-07-21
OK, but what I was trying to get at was, are you just trying to get the DNS to resolve for your own clients on your network? In which case fine, or are you trying to get it to resolve for external clients accessing your web-server? In which case, not fine.

DynamicDNS programs do a whatsmyip (Or similar) query for themselves and then enter that IP address into the DNS servers you have registered your domain with (or that you specify).
External clients will NOT query your server for DNS unless they have your IP set in their NIC configuration. However internal clients can, but then you wouldn't need DynDNS software....

---

