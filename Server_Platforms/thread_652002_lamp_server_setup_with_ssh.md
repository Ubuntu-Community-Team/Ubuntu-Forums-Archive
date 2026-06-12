---
title: "lamp server setup with ssh"
date: 2007-12-28
forum: Server Platforms
---

### Post by penguinfan on 2007-12-28
OK, so i set up a headless lamp computer that i would like to access from any computer in the world. This server will basically just have some info, pics and an few manuals on.

I setup everything according to [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)
I created an DynDNS account, installed ddclient, ssh server and a lot more.

Everything used to work fine if i access the server from within my lan, but when i connect via [http://my.dyndns.account.org](http://my.dyndns.account.org) i get to the login screen of my router.

I've been looking in the posts for the last 2 days but couldnt find a similar problem, hence, i would like to beg to the community to help me in my stupidity :)

---

### Post by cdenley on 2007-12-28
Your DynDNS domain resolves to your router's IP. You have to tell your router what to do with incoming connections on port 80 by configuring port-forwarding. With some routers, you can't connect to a server on the LAN by using the WAN IP (which your domain resolves to), but computers can still see it over the internet.

---

### Post by jtc on 2007-12-28
When you say you connect towards [http://my.dyndns.account.org](http://my.dyndns.account.org), then you are connecting to that url from inside your LAN? What happens if you try to connect to it from the outside?

(In other words: Have you set, and are you familiar with, port forwarding in your router?)

---

### Post by penguinfan on 2007-12-28
hi crew,

i've forwarded the port. It's using port 80 at the moment. 
I have a Mega 100WR router and there is available rules with default ports that one can easily select and add.

I can access the server by [http://my.ip.here/](http://my.ip.here/) from within the lan. But when i do [http://my.username.dyndns.org/](http://my.username.dyndns.org/) i either get to the router or the page cannot be displayed.

Thanx so far

---

### Post by penguinfan on 2007-12-28
OK i'm a little bit lost.
Cdenley: you mentioned that i should tell the router what to do with incoming connections. I'm looking around, but not sure what to look for.

I'll let u know

---

### Post by cdenley on 2007-12-28
I was talking about forwarding the port, which it sounds like you already did. I also mentioned in my post that some routers will not forward the port for clients on your LAN. You should try or have someone else try accessing it from a computer outside your LAN.

---

### Post by penguinfan on 2007-12-28
OK, tried to access from outside my lan. And it's working. yepeeee

Thanx Cdenley and jtc. Ubuntu rocks.
PS i would like to thank my wife for putting up with my crap :)

---

### Post by penguinfan on 2007-12-28
what i've learned when setting up a webserver;

1. be patient
2. read the posts
3. dont feel stupid (even though your wife might think so)
4. go through the setup steps point for point
AND 5. remember. . . check your router settings. Like in my case this stupid cheap router won't forward requests from within the lan. Wonder whay that is??

---

