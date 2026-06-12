---
title: "Help locating confusing problem? What am I missing?"
date: 2011-08-19
forum: Server Platforms
---

### Post by JackRabid on 2011-08-19
Being new to, well- more or less everything I'm trying to do here, I'm  not 100 percent sure of what the problem is and as such am reluctant to  start 'flipping switches at random'. I'm hoping someone might be able to  clue me in as I'm almost certain that this is the peak of the hill and  things will make total sense once I see it from the other side. I've  googled, forum searched, reread previous results, forum browsed... but  again... without being fairly certain I have reluctance. 

Overview: Things work some of the time but there are sporadic outages.

**Topology:**
Cable Modem -> Linksys SOHO router -> PC1, PC2 ; Linksys Hub -> Closet1, Closet2, Desk.

**As it applies:**
Modem -> Router -> Hub -> Closet1, Closet2, Desk

**Machines:** 
_Closet1_ ; Low-end machine: 10.04.02 - Apache, Webmin, MySQL...  'web server' - nothing that ever loads the system past 25%. Something  like .03 over 15 minutes.
_Closet2_ ; Low/Mid machine: 10.04.02 - Webmin, MySQL... 'app server'... When something is running it's at like 30%
_Desk_ ; Windows Daily Driver.

Closet1, Closet2 - Static local IP's. Everything else comes from the Linksys SOHO.

Dynamic IP\Name redirection - No-IP.org
[B]
Problem Details:[/B]
As mentioned above, most of the time things 'work'. But other times the  server doesn't respond and about the only thing that can be done is to  try again in 5 minutes or so.

I say about because if I'm at home I can load Webmin by the local IP to  'wake things up'. Http requests to the local IP are also served so I  know the machine isn't 'dead' or load-locked or anything...

During the outages requests to [name].no-ip.org:[RouterAdminPort] are  also served so I know it's not an external\no-ip problem...

[B]My Thoughts:
[/B]
Every time I've sat down to poke at this over the last couple of months I  keep finding myself convinced that what breaks things for me is the  'two-machine factor' and I keep looking towards /etc/hosts and  /etc/hostname... I'm sure I've missed something that somehow tells the  machine to serve requests from [name].no-ip.org, or that somehow the two  servers are confusing each other.

And while I find myself looking at /hosts and /hostname, I'm not sure of  what will\won't break things. Admin is via putty and both Closet1 and  Closet2 are headless machines in an inconvenient place that I can't get a  monitor to. Everything I've poked at down this route thus far hasn't  had the results I've expected.

Anyway, though I find myself looking at /hosts, /hostname I'm not  entirely certain that's my solution... a small part of me thinks I might  need a DNS server. More so if I add a mailserver to one of the  machines. But another part hesitates thinking that may be a nail where I  really just need a bit of glue. Through all my searching one of the  questions I've not been able to pin down is when I *NEED* my own DNS  server...


**Conclusion**:

All in all I feel the same way now as I did right before I finally *understood* how a 3-way light switch worked...

I had been wiring houses for 8 or 9 months and every time I had to pull  wire for a 3-way I would have to actually stop and think about how it  needed to run. ..."OK... um... 2-Conductor from AtoB, 2-Conductor from  BtoC, 3-Conductor from B\CtoD..."

But then one day as we were returning from lunch I spotted a switch that  had evidently fallen out of the supply box and had gotten run over as  we left. Looking it over it was pretty easy to see that it was unusable  so I set it by my 'stuff' so I would remember to get a replacement  later...

Anyway... taking a break later that afternoon I started playing with the  switch and eventually that turned into taking the switch apart, and  while that made it harder to explain to my boss when I handed it to him  later... Seeing the way it worked from the inside made it possible for  me to just pull 3-ways. No more thinking and walking through it, now I  can start at B and just pull wires wherever they need to go. Point is I  feel the same way about this... a cognitive-bottleneck if you will.

All that said I suppose the only thing left is to invite questions for things I didn't yet mention and to say...

...many thanks to anyone that can help me work through this bit of frustration.

---

### Post by volkswagner on 2011-08-19
I think you may have hit the nail on the head with DNS.

