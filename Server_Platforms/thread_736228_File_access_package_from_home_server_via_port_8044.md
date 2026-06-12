---
title: "File access package from home server via port 80/443"
date: 2008-03-26
forum: Server Platforms
---

### Post by super_czar on 2008-03-26
Hola..

Is there any package that would allow me to remotely access files from my local ubuntu LAMP server via port 80 or 443?

I am running an ubuntu server at my home which is serving multiple purposes, mostly tuned towards enabling access to my home network from office/while travelling

- Torrentbox
- Music server (Ampache)
- Online album
- Proxy server

All of these (php ) apps sit under multiple folders under var/www/

The only issue I have now is how do I access files from my local machine that are outside var/www/

I know I can use SFTP but my office proxy allows for only port 80/443 connections
Is there any other method I could possibly use?

I know I can use webmin to do this but I do not want to install an overtly complex application like it...any other way to do it?

---

### Post by pseudo-random on 2008-03-26
You need something like phpexplorer. Lets you get right to the / of things...

---

