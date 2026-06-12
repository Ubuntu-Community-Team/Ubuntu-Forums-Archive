---
title: "Wifi Bridge Mayhem"
date: 2013-01-11
forum: The Cafe
---

### Post by SR_ELPIRATA on 2013-01-11
LOL Didnt know where to put this since its not really ubuntu related :)

Where to start... well, basically, for one of my clients I was working on a way to get their internet to work on both their office and home (since they are about 100ft apart). I used whatever they had in their office, and that meant reusing 2 of their 5 routers (no clue who was the genius tech guy that suggested having 5 routers with all of them doing dhcp).

I managed to establish a bridge between 2 TP-LINK routers and got internet working and everyone could see each other, nirvana!

I go away for about 2 weeks and I come back and... it still working! but since their DSL went down, they got another brand internet (a mifi style), and somehow somebody managed to disconnect the bridge, although didnt erase everything I did.

Long story short... I reconnected the missing router for the bridge and its working again (with the old internet router mind you, but they want to use the new one now).

So I start dabbling around and THIS is what is intriguing me. Their DSL router is 192.168.1.1, and for the bridge Im using 2 TP-Link routers, WR841ND as 192.168.1.104 and this is the one wired to the network, and the WR340G which is at their home with IP 192.168.1.103.

So, I come back, and decided to ping these and DSl is fine, and remote router is fine, but the 104 is not answering. Cable is connected, and I can see the bridge is working because from the office I can get to the 340G web control panel and see that the bridge is working. But the 841ND never shows an IP. Its like somehow the IP went invisible and no way I try seems to work to find its control panel (which used to work).

But, it works, I can go with my android and using my wifi scanner I can see the 3 routers (which are all named the same, with same password, so that I can go to the home or office and never have to switch routers manually), but with 'fing' (android utility) I can see all the IPs used in the network, and... again I can see the DSL, the 340G and all mobiles, laptops and computers, but the 841ND is not showing at all. And it works, I can still use the wireless and access shared folders in the network.

Anyone ever seen anything like this? I would say that with this I have seen it all... but in this field... you never see it all.

Since I cant see the 841ND Im forced to reset the router and that means Im gonna have to start from scratch again, but wanted to know if anyone ever experienced something like this :)

ELP

---

