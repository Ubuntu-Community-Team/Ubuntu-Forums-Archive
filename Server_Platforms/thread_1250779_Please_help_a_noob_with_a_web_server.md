---
title: "Please help a noob with a web server"
date: 2009-08-26
forum: Server Platforms
---

### Post by Insomn1ar on 2009-08-26
Hello everyone,
 
Since I was around 13-14 I have always been fascinated with the web. I used to rent a small hosting package and had a great deal of fun installing Joomla/Wordpress and then messing around in them. I had a friend a few years old who had a server running in his room. I always wanted to do something similar but never felt I had the knowledge. I recently built myself a awesome new machine and I have a semi-decent old computer I have installed ubuntu server on.
 
This is my first time ever using Linux/Ubuntu so excuse me for being a bit of a noob here. But I am really wanting to learn :)
 
I have apache2,php5 and mysql installed on the server. I am installing everything through SSH (which btw is pretty cool, coming from being so used to a GUI on a computer it is pretty fascinating). I have installed Wordpress in my /var/www directory and I set it up. However I have gotta be doing some wrong here because when I install it using a computer in my network (I can only access it through my LAN IP 192.168.x.x) I cannot reach it using my IP as it just brings me to my routers page. After installing wordpress it all looks great on the local network. All the links have 192.168.x.x in the links and when I browse to the page on my phone which isn't in the network (I have also tested this on my brother computer at his house) and all I get is a page with just the wordpress text, no css or images. I can find these by typing out my IP 88.105.xx.xx and browsing directly where it would be in my local network so I know the files are there, just that the site is configured for that local IP.
 
I thought I would reinstall it, this time on a computer outside of the network the server was in. This time it works fine on any of the computers outside the network. However when I browse to that page in my local network (using 192.168.x.x address) I get the same problem I was having before, this time in reverse (I cannot see these outside of network css files/images unless browsing directly to them using an other IP infront of it.
 
I think it may be my router as I saw nothing in the router on Static LAN ips and only DHCP. Maybe something with DNS. I dunno ..really confused me here and spent the last 9 hours trying to google solutions/troubleshooting.
 
Thanks for any help guys/gals, much appreciated :KS
 
Sam.

---

### Post by terazen on 2009-08-27
I think your problem is with what url the server expects to receive requests on.  Right now it's using it's own ip address for the links.

Maybe this helps?
[http://codex.wordpress.org/Changing_The_Site_URL](http://codex.wordpress.org/Changing_The_Site_URL)

---

### Post by cian1500ww on 2009-08-27
Do you have a static ip address setup for the machine and port 80 forwarded to it ?

---

### Post by Insomn1ar on 2009-08-27
> **cian1500ww said:**
> Do you have a static ip address setup for the machine and port 80 forwarded to it ?
 
My router makes no mention of it, thats my problem I think. I was considering purchasing a new one today as someone wants to buy me a present for doing well at my GCSEs(hehe) :) I will try terazens solution ina bit. If that doesn't solve it I will stick in an order for a new router.
 
Thanks :)
 
more input appreciated.
 
EDIT: Can someone tell me which router they use and give me some links so I can get a good idea of what to buy.

---

### Post by cian1500ww on 2009-08-27
I use linksys WAG325N but any Linksys router would have the necessary specs. WHat kind of a router do you have ? Oh and congratulations on getting your GCSE's :)

---

### Post by Insomn1ar on 2009-08-27
Thank you very much mate, I was looking at a few routers on [http://ebuyer.co.uk](http://ebuyer.co.uk) and they seem to offer Static IP routing. Just got off the phone with my ISP as I have upgraded to business broadband - so get a static IP which will be great also :P. Should start working soon.
 
I have just installed joomla to check and see if it was a problem relating at all to wordpress. It would seem that Joomla works fine when I browse to it outside my local network. 
 
Hmm ...

---

