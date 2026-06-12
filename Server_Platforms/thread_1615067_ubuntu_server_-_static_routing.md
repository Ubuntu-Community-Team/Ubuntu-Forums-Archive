---
title: "ubuntu server - static routing"
date: 2010-11-06
forum: Server Platforms
---

### Post by AuthorizedAgent on 2010-11-06
Hello,

hopefully this isnt a repeat post. i chk'd and saw none.

I am new to the linux community. I am in the process of self teaching my way into it. I have recently set up Ubuntu Server Edition on a spare netbook I had and I installed shorewall, ssh, mysql and a few others.


I have already opened up single port fwd'ing on my WRT610N linksys cisco router. What i am trying to do now is set up static routing to the server. (I understand i need to do this to make server available to the internet?)

ultimately i am going to be using this server/web-server to host my website on for business.

also i will want to play around with attaching external hdd's for shared server storage and learn to run programs on the server and store files to it from offsite.

if anyone can be of help i would appreciate it.
I dont know what info i will need to supply, just ask.

Thanks

---

### Post by Cosma on 2010-11-06
you don't need to configure any routing (other than the default route on the server). just enable portforwarding (DNAT) on your router for the needed ports and make sure that your server has a static ip and doesn't block the ports.

---

### Post by AuthorizedAgent on 2010-11-06
Great! Thank you.

Btw, do i need to setup a static ip for the server or has Ubuntu Server already done this?

Thanks again.

EDIT: also is there a way around using the router's DDNS service? i would like to attach a domain name to the static ip of the server. also does the static ip in question does it also need to be set up with a public ip or the router supplied ip?

---

### Post by Cosma on 2010-11-06
> **AuthorizedAgent said:**
> 
Btw, do i need to setup a static ip for the server or has Ubuntu Server already done this?


during the installation you were able to configure a static ip/dhcp address. check this file to see what you have configured at the moment:
/etc/network/interfaces

you should read the ubuntu serverguide to better understand how to configure networking:
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

---

### Post by Cosma on 2010-11-06
> **AuthorizedAgent said:**
> 
EDIT: also is there a way around using the router's DDNS service? i would like to attach a domain name to the static ip of the server. also does the static ip in question does it also need to be set up with a public ip or the router supplied ip?

first of all, do you get a static ip from your internet provider?

second, i only told you to configure a static ip on the server because if you enable portforwarding, then you have to do this with the ip of the server. that means if the ip of the server changes over time, then your forwarding will stop working.

---

### Post by AuthorizedAgent on 2010-11-06
network interface:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#LAST LINE

EDIT:
obtained hwadd and just did a dhcp reservation for the ip assigned to the server by the router. this should relieve concerns about the static ip config correct?

__________________

ISP does not provide static ip. however i will still need a static ip if i wish to do some kind of ddns.

_______

checking out the guide now. thanks

---

### Post by Cosma on 2010-11-06
> 
auto eth0
 iface eth0 inet dhcp
that means you use dhcp to get a dynamic ip from your router (check the link that i posted to see how you have to configure it)

> **AuthorizedAgent said:**
> 
ISP does not provide static ip. however i will still need a static ip if i wish to do some kind of ddns.


you don't need a static ip to use ddns (dynamic dns) because thats the whole reason why this service was created. you have to sign up at some ddns provider to get a account and a dns name. after that you use this account to configure the ddns at your router.

it will look like this:

internet -> "your-ddns-name" -> [WRT610N with dynamic ip] --forwarding--> [your server with static internal ip]

if you want to buy a real dns name then you can do two things to make this work.

[LIST=1]
[*]get a static ip and point the dns name at this ip
[*]try to find a dns provider that can forward your dns name to a other dns name like this: [real dns name] -> [dyndns name] -> [your router] -> [your server]
[/LIST]

---

### Post by Cosma on 2010-11-06
> **AuthorizedAgent said:**
> 
EDIT:
obtained hwadd and just did a dhcp reservation for the ip assigned to the server by the router. this should relieve concerns about the static ip config correct?


this will work but it's better to configure a static ip at the server

---

### Post by AuthorizedAgent on 2010-11-06
ok. thanks. i am attempting to do the static ip. the server guide wasnt instructive enough so googling now.

thanks for the help

---

