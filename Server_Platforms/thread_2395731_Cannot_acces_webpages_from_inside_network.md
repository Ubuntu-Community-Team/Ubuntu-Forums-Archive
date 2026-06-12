---
title: "Cannot acces webpages from inside network?"
date: 2018-07-05
forum: Server Platforms
---

### Post by Heeter on 2018-07-05
Hi all,

This is for my ubuntu 16.04 Server running Apache2 Mysql, php,,,,,

This is a mature server that has had no issues working for me.

Yesterday, this problem started where I can't access the webpages that it serves from inside the same network.

I can access the webpages just fine outside. But refuses to connect from inside the same network that the server is on.

I have tried 2 different computers and my android phone, and multiple browsers. Tried wired and wireless computers, nothing

I do connect to the webpage when I type in the local IP address of the server into my laptop browser.

But it doesn't work when I type in the domain name.

Any help would be greatly appreciated

---

### Post by wyliecoyoteuk on 2018-07-06
How is your local DNS configured?

---

### Post by SeijiSensei on 2018-07-06
Open a terminal and type the command "host server.domain.name" using the name of your server.  Does it resolve to an IP address?

---

### Post by TheFu on 2018-07-06
Definitely a DNS issue or perhaps some router changes or firewall changes happened?   Some consumer router firmware prevents access to services inside the network as security protection.

But I'm with most of the others questioning the name resolution.  Newer versions of Android only support DNS for resolution which can break android access to non-routable, internal, IPs.

---

### Post by Heeter on 2018-07-06
Hey Guys,

Thanks for Ideas, I went into the router and sure enough I mistyped a DNS into the wrong section of the router.

Thanks for all your help in figuring out the DNS issue

---

