---
title: "Travelling, and connecting to a network."
date: 2008-10-26
forum: System76 Support
---

### Post by einnar on 2008-10-26
I'm not sure if this is a system76 or a network problem...

I have no problems connecting with LAN or wireless at home. None. When I travel, though, I quite often have to contact the helpdesk of various network providers to get my network to work. 

Wireless is usually getting my MAC properly regestered with the system. The techs tell me it is Linux that their systems have issues with. 

LAN connections the answer is usually "maybe you have a bad network card"..

I can connect. Talking to the techs, I have the right gateway, DNS, etc. I can fire up various tools, and see other machines talking on the network, I just can't connect to any sites. 

Any thoughts?

Thanks.

---

### Post by ctsdownloads on 2008-10-26
> **einnar said:**
> I'm not sure if this is a system76 or a network problem...

I have no problems connecting with LAN or wireless at home. None. When I travel, though, I quite often have to contact the helpdesk of various network providers to get my network to work. 

Wireless is usually getting my MAC properly regestered with the system. The techs tell me it is Linux that their systems have issues with. 

LAN connections the answer is usually "maybe you have a bad network card"..

I can connect. Talking to the techs, I have the right gateway, DNS, etc. I can fire up various tools, and see other machines talking on the network, I just can't connect to any sites. 

Any thoughts?

Thanks.

Almost sounds like one away from home destination you having issues with? 

> The techs tell me it is Linux that their systems have issues with. 

Is this an issue with different hotels, coffee shops or what? Need to know a little more and if this is something that has been tested with one provider. I travel a lot of with my system76 notebook, among other ubuntu notebooks - if you are being assigned an IP by the network and the network's DNS is not bad, you should be fine.

---

### Post by asmiller-ke6seh on 2008-10-27
I have found WICD, and it is. So long as I have enough signal strength and a friendly access administrator I can connect 99% of the time on my SERP2 laptop.

---

### Post by einnar on 2008-10-28
ctsdownloads - If you re-read my original post, you'll notice I said multiple. Both locations, and providers. This includes Texas, Michigan, various places on the east coast of the US, as well as 3 countries in Europe. I'm not using a 2nd party air card, or network card. I'm not using a provider that I travel with. I get where work sends me, and I use a hotel, or local provider for my work area. The free ones I rarely get to work, as nobody on a helpdesk wants to help. The paid ones I get assistance, as they have money from me and it's all part of the game.

I've recently found (In the last 2 days) that disabling IPv6 lets me browse their networks, but in many cases I need a fixed IP, as DHCP does not work properly for me. I will get an IP address, but not always the correct subnet mask or gateway.

If I manually put in the connection information for a fixed IP, it works fine.

---

