---
title: "whats the point of this &quot;router&quot;"
date: 2006-04-06
forum: The Cafe
---

### Post by evilgold on 2006-04-06
[http://www.newegg.com/Product/Product.asp?Item=N82E16833124151](http://www.newegg.com/Product/Product.asp?Item=N82E16833124151)

My friend baught this by mistake, because he needed a router... now to me, a router means more then one lan port, but apparently this is not the case. This thing just has one lan port and one wan. It cost $40 which is more then a lot of four port (and probably some wireless) routers. 

Also the description says it can connect all of the pcs on a network to the internet with one ip... however i dont see how this is possible without the addition of  more then one port, or additional hardware.

Seeing as its on newegg and by linksys, I know there is a good reason for this, and its $40 price tag..I'm hopeing someone here could point it out to me.

---

### Post by Virogenesis on 2006-04-06
well with router you'll need a switch like you say there isn't much point in them unless you have like a 16port switch you wish to use.

Now it can provide 1 ip to the ninternet by assigning the ips to internal ones.
It does this by using a internal dchp server/client usually these things have linux installed on them I use to have a dlink which t you could telnet to. 
Bloody useless thing died on me

---

### Post by stoeptegel on 2006-04-07
I don't see a reason why it should have a high price tag, but that could be me though. I think linksys just is a little bit more expensive when it comes to routers.

I think you've confused routers and switches. 
A router is nothing more than a device that can assign IP addresses to the computers in your network. (doing this as a local gateway for the computers) 
A switch is the hardware part that separates the traffic on different cables in a efficient way. 
The routers with built-in switches are very often just called routers, so that's probably where the problem comes from. 

If you want your LAN on 1000mbit you don't need a built-in switch anyway since the normal priced routers with built-in switched all are 100mbit, which is slow compared to 1000mbit. So if you use it like this the router isn't useless.

---

### Post by htinn on 2006-04-07
I think the "point" behind a router like that is it gives the ISP something they can give to their customers. :)

---

### Post by woedend on 2006-04-07
lol...i didnt think anyone actually bought those.  As to why?  Well, for one,  external firewall....shoulda got a befsr41 though, never know when you might need 4 ports.

---

### Post by briancurtin on 2006-04-07
[QUOTE=evilgold][http://www.newegg.com/Product/Product.asp?Item=N82E16833124151](http://www.newegg.com/Product/Product.asp?Item=N82E16833124151)

My friend baught this by mistake, because he needed a router... now to me, a router means more then one lan port, but apparently this is not the case. This thing just has one lan port and one wan.[/QUOTE]
...and it is clearly specified in the title that it is a one-port deal. if you or your friend bought this expecting more than one port, then it is completely your fault.

---

### Post by evilgold on 2006-04-07
Thanks for clearing this up for me a bit, i now understand why its a router, and what i normally call a router is actually a router+switch. 

So i guess it is rather pointless, buying a seperate switch would cost even more money.

---

### Post by stoeptegel on 2006-04-07
[QUOTE=evilgold]
So i guess it is rather pointless, buying a seperate switch would cost even more money.[/QUOTE]

Yes, but like i said the advantage of this is that you can buy a 1000mbit switch instead. (though you would still need 1000mbit ethernet cards to get full use of it)
A good bang for the buck 1000mbit switch for home use is a asus gigaX 1105 or 1108.

---

### Post by vayu on 2006-04-07
[QUOTE=evilgold]
Seeing as its on newegg and by linksys, I know there is a good reason for this, and its $40 price tag..I'm hopeing someone here could point it out to me.[/QUOTE]


I bought this exact router because the store had a choice between this and the same thing with 4 ports that was about $20 more.  I needed 8 ports.  So it was better for me to apply the $20 towards the switch that gave me 16 ports.

---

### Post by Virogenesis on 2006-04-07
[QUOTE=stoeptegel]Yes, but like i said the advantage of this is that you can buy a 1000mbit switch instead. (though you would still need 1000mbit ethernet cards to get full use of it)
A good bang for the buck 1000mbit switch for home use is a asus gigaX 1105 or 1108.[/QUOTE]
Incorrect thats only a 10/100mb router so  you'll face a bottle neck with this but I get what you mean

---

### Post by Cyril on 2006-04-07
I believe devices connected to the switch can still communicate with one another with 1000mbit since they do not have to communicate through the router.

---

### Post by stoeptegel on 2006-04-07
[QUOTE=Cyril]I believe devices connected to the switch can still communicate with one another with 1000mbit since they do not have to communicate through the router.[/QUOTE]

Correct. (when on the same subnet)
All LAN-LAN traffic won't make it to the router, it'll stay on the LAN side of the switch so to speak and therefore will be 1000mbit. (if the rest of the LAN network supports it though)

---

### Post by prizrak on 2006-04-07
[QUOTE=stoeptegel]I don't see a reason why it should have a high price tag, but that could be me though. I think linksys just is a little bit more expensive when it comes to routers.

I think you've confused routers and switches. 
A router is nothing more than a device that can assign IP addresses to the computers in your network. (doing this as a local gateway for the computers) 
A switch is the hardware part that separates the traffic on different cables in a efficient way. 
The routers with built-in switches are very often just called routers, so that's probably where the problem comes from. 

If you want your LAN on 1000mbit you don't need a built-in switch anyway since the normal priced routers with built-in switched all are 100mbit, which is slow compared to 1000mbit. So if you use it like this the router isn't useless.[/QUOTE]
A router is a device that routes network traffic through different segments on the network. It does not serve any IP's. IP serving is done by the use of a DHCP server that CAN be built into the router same way a switch can be.

---

### Post by stoeptegel on 2006-04-07
[QUOTE=prizrak]A router is a device that routes network traffic through different segments on the network. It does not serve any IP's. IP serving is done by the use of a DHCP server that CAN be built into the router same way a switch can be.[/QUOTE]

The first i know, i let that away for making it easier to understand. (now the TS doesn't know the difference between switch and router anymore, lol)
I didn't knew a switch can do DHCP though.

---

### Post by prizrak on 2006-04-07
[QUOTE=stoeptegel]The first i know, i let that away for making it easier to understand. (now the TS doesn't know the difference between switch and router anymore, lol)
I didn't knew a switch can do DHCP though.[/QUOTE]
I personally never encountered a DHCP server running on a switch but it's not out of the question. Now if you really wanna confuse someone tell them about a brouter ;)

---

### Post by mips on 2006-04-07
[QUOTE=prizrak]I personally never encountered a DHCP server running on a switch but it's not out of the question. Now if you really wanna confuse someone tell them about a brouter ;)[/QUOTE]


Hmm, me neither. The boundries between routers and switches are fading. Switches ***used*** to operate exclusively at layer-2 but this is no longer the case. Switches can now operate at layer-3 and up which in essence makes them routers although the functionality is implemented in hardware instead of software. It's becoming a gray area.

The first time I worked on a Cisco Catalyst 6500 I was kinda confused. One part was running CatOS and the other part IOS and it was if as you operated on two seperate entities untill we converted to native IOS which handled both parts as one and it looked like you were configurating router interfaces...  :rolleyes:

---

