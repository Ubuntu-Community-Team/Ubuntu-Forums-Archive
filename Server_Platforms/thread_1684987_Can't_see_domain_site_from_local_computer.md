---
title: "Can't see domain site from local computer"
date: 2011-02-10
forum: Server Platforms
---

### Post by mpratt on 2011-02-10
I am running ubuntu 10.04, and I have one website up and running 1 website.from my local server, from my local computer on the same network I can type in the ip address of my server and I do get the default webserver is running page, however when I try to connect to my domain, it cannot find it. I have run a ping, and it reached it just fine. Any suggestions would be usefull.

---

### Post by papibe on 2011-02-10
Could you post how exactly are you reaching your server when having success and faling?

Regards.

---

### Post by mpratt on 2011-02-10
> **papibe said:**
> Could you post how exactly are you reaching your server when having success and faling?
 
Regards.
 
I have my server sitting in the den, and I am trying to access the website from the laptop in my room. If I type in the ip address of the server I do indeed get the 
**It works!**

This is the default web page for this server.
The web server software is running but no content has been added, yet.
 
but when I try to access my website I created that is using my domain name, which I host at godaddy.com, it can't find the website. I can do a ping from my laptop to the domain name, and it returns no drops, so ping can hit the domain, but I cant' access it from Internet Explorer or Firefox.

---

### Post by papibe on 2011-02-10
That's generally not possible, since most routers don't allow it. There's a few that do, but I wouldn't know how to give you details.

Try checking your router's manual or go to its support website.

Good Luck!

---

### Post by elico on 2011-02-10
if you fo get ping and also can get the page with the ip..
add to your /etc/hosts file 
the line like
ip domain 
4.4.4.4 domain.com

and try  to reach the site again.
if you dont get it then it's something with your software.
if you do get it it means you have some DNS issues on you machine or in godaddy.

---

### Post by mpratt on 2011-02-10
> **papibe said:**
> That's generally not possible, since most routers don't allow it. There's a few that do, but I wouldn't know how to give you details.
 
Try checking your router's manual or go to its support website.
 
Good Luck!
 
when you say thats generally not possible, do you mean not possible to see domain from local machine?

---

### Post by acelino on 2011-02-10
make sure that A record on the registrar is pointing on your servers's IP address.

---

### Post by cariboo on 2011-02-10
Most routers won't allow you to access your external ip address from inside your internal network, go somewhere that has free wifi and try to access your web site by domain name.

---

