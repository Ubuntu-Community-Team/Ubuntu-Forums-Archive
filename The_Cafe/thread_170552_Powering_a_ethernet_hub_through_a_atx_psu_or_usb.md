---
title: "Powering a ethernet hub through a atx psu or usb"
date: 2006-05-04
forum: The Cafe
---

### Post by Virogenesis on 2006-05-04
I'm planning on building a firewall and basically I'm wondering if its possible to somehow wire a ethernet hub up to the computer's psu or maybe power it from usb.
Does anyone happen to know how I might be able to do something like this soldering shouldn't be a problem as my brother has a iron and I believe hes pretty good with it.
Cheers

---

### Post by mips on 2006-05-04
That all depends on the hubs power requirements.

Doubt USB will work.

Why do you want to do it this way ?

---

### Post by Virogenesis on 2006-05-04
I just found something that will boast the power of the rail of the usb from 5volt to 9 volts.
Not sure if this is the way to go mind.
Basically I'm experiencing problems with my router and have a old comp laying around so I thought what better way to put it to use and what have you as I wish to mount the hub inside the case I do not see the need for another power supply plus I'd prefer it to be neat and what a cool hack it would be to having the hub being powered by the comp itself.

---

### Post by ekarni on 2006-05-04
It really depends on the hub's power requirements.  USB is only spec'd for 500mA at 5V (IIRC - please correct me if I'm mistaken).  It's unlikely that that is enough juice to power your hub.  The other option is to plug it into a standard internal power plug like what's used for hard disks and CD-ROMs.  You can get +12 and +5V off of those.

Here are some things to start with:
-Take a ruler and make sure the hub will physically fit inside the case you've got.  Doesn't help to get halfway into this and find out it won't fit!
-Attempt to figure out the power requirements.  Assuming the hub is currently powered by a wall transformer, read the sticker on that and see what it's designed to take (volts and current).  

If the hub is already designed for DC input, you might be able to splice into the existing power plug, assuming the volts are compatible.  Otherwise, if it's AC input, the AC gets rectified to DC inside the hub.  Things will get ugly in a hurry if that's the case.

How many CAT5 jacks do you need?  Might be a whole lot simpler to just buy a few cheap NIC cards than do this mod (but admittedly less of a fun challenge).

---

### Post by mips on 2006-05-04
Like I said, you need to know the hubs power requirements.

It not only about voltage but also current (A/Amps)
[www.usb.org](www.usb.org)

It will probably be easier to power the hub off one of the PSU DC outputs.

---

### Post by Virogenesis on 2006-05-04
I haven't yet brought the switch so I can basicaly choose and I'd prefer to use psu over the usb anyway so thats good. 
As for using nics instead of a switch that would work apart from the fact I'll be switching over to flex itx board later on and the board I've basically chosen has only 2 pci but I only need one so thats fine.

---

### Post by jason.b.c on 2006-05-04
> I'm planning on building a firewall and basically I'm wondering if its possible to somehow wire a ethernet hub up to the computer's psu or maybe power it from usb.

Why??, You would be doing it in the most difficult way..[-X 



[QUOTE=Virogenesis]I just found something that will boast the power of the rail of the usb from 5volt to 9 volts.
Not sure if this is the way to go mind.
Basically I'm experiencing problems with my router and have a old comp laying around so I thought what better way to put it to use and what have you as I wish to mount the hub inside the case I do not see the need for another power supply plus I'd prefer it to be neat and what a cool hack it would be to having the hub being powered by the comp itself.[/QUOTE]

Have a look at these.:>  [www.ipcop.org](www.ipcop.org)   and   [http://forums.freesco.org/support/index.php?](http://forums.freesco.org/support/index.php?) and [www.routerboard.com/rb44.html](www.routerboard.com/rb44.html)

;)

---

### Post by Virogenesis on 2006-05-05
[QUOTE=jason.b.c]Why??, You would be doing it in the most difficult way..[-X 
[/QUOTE]
Because later on I'll be putting the router inside a desk so since I'm doing it I might aswell do it good but this won't be until I change my room around again. 

Have a look at these.:>  [www.ipcop.org](www.ipcop.org)   and   [http://forums.freesco.org/support/index.php?](http://forums.freesco.org/support/index.php?) and [www.routerboard.com/rb44.html](www.routerboard.com/rb44.html)

;)[/QUOTE]
Yeah I know about these thats why I require a hub I'm not sure to use smoothwall or ipcop yet.

I'll post some pics when I'm done

---

### Post by mips on 2006-05-05
Also have a look at m0n0wall

---

### Post by jason.b.c on 2006-05-05
> **Virogenesis]Because later on I'll be putting the_ router _inside a desk so since I'm doing it I might aswell do it good but this won't be until I change my room around again. 

Have a look at these.:>  [www.ipcop.org](www.ipcop.org)   and   [http://forums.freesco.org/support/index.php?](http://forums.freesco.org/support/index.php?) and [www.routerboard.com/rb44.html](www.routerboard.com/rb44.html)

 said:**
> 
[QUOTE=Virogenesis]with my router and _have a old comp laying around_ so I thought what better way to put it to use 


Why do need a router??  You mean **Ethernet hub/router**, Right??

You said you have an old computer laying around, Well, you don't need a router if you use stuff like this:>  [www.ipcop.org](www.ipcop.org) and [www.routerboard.com/rb44.html](www.routerboard.com/rb44.html)  to build one..    

That routerboard thing **takes the place of your router !**;)

---

### Post by Virogenesis on 2006-05-05
[QUOTE=jason.b.c]Why do need a router??  You mean **Ethernet hub/router**, Right??

You said you have an old computer laying around, Well, you don't need a router if you use stuff like this:>  [www.ipcop.org](www.ipcop.org) and [www.routerboard.com/rb44.html](www.routerboard.com/rb44.html)  to build one..    

That routerboard thing **takes the place of your router !**;)[/QUOTE]
I know it does BUT I don't have the money for a switch/hub right now so I'll use my old router (as a hub its going to be double natted which sucks), a speedtouch 330 usb dsl modem.
I'll sell my netgear dg814 on ebay and with the money I get from that I'll source a hub to take its place.
Like I say I know about IPCop I was the one who convinced my bro to set up a firewall using ipcop he did but decided he preferred smoothwall express.
O yeah I got him to set up a server using debian so I haven't done too bad.

---

