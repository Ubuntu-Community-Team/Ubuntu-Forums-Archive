---
title: "web server administration"
date: 2010-01-11
forum: Server Platforms
---

### Post by itachisxeyes on 2010-01-11
does anyone know of a good site/book/guide to learn about linux web server administration?
and also how do you find the your own nameserver numbers? would that just be the IP of my web server? 
networking isn't my forte, but i do intend to learn with this project.

---

### Post by HighCommander540 on 2010-01-11
> **itachisxeyes said:**
> does anyone know of a good site/book/guide to learn about linux web server administration?
and also how do you find the your own nameserver numbers? would that just be the IP of my web server? 
networking isn't my forte, but i do intend to learn with this project.

Well if you are using a router, there should be a page on your router administration that shows your nameservers. If not you Linux keeps the name servers it uses with DHCP in a fail located here "/etc/resolv.conf".

For an administration guide, what do you really mean by that? There are many guides here on the Ubuntu forums on how to set up a web server. Just use the search feature.

---

### Post by itachisxeyes on 2010-01-11
> **HighCommander540 said:**
> 
For an administration guide, what do you really mean by that? There are many guides here on the Ubuntu forums on how to set up a web server. Just use the search feature.

thanks (^_^)

and as far as the guide, i was just seeing what if any people with more experience really felt did a good job, i have one already, and have been doing a good deal of googleing XD
though to be more specific, i was looking for web server management, i already know how to set it up for the most part, just i never really had to manage one so i wanted to read up on it before i got started

---

### Post by HighCommander540 on 2010-01-11
> **itachisxeyes said:**
> thanks (^_^)

and as far as the guide, i was just seeing what if any people with more experience really felt did a good job, i have one already, and have been doing a good deal of googleing XD
though to be more specific, i was looking for web server management, i already know how to set it up for the most part, just i never really had to manage one so i wanted to read up on it before i got started

Webmin is a good GUI or HTTP server manager.

---

### Post by Iowan on 2010-01-11
I have a couple of Apress "Ubuntu Server Administration" books. Some good info - but not web-server specific.

---

### Post by cariboo on 2010-01-11
For free documentation, try [The Linux Documentation Project]("http://tldp.org").

---

