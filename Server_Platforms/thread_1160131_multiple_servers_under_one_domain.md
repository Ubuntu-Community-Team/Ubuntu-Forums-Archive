---
title: "multiple servers under one domain"
date: 2009-05-15
forum: Server Platforms
---

### Post by pigfarmer0 on 2009-05-15
I have a linux server running ubuntu 7.10 and have recently set up a windows server on another pc. I want to be able to access the linux server from the same domain as before; i.e. [www.example.com](www.example.com), and access the windows server from [www.example.com/windows](www.example.com/windows). Is there a way to do this? 
Any help would be greatly appreciated
Thanks

---

### Post by FrankT-Qc on 2009-05-15
If you have two IPs you can access, you can always use redirection...

If not :

Many proxy solutions have redirection features that could help you.

Instead of sending traffic directly to one of your machine's web server, direct traffic to your proxy (that can be on the same machine as one of the web servers) which then redirects traffic to the right server...


example : 
box1 :
ubuntu + proxy (port 80) + webserver(port 8080)
direct [www.whatever.com/towinmachine](www.whatever.com/towinmachine) to box2:80
direct the rest to box1:8080

box2 :
unmodified windows machine

NOTE : redirecting external traffic to "localhost:8080" is something i would **avoid at all cost**... Rather you might want to use "123.456.789.123:8080", (your box1's ip) it sounds silly (and anti performant...) but if you go through localhost, you might be bypassing allot of security policies... You can still use localhost, but be sure to be totally conscious of what you're doing...


have fun

---

### Post by pigfarmer0 on 2009-05-15
Thanks I've got that to work :D

---

