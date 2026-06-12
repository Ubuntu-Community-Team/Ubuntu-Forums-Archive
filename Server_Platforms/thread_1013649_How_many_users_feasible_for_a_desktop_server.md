---
title: "How many users feasible for a desktop server?"
date: 2008-12-17
forum: Server Platforms
---

### Post by dimothy10 on 2008-12-17
Dear all,

I was wondering what a feasible number of users would be feasible for Ubuntu Server running on a run of the mill desktop PC?

I only query as the hotel I work in has a 250 user bespoke server that is not meeting the need of our 500+ potential users.  Seeing as there is no need for a file server, user names, print services and just a requirement to assign IPs and route to the internet could a few mid range PCs bought off the shelf help alleviate the choking our server is currently going through?  Or does it require an altogether more comprehensive approach?

Regards


tim

---

### Post by gtdaqua on 2008-12-17
Assign IPs and route to the Internet? Then a router can do the job. In fact, that is the whole reason why you buy a router - Route traffic and optionally assign IP addresses.

---

### Post by windependence on 2008-12-17
Everything you need right here with a web interface:

[www.pfsense.org](www.pfsense.org)

-Tim

---

### Post by dimothy10 on 2008-12-17
The realisaztion has finally dawned.  Seeing as there is no longer a charge in the hotel for the internet then there is no use for the server nor a requirement to log each rooms access.  As you have so correctly pointed out a router would be all that is needed to allow the guest to connect still.  Assuming there are already suitable switches in place would a mid range desktop be able to cope with 500+ IPs to route to the internet connection?  Apologise if this is a somewhat silly questions

---

### Post by gtdaqua on 2008-12-17
> **dimothy10 said:**
> The realisaztion has finally dawned.  Seeing as there is no longer a charge in the hotel for the internet then there is no use for the server nor a requirement to log each rooms access.  As you have so correctly pointed out a router would be all that is needed to allow the guest to connect still.  Assuming there are already suitable switches in place would a mid range desktop be able to cope with 500+ IPs to route to the internet connection?  Apologise if this is a somewhat silly questions

Why do you want a desktop to route traffic? Dont use a desktop. A router can simply do that. You just need bandwidth to handle that kind of traffic (i.e if all 500 are going access internet same time and big time!)

---

### Post by dimothy10 on 2008-12-17
was more worried about cost as there is no budget to solve this problem.   The solution currently proposed to management is just to remove the internet from the rooms altogether.  The reason I was suggesting a desktop as opposed to a router is a desktop can be picked up for cheap coupled with some flavour of linux to perform the same task.  How expensive would a router for this kind of usage be roughly?

---

### Post by gtdaqua on 2008-12-17
> **dimothy10 said:**
> was more worried about cost as there is no budget to solve this problem.   The solution currently proposed to management is just to remove the internet from the rooms altogether.  The reason I was suggesting a desktop as opposed to a router is a desktop can be picked up for cheap coupled with some flavour of linux to perform the same task.  How expensive would a router for this kind of usage be roughly?

A router more expensive than a desktop?? Well, you are not looking at data-centre class Enterprise-level Cisco Router, are you? Get a simple Linksys or D-Link Router. A gigabit port would be good too.

[D-Link DGL-4100 4-Port Gigabit Switch Broadband Gaming Router]("http://www.amazon.com/D-Link-DGL-4100-4-Port-Gigabit-Broadband/dp/B0006TIA0C/ref=sr_1_1?ie=UTF8&s=electronics&qid=1229507093&sr=1-1"). 

This one is about $100. You should be able to get something that is even cheaper. 

Mind you, this is not an enterprise-class router. A mid-range router that will simply forward traffic between Internet and your clients with some basic firewall functions.

---

### Post by dimothy10 on 2008-12-17
I have to admit I was barking somewhere towards the wrong tree.  I had certainly narrowed my mind to thinking that an enterprise style router would be what was required and hadnt even considered a cheaper alternative like the one you have suggested.  Perhaps this is the easy solution needed!  Thanks for all the help and patience

---

### Post by windependence on 2008-12-17
That's why I suggested pfsense. It comes as an ISO and the footprint is only 50 MB. You could even run it off a flash card. It will scale to the number of people you are trying to serve if installed on even an older PC. You would still need a switch behind it however, and you would need the required number of ports unless you are going to try to do wireless, in which case you could use several cheap access points. While I agree with gtd on the reasoning, my experience is a small soho router like described will not handle the traffic you would expect from that many users.

-Tim

---

### Post by gtdaqua on 2008-12-17
> **windependence said:**
> That's why I suggested pfsense. It comes as an ISO and the footprint is only 50 MB. You could even run it off a flash card. It will scale to the number of people you are trying to serve if installed on even an older PC. You would still need a switch behind it however, and you would need the required number of ports unless you are going to try to do wireless, in which case you could use several cheap access points. While I agree with gtd on the reasoning, my experience is a small soho router like described will not handle the traffic you would expect from that many users.

-Tim

Tim, you are complicating. This is not at all required. All you need is 50$ router to do the job. Ofcourse pfsense can do it but that is complex.

SOHO router CAN handle the traffic of those many users. If there could be any problem, it would be from the network bandwidth (internet bandwidth) side.

---

### Post by gtdaqua on 2008-12-17
> **dimothy10 said:**
> I have to admit I was barking somewhere towards the wrong tree.  I had certainly narrowed my mind to thinking that an enterprise style router would be what was required and hadnt even considered a cheaper alternative like the one you have suggested.  Perhaps this is the easy solution needed!  Thanks for all the help and patience

