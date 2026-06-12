---
title: "Are thin clients the way forward?"
date: 2007-11-30
forum: The Cafe
---

### Post by ukripper on 2007-11-30
Was browsing through and stumbled upon this eye catching news on dumb terminals. What you guys think would this be our future rather than having thick clients in companies and schools. 

Thin clients the way forward?

[http://news.bbc.co.uk/1/hi/technology/7115538.stm](http://news.bbc.co.uk/1/hi/technology/7115538.stm)

---

### Post by n3tfury on 2007-11-30
> **ukripper said:**
> Was browsing through and stumbled upon this eye catching news on dumb terminals. What you guys think would this be our future rather than having thick clients in companies and schools. 

Thin clients the way forward?

[http://news.bbc.co.uk/1/hi/technology/7115538.stm](http://news.bbc.co.uk/1/hi/technology/7115538.stm)

eye catching news?  you realize that thin client tech has been around awhile right?  it REALLY depends on what the client needs to accomplish, but there are alot of uses for thin client tech that smaller companies don't embrace for one reason or another.

---

### Post by ukripper on 2007-11-30
> **n3tfury said:**
> eye catching news?  you realize that thin client tech has been around awhile right?  it REALLY depends on what the client needs to accomplish, but there are alot of uses for thin client tech that smaller companies don't embrace for one reason or another.

That is why I put it for schools and companies only.

i very much understand concept of thin clients as  I develop database apps for thin clients too that is why I thought it ll be good idea to get some feedback from community and perhaps put my development time towards thin clients bit more. It is eye catching for me, might not be for you!

---

### Post by loell on 2007-11-30
i believe it is when it comes to multiple workstations.

---

### Post by ukripper on 2007-11-30
i personally think the way machines are getting powerful day by day (currently quad core comes under affordable range to average being in uk) -dumb terminals  can really take benefit of such powerful network, given that we have good switches to cope up with request/response on gigabit network connecting to this server. Days are not far when soon 16 cores with multiple CPUs will be available to force off the current trend on standalone machines/servers  in business environment-just my personal opinion.

---

### Post by Tundro Walker on 2007-12-01
For most companies, it will come down to a cost-benefit analysis.

Google as well as all the various "folding" / "seti" projects have shown that distributed computing, using multiple desktops to act like a larger monolithic server, is a viable option.

So, for instance, most companies have a call center environment, where folks are pretty much just answering the phone, and using the computer to retrieve customer info to fulfill sales or customer service inquiries.  You could see two options with that...

1) give all those folks a cheap thin-client, maybe to the tune of $200 each, which has just enough horse-power to do whatever is needed by the employee for their job role.

2) give them a full-blown $1000-2000 desktop, but "handicap" it so they can only use it for their job role, which uses little of the comp's full potential, and the rest of the CPU cycles and memory get pooled into the company's distributed computing system, letting their comp act as a small part of a much larger processing network.

I personally like model #2, because (while I'm not an expert) it seems like a lot of companies still go the route of giving every employee a full blown desktop computer (although some are old and slow or have little RAM).  So, why not go the extra mile and just beef up those machines a bit and let them replace some of the monolithic uber-servers?  With RAID technology and such floating around, it seems like a little bit of all the network data could be redundantly stored across all the comps in the distributed system, so if one person's comp goes down, you don't lose anything.

All those folks in the call center can still do their job, but when some process starts up that needs a lot of horsepower, it could farm off to any comp's on the distributed network that have resources available.

I'm pretty sure I'm making this sound easier than it really is.  It just seems that the whole Folding@Home and Google search engine which both rely on lots and lots of worker bee comp's which ultimately out-process several huge super-comps seems to be very effective.

I think what might make idea #2 more attractive is when companies can actually get paid to "rent out" their unused CPU resources.  EG: it would be like Folding@Home, except you get paid for how much you process instead of doing it for free.  

In that respect, a company using #2 option could get a dual benefit...

1) they'd have a bunch of desktops (1 per employee or so) which would all be part of its own distributed comp network, circumventing the need for some huge servers here and there, and being able to expand or contract by just adding more desktops to the network.

2) if the company is currently not maxing out the resources of its distributed network, they could lease the unused resources to a data-grinding company and get paid for it.

This all hinges on how much a data-grinding company would be willing to pay.  If you can't even re-coup the cost of leaving your computer on all night by allowing them to use it, then it won't be worth it.  But, if you can make a decent profit, it might get more companies at least interested in the idea.  It obviously won't be boat-loads of money.  I mean, if the data-grinding company was going to hand out tons of cash for the unused resources, why don't they just buy a warehouse and tons of comps for themselves instead?  No, they'll hand out a modest amount of money, and most likely work up contracts, where large companies that have tons of resources can perhaps get paid a bit more than smaller companies that have less (and perhaps less reliable) resources.

It'll be interesting to see this concept expand further.  I'm all for having tons of worker bee/ants rather than uber-servers.

Anyone care to elaborate on the subject?  I'm pretty sure I only have half the details...I'm sure there's down-sides to this.

EDIT: just thought it'd be interesting to note, the human brain operates like a distributed computer network, too...a computer can process information faster than the human brain, but it has to do it in sequence (per CPU core).  We can use threading and such to make it seem like it's doing things all at once, but it's still number crunching one bit at a time in sequence.  The human brain, however, has trillions of synapses all firing in unison.  So, while they don't process as fast as a computer, the brain has a vast superiority in concurrency.  So, to get the distributed model to work, I guess it would work best with tasks that require a lot of concurrent processing.  If it's a task that requires one single thing be done before the next, I guess it won't matter how many little bees you have buzzing...only one is allowed to buzz on that task.  I think in that case, it might be good to mix the distributed network with a few uber-servers which can take on very large single processes while the little worker bees work on any small concurrency processes.

---

