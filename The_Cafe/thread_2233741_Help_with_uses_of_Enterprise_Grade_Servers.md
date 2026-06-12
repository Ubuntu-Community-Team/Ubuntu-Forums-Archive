---
title: "Help with uses of Enterprise Grade Servers"
date: 2014-07-10
forum: The Cafe
---

### Post by ads2996 on 2014-07-10
Hi,

I recently acquired 3 enterprise grade servers. I have 2 proliants with (2xDual Core at 2.6ghz 1Mb L2 with 32gb ram) each. I then have a blade server with (2x Quad Core at 2.66Ghz 2x6mb L2 with 4gb of ram). THe two proliants have 1tb of storage once i work out how to access it. I also have a 3tb drive box which i dont know how to connect right now. The two proliants have a full copy of windows server 2008 r2 enterprise currently.

I had the thought of running MC servers for money or something like that or source games and the such. Doing things like seti@home, while i would love to are pretty much out the window, cause i still live at home and my parents pay the bill. If i can make £39 a month that would pay for fibre optic to our house entirely which we would all benefit from. I am unsure about how much power consumption would be but i would guess about £5-10. So anything after £50 is profit at a guess.

I also considered one of them as a render farm for any video editing i do in after effects. which is rare so would be run on the side occasionally with what ever else they are doing.

Any help is greatly appreciated. Thanks in advance.

---

### Post by ads2996 on 2014-07-10
I realise that i am asking the near impossible and that it will take time to actually make any money from it, but just looking for a place to start.

---

### Post by ssam on 2014-07-10
Get yourself a watt meter (something like [https://en.wikipedia.org/wiki/Kill_A_Watt](https://en.wikipedia.org/wiki/Kill_A_Watt) ) and figure out exactly how much it will cost. Also remember that when people pay for commercial server hosting they are paying for high reliability (redundant power and networks), large amounts of bandwidth and 24-7 technicians to deal with faults. If you have a hardware failure, how long will it take you to get the server repaired or replaced.

On a more positive note. If you can use the machines to learn how to set up and administer servers then there is plenty of money to make in linux systems administration.

---

### Post by ads2996 on 2014-07-10
A kill-a-watt looks good. Probably if a part breaks then it wouldn't be replaced. But the two proliant servers are identical so could keep one as a spare. They have two power supplies (one backup) and redundant storage is also an easy option. As for redundant network, do you mean multiple connections to the internet or multiple to the router?

The more i look into this, the more i begin to realise that the best option may be just to have them on when ever i want to do something like running a minecraft server for my friends or as a renderer for after effects as my laptop is pretty slow at that and forget about the money making.

---

### Post by CharlesA on 2014-07-10
If you are serious about hosting MC and other services, you would be better off hosting it at a datacenter - high speed connections and more available bandwidth, but it's also quite expensive.

You'd be looking at colocation.

---

### Post by tgalati4 on 2014-07-10
Depending on your electric rates, those servers will burn about $200 US per year.  You can more accurately estimate it by using a Kill-a-Watt, but the bottom line is your hosted services need to bring in more than that, plus the cost of bandwidth and the cost of your time for maintenance.   High upload bandwidth could be expensive in your area, so you need to figure that in the equation.  

If you just want to load up services and experiment then your servers can be put to sleep when you are not using them and use Wake-on-Lan to wake them when you want to play around.  Leaving them on 24/7 not doing anything gets expensive and probably the reason you got them in the first place.

---

### Post by ads2996 on 2014-07-11
Thanks k you for all your help with this, I've come to the conclusion that making money from them is very limited cause of my Internet. Me and 2 of my friends may buy a dedicated server for minecraft and run two worlds one for public and one for solely us or something like that. As for my servers I'll leave for if I want to render something and for running servers for me and my friends if they are over or to try out a new mod pack or challenge maps. I would also consider using the blade with the vm ware server for trying out different ones.

---

### Post by CharlesA on 2014-07-11
That might be cheaper than doing a colo, but maybe not if you already have the hardware.

---

### Post by ads2996 on 2014-07-11
I've got the hardware alright, just don't have the Internet to cope with it. :-(

---

### Post by CharlesA on 2014-07-11
> **ads2996 said:**
> I've got the hardware alright, just don't have the Internet to cope with it. :-(

Which is why you could do [colocation]("http://en.wikipedia.org/wiki/Colocation_centre"), which might be cheaper than a dedicated server, but you can always look around for prices.

---

