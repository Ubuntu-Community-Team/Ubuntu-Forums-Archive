---
title: "ircd-hybrid server can't accessed from client computer"
date: 2008-10-17
forum: Server Platforms
---

### Post by Putu Wiramaswara Widya on 2008-10-17
I Have the problem with my IRCD-Hybrid IRC Server...

My school has an Ubuntu 8.04 LTS Server. That server was used for Internet Gateway, Local Web server, Local E-Mail server and Local DNS Server.

I have install IRCD-Hybrid server package to allow the user in my school to chat using an IRC Client. Unfortunately, the user can't access IRC Server both by the Server's Domain Name and Server's IP Address with the "Connection Refused" message (Internet GW, Web and E-Mail Server are Okay!). I have tried it from the server itself, and same as the client (Except using "localhost")

Is there any help for me??

---

### Post by kennedy7 on 2008-11-13
yeah, change the ports to 6667 and forward your router to them, then replace 127.0.0.1 and 192.169.0.1 to the servers public ip.
Then it should work. If it doesnt you can ask more question at my irc
tyspage.doesntexist.com/6667 channel #ty.

---

