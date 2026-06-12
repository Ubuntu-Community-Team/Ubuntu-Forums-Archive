---
title: "Setting up a router"
date: 2005-12-17
forum: The Cafe
---

### Post by xequence on 2005-12-17
I have a linksys router, and I want to hook up two computers to the internet. (In about a month it will be 3).

Is this really easy? What would I need?

As far as I know now, it would be like this:

(picture coming in a minute)

---

### Post by Ride Jib on 2005-12-17
[QUOTE=xequence]I have a linksys router, and I want to hook up two computers to the internet. (In about a month it will be 3).

Is this really easy? What would I need?

As far as I know now, it would be like this:

(picture coming in a minute)[/QUOTE]

Yeah, that's all there is to it. It's very simple. Each computer has a cat5 (or 5e or 6 depending on your router) ethernet jack. That gets plugged into the router, and the rest is simple steps to follow that comes with your router's intruction manual. 

Adding more computers later on is as simple as plugging them into the router (if you use dhcp).

---

### Post by xequence on 2005-12-17
Thats great =D I might be able to get it set up in a couple days then.

Are there any complications with routers and bittorent?

Its the main reason for the router - to have a certain computer hooked up to the internet all the time, for constant uploading or downloading.

---

### Post by ember on 2005-12-17
Some routers have problems with the many connections filesharing like bittorrent opens, but as far as I know, Linksys is not among them.

---

### Post by prizrak on 2005-12-17
[QUOTE=xequence]Thats great =D I might be able to get it set up in a couple days then.

Are there any complications with routers and bittorent?

Its the main reason for the router - to have a certain computer hooked up to the internet all the time, for constant uploading or downloading.[/QUOTE]
You are going to have to go into the router setup page, and open up ports 6881 - 6889. You might have to forward them rather than just open. That means is that you will assign an IP address next to the ports that are gonna be open.

---

### Post by xequence on 2005-12-17
[QUOTE=prizrak]You are going to have to go into the router setup page, and open up ports 6881 - 6889. You might have to forward them rather than just open. That means is that you will assign an IP address next to the ports that are gonna be open.[/QUOTE]

How would I get to the router set up page? As far as I know, the router didnt come with any software. Only some FAQ on a CD, though there might be something there somewhere...

Is there a guide to do that? Looks a little hard... And I dont use 6881 for bittorent. I use 7000 something right now, and I switch often.

Also, I can get a wireless router for 10$ at futureshop. What extra stuff would I need to get it working? Like would I need a wireless network card thingy?

---

### Post by Lambert on 2005-12-17
To enter router configuration you would enter the ip addrees of the router in  to a browser. You can try this as I believe linksys uses this.

[http://192.168.1.1]("http://102.168.1.1")

You might get a login in screen so you'll have to find what the user/password is. It may be in the faq section on the disk.

Linksys has user guides on their site for their routers in pdf format if you need more help.

For wireless you would need to just plug the access point into the router and a card on the same protocol A B or G. some cards support both A & G

On the access point you will have to enter a configuration page the same way to set it up, this is usually done via a wired connection first to the ap. Then set up the card and configure network settings. Wireless in linux can be tricky. Do your homework on what card you buy first as the time spent there will be wel worth your time.

---

### Post by xequence on 2005-12-17
Ok, now I know how to do it... Just have to find my router now.

---

### Post by prizrak on 2005-12-18
To log into the Linksys router for the first time, type in "admin" as your password while leaving the username blank. Lucky for you I got a Linksys meself so you can get mucho help ;) 
If you switch ports open consider setting your downloading machine (if that's the only one you will use for dl) as a DMZ host it will open up all router ports for it, all you have to do for that is get to the page where you set it up and enter the last octet of the IP of the machine you want DMZ'ed. Unless the computer is never turned off you will be better off by manually assigning the IP address so that it doesn't change on you. (AFAIK Linksys doesn't let you make DHCP assignments permanent tho that mighta changed on the newer routers). Goodluck remember help is just a forum post away :)

---

### Post by WildTangent on 2005-12-18
[QUOTE=prizrak]To log into the Linksys router for the first time, type in "admin" as your password while leaving the username blank. Lucky for you I got a Linksys meself so you can get mucho help ;) 
If you switch ports open consider setting your downloading machine (if that's the only one you will use for dl) as a DMZ host it will open up all router ports for it, all you have to do for that is get to the page where you set it up and enter the last octet of the IP of the machine you want DMZ'ed. Unless the computer is never turned off you will be better off by manually assigning the IP address so that it doesn't change on you. (AFAIK Linksys doesn't let you make DHCP assignments permanent tho that mighta changed on the newer routers). Goodluck remember help is just a forum post away :)[/QUOTE]
WOAH!!! Setting it up in the DMZ makes it completely open to everything. I know linux is much more secure than Windows, but you shouldn't take any chances.

-Wild

---

