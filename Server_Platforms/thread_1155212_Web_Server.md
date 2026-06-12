---
title: "Web Server"
date: 2009-05-10
forum: Server Platforms
---

### Post by k33bz on 2009-05-10
I want to set up a web server so others on the internet can view my writings, maybe even set up a shopping cart to purchase a few things. My ISP uses a firewall. So my question is what, or how can I set this up?

---

### Post by jamesrfla on 2009-05-10
You can host web sites using apache2. Providing your ISP and if it is DSL or cable would help.

---

### Post by k33bz on 2009-05-10
My ISP is cable. The company is Cableone, if that helps.

---

### Post by albinootje on 2009-05-10
> **k33bz said:**
> I want to set up a web server so others on the internet can view my writings, maybe even set up a shopping cart to purchase a few things. My ISP uses a firewall. So my question is what, or how can I set this up?

Normally you would need to use port_forwarding in your DSL-router or cable-modem to point it to your port 80 (and 443 for [https://)](https://))

Installing apache is as easy as this :
```

sudo apt-get install apache2

```
If you're interested in a more light-weight web server with a somewhat easier configuration, try this instead :
```

sudo apt-get install lighttpd

```
See also : [https://help.ubuntu.com/community/lighttpd](https://help.ubuntu.com/community/lighttpd)

---

### Post by daboroe on 2009-05-10
i beleive apache2 is better.

---

### Post by k33bz on 2009-05-11
ok, I got that all set up, I am not sure if it is visible outside my own network and available to the Internet. Will be checking that here later today.

However, I am having a hard time looking for domain information for my server's IP address. How do I go about adding a URL to my server that isnt just typing in the IP address?

---

### Post by albinootje on 2009-05-11
> **k33bz said:**
> I am having a hard time looking for domain information for my server's IP address. How do I go about adding a URL to my server that isnt just typing in the IP address?

Can you clarify your question ?
Are you looking for something like [http://www.dyndns.com](http://www.dyndns.com) to have some sub domain for your webserver ? Or do you want a real domain ?

---

### Post by trentscott4 on 2009-05-11
You simply buy a domain name from a registrar like GoDaddy (Google for coupons to save a couple bucks), make an account at ZoneEdit.com or everyDNS.net and create an "A record" that points to your home IP address. You can find that by going to whatismyip.com. If you want to run mail (eventually), you'd create an additional "MX record" that points to your IP.

Then, you need to login to your router and forward port 80 (for a webserver) to your server machine's LAN (internal) IP. i.e. You can find that by opening a console on the server and typing 'ifconfig'.

---

### Post by k33bz on 2009-05-11
> **trentscott4 said:**
> You simply buy a domain name from a registrar like GoDaddy (Google for coupons to save a couple bucks), make an account at ZoneEdit.com or everyDNS.net and create an "A record" that points to your home IP address. You can find that by going to whatismyip.com. If you want to run mail (eventually), you'd create an additional "MX record" that points to your IP.

Then, you need to login to your router and forward port 80 (for a webserver) to your server machine's LAN (internal) IP. i.e. You can find that by opening a console on the server and typing 'ifconfig'.

yes, all of that I have done, as far as setting my web server up. Just havnt done the domain name. So I do have to buy a domain name for it to point to my server?

also if someone can please go to IP address xx.xxx.xxx.xx and let me know if my server is visible from the internet, and not just my local network, thanks.

---

### Post by marcgh on 2009-05-11
Bad news: 
I tried just a minute ago....server is not visible
Sorry mate.

---

### Post by k33bz on 2009-05-11
> **marcgh said:**
> Bad news: 
I tried just a minute ago....server is not visible
Sorry mate.

k, thanks for looking for me. Guess I might of done something wrong with the port forwarding.

When I port forward on my Router, is it my physical IP address of my server I use or is it the IP address that is visible to the internet. Right now I have it set on My server's Physical IP address

just noticed the ip address I posted, sorry was missing some numbers, this is the IP address: xx.xxx.xx.x It works, thanks for those who have checked.

Guess I will have to wait for my domain name to finish registering.

---

### Post by trentscott4 on 2009-05-11
If you have a dynamic IP from your ISP like I do, they'll keep changing your IP every couple months.  ZoneEdit and everyDNS have some neat scripts that you can download to update your DNS record(s) with the current IP automatically.

Something worth checking out ;).

---

### Post by k33bz on 2009-05-11
> **trentscott4 said:**
> If you have a dynamic IP from your ISP like I do, they'll keep changing your IP every couple months.  ZoneEdit and everyDNS have some neat scripts that you can download to update your DNS record(s) with the current IP automatically.

Something worth checking out ;).

I am pretty sure my ISP does that, and I will be going with ZoneEdit as soon as my domain name is done being registered. The place I got it from says it will take 24 hours.

---

### Post by albinootje on 2009-05-12
> **k33bz said:**
> 
When I port forward on my Router, is it my physical IP address of my server I use or is it the IP address that is visible to the internet. Right now I have it set on My server's Physical IP address



Here's an image showing an example of a port forward setup in a router :
[http://ubuntuforums.org/attachment.php?attachmentid=3511&d=1131829373](http://ubuntuforums.org/attachment.php?attachmentid=3511&d=1131829373)
(From this thread : [http://ubuntuforums.org/showthread.php?t=89419](http://ubuntuforums.org/showthread.php?t=89419))

Your 24.x.x.x ip address is your public ip address, and the port forwarding needs to be set to point to port 80 of your LAN ip address, e.g. 192.168.1.2 or 10.0.0.2 etc.

---

### Post by daboroe on 2009-05-14
you can purchase a domain or get a subdomain from no-ip.orgor dyndns.org

thanks

---

### Post by 3L33T on 2009-05-14
> **k33bz said:**
> 
When I port forward on my Router, is it my physical IP address of my server I use or is it the IP address that is visible to the internet. Right now I have it set on My server's Physical IP address


Use the physical LAN ip address of your server.

> 
just noticed the ip address I posted, sorry was missing some numbers, this is the IP address: xx.xxx.xx.x It works, thanks for those who have checked.

Guess I will have to wait for my domain name to finish registering.

What is the IP address again??? I can test it for you by running a bunch of portscans ;)

---

### Post by mbeach on 2009-05-14
by the way, if you need to check your own ports' availability, you may find:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)
of some value.

---

