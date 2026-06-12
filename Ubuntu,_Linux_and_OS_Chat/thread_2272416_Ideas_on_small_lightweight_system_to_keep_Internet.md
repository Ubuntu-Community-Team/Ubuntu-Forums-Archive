---
title: "Ideas on small lightweight system to keep Internet on in our server closet"
date: 2015-04-06
forum: Ubuntu, Linux and OS Chat
---

### Post by greavette on 2015-04-06
Hello,

In our small office we have a security gateway (running Untangle) on a physical server.  We have two 48 port managed switches and two large Virtual Hosts running our various Virtual Machines.  Our office is in Northern Ontario (Canada) where Power can at times be a problem. For the most part power is stable but we have on more than one occassion had an outage that outlasted our UPS backups.  So we have employed Battery Backup units for our various hardware which will kick in shutdown instructions to gracefully turn off our hardware if the outage is prolonged.  

We also have a Avtech Temperature Monitor system that keeps tabs on the temperature of our server room and any power outage issues (sends alerts).  

What I'd like to develop is a system that stands beside what we currently have...a system that keeps our temperature monitor and our Internet (DSL) up as long as possible. Right now our DSL modem connects to our Security Gateway.  But if the power outage is prolonged the security gateway will come down.   Is there a way to split the signal from the DSL modem to a separate smaller less power hungry system?  My first thought is to use a small Raspberry Pi and install something on it that would act as a security gateway.  Is there software I could install on the Pi to achieve this?  Then behind the Raspberry Pi I would have a small switch to connect the Pi and Temperature Alert monitor.  Using this small system in place my guess is I could get a decent UPS (2200 perhaps) and keep this small system up and running for 7-10 hours (maybe longer).  

If this is overly complicated then I could put the security gateway on the battery backup.  Have the separate small switch attached to another NIC on the gateway and give me what I need...but this gateway is much larger and would use more power than a small Pi so the length of time I could keep this system up and running would be greatly reduced.

Any ides or thoughts on how best to solve this would be greatly appreciated.

Thank you.

---

### Post by TheFu on 2015-04-06
A new generation chromebook running a minimal Linux should be able to get 8+ hrs. $130 - just saw a Best Buy deal a few days ago. With the screen off/closed, perhaps 2x that time? I dunno.

I did some work in Nepal a few years ago where they have power outages daily due to power generation limits in the country. 6 hrs of power, 6 hrs of none and the time shifts 1 hour every day so everyone is equally impacted. It is strange to be in the toilet with no windows and have the power go out. There they had an inverter that charged a bank of batteries for use when the power was off. In that part of the world, getting that stuff was really easy, since everyone needed one. They only used desktops when power was available.  The wifi, router, switches were powered all the time.  I deployed an [Alix2d13]("http://www.pcengines.ch/alix2d13.htm") running pfsense for them. Think it used less than 4W.  pfSense is a full featured, enterprise-class, edge router+firewall solution. It is used by universities around the world for this purpose.  The monastery didn't need much throughput so the low-power Alix was perfect. They really just wanted strong QoS management to ensure the office system always got priority treatment over monks and visitors.  They had multiple Ubiquiti wifi-APs - amazing APs if you have any wifi needs, highly recommended.

Would your office environment support a generator?  That would be the easiest solution and you won't need to go to low-powered solutions.

An rpi is just too slow for throughput to be considered.  People seem to forget they suck at network and disk I/O.

