---
title: "Advice for server setup?"
date: 2008-03-14
forum: Server Platforms
---

### Post by jamestech on 2008-03-14
Right I have been assigned a task for work.

I work in a computer repair shop, we currently have 2x ADSL connections for our broadband, both on seperate routers.

I have been asked to set up and Ubuntu server with 3xNIC's. The idea being that I set up the server as below



ADSL Line 1 -> Router --------------\
[COLOR="White"]ah, you make it into white text....[/COLOR]>Ubuntu Server -> Client PC's
ADSL Line 1 -> Router --------------/

The routers will be used purely as modems, I would be setting the Ubuntu machine up as DHCP for the LAN and the routers will be set up with the ubuntu machine as a DMZ.


What is the best way to go about doing this, our main needs are to spread the network load a little for the broadband and the possibility to monitor traffic as we frequently have bugged machines attempting to send out spam and eating our bandwidth.

---

### Post by faulkes on 2008-03-14
> **jamestech said:**
> 

ADSL Line 1 -> Router ->
                                            Ubuntu Server -> Client PC's
ADSL Line 1 -> Router ->

The routers will be used purely as modems, I would be setting the Ubuntu machine up as DHCP for the LAN and the routers will be set up with the ubuntu machine as a DMZ.


The only issue I see is that there is no routing protocol updates
which would help you load balance the traffic between the two
connections.  The only solution I could think might work would be
two equal cost default routes outbound from the linux machine.

Not sure what is required to do that though, although I hazard a
guess it has to do with tc.

```

man tc

```

Faulkes

---

### Post by Brazen on 2008-03-14
Ok, I just wrote up a big ol' long post about what the heck the OP is talking about since you can't have a DMZ without a firewall, but I think I figured it out.  OP must have a soho firewall/router that defines a "DMZ" as just an ip address that everything gets port-forwarded to.

So I do have one question:  Don't you have a seperate modem between each router and adsl line?  What model of routers are we talking about here?

Also I think maybe your diagram is supposed to be more like this:

adsl1 ----- router1 -----\
[COLOR="White"]whitespacewhitespac[/COLOR]Ubuntu -------- client pcs
adsl2 ----- router2 ----/

but are you sure it's not like this:

adsl1 ----- modem1 ---- router1 -----\
[COLOR="White"]whitespacewhitespacewhitespace[/COLOR]Ubuntu -------- client pcs
adsl2 ----- modem2 ---- router2 ----/

I guess the important thing to know is, do you have just regular ethernet plugged into your routers, because if so then you can ditch the routers and use your Ubuntu box as the router and have it authenticate both adsl lines.  I thought most adsl setups use a phone line plugged into a modem and ethernet from the modem to the router, but it is possible that you have a phone line plugged directly into your router.  Again, at least giving the model of the router will help greatly in figuring this out.

---

### Post by jamestech on 2008-03-14
Brazen:

Yes it should look like the first diagram (I did put some spaces in to align it, but they seem to have disappeared), both routers have the ADSL modems built in. I am at home now and don't have the model numbers for the two routers but I can't think why you would need them besides to check if they have the modems built in?

I assume there wouldn't really need to be any configuration on the routers besides setting up the DMZ which I am perfectly capable of?


faulkes:

You have lost me here "two equal cost default routes outbound from the linux machine" can you word that differently for me?

---

### Post by faulkes on 2008-03-14
When you connect two routers too two different ethernet adapters, each adapter sits
on a network.  Typically in most setups, you have what is called a "default route",
this means that if a packet does not match local addressing, it gets sent to the 
default gateway which forwards it on.

In your setup, you have two networks but only one default route, which means all
packets  leaving your network will only ever go through one of the adsl 
modem/routers.

"Two equal cost default routes" basicly creates a round-robin effect of sending out 
packets each interface (usually doing route caching).  This is common in cisco 
networking.

Faulkes

---

### Post by rickyjones on 2008-03-14
> **faulkes said:**
> When you connect two routers too two different ethernet adapters, each adapter sites
on a network.  Typically in most setups, you have what is called a "default route",
this means that if a packet does not match local addressing, it gets sent to the 
default gateway which forwards it on.

In your setup, you have two networks but only one default route, which means all
packets  leaving your network will only ever go through one of the adsl 
modem/routers.

"Two equal cost default routes" basicly creates a round-robin effect of sending out 
packets each interface (usually doing route caching).  This is common in cisco 
networking.

Faulkes

I really cannot give any advice on the configuration of the server but it might be worth looking into a device dedicated to this. You can purchase routers that take two internet connections and turn them into one connection. This might be a better solution when looking at a total cost/time scenario.

[http://www.provantage.com/linksys-rv016~7LNKR00L.htm](http://www.provantage.com/linksys-rv016~7LNKR00L.htm)

Here is the google search I used - you might find more results for a better price - [http://www.google.com/search?hl=en&q=dual+internet+connection+router&btnG=Google+Search&aq=2&oq=dual+internet+co](http://www.google.com/search?hl=en&q=dual+internet+connection+router&btnG=Google+Search&aq=2&oq=dual+internet+co)

-Richard

---

### Post by SuperMiguel on 2008-03-14
how can u connect the router to the server and then from the server to the client??? i would think the clients and server are connected to a similar port in the router or switch it self..

---

### Post by Harlequin on 2008-03-14
Don't use DMZ on the adsl modem routers - use bridge mode.  THis essentially disables the router component of the modems as you dont want it.

You will then end up with ETH0 & ETH1 being internet connections and ETH2 as a connection to the rest of your network.  

(Note there is no need to have 3 network cards in the server as the same effect can be had by pluggin everything into the one switch and having the two adsl modems on different subnets to the rest of your network and having the server act as your DHCP server with routes set to the two modems)

As for load balancing between the two read this.

[http://www.debianadmin.com/linux-ethernet-bonding-configuration.html#more-77](http://www.debianadmin.com/linux-ethernet-bonding-configuration.html#more-77)

---