If you are looking at a slightly higher level of router, then you could look at Cisco 800 series (start from $250) or equivalent 3com or D-Link. But having a desktop do a router's job is simply complicated. You only need this if you want to content-filter, log the network traffic for extensive audit etc.

---

### Post by Zack McCool on 2008-12-17
A $50 router will NOT handle the traffic from 500 users very well.  You will have a serious bottleneck at the router.  

A mid-range Cisco router would be the best way to go, though a PC with a NIC and switch for each floor would likely do the trick fine, and using software like pfsense is no more complicated than using a router's interface once the initial installation is complete.

Your standard home router has a very slow CPU and is not designed to handle more than 1024 connections concurrently.  Standard web browsing will often open a few at a time, and once you add in e-mail and maybe streaming content, the router will be quickly bogged down.

It is also not advisable for the hotel to decide to drop the internet offering altogether...   Most travelers today insist on at least a wired connection, and many won't stay at a hotel that doesn't offer free wireless.  Many of us are working even when not at work, and need some form of connectivity.  I know when I choose a hotel, I immediately remove all of the locations that do not have in-room internet, even on family trips...

---

### Post by dimothy10 on 2008-12-17
I totally agree with the lunacy of dropping the internet in the hotel altogether.  Today is actually my last day of work there so it will no longer be my problem but i certainly feel for the people working the front desk having to explain why there is not internet.  Not terribly up to speed on Cisco routers, or indeed enterprise routers as a whole, so any model recommendations for a decent (ish) router?  Woofers and tweeters are not really necessary as the system is totally separate from that of the front desk (ie customer details and credit cards) so would rely mainly on guests to have their own security in place on their laptops.  Will look in to the configuration and state of the switches today and see if they are up to snuff.  thanks again for all your help.

---

### Post by windependence on 2008-12-17
> **gtdaqua said:**
> Tim, you are complicating. This is not at all required. All you need is 50$ router to do the job. Ofcourse pfsense can do it but that is complex.

SOHO router CAN handle the traffic of those many users. If there could be any problem, it would be from the network bandwidth (internet bandwidth) side.
gtd, I had a client who had this many users on a soho router and the box actually got hot to the touch and would just shut down the network at random times. On the other hand, I have quite a few businesses where we run pfsense boxes built out of old PIII PCs for a gateway box and 24 or 48 port switches behind them. They run so well, we screwed ourselves out of service work. They almost never have problems, and we admin them remotely.

-Tim

---

### Post by gtdaqua on 2008-12-17
> **Zack McCool said:**
> A $50 router will NOT handle the traffic from 500 users very well.  You will have a serious bottleneck at the router.  

A mid-range Cisco router would be the best way to go, though a PC with a NIC and switch for each floor would likely do the trick fine, and using software like pfsense is no more complicated than using a router's interface once the initial installation is complete.

Your standard home router has a very slow CPU and is not designed to handle more than 1024 connections concurrently.  Standard web browsing will often open a few at a time, and once you add in e-mail and maybe streaming content, the router will be quickly bogged down.

It is also not advisable for the hotel to decide to drop the internet offering altogether...   Most travelers today insist on at least a wired connection, and many won't stay at a hotel that doesn't offer free wireless.  Many of us are working even when not at work, and need some form of connectivity.  I know when I choose a hotel, I immediately remove all of the locations that do not have in-room internet, even on family trips...

I have clearly said that the problem is going to be on the internet bandwidth. With a poor bandwidth, even a Cisco 28xx series is going to fail in this scenario. 

If this is an ADSL connection (which I think it is), all 500 simultaneously accessing internet is going to be a problem even on 10Mbps pipe. If your OUT interface is slow/poor, then Cisco 28xx and the $50 router are the same.

If this is a Leased Line, then you want to think about getting a higher-end router for optimal performance.

---

### Post by Zack McCool on 2008-12-17
> **gtdaqua said:**
> I have clearly said that the problem is going to be on the internet bandwidth. With a poor bandwidth, even a Cisco 28xx series is going to fail in this scenario. 

The problem is NOT the bandwith to the internet, but rather the router's ability to handle the connections and do the routing.  A soho device is just not designed for this and will not be reliable.

> 
If this is an ADSL connection (which I think it is), all 500 simultaneously accessing internet is going to be a problem even on 10Mbps pipe. If your OUT interface is slow/poor, then Cisco 28xx and the $50 router are the same.

Sure, but I didn't see anywhere where the connection was mentioned.  He did mention that there are currently 250 users, so I doubt it's adsl.  This is a hotel, afterall...

> 
If this is a Leased Line, then you want to think about getting a higher-end router for optimal performance.

If this is anyplace with more than 50 users, you would want a mid-range or better router and a good pipe to the internet.  And rather than spending all that money on a higher-end router, a low-end pc (PIII) can easily handle the load, provided it has enough bandwith coming out of the back-end.

---

### Post by bsmith1051 on 2008-12-18
don't forget that a generic Class-D (C?) sub-net will only support 255 IP assignments.  So they might need to switch from 192.168.1.x to 172.1.x.x.  Or, use two separate LANs each with their own uplink.

re routers, a SOHO unit probably won't have enough memory to track all the connections without occasionally crashing.  A mid-range router should have no problem but, then, they're just dedicated PCs so the hardened Linux app would be equivalent.

---

