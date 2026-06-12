---
title: "problems with Apache server, ftp server"
date: 2006-05-03
forum: Server Platforms
---

### Post by twaern on 2006-05-03
i run Ubuntu 5.10 Breezy .. Server Install 

i have installed apache, ftp, etc... but can only access the servers via my internal ip of 192.168.2.10 ... but other users can access it via 

[http://twaern.is-a-geek.org](http://twaern.is-a-geek.org) 

-----


i cant even when i type [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) bring the page up.  but when i ask my friends to connect to the server using [http://twaern.is-a-geek.org](http://twaern.is-a-geek.org) it works for them


anyone know whats going on, if you need more information just ask will try to be more clear.. i am a newbie just experimenting with linux ..

---

### Post by wsanders on 2006-05-03
It sounds like your router isn't configured to forward requests for port 80 to your computer. Let us know the brand/model of your router and we can walk you through setting up port forwarding.

---

### Post by twaern on 2006-05-04
I have a DSL connection, and the router is one of the ones with a DSL Modem/Router installed. but the main problem is if someone types in [http://twaern.is-a-geek.org](http://twaern.is-a-geek.org) on another internet connection like from the outside world they pull up apache . its just from any computer thats connected to my router doesnt pull up apache from any address except for [http://192.168.2.10](http://192.168.2.10)

---

### Post by airtonix on 2006-05-04
yeah twaern, firstly....if poeple outside your connection can get your apache frontpage it means that port forwarding is happening....

What you might want ensure is that there aren't any firewall rules enforcing this restricted view from your internal side......like only allow incomgin port 80 requests from that ip only.....

Then you may want to check out the apache config file and see if that is limiting what ip can connec to the apache server via port 80...

just some suggestions....

---

