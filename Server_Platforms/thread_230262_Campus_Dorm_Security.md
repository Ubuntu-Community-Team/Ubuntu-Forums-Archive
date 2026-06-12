---
title: "Campus Dorm Security"
date: 2006-08-05
forum: Server Platforms
---

### Post by Twister594 on 2006-08-05
Hi guys!

I'm a user of Windows, OS X, and Ubuntu - each installed on a dedicated machine.  I'm going off to University this month and I would like suggestions for an unbloated Ubuntu firewall.

I'm used to having my wireless router at home, which I use as a distribution of the cable internet but also very important as a hardware firewall - I have not ran a software firewall in years.  By the way, I would just use my own router in the dorm, but my university prohibits this.

So being plugged right into the middle of an idiot fest of viruses , haxorz, and script kiddies - what can protect my wonderful ubuntu from the bad guys?

Also, if there are any other security suggestions, or even suggestions for a good Windows firewall, please post those as well.

Thanks!

---

### Post by Jagot on 2006-08-05
Ubuntu comes with it's own very secure firewall in the form of iptables.  You can read more about configuring it here:

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

You can also download a package called Firestarter which provides easy configuration of iptables.

---

### Post by slimdog360 on 2006-08-06
also you should use the Noscript and Adblock extenstions for firefox. Also there there another frontend for iptables called guarddog, I prefer it over firestarter, but I couldnt image that there is much difference between the two. 
Maybe just try different ones and see what you prefer.

---

### Post by John.Michael.Kane on 2006-08-06
You can also build your own using one of these ipcop/monowall/pfense/smoothwall

---

### Post by jreid08 on 2006-08-23
> **Twister594 said:**
> By the way, I would just use my own router in the dorm, but my university prohibits this.

This is the dumbest policy I've ever heard of.  In fact I have a hard time believing it.:confused: 

If this is true I'd ignore it and use a router anyway.  Just turn off the wireless broadcast and keep the router in a desk drawer or behind your desk.:-\"

---

### Post by gruepig on 2006-08-24
> **jreid08 said:**
> This is the dumbest policy I've ever heard of.  In fact I have a hard time believing it.:confused: 

If this is true I'd ignore it and use a router anyway.  Just turn off the wireless broadcast and keep the router in a desk drawer or behind your desk.:-\"

It's not so hard to believe and actually not that dumb of a policy.  You and the original poster may know what you are doing with a router, but many of his/her classmates likely do not, and a router that's not set up properly (plugged in backwards, misconfigured, handing out dhcp addresses to all other machines on the same segment, has buggy firmware, causing routing protocol problems, etc.) can cause problems for others on the network.  Banning routers probably saves residential students (and the IT staff!) a few outages and headaches.  Also, depending on the uni's policy, students may be authorized to use their network, but not authorized to allow other people/computers to use it.

(But then all policies are at least somewhat dumb if they can't allow for exceptions.)

---

### Post by jreid08 on 2006-08-25
> **gruepig said:**
> It's not so hard to believe and actually not that dumb of a policy.  You and the original poster may know what you are doing with a router, but many of his/her classmates likely do not, and a router that's not set up properly (plugged in backwards, misconfigured, handing out dhcp addresses to all other machines on the same segment, has buggy firmware, causing routing protocol problems, etc.) can cause problems for others on the network.  Banning routers probably saves residential students (and the IT staff!) a few outages and headaches.  Also, depending on the uni's policy, students may be authorized to use their network, but not authorized to allow other people/computers to use it.

(But then all policies are at least somewhat dumb if they can't allow for exceptions.)

Hey, we're talking about consumer grade routers - easier than a VCR.  I emailed my Alma when I posted here and they told me they don't have a policy like that.  Anyway, I was a non-trad former Army when I went to college.  Since I wasn't a green high school grad I had a tendancy to to stick up for myself and be outspoken when it came to the powers that were at the time.

If I were going to college now, I'd run IPCop and use a switch or hub - they wouldn't be able to ding you for using a router!:cool:   IPCop can be a little tricky to set up - took me a little over a week to figure it out but if you have some "more" technical friends in the dorm - they can help speed up the process.  All you need is an old PC.  I got mine from a garage sale for $15.00.  The software is free and can be downloaded from [http://ipcop.org/](http://ipcop.org/).  You'll need at least 2 nic cards - go cheap, I'm using 3 D-Link card from newegg.com, I think I paid $8 or $9 each for them.  Go with a cheap hub too from the same place, you can pick one up for about $15 to $20.  You'll need a hub or a switch because you can't go nic to nic.

Good luck!

---

### Post by helmet on 2006-08-25
> **jreid08 said:**
> HYou'll need a hub or a switch because you can't go nic to nic.

Good luck!

sure you can....crossover cable

---

