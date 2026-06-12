---
title: "help me to automatically change my ip address frequently to secure my connection"
date: 2012-03-18
forum: Security
---

### Post by tiglin1989 on 2012-03-18
hello to all netty persons,
[U]help me to automatically change my ip address frequently to secure my connection

[/U]hello , since a long time i am facing a problem ,while _chattin_g, to not to use it properly , due to every time intruders enter in the system and try to not to run the system easily, i am little bit bored with these situations , so now try_ to change my ip address automatically & frequently to secure my connection and still enjoy web chatting and surfing without any fear of lost my data and system configuration_. 
though with help of ```
ifconfig
``` , i _change my ip address but the connection stop to work_ and i can't use it properly.
so please help with your valuable suggestions to fight with these type of problems easily and_ hide my ip_ _address_ and _entire system details_ enough from others.
thanking you all.

---

### Post by dmouck on 2012-03-20
This seems like a rather odd request, to constantly change your IP address to people can't access your system. I think a better solution would be to secure your system. 
Please tell us some information about your system, such as the version of Ubuntu that you are using, and exactly what is happening.

---

### Post by mauleshjani on 2012-03-21
> **dmouck said:**
> This seems like a rather odd request, to constantly change your IP address to people can't access your system. I think a better solution would be to secure your system. 
Please tell us some information about your system, such as the version of Ubuntu that you are using, and exactly what is happening.

yes sir,
i'm using ubuntu 11.10
my all configurations r ok... wlan0 ok, eth0 ok, but my problem is to ---i want to make myself invisible or  hide myself from others .... show me the way to hide my ip address and my system and still network running and my work also... to protect me from other spying me....
thanks a lot

---

### Post by SeijiSensei on 2012-03-22
Don't run software that exposes yourself.  There's really no other answer to this question.

---

### Post by haqking on 2012-03-22
using ifconfig will show your local machine IP address which is likely using NAT behind a router from your ISP.

Your internet presence is through your ISP IP address allocated to you which is either static or dynamic, how often that changes is upto your ISP.

use a proxy such [www.hidemyass.com](www.hidemyass.com) or configure TOR and Polipo/Privoxy locally on your machine for some anonymizing

Cheers

---

### Post by tiglin1989 on 2012-03-22
_hide ip address and change it frequently to protect system while networking_

hello to all linux users,
please show me the way to --_help me to automatically change my ip address frequently to secure my connection_ from other spying me,

i try a lot _ to change my ip address automatically & frequently to secure  my connection and still enjoy web chatting and surfing without any fear  of losing my data and system configuration_. 

though with help of command ===>   ifconfig
, i _change my ip address but the connection stop to work_ and i can't use it properly,

so please show me the proper way to hide my system details from others : and after applying changes i must be able to use my network very easily,

thanking you all,

---

### Post by howefield on 2012-03-22
Threads merged and excessive bumps removed to "tidy" up thread and make it easier to read.

---

### Post by Bucky Ball on 2012-03-22
Unless you are using a static IP address you will have a different IP address everytime you boot the machine. 

Who do you imagine is spying on you???

You change your IP address via the Network Manager (right click and 'Edit Connections'). Your main problem doing that is the router is probably trying to serve you one via DHCP so when you boot the machine (or change the address) you're trying to force the router to use the IP you've set and the router is attempting to serve you an IP. Clang!

You probably need to do some tweaking at both ends ...

---

### Post by tiglin1989 on 2012-03-22
> **haqking said:**
> using ifconfig will show your local machine IP address which is likely using NAT behind a router from your ISP.

Your internet presence is through your ISP IP address allocated to you which is either static or dynamic, how often that changes is upto your ISP.

use a proxy such [www.hidemyass.com]("http://www.hidemyass.com") or configure TOR and Polipo/Privoxy locally on your machine for some anonymizing

Cheers

many many thanks sir, 
i m using ubuntu 11.10 , installed TOR but it is not started , pl show me a _simple method_ through_ terminal command_ to change my _SYSTEM IP / ISP PROVIDED IP_ automatically , so no one can spy me through _ip address_ and i become invisible to them.

i'm a new one but still hard working to follow you.
thanking you.

---

### Post by haqking on 2012-03-22
> **tiglin1989 said:**
> many many thanks sir, 
i m using ubuntu 11.10 , installed TOR but it is not started , pl show me a _simple method_ through_ terminal command_ to change my _SYSTEM IP / ISP PROVIDED IP_ automatically , so no one can spy me through _ip address_ and i become invisible to them.

i'm a new one but still hard working to follow you.
thanking you.

your ISP IP is assigned to you from them.

You can hide it and your presence online to some degree using a proxy as i mentioned and already provided links to as an example.

to configure tor see here [http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)

you will never be completely anonymous or invisible.

for anonymous browsing just download the browser tor bundle, or follow the guide above to configure it locally so you can use it with IRC and such.

nothing you do online will be 100% invisible to a determined individual.

Cheers

---

### Post by tiglin1989 on 2012-03-22
thanking you sir,

---

### Post by mauleshjani on 2012-03-24
pl show the easiest way ....

---

### Post by haqking on 2012-03-24
> **mauleshjani said:**
> pl show the easiest way ....

read the posts and links above

---

### Post by mauleshjani on 2012-04-29
again i would like to request all ...to show me the easiest way to become invisible....
thanking you all

---

### Post by JKyleOKC on 2012-04-29
> **mauleshjani said:**
> again i would like to request all ...to show me the easiest way to become invisible....
thanking you allThe only way to become completely invisible is to unplug the cable (or turn off the wireless) that connects you to the net, or even simpler, turn off the computer and dump it into the trash bin.

To learn why this is so, install the "wireshark" package and run it for a few minutes. This will show you all of the (thousands of) transactions that take place every minute, behind the scenes. If you could somehow change your IP that rapidly, you would still see attempts at communication but you would no longer be able to browse; every request for data that you sent would get a reply but it would be sent to your old address, not your new one.

---

### Post by CharlesA on 2012-04-29
> **JKyleOKC said:**
> The only way to become completely invisible is to unplug the cable (or turn off the wireless) that connects you to the net, or even simpler, turn off the computer and dump it into the trash bin.

To learn why this is so, install the "wireshark" package and run it for a few minutes. This will show you all of the (thousands of) transactions that take place every minute, behind the scenes. If you could somehow change your IP that rapidly, you would still see attempts at communication but you would no longer be able to browse; every request for data that you sent would get a reply but it would be sent to your old address, not your new one.

This. You can use TOR, but you still won't be invisible on the internet - there will always be traces left behind.

---

