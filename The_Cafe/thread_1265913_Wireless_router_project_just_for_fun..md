---
title: "Wireless router project just for fun."
date: 2009-09-14
forum: The Cafe
---

### Post by Megrimn on 2009-09-14
here's the situation:

2 wireless routers, 1 internet connection.

Goal: 

Receive internet connection on a pc via a wired connection to one router communicating wirelessly with the router with the physical connection to the internet.

Diagram:


   [COLOR="Magenta"]INTERWEBZ[/COLOR][COLOR="Lime"]<-wired->[/COLOR][COLOR="Red"]ROUTER_A[/COLOR][COLOR="Purple"] < - wireless - >[/COLOR][COLOR="Red"]ROUTER_B[/COLOR][COLOR="Lime"]<-wired->[/COLOR][COLOR="Navy"]PC[/COLOR]



(basically, the internet's in the basement.  my computer's upstairs. I can't run a wire upstairs, and I don't want to buy a wireless thing for the computer.  I'd rather not use my laptop as a hub.  can I run wireless from one router to the next w/o any wires?)

Plausible or unsolvable? discuss. :P

---

### Post by pwnst*r on 2009-09-14
Linksys compatible with DD-WRT + run one as a client bridge.  i'm doing it for my PS3 and 360 in my living room which both are connected to the client bridge.

for reference i use a WRT150N for my primary and a WRT54GL for my second router.

[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

---

### Post by drumfire420 on 2009-09-14
The DD-WRT project makes that really easy, assuming your routers are supported.  They even have guides on how to do that (make a wireless bridge)

[http://www.dd-wrt.com/](http://www.dd-wrt.com/)

You can get REALLY complex with this, so have fun ^_^

---

### Post by drumfire420 on 2009-09-14
> **pwnst*r said:**
> Linksys compatible with DD-WRT + run one as a client bridge.  i'm doing it for my PS3 and 360 in my living room which both are connected to the client bridge.

for reference i use a WRT150N for my primary and a WRT54GL for my second router.

[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

Great minds?  ... i guess you're just a faster typer.:)

---

### Post by Megrimn on 2009-09-14
+1 Then it's definitely plausible.

---

### Post by Bucky Ball on 2009-09-20
Okay, I have two D-Link routers. One has no wireless but is the print server and four ports. Internet cable connected WAN port of that.

Second router is a D-Link virtually the same except no print server but has wireless. 

I have the wireless router plugged in through a regular LAN ethernet port on BOTH routers (NOT the WAN port on the wireless) and the second router has separate IP and is acting as access point. Gateway is the Wired router, just like any of the machines.

So, Wired router = internet cable into WAN port, two computer hard wired to LAN ports and Wireless router hard wire from one of its LAN ports to a LAN port on the Wired router.

This setup covers my two desktops (wired) and my laptop (wireless). I get quite a bit of coverage.

Let me know if you want anymore detail.

---

