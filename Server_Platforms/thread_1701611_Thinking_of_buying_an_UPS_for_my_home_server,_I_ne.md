---
title: "Thinking of buying an UPS for my home server, I need some tips"
date: 2011-03-06
forum: Server Platforms
---

### Post by gunnarflax on 2011-03-06
Hi!
I've finally gotten my home server set up as I want it and I'm also running a minecraft server on it. A week ago we had a power failure in my neighbourhood and the server went down, also ruining a level-file for the minecraft server (luckily I do regular backups). Now I want an UPS for the server so that when a power outage occurs the server will still be running (hopefully until the power comes back on).

What I really want to be able to do is that when the power for the server switches to the UPS it will turn off safely, not ruining any of the files. Is this possible? And is it possible to get it running again automatically when the power gets back on?

And I was also wondering if anyone had any tips on what to buy? :)

Thanks!

---

### Post by An Sanct on 2011-03-06
As far as I understand UPSs, they behave like a battery for a laptop, so if there is no direct electricity and the battery is weak, it sends the system to a suspended/shut down mode. (Alerts are possible via mail/SMS/...)

In Ubuntu you also have a UPS deamons (upsd or nut and maybe others)

[Setting up UPS + nut + Ubuntu server]("http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html")

The most vital thing you have to consider is the power of the UPS, now with a good server, luckily you won't have to "feed" a monitor, so that means more power for the server.

[Some basic UPS thoughts ...]("http://en.wikipedia.org/wiki/Uninterruptible_power_supply")

And remember :) P = U * I * I (power equals voltage * current square)

---

### Post by gunnarflax on 2011-03-06
Huge thanks for that walkthrough, I'm gonna need it :) do anyone got any recommendations on a UPS that works well for them and integrates well with ubuntu? I do not know if this can differ between UPS:es because I've never used one before, so it's good to know so I don't buy the wrong one and have to go through all the hassle with replacing it :)

---

### Post by An Sanct on 2011-03-07
I can't help here, I am not using an UPS (yet), but to be sure, google for these terms: "ups manufacturer" + Ubuntu, that should bring up info on users satisfaction...

Also, there is an official catalog of [Ubuntu certified hardware]("http://www.ubuntu.com/certification/catalog"), but it "young" and I haven't spotted any UPS known to me there.

---

### Post by gunnarflax on 2011-03-07
Ok, thanks, I will do some researching. I'll post what I find :)

---

### Post by SeijiSensei on 2011-03-07
I use [APCs]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007932+50001317&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=72&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=") because they're well-supported in Linux.  There's a daemon called [apcupsd]("http://packages.ubuntu.com/lucid/apcupsd") which will monitor the UPS and shut down the system gracefully if the battery runs low.  In networked arrangements, you can set up a client/server configuration where the monitoring daemon will notify the other machines that the need to shut down.

---

### Post by tyleruk on 2011-03-07
I would recommend you test your ups once you have it setup, i.e. pull the power out of it to simulate a power cut, just to ensure you have your setup correct. 

There is nothing worse than spending all this time setting up and installing your UPS just to find out it doesn&#8217;t work when you really need it to.

---

### Post by gunnarflax on 2011-03-07
Yeah, a user posted this [excellent guide]("http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html") previously and it has some great tips on configuring and setting up the server.

I think I will go with a APC UPS since so many are recommending it and I've found a good one for a great price so I will try my luck with that one :) Thanks guys, I will post my progress setting it up later on :P

---

