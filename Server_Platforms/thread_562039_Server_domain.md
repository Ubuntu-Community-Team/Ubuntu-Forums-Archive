---
title: "Server domain"
date: 2007-09-28
forum: Server Platforms
---

### Post by Mario_Lib on 2007-09-28
i'm setting up a ubuntu server as a local lan server i read i lot o toturials but when i need to configure the postfix asks about the server domain name

i don't know how to give my server a domain name and let other local pcs see it

---

### Post by 505 on 2007-09-28
The server domain only applies when you have an own domain, such as example.org. You can then name this server.example.org, and with proper DNS settings the world can find you server. If you don't need that, then use no domain, and clients from within the network can find the server by its IP address.

---

### Post by koenn on 2007-09-28
the domain name postfix want to know about is the part after the @ in the email addresses it will handle (william.gates@microsoft.com ==> domain is microsoft.com). It needs to know so that it sees your domain name in "From" or "To" fiels, it will know what to do. 

This in turn has to do with what domain name you use on your network, and how you want to handle mail for other domains (e.g. [email]you@your.isp.com[/email])

If your just playing with your own network, the mail domain is whatever you put for domain name when setting up the server.

---