However, some Atom-like CPU solutions CAN easily be used for GigE speeds.  I have a $50 [AMD E350 APU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128468&cm_re=gigabyte_e350_apu-_-13-128-468-_-Product") that does it today; total cost of the build was $150 in 2012. 26W at spin-up, but 13W normally. If I connected CF for storage, the power use should drop. Check out some other solutions from Netgate [http://store.netgate.com/ALIX2D13-DIY-Kit-P172.aspx](http://store.netgate.com/ALIX2D13-DIY-Kit-P172.aspx) - that's were I got the Alix system.  Low power means almost zero heat.  I would strongly suggest you go with a low-power x86 solution, if you don't get a generator.  If your Untangle box is an old-style data center power-sucking thing that is really the best suggestion I have.  Can you migrate that software to a more efficient platform? Get two and configure them identically, since these cheap system don't have redundancy.

I don't think there is a good way to switch DSL connections. Really it comes to replacing a power hungry box with a lower-power box.

---

### Post by tgalati4 on 2015-04-07
An alternative is to get a 4-port (or 8-port) switch with *openwrt* or *dd-wrt* on it and run Wake-on-LAN (WoL) or Power-on-LAN (PoL).  You can run small linux scripts to detect when power comes back and then send PoL packets to your server equipment so they boot back up after power returns.  You can ssh into the switch and then log into other devices in the server room to perform maintanence.   With a little work, you can probably integrate your environmental telemetry.  You can run a 4-port switch for several hours on a decent UPS.  *openwrt* can handle most gateway policies.  

The real question is how productive can you be when the power is out?  Do you really need 48 active ports when the power is out?  I would make a triage tree and map out what essential services are needed during a power outage of 10 minutes, 1-hour, 4-hours, 12-hours, 24-hours, 96-hours.

During the Northridge earthquake in 1994, we lost power in our area for 4 days.  Each time increment can have a different backup solution in layers so that you degrade capabilities gracefully.

A raspberrypi would be find for monitoring and as a "canary" to see if it is still alive (by *ping* and *ssh* from outside), but as the TheFu suggests, they are not optimized for network (the USB port and 100BaseT go through the same, slow USB controller) so would not make a good security gateway.  At least with the Pi, you can use it to control the coffee maker when the power returns.  That's a real benefit, as it is going to be a long night.

---

### Post by TheFu on 2015-04-07
tgalati4 - that is brilliant!  A single $90 900VA UPS powering a single dd-wrt router should go for 16-24 hrs (my guess). Of course, having another public IP would need to be assigned and forwarded to the tiny router and most people wouldn't want that device in-line for all traffic.

Or would a traffic replication device work? Check IT security sites to find this sort of equipment.  My supplier (cheap "star" device) for $15 ran out. They weren't all that great anyway. [https://greatscottgadgets.com/throwingstar/](https://greatscottgadgets.com/throwingstar/) has some options for purchase.

---

### Post by 1clue on 2015-04-07
I think I'm missing something here.


[LIST=1]
[*]Is the raspberry pi routing packets or is it just a holder for a few sensors and a power relay? 
[*]How fast is your connection? 
[*]How much actual data throughput do you have? 
[*]Do you need VPN or UTM? 
[/LIST]
 
A raspberry pi is a horrible router.  I have several, they're great little appliance boards but they are no good for handling traffic at any speed I can imagine a 48-port switch being part of.  Yes they go for $20  but you can also get a purpose-built wifi router for $20 on Amazon, and it comes with a power supply.  Keep in mind also that EVERYTHING on the pi runs through the same USB chip, including the network.  And it's not gigabit, it's 100mbps and even the new raspberry pi 2 b can't saturate that **single** 100 mbps connection from what I've seen.

I would seriously consider what your network speed will likely be in a few years.  My location is less than 2 years from gigabit speeds.

There is a series of new Intel Atom-based CPUS with QuickAssist hardware encryption/compression acceleration.  There are appliances and boards based on these processors available right now, although you may have to scratch to get driver support for the non-AES encryption if you're outside the USA.  These atoms use less than 20w TDP and are meant to replace much bigger hardware in the router stack, including E-series stuff.  I have one of these:  [http://www.supermicro.com/products/motherboard/atom/x10/a1srm-ln7f-2758.cfm](http://www.supermicro.com/products/motherboard/atom/x10/a1srm-ln7f-2758.cfm) with 16g ecc RAM.

I don't have mine set up yet but I've seen plenty of appliances with pfSense or Linux (usually CentOS) with the dual core version of my chip.  Look here:  [http://store.netgate.com/Search.aspx?k=c2358](http://store.netgate.com/Search.aspx?k=c2358)  This should be able to saturate a gigabit full duplex connection with VPN traffic and a full threat management suite, unless they don't support drives for the UTM.

---

### Post by tgalati4 on 2015-04-07
My thinking is that you host a maintenance page using a light web server on *openwrt* router--using the same static IP address as the main site.  When the power comes back, run a script to change the sites table to swap out the router for the real server.  This won't cover every Use Case, but you get some time on an UPS to figure out what to do next.  An alternative is to have a backup website using a cloud service provider and use the router and clever scripting to activate the cloud instance when the power is down.

If you really need to keep a 48-port switch running, then get an UPS with a room-sized bank of batteries.  My guess is a cloud provider would be cheaper than replacing batteries every 3 years.

There are too many details missing from the OP's Use Case to make helpful suggestions.

---

### Post by TheFu on 2015-04-07
I was assuming this was a tiny business office and internet was only needed for back-office systems and perhaps remote access for workers through a VPN, not primary internet-facing things like web and email.

But we don't really know.

---

### Post by 1clue on 2015-04-07
A cloud server would really really be cheaper than a battery backup for a full server rack, but I don't think we can make that assumption with the information we have right now.

Size of the office doesn't matter much IMO, what matters is the amount of information traveling through the router and the processing the router needs to do on it.  My c2758 setup from a couple posts up is for my home office.  I need really good VPN performance, which is why I got it, and I figured I could use a couple VMs off of that.

In my experience many businesses with fewer than 200 seats have slower Internet connections than many of their employees, and possibly more stringent firewall requirements.  My work Internet is unable to exceed 15/5 and is users-only, but my home is currently contracted at 60/10 and can get 200/something.  In 2 years I expect gigabit here, no telling what they'll get at work.

---

### Post by 1clue on 2015-04-07
Sorry for polluting this thread with a bunch of stodgy business-attitude posts, but I can't help it.  I see a lot of reliability issues that really cost the business a lot of money, that could be solved for not much more money than they spent on half-baked SOHO solutions.

If this is actually a business or even a volunteer type setup with a lot of people working, then you need to ignore the cost of the networking gear and pay attention to real costs:
[LIST=1]
[*]How much does it cost per hour for your network to be down?
[LIST=1]
[*]Money made from hosted sites.
[*]Mission not accomplished (e.g. a charity not able to do its work, or games not able to be played, movies not watched in a home environment.)
[*]Salaries/wages for people who are paid to do work but are twiddling their thumbs waiting for your IT staff to fix it.
[*]Money lost because all those people are not making the money you're paying them to make.  This is different from the previous item.
[*]Cost of the building use, heat, AC, etc.
[*]Cost of broken equipment, and the length of time you can expect to pass before you could possibly fix it.
[/LIST]

[*]Is it feasible to install a solution that brings everyone up to normal working state rapidly?  How much does it cost?
[LIST=1]
[*]This includes hot spares/fail-over/cold spares/pass-through/etc as you would expect in an enterprise site.
[/LIST]

[*]What is the most feasible way to lose the least money in an outage?
[LIST=1]
[*]This includes spending a little bit more than you anticipated to get a whole lot more reliability.
[/LIST]
[/LIST]

---

