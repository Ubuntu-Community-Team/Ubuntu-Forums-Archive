---
title: "need help in a simple server"
date: 2009-11-12
forum: Server Platforms
---

### Post by MrLOVER on 2009-11-12
hi friends, i am goin to start a small business of internet cable provider in my town. i want to ask you a problem that no one else answered me yet. 
im a new user of linux, i don't know anything about it yet, just i installed ubuntu desktop 9.10 and successfully configured its nat services by reading a guide on this forum. but i want to install server adition of ubuntu and that has no graphical user interface, so i will have to do everything by typing commands, and i don't know all commands :( , what i want to do is...

i want to make a simple NAT enabled server to share internet to my users,
i don't want to enable dhcp.
i want to control bandwidth usage to each user as per their package.

so most important thing is that bandwidth limits, as i know i can limit bandwidth to a specific ip address, but what if user change his ip address ?
so next thing i think is limiting bandwidth on specific mac addresses, but i have heared that mac addresses can also be changed by hacking softwares,
so please recommend me how can i make this server possible with all above conditions. i will be really thankfull to you if you solve my problem.
also tell me all procedure to make this server step by step.

thanks

addition: you can also guide me if my way of user management is wrong, if there is other way for all client managements please guide me. i need your help as i can't do anything at my own in linux. thanks

---

### Post by mrsteveman1 on 2009-11-12
By cable do you mean ethernet? Or like, cable television?

If you're going to be setting up a commercial cable internet service you're already going to be deal with fairly sophisticated hardware and you might want to look into equipment for managing the users rather than looking to Ubuntu.

Either way it's probably best to have a sort of appliance to manage a network like this rather than trying to implement and manage it all while you're still learning linux. I'm probably not much help there as i'm not aware of any Linux distributions specifically targeted at such a situation (managing access networks, to say nothing of commercial payment integration and reporting).

So yea, explain a bit more about what you're doing, are you accepting payment for this from users? building out a physical network yourself?

---

### Post by SteveHillier on 2009-11-12
I have two web servers configured.
The first is Fedora with Plesk as a control panel.  Plesk is a paid for product.  Although they say it is supported on Ubuntu I could not get that installation to work.  Plesk is also very twitchy about which version of Fedora you try to install on.
My second server runs OpenPanel on Ubuntu 8.04 LTS server package.  The 8.04 install is straight forward.  Look at the OpenPanel website for download and install details.  A couple of simple command line entries and it does it for itself (I used the script that describes itself as dating your wife and eating your children).
What ever you are doing I would suggest you download and install the latest LTS server edition.  The server has to be robust and these releases are designed for that.
Good luck brave fellow.  Talk about jumping in the deep end!!

---

### Post by MrLOVER on 2009-11-12
> **mrsteveman1 said:**
> By cable do you mean ethernet? Or like, cable television?

If you're going to be setting up a commercial cable internet service you're already going to be deal with fairly sophisticated hardware and you might want to look into equipment for managing the users rather than looking to Ubuntu.

Either way it's probably best to have a sort of appliance to manage a network like this rather than trying to implement and manage it all while you're still learning linux. I'm probably not much help there as i'm not aware of any Linux distributions specifically targeted at such a situation (managing access networks, to say nothing of commercial payment integration and reporting).

So yea, explain a bit more about what you're doing, are you accepting payment for this from users? building out a physical network yourself?

im already having a small business in my town of television cable. and now adays im taking classes of CCNA and also thinking to take some classes of linux in my college.
i have a good learning mind and once i saw Linux and its features i want to learn it too. i liked the way Linux deal with different things. and ofcorse i like it because its open source and free to use.
by cable i mean internet cable through Ethernet. i have a dual core 2.8 Ghz with 4gb ram and 500gb hard drive, 3 Ethernet cards out of two will provide me internet from 2 different ISPs and 1 will share internet to my local network. i want to use it as a server and want to install Linux on it. i have tried windows servers but i can't spend that much money on buying software. i therefore said im going to start a small level business with what i have and Linux is free and i heared that we can do anything in Linux with commands. anything mean all kind of client management. please guide me the best way you can to set up a secure server with all kind of client management like bandwidth control etc,
i don't know if there is any restrictions on ubuntu usage as a server in a small business like i do? if there is any i would respect the rules and regulations.

thanks

---

### Post by clevertomato on 2009-11-12
Not sure if it would meet all your needs, but pfSense comes to mind for at least some, if not all, of what you want to do. Have you looked at its features? I put it on an old PII-266 Mhz with 256 MB RAM and threw it in the closet as my home router and firewall, but its capabilities are VAST. Google pfSense if you're interested.

---

### Post by scottuss on 2009-11-13
With the greatest of respect, a simple server as you say, is not what you require to run an ISP.

Even if you only have a handful of customers, actually running and managing something like that would be far more complex that I perhaps think you realise. I'm not saying don't do it, you absolutely should follow what you want to do, but it probably helps to either 1) have the knowledge and experience to undertake the task or 2) have somebody that has the knowledge and experience to work alongside you.

