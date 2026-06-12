---
title: "should my server be my router too or use other comp for router??"
date: 2006-12-25
forum: Server Platforms
---

### Post by envis on 2006-12-25
i have a bunch of computers on my network, my Ubuntu server and others... they are all behind a D-Link "domestic router"...

it turns out that the D-Link router bugs and freezes my upload to 200kbs after just a bit of uploading... i cannot have my server behind that router and waste my bandwidth no more.

i am considering either:

-turning some pentium 1 into a "router" and use it instead of the D-Link, but its a lot of stuff to set up and learn...

or i could just,

-connect my Ubuntu server directly to the internet and make it be the DHCP server for the others computer too....

im a bit of a newbie to that whole setting up a server, setting up a network thing...

would there be anything wrong with connecting the server directly to the internet and use it as DHCP server at the same time so to give connection to the other computers in my house?...

would the fact that the server would also be a "router" for the rest of the network slow down the server when other computers use the internet... the server is a AMD64, 3000Mhz, 1gig of RAM, SATA 250 gig hard drive.... not a bad machine...

what would be best? can anyone give me some recommendations on that? i am hosting a radio station among with other websites that are growing on my server.... i need the server to respond very well!....

---

### Post by tooscaredtotry on 2006-12-25
I'd imagine it would depend on the number of hosts you have connecting to your server from the outside.  If you have another machine, I would probably make it a dedicated dhcp/router box just to split things up.

If I understand you correctly, your options are:

Server = router, dhcp, streaming audio

or

P1 = dhcp, router
Server = streaming audio

If this is the case, then you'd probably be better off having them separate if you can setup forwarding correctly, and as long as the P1 can handle all the traffic you're going to throw at it.... I'm not sure about that part.

---

### Post by Bite_me_Bill on 2006-12-25
If you have plenty of systems laying around here is a suggestion.


ISP Modem -> Firewall (Endain, IPCop, Smoothwall, MonoWall, Ect...) -> Switch -> Systems

---

### Post by Brazen on 2006-12-26
Yeah, definately do not use a server as a router.  Use your P1 box and turn it into a router.  I highly recommend pfsense for a router distrobution.

---

### Post by MrHorus on 2006-12-27
> **envis said:**
> 
-turning some pentium 1 into a "router" and use it instead of the D-Link, but its a lot of stuff to set up and learn...



No it's not - you might be pleasently suprised at just how easy it is :)

I've done it many times and from a hardware perspective, all you require is an old box with two network cards and a switch.

There is a flag somewhere in /proc that you change from a 0 to a 1 to enable IP forarding and then you enable masquerading (NAT) through iptables.

If you have a publicly routable subnet then you don't even need to worry about NAT although you will still want to fiddle around in iptables and set up some sensable rules.

Do a bit of Googling about iptables, masquerading and NAT and you will see just how easy it is :)

---

### Post by PilotJLR on 2006-12-28
I've frankly seen D-Link routers to be quite stable... consider at least upgrading its firmware before you junk it.

---

### Post by envis on 2006-12-30
thanks for all the ideas

but i already put myself to work after the second post or so and i followed the guy's idea, i started transforming a box into a router.. not the p1... i hate that p1, computers of that generation are a mystery to me i cant make them work ](*,) ... i used a a less old amd900 and installed IPCOP on it... 

and its turning out to be really great setup... now i need some switches or hubs to finish the installation properly.. even though i managed to start using it already with a band-aid setup...   i saw 5 ports hubs for 16.xx$ on the futureshop website...

---

### Post by pppetter on 2006-12-30
envis! don't buy a Hub, buy a Switch! there's a considerat difference between the two :)

---

### Post by envis on 2007-01-04
i have nothing against D-Link, the switch i bougth to split my green network is a D-Link...

i have my ip cop all set now and my ubuntu server goes through the ipcop only and i have no more uplaod speed problems

its great 8)

---

### Post by nix4me on 2007-01-04
Do not use server as router.  Very insafe.

Use a dedicated computer running ipcop, monowall or pfsense as a router/firewall.

nix4me

---

### Post by MJN on 2007-01-05
As others have said/hinted, I'd stick with the hardware router you've already got - what model is it and what firmware version are you using?

Using the DLink has many advantages (assuming you can fix the bug you've got - highly likely given how big it is): works out of the box pretty much, uses far less power than a PC, silent operation...

Mathew

---

### Post by teaker1s on 2007-01-05
I had a dlink dsl504t and it was a pile of junk as the linux version was so outdated and so was the firmware update.
 Found netgear great and linksys WAG54GS reasonable compared to dlink

---

### Post by MJN on 2007-01-05
That's nice, thanks. I think D-Link are superb.

Next! ;)

---

