---
title: "Ultra-lightweight webserver for wordpress blog?"
date: 2011-08-11
forum: Server Platforms
---

### Post by robgr85 on 2011-08-11
Hi!

I have small home atom-server on netbook (with damaged screen) with Intel Atom N450 1.6Ghz CPU and 1GB of RAM. I am looking for web server, that would not eat much resources when hosting wordpress blog (up to 50-100 readers at once in veeeeeery far future) - posts in most cases will be only text based, without big images or archives (I'm not sure if it is important).

The brain of my atom-server is latest 32-bit ubuntu server, without X's, I access it from ssh console only. It is already:
- proxy gate for my internal network (squid)
- my gmail backup/IMAP (dovecot & getmail)
- file server for my internal network (samba)
- vpn gate (openvpn)
- hosting torrents (transmission)
- firewall (ufw)
- repository (subversion, just for my personal projects)
- mysql (just for my personal training)

and I would like to get something really lightweigt to serve wordpress blog. I think, that apache might be overkill for my small needs. 

In near future I will probably add 1 cam monitoring with zoneminder - as far as I remember it does not depends on apache, and some other webservers can be used.

I would appreciate for adivces, having security, zoneminder compatibility & small hardware requirements in mind.

Thanks

---

### Post by stlsaint on 2011-08-11
[NGINX]("http://wiki.nginx.org/") .. A personal fav of mine!

> "ginx is a free, open-source, high-performance HTTP server and reverse proxy, as well as an IMAP/POP3 proxy server. Igor Sysoev started development of Nginx in 2002, with the first public release in 2004. Nginx now hosts nearly 7.65% (22.8M) of all domains worldwide. 

Nginx is known for its high performance, stability, rich feature set, simple configuration, and low resource consumption."

---

### Post by robgr85 on 2011-08-12
> **stlsaint said:**
> [NGINX]("http://wiki.nginx.org/") .. A personal fav of mine!

Thanks, I will take a look at it.

---

### Post by robgr85 on 2011-08-18
> **salemeni said:**
> you can use lighttpd 
[www.lighttpd.net](www.lighttpd.net)

Thanks for the tip, but nginx sounds a bit better to me.

---

### Post by PierreRobiquet on 2011-08-18
> **robgr85 said:**
> Hi!

I have small home atom-server on netbook (with damaged screen) with Intel Atom N450 1.6Ghz CPU and 1GB of RAM. I am looking for web server, that would not eat much resources when hosting wordpress blog (up to 50-100 readers at once in veeeeeery far future) - posts in most cases will be only text based, without big images or archives (I'm not sure if it is important).


I run a very similar set up except I'm running it on an Intel Atom N270, have you thought about giving the RAM a bump to 2GB? It's fairly cheap to do and will lift some of the constraints.

---

### Post by robgr85 on 2011-08-18
> **ConcreteDonkey said:**
> I run a very similar set up except I'm running it on an Intel Atom N270, have you thought about giving the RAM a bump to 2GB? It's fairly cheap to do and will lift some of the constraints.

Currently, there is enough RAM for my small server system (when everything is running there is still some free memory left). Maybe I'll change RAM in the future - if the load problems arise, but now I do not feel the need for any changes.

---