I'm sure the Ubuntu forums will help you out a lot with server config etc, but running an ISP is a big task that needs more guidance than some forum posts. You don't want angry customers that can't get onto the Internet or have slow / interrupted access because of a badly configured server.

That said, good luck!

---

### Post by MrLOVER on 2009-11-13
> **scottuss said:**
> With the greatest of respect, a simple server as you say, is not what you require to run an ISP.

Even if you only have a handful of customers, actually running and managing something like that would be far more complex that I perhaps think you realise. I'm not saying don't do it, you absolutely should follow what you want to do, but it probably helps to either 1) have the knowledge and experience to undertake the task or 2) have somebody that has the knowledge and experience to work alongside you.

I'm sure the Ubuntu forums will help you out a lot with server config etc, but running an ISP is a big task that needs more guidance than some forum posts. You don't want angry customers that can't get onto the Internet or have slow / interrupted access because of a badly configured server.

That said, good luck!

i understand what you said and i will let some experienced person make my server, but even if this happen i want to learn Linux, as i have a chance and a networking environment to test everything i want. i would apreciate if someone just start telling me what i need to do first in my server and then explain how to do that. i would love to learn it step by step.

so for now i want someone to tell me what is the first step to make a server like i want?
[B][COLOR=DarkGreen]
1.  i mean tell me how to enable a simple NAT service in ubuntu 9.10 server with the following conditions,

i have 3 Ethernet cards, [COLOR=DarkRed](Eth0[/COLOR] and [COLOR=DarkRed]Eth1)[/COLOR] will provide me internet from two different ISPs in my server and [COLOR=DarkRed]Eth2[/COLOR] will be used to share internet to my clients. and [COLOR=DarkRed]Eth2[/COLOR] should use both of my [COLOR=DarkRed]Eth0[/COLOR] and [COLOR=DarkRed]Eth1[/COLOR] to balance the load of traffic.

2. how can i enable DHCP.

3. how can i give priority to a specific ip over other ips?[/COLOR][/B]

thanks and i hope this is the best way to learn.
Regards,,,
 Mr.LOVER

---

### Post by sloggerkhan on 2009-11-13
you need to use iptables routing, which can be highly complicated.
I suggest that to simplify, maybe you try a frontend, firhol would have worked, but I don't know if they're still alive. In any case, linux firewall projects will let you couple your network interfaces the way you want.

I have no ideas on bandwidth limiting, though.

---

### Post by scottuss on 2009-11-15
Bandwidth limiting can be done with trickle or wondershaper

---

### Post by Lars Noodén on 2009-11-16
> **MrLOVER said:**
> 
so for now i want someone to tell me what is the first step to make a server like i want?
[B][COLOR=DarkGreen]
1.  i mean tell me how to enable a simple NAT service in ubuntu 9.10 server with the following conditions,

i have 3 Ethernet cards, [COLOR=DarkRed](Eth0[/COLOR] and [COLOR=DarkRed]Eth1)[/COLOR] will provide me internet from two different ISPs in my server and [COLOR=DarkRed]Eth2[/COLOR] will be used to share internet to my clients. and [COLOR=DarkRed]Eth2[/COLOR] should use both of my [COLOR=DarkRed]Eth0[/COLOR] and [COLOR=DarkRed]Eth1[/COLOR] to balance the load of traffic.

2. how can i enable DHCP.

3. how can i give priority to a specific ip over other ips?[/COLOR][/B]



1.  Learn IPTables
[http://www.frozentux.net/documents/iptables-tutorial/](http://www.frozentux.net/documents/iptables-tutorial/)

2.  Use dnsmasq

3.  Master IPTables

---

