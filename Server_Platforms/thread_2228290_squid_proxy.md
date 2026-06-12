---
title: "squid proxy"
date: 2014-06-06
forum: Server Platforms
---

### Post by damienmcjr on 2014-06-06
hey im trying to set up squid for content filtering on my network. what i want to do is to filter all out going traffic so people are not using proxies to by pass my settings other than my self to have unblocked access. i have open dns setup but you can by pass it by changing the dns and every user is an admin on their own pcs so its not possible to lock them down

iv tried to setup squid but it gives me an error when i run initialize the cache 
this the error 
[COLOR=#393939][FONT=arial]Initializing the Squid cache with the command squid3 -f /etc/squid3/squid.conf -z ..
[/FONT][/COLOR]
2014/06/06 20:56:22 kid1| Creating missing swap directories
2014/06/06 20:56:22 kid1| No cache_dir stores are configured.

my configuration is 
hp ml115 server with 40gb os
webmin and putty for remote access to server 
2x 320gb ntfs samba
dhcp server running 
os is lubuntu 14.04
webmin + putty for remote

---

### Post by deadflowr on 2014-06-06
Thread moved to **Server Platforms**

---

### Post by damienmcjr on 2014-06-07
> **deadflowr said:**
> Thread moved to **Server Platforms**
thanks dident know where to put it

---

### Post by elico on 2014-06-12
You know it's not really an error...
Squid is a caching service and in most cases there is a need for a caching directory.
In anyway since squid is pretty smart it's better to have a small cache directory just to make the internet surfing faster in some cases.
squid -z is not in use for you so just start squid.
If you have other questions about it just ask..

> **damienmcjr said:**
> hey im trying to set up squid for content filtering on my network. what i want to do is to filter all out going traffic so people are not using proxies to by pass my settings other than my self to have unblocked access. i have open dns setup but you can by pass it by changing the dns and every user is an admin on their own pcs so its not possible to lock them down

iv tried to setup squid but it gives me an error when i run initialize the cache 
this the error 
[COLOR=#393939][FONT=arial]Initializing the Squid cache with the command squid3 -f /etc/squid3/squid.conf -z ..
[/FONT][/COLOR]
2014/06/06 20:56:22 kid1| Creating missing swap directories
2014/06/06 20:56:22 kid1| No cache_dir stores are configured.

my configuration is 
hp ml115 server with 40gb os
webmin and putty for remote access to server 
2x 320gb ntfs samba
dhcp server running 
os is lubuntu 14.04
webmin + putty for remote

---

