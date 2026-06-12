---
title: "Help with ISPconfig"
date: 2008-08-29
forum: Server Platforms
---

### Post by serverCrazy on 2008-08-29
hi guys, i have recently have installed ISPconfig on a Ubuntu 8.04 server. However, i could not understand few things (configuration bits).

on management -> server -> settings:

the ip address: is the Router ip, lets say: 192.168.0.1 or my server which lets say: 192.168.0.7.

the ip list: which ip i have to list.

when you click on a web site: it appears a list of settings, so which ip do i have to put for this website.



when i buy a new domain and want to use on this site on my server, so i guess that i have to point to my ip address and than the ispconfig do the job of managing the domain names.

what about if i dont have a domain, so i guess that i can use a subdomain, like [http://user.mydomain.com/](http://user.mydomain.com/) or [http://mydomain.com/user/](http://mydomain.com/user/). How to do that?

if you guys could help qwith that thanks, if you guys want to have a look inside the system, let me know when and i will grant the pass for that period of time.

thanks for the coorperation and help

---

### Post by windependence on 2008-08-30
[http://www.ispconfig.org/downloads/manual_en/manual_kunde_en_src.htm](http://www.ispconfig.org/downloads/manual_en/manual_kunde_en_src.htm)

-Tim

---

### Post by serverCrazy on 2008-08-30
sorry, windependence, but thats documentation does not answer my questions, because it is too general. i had read that before, however i could not get started, so i what i did was, if someone want they can have a look at the system as administrator and see if it is right or not.

what happen is that, the ISPconfig is up and running, i also have a website there, to test it, but when i point the domain to my ip address, it goes to my server on port 80. I am not sure about it.

I need some help on that,

thanks for you time and willing

---

### Post by windependence on 2008-08-31
Are you only hosting one site or just a few (less than 10)? If so, it would probably be easier to skip ISPconfig and do your configs manually. Control panels have some quirky way of handling things on the backend sometimes. I have supported Plesk, but I am not too familiar with ISPconfig. I can try to help you though and so we need to figure out if you actually NEED a control panel.

Also, if you are having trouble understanding the oprions in the control panel, you should probably get yourself a good book on web hosting and how that all works so you can understand what you are doing. I am not saying this to be rude, but it's like jumping in the pool without knowing how to swim.

-Tim

---

### Post by serverCrazy on 2008-08-31
i agree with you, windepence, however, you only learn how to swim when you get inside a pool with narrow water. 

My idea is to start a web design business (I already do that), however i would like to host these web page myself instead of paying someone else to do that, in that way i could earn more money and have more control over the business.

How many web sites it will be, this is a diferent matter.

it is Plesk any good and easy to install on a ubuntu 8.04 server, i dont have any problem to switch.

do you recomend any good book on web hosting, because i only find books that just talk about the tool to use it, but dont explain how to link all together in order to work.

if you can help me would be great, if you have time and willing.

anyway thanks for your reply, i see that you are really good.

---

### Post by windependence on 2008-08-31
Well for books, I have "Apache, The Definitive Guide" from O'Reily and that's pretty good. There are also lots of good tutorials on the web.

You should be aware though before you jump in, that if you are going to do this right, you will need a few things:

A redundant web server - that is two of everyting
Redundant UPS
Managed routers and switches (recommended)
A good hardware firewall
Good backup strategy
A "real" IP address - dynamic will work but not for a professional business.
Sufficient bandwidth (proobably a MINIMUM of 1.5mbs up and down) Upspeed is most important unlike the speeds most ISPs advertise which are down.
A clean, cool environment for your servers.
Sufficient power
Data connections from two different providers is highly recommended.

People will probably come here and say you don't need this or that I have listed but the reality of it is, if you are going to do this professionally for your customers, they want their site to up ALL the time, no excuses. Think what would happen if your server is down and you have just 20 customers on it. do you suppose they will be calling you and be a little upset? If you have one single point of failure on your network, you are doomed.

Plesk is commercial and is not cheap. It's a good product though. You could use ISPconfig. Personally, I don't us any of them because they are all big security risks.

Here is a tutorial to get you started;

[http://www.w3schools.com/hosting/default.asp](http://www.w3schools.com/hosting/default.asp)

-Tim

---

