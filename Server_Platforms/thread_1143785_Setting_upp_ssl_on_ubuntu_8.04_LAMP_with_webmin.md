---
title: "Setting upp ssl on ubuntu 8.04 LAMP with webmin"
date: 2009-04-30
forum: Server Platforms
---

### Post by aberry5555 on 2009-04-30
Hi there, I'm having some difficult getting my head around how to install SSL certificates in to my web server, and if anybody could point me in the right direction I'd be much appreciated!

Basically I have a server with 1 and 1 hosting and it was installed with ubuntu 8.04 minimal. I then went on to install LAMP using a single command that I've forgotten now... it's something like "sudo (missing bit here) lamp-server", which worked fine; I have apache, PHP and mysql working all ok together.

I then installed the CMS Webmin and set up two name-based virtual hosts listening on both the IPs I have.

Basically, from here, I'm stuck. I'm trying to install an SSL certificate for each virtual host on it's own IP, I've tried using webmin's configuration utility to do SSL - per - ip, but when I try to either upload or type out my private key and cert it gives me the error that neither of them are in the correct PEM format..

If anyone knows webmin and can tell me where to go from here I'd much appreciate it, as I'd like to keep it as much based in the CMS as possible, if there really is no other way than to SSH in and working through command line then it's fine, but I really need some pointers!

---

