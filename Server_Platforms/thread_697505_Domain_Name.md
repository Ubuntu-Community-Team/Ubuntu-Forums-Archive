---
title: "Domain Name"
date: 2008-02-15
forum: Server Platforms
---

### Post by Holmes89 on 2008-02-15
I have a domain name I purchased from GoDaddy for the webpage I was planning on hosting. I am now using a static IP from DynDns.org. Is there an easy way for me to link my webserver and my domain name and am I doing the right thing going through DynDns.org? or is there a better website that can offer me the same thing for free? (I'm currently using a trial)

---

### Post by crouton on 2008-02-15
I think all you need to do is put your domain name in your DynDNS account and tell it to forward all requests to your webserver's IP.  It sounds like you have a paying account with DynDNS so just hit up their website for how to do this; their free service (last I checked) was restricted to giving you a <hostname.dyndns.org> redirection to a specified IP.

---

### Post by Holmes89 on 2008-02-15
No I don't have a paid account only a free account. So what do I do, and is there a better service?

---

### Post by sterilegenie on 2008-02-15
Log into your godaddy account, go to manage domains, select the domain you want to change and change the ip address to the one that points to your server.

---

### Post by rickyjones on 2008-02-15
> **Holmes89 said:**
> I have a domain name I purchased from GoDaddy for the webpage I was planning on hosting. I am now using a static IP from DynDns.org. Is there an easy way for me to link my webserver and my domain name and am I doing the right thing going through DynDns.org? or is there a better website that can offer me the same thing for free? (I'm currently using a trial)

Alright, first we need to define some goals and what we have at our disposal. 

Goal: When someone types in "www.domain.com" you want this to go to your server with an IP address of "xxx.xxx.xxx.xxx"

That was the goal. What we have at our disposal is:

1) Domain name hosting: Godaddy.com has the domain name "domain.com" and the records are being hosted with Godaddy.
2) We have our IP address: "xxx.xxx.xxx.xxx" is YOUR PUBLIC IP Address, correct? 
2) a) Is the above IP address STATIC or DYNAMIC?

Now we have the necessary information.

If you have a static IP: From Godaddy.com you will edit your DNS records for your domain. Create the "www" record and point it to your IP of "xxx.xxx.xxx.xxx"

If you have a Dynamic IP then this will be a bit more complicated. 
1) Using a service like DynDNS.org (I use them too) create a Dynamic Host Service. Example: myhome.ath.cx.
2) On Godaddy, create a CNAME record of "www" - point it to your DynDNS name (myhome.ath.cx).

It should be as simple as that. I hope this helps get you in the correct direction!

-Richard

---

### Post by Holmes89 on 2008-02-15
Is that DynDns service free? I'll try the rest of it, thanks for all of the help

---

### Post by rickyjones on 2008-02-16
> **Holmes89 said:**
> Is that DynDns service free? I'll try the rest of it, thanks for all of the help

I've been using that dynamic host service for free for many years.

---

### Post by Holmes89 on 2008-02-16
Do I have to do something if I have a special port open? Like to connect to my webserver is xxxxx.dyndns.org:xxxx how do I route it within the domain name?

---

### Post by canh_nguyen on 2008-02-16
> **Holmes89 said:**
> Do I have to do something if I have a special port open?

Login your modem, go to Advance Setup ->NAT -> Virtual Server to forward request. Ex:




Rule--- Application-------Protocol---Start Port---End Port--- Local IP Address
1------- HTTP_Server---- ALL----------- 80 ------- 80 --------- 192.168.1.105
2------- POP3 ------------- ALL-----------110------- 110-------- 192.168.1.105
3------- SMTP--------------ALL----------- 25--------- 25--------- 192.168.1.105
4------- VNC--------------- ALL-----------5900------5900--------192.168.1.105
5------- HTTP_Server----- ALL-----------10000---10000--------192.168.1.105

---

