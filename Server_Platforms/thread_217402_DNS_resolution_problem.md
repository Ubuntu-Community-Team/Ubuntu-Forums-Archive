---
title: "DNS resolution problem"
date: 2006-07-17
forum: Server Platforms
---

### Post by tuxy on 2006-07-17
I have hosted a small webpage on my Apache server in /var/www/index.html. In my home LAN if I type in my PC's IP address or Hostname the webpage pop's up nice and quickly. I thought of making this web page visible out side my LAN ,for example-accessing the webpage from my work as well. Basically my home PC works like a small webserver with my static webpages on it.

So what I have done is I have registered my dynamic IP address in DynDNS so that I can get an URL & it is easy to remember. But, if i enter this URL or the DNS name I get my network router login page. I heard some where that I have to port forward the access to my local PC which has that webpage in it. I have tried portforwarding port 80 and 8080 from my router config. But still I get the router login page instead of my LAN PC's web page!!!

Am I doing the right thing in here?

I want to know more about forwarding the port to my PC from the router so that when some one accessing my web page they should not get my router login web page-they should get the webpage which is residing on my local LAN PC.

Quick help will be greatly appreciated.

---

### Post by DrSturgeon on 2006-07-17
All you *should* need to do is forward port 80 to your server, like you did.

But it sounds like your network router is running its own webserver for configuration, which means it's using port 80 itself, and probably not letting it get forwarded.

This is a little strange, because usually the router's configuration page is only accessible from the LAN side, not the WAN side of the router.  In fact, you don't really want people outside your network to be able to configure your router.

So, you need to do one of two things (#1 is preferrable)

1. Turn off the router configuration page on the WAN side of the router.
2. Change the router configuration page to a different port.

Then I bet your forward starts working.

If either of those two things are possible, they'd be in your router config somewhere; if not, it might be time to get a new router (or build a linux one!)

---

### Post by tuxy on 2006-07-18
I have gone through my router config I cudnt find any config setup by which I can turn off the WAN side.

How to change the router config page to diff port?

---

### Post by MJN on 2006-07-18
[LEFT]It might help if you tell us what make/model your router is! ;) [/LEFT]

---

### Post by tuxy on 2006-07-18
The router is NetCommNB5 modem.

---

### Post by tuxy on 2006-07-19
I figured it out. I have "rebooted" my Netcomm modem now everything works fine. It needs be booted again for the new settings to take place. 
Hooooh! :)

---

### Post by peru on 2006-07-21
I have the same problem as tuxy, with one small catch: I don't have access to my router! (ISP won't give me admin password - and, yes, I will be finding a new ISP but I can't for some time.)

So, got domain registered through Dyndns but entering the URL gets to my router admin page. Any (other) way around this?

---

