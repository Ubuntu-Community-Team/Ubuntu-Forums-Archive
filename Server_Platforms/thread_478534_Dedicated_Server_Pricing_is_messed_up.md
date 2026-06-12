---
title: "Dedicated Server Pricing is messed up"
date: 2007-06-19
forum: Server Platforms
---

### Post by Warpnow on 2007-06-19
Like... $30-$50 for a server with 256mb of ram...

Like ...$80-$120 for a server with 512

Like...$120-$200 for a server with a gig

Why is hardware what server pricing is centered around? For the price you pay, it becomes negligible in the long run. 

What we need is a server maintence place, where you build the machine...and they just host it. You pay for bandwith and a certain tier of support. Tier 1 could be basic hardware maintenance and keeping it running. Tier 2 could be OS configuration, and Tier 3 could be full support.

Why should I pay an extra $100 a month for a $50 stick of ram and a $30 HD upgrade? I end up paying thousands extra for those less than $100 upgrades. Even cpu upgrades are aren't that expneisve and are neglibile in alot uses. Any decently powerful cpu can run a webserver, for instance.

---

### Post by MrHorus on 2007-06-19
> **Warpnow said:**
> Like... $30-$50 for a server with 256mb of ram...

Like ...$80-$120 for a server with 512

Like...$120-$200 for a server with a gig

Why is hardware what server pricing is centered around? For the price you pay, it becomes negligible in the long run. 



Because it's old kit that nobody really wants, that's why.

If it bothers you that much then buy your own box and arrange your own colocation deal - there are plenty of datacenters in the world.

---

### Post by Warpnow on 2007-06-19
For some reason colocation seems as expensive as dedicated server hosting. Heh.

---

### Post by MrHorus on 2007-06-19
Most likely the big boys that offer the dedicated servers are able to negotiate a nice deal from the datacentre and carrier for taking x number of cages and xMBit/s of bandwidth.

---

### Post by dysolve on 2007-06-21
I maybe in australia but I haev spoken to my isp and told them what i wanted to do( host web and email servers @ home) and they recommend that I get another adsl2+ annex M connection. @ current I have 4mbit down 1.5mbit up annex M will give me the same down but around 2.2mbit(tested) up. would cost me another phone line rental a month $30AU and the ADSL $100Au a month for 40 gig down no upload limit would also included at least 6 fixed Ip address.. I already have my dual p2 400mhz 2 gig ram server and I am aloud to charge people for the service of hosting. I think I have lined up 6 ppl who want hosting. so if I charge then $15-20 each per month(200meg + 10 e-mail addy).... you can figure out the rest... now I just have to figure out how to get the server running properly and setup the firewall.

btw I think I know the reason they charge for servers the way they do.. M work just bought two IBM rack mounts AU$30000+ (bought before i worked there) because they where told that databases need loads of ram and hard disk space . Dell also told the same to my old work ....... So I think people shop around for a new server find out it costs over 10g and poo there pants and then think .. $50 a month is cheap for an extra 512meg of ram.... but that just my thought's

---

### Post by MJN on 2007-06-22
Pricing rarely has anything to do with true costs (other than defining minimum acceptable profit margins). The price you see is simply a result of supply and demand (see [http://en.wikipedia.org/wiki/Supply_and_demand](http://en.wikipedia.org/wiki/Supply_and_demand) for further info if you're really short of sleep!).
 
Mathew

---

### Post by coastdweller on 2007-06-24
The old rule of thumb was the more performing of a machine the more resources (Bandwidth, power) it can use.

---

### Post by ixus_123 on 2007-06-24
you're paying for support mostly.

With RAM and oter parts stock needs to be held for disaster recovery. Not a problem if everyone is using dell 2850s for example but if you are using some discontinued stock - be that hard disks, RAM, mother board etc, it takes up (double) the floor space.

Costs will go up with response time - SSH goes down or another service do you want it fixed in 2 minutes or an hour?  The data centre that has the staff available and monitoring systems in place will fix it faster. More staff = more money.

For any sort of home server you're probably good to run your own server. If you want high availability, clusters, firewalls with FO or any other complex set ups then expect to be paying lots don't forget about RAID and tape backups - tens of thousands a month is not uncommon especially if you want to use a SAN.

For your email business the benefit you'll have of being hosted rather than hosting yourself is that your solution will be easier to scale. Need more bandwidth - one phone call.  More RAM, faster CPU - again just a phone call. Whole new chasis, fibre cards, mirrored set etc - all a hell of a lot easier. It may cost a lot but it should only be a small percentage of your revenue

---