With just a few machines you can use /etc/hosts on all your local machines to map ip addresses to hostnames.

Alternative one would be to run a local DNS server.

Alternative two, would be to allow your router to act as the DNS server.  If your router has the ability to reserve an ip address for a given mac address this can replace the /etc/hosts solution.

For all your static ip machines, use the router to make the ip static with the mac/ip reserve.  You will then be able to set the /etc/network/interfaces file to DHCP for the adapter.  What this accomplishes is the router is aware of ip and hostname, so any request via hostname will be resolved at the router.

In my opinion this is the simplest, most robust solution for using hostanmes on a LAN.  Just be sure to backup your router settings, once complete, as it can be a pain to reconfigure all those ip's, port forwards, etc.

Don't rule out a hardware issue.  I had a finicky 5port switch that would loose connections intermittently.  I could get it to respond by unplugging it from the power supply for a reset.  I eventually replaced the switch, now problem is gone.

For the understanding, what happens if you your server static ip is set at the server:  If all is working well, then you reboot or restart networking service, this is where machines can become unaware.  This includes a router reset also.

---

### Post by JackRabid on 2011-09-27
That's what I was afraid of...

I came across a 64-bit desktop that I think I'm going to try running everything on after while I reconfigure the other machines after I max the memory on the new machine. See how well it acts with just one server machine and work to reconfig my setup from there.

I still hesitate to commit to any single course as my SOHO router remains a possible culprit. If the problem persists after the single-system move, I'll look into replacing the router before I move on to additional network deployment. My project has advanced well on other fronts that I may as well plan for a DNS and mail server anyway as I'll need the DNS for a component of the project...

Blah... anyway... Thanks for confirming my suspicions. Let's see how much of the new system I can get setup tomorrow.

Thanks :)

---

### Post by bab1 on 2011-09-27
> **JackRabid said:**
> That's what I was afraid of...

I came across a 64-bit desktop that I think I'm going to try running everything on after while I reconfigure the other machines after I max the memory on the new machine. See how well it acts with just one server machine and work to reconfig my setup from there.

I still hesitate to commit to any single course as my SOHO router remains a possible culprit. If the problem persists after the single-system move, I'll look into replacing the router before I move on to additional network deployment. My project has advanced well on other fronts that I may as well plan for a DNS and mail server anyway as I'll need the DNS for a component of the project...

Blah... anyway... Thanks for confirming my suspicions. Let's see how much of the new system I can get setup tomorrow.

Thanks :)

I don't see it that way at all.  It may be so, but you really haven't tested or diagnosed it (like your story of physically taking apart the switch).  All you have done is guessed.

Some questions: What dies this really mean?```
Cable Modem -> Linksys SOHO router -> [COLOR="Red"]**PC1, PC2**[/COLOR] ; Linksys Hub -> Closet1, Closet2, Desk.
```

What are the PC1 and PC2 devices?  Are they also known as Closet1 and Closet2?

Are you really using a hub (a common wire to all devices connected) or is it really a switch.  I shouldn't mater, but it might come in handy for diagnoses later if it really was a hub.  A simple first test might be to ask yourself is the hub a 10 mbps or a 100 mbps device.  Most hubs made were 10 mbps (Ethernet) while 100 mbps (Fast Ethernet) devices are switches.

I have a network that is completely configure by conf files (no DHCP at all).  Name resolution on the LAN is configured by /etc/hosts and /etc/hostname.  I have had zero failures over that last 6 years.  the failure points are multiple (each host) with eight devices.  Each host resolves LAN names of the other hosts locally to itself and if it were to fail it would not affect the other hosts capabilities.

So I have redundancy and stability.  What I don't have is ease of setup.  I have to manually configure any new host I permanently add to the network.  I do supply DHCP for guests and hand held devices, but I don't consider that cheating.  :D

The big questions don't have to do with the physical equipment.  What is the naming and IP addressing scheme (hostnames and IP addresses) for the network.

Just to be really sure; is this your question:*"Things work some of the time but there are sporadic outages."*?  What kind of error messages appear in the logs?  What doesn't work exactly?  What diagnostic testing have you done?

---

