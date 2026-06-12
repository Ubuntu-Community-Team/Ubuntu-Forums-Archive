---
title: "How much RAM is too much?"
date: 2014-03-13
forum: System76 Support
---

### Post by craig10 on 2014-03-13
Hi there, ):P

Hopefully this question falls under the guidelines here, even though I'm not looking for support (per se) for a machine I own ... yet.

I'm looking at buying a Gazelle Professional.

SHORT VERSION of this question: Is 8 GB of RAM enough for a computer I'll still be using in 5, maybe even 10 years?

Now for more detail:

I'm one of those people that buys a new computer once every five to ten years. My current one -- on its last legs -- is ten years old. With finances looking better now than they did ten years ago I will hopefully budget to buy something new more often, but my habit has been to keep a computer going until I just can't stand how slow it has become -- because software requirements have finally overtaken its specs, not because I need to defrag or clean out my pet viruses.

So it occurs to me that I should buy something with way more RAM than is necessary initially, so that in five or ten years I won't be tearing my hair out.

But how much RAM is overkill?

First, I don't use my laptop for gaming or for high end graphics work. I do *some* graphics work, but it's primarily low resolution Web graphics when I'm fixing up a website. (I don't generally create new websites unless they're my own projects, and even then they're usually light on graphics as that's not my forte.) I find my current ten-year-old machine slows to a crawl if I open more than about a dozen tabs in Firefox. But the fact is, when I'm neck deep in researching something, I could easily open 50 tabs and have another 50 open on news websites, and then god help me if I need to open a spreadsheet. It's painful, especially as it's a work computer and I can't sit around all day while my hard drive thrashes away.

I'm sure 4 GB of RAM would beat the 1.5 I have now hands down. I would easily spring for 8 GB. But this (and other upgrades from the base model) all starts to add up, and so I ask myself, "Is 16 GB overkill? Will I thank the gods for my foresight in ten years for buying 16 gig of RAM now, or will it ultimately be a waste for me?"

I know I can theoretically buy and add more RAM later, but I did that with my current machine and, quite frankly, I'm not fully convinced that worked, as I should have seen a huge increase in performance from the 512 MB I started with, but I didn't. Plus, there's no guarantee there will be the right RAM readily available in a decade.

Do any of you have any thoughts on this?

Thanks very much in advance.


Craig

---

### Post by Bashing-om on 2014-03-13
craig10; Well,

IMHO -> There ain't no such thing as TOO much ram . (just a waste of resources if it is not used)
Consider:
One never really knows what tomorrow will bring or what you may be doing with your computer;
Applications are getting more and more graphically resource hungry; -not even counting now how much number crunching is done.
My old system ran 10.04 ubuntu just fine, 12.04 ubuntu -> forget about it !
What will it take in 5 years just to dock your PDA to your desk top machine ? I bet that machine best have some horse power ! Horse power means lots and lots of ram !
Look at what just the last year has produced in meeting users demands for graphics, 5 or 10 years from now, well the mind boggles just trying to contemplate what will be.

In our world, as soon as you get that new machine out of the box, it is already obsolete ! Lay your hands on the best hardware your pocket book can stand. Then maybe it will be around in a few years.

Then, relatively speaking, ram is cheap ! .. lot's of ram is good insurance !

[INDENT][INDENT]there ain't no such thing as too much ram
[/INDENT][/INDENT]

---

### Post by craig10 on 2014-03-14
Bashing-om,

I see you're a pretty prolific poster, so I appreciate your taking the time to address my "wonderings".

You make good points on both sides of the thought process (I was going to single a couple out, but then I realised I'd actually end up quoting just about every sentence), and it helps to have your input.

By the time I'm ready to hit the order button, it will indeed be the read-out on my calculator that will determine which upgrades from the base model make the cut.

Thanks again.


Craig

---

### Post by untrustytahr on 2014-03-14
FWIW, 
you give a time interval of 5 or 10 years... there's a big difference between what will exist in 5 years and what will exist in 10, so it would be difficult to tell.  I have 16 in mine and doesn't even get close to taxing it.  The only reason I went that high was because i'll run MANY vm's in a simulated network.  I honestly thought it would use more resources than it does.  A couple of good commands to know

```
free -m
```

```
vmstat 1 15
```
will give you 15 readings at one second intervals.  you can see what's going on as far as paging (swapping) in the SO SI column.

---

### Post by alfalfa55 on 2014-03-16
As the machine gets older, the price of memory goes up (hard to get) because memory is constantly changing and no one wants to be stuck with old memory that they might not be able to sell.  I bought my System 76 three years ago with 16G of memory and have not regretted the choice.

---

### Post by houstonbofh on 2014-03-23
When you buy it, fill it.  It may be more expensive later, and it WILL be a lot more trouble.  It was 3 years ago when I got my Lemur Ultra Thin.  At the time, it was maxed out with 8 gig, and a 120 gig Intel SSD.  I have replaced the SSD with a larger one, but the memory is still enough for everything I do, including a few VMs.  It is fun to see clients look at my VirtManager window when things really get going. :)

---

### Post by lostfawords on 2014-04-02
new machine policy here is max out the board at the start.  old ram is a pita to source and the only real considerations are cost and *maybe* power usage..(not too sure how significant an effect that actually is, but it would almost certainly be offset by the usage of SSDs over spinnys. (Moaaar SSDs!))

---

### Post by BBQdave on 2014-04-02
> **lostfawords said:**
> ...but it would almost certainly be offset by the usage of SSDs over spinnys.

Main notebook failed (i3 with 4GB of RAM). Popped a SSD into my secondary notebook (Lenovo T400 Thinkpad, Core 2 Duo with 2GB of RAM) - Ubuntu Unity 12.04 LTS just as smooth :) 

A SSD can definitely breathe new life into old hardware. Depending on your needs (and I am a little frugal with hardware), I picked up my second hand Lenovo for $20, added SSD for $50 (sale at Newegg) and I am off and running with a solid notebook. My uses are amateur graphics design (GIMP, Scribus) and browser and word editing use, heavily use Rhythmbox.

Not firing up VM's with this machine, but it does what I need nicely. System76 has nice machines, had my eye on a couple. A System76 default hardware configuration, most likely will get you to 5 years. Beyond that, new hardware may be a better choice for the future needs (and new software demands on resources).

---

### Post by jaylittle on 2014-04-04
I own a Gazelle Pro and I have 16 gigs of RAM.  The primary reason was that I work with virtual machines and VMWare a great deal.  16 gigs of RAM on the host comes in handy when you have two virtual machines booted that each are setup to use 4 gigs of RAM on their own ;)  Beyond that, the only time I've ever really made use of the RAM in this machine was when I was auditing a client's NT passwords the other day using Ophcrack and it loaded up a rather large (7+ gigs) set of rainbow tables completely into RAM.

---

### Post by monkeybrain20122 on 2014-04-04
Instead of buying an expensive machine and expecting it to last for 10 years, I would suggest picking up a cheap one (maybe a reburbished one) with shorter life expectancy based on more immediate considerations  and upgrade/replace when needed. Your requirement seems to be quite modest (4G of ram is plenty I would say) you can definitely fetch a  cheap machine that can meet your needs for a year or two.

No one knows what tomorrow's requirements will be. IMO using a number of cheap, not state of the art but reasonably up to date machines stretching out a long peroid is a much better strategy than investing in one expensive, state of the art machine and expecting it to last for the same peroid. What is state of the art today will soon become obsolete if you are looking at a 5-10 year span. I am certain that I will be able to buy your current state of the art machine or even a better one as a reburb in a few years with a fraction of the price. On the other hand since you have invested heavily in your (by then pretty old) machine you will be obliged to stick with it and beyond. At some point you will be posting here asking for help regarding old hardware. :)

You've already lost just by locking yourself in a situation that requires a future proof strategy, because there is no such thing. I recommend flexibility. :)

---

### Post by itendo on 2014-04-06
The company I worked for ran into an issue with machines being underpowered and if, as you mention, this is a work machine, then put a billable rate behind every interaction where your machine grinds to a halt. Frankly, a 4-12 second delay can translate into 20 poorly focused minutes of work, or a five minute break where you walk away or get absorbed in something else. It has been my experience that becoming distracted or waylaid by a machine squanders something far more precious than the cost of RAM; it squanders your focus.

---

### Post by Dlambert on 2014-04-16
Honestly, don't buy the machine maxed out. Upgrade the RAM yourself to save some money.

---

### Post by philbert on 2014-04-16
I bought my Gazelle Pro 7 July 2012  and put in 16GB.  To be sure, I don't use more than 4, most of the time. But I had I filled both slots with 4 each, I feared that I would have paid more once the speed I was using was no longer commodity. The jump from 8 to 16 is a bit pricy. But I think it is worth it. When built my built my tower in January 2008, I put in  8GB on the board, as 2GB was the max for each slot for my board. But I am still using that machine over 6 years later.

---

### Post by Newbunto on 2014-04-24
> I know I can theoretically buy and add more RAM later

You will notice though that if you buy with 8GB then that is 2x4GB, so in order to upgrade to 16GB later you can end up needing to throw away your 8GB and buy 16GB, depending on how many slots for memory the computer has and depending on what constraints exist regarding mixing and matching. If you are seriously contemplating adding more RAM later then you would need to research that.

I tend to follow your strategy too i.e. buy a reasonably high-spec computer and keep it for 7-10 years rather than replacing every 3-4 years.

If it were me, I would choose 16GB. The price difference between 8GB and 16GB for a computer than you are going to use for 10 years is just $11 per year. That will avoid the hassle of trying to upgrade the memory later (which is more of a hassle on a laptop than on a desktop).

I bought my S76 laptop a couple of years ago with 16GB.

As other posts note, if you leave it too long before adding memory then getting the old memory can be difficult.

I think the only time that it makes sense to buy more memory later is if the memory that you are choosing is bleeding edge or exotic i.e. you would be paying a premium for it now. "Dual Channel DDR3 SDRAM at 1600MHz - 8 GB" is not.

---

### Post by craig10 on 2014-04-28
Hi all,

Thanks very much for all of your comments. They were all helpful with my final decision to go with 8 GB of RAM along with the decision that I will likely upgrade closer to the five-year mark than then ten. Have had the Gazelle Professional for about a month now (actually, I think it's a month and a day) and am not even close to taxing the 8GB, but then I didn't expect to at this point. We'll see what the future brings, but I'll make plans to be prepared to upgrade my hardware more often than I have in the past.

I thought I saw a thread on here for reviews, and will post something positive about System76. I haven't asked them for post-sale support, but everything pre-sale was excellent, and I'm happy with the hardware.

Now, there is one thing I have been banging my head against the wall trying to figure out, but I'll post a new thread about that. Thanks again!


Craig

---

### Post by houstonbofh on 2014-04-28
I would recommend occasionally looking at ram upgrade pricing.  It will go down for quite a while, then it will start to go up as a new format takes over.  Buy then, as it will never be cheaper.

---

### Post by Newbunto on 2014-06-17
One other comment: If you are going to be doing any virtualisation (i.e. running multiple virtual machines on the one box) then you can go through memory very quickly and you should definitely err on the side of "more than you think you need".

---

### Post by porcini_m.2 on 2014-08-18
> **monkeybrain20122 said:**
> Instead of buying an expensive machine and expecting it to last for 10 years, I would suggest picking up a cheap one (maybe a reburbished one) with shorter life expectancy based on more immediate considerations  and upgrade/replace when needed. Your requirement seems to be quite modest (4G of ram is plenty I would say) you can definitely fetch a  cheap machine that can meet your needs for a year or two.

No one knows what tomorrow's requirements will be. IMO using a number of cheap, not state of the art but reasonably up to date machines stretching out a long peroid is a much better strategy than investing in one expensive, state of the art machine and expecting it to last for the same peroid. What is state of the art today will soon become obsolete if you are looking at a 5-10 year span. I am certain that I will be able to buy your current state of the art machine or even a better one as a reburb in a few years with a fraction of the price. On the other hand since you have invested heavily in your (by then pretty old) machine you will be obliged to stick with it and beyond. At some point you will be posting here asking for help regarding old hardware. :)

You've already lost just by locking yourself in a situation that requires a future proof strategy, because there is no such thing. I recommend flexibility. :)

The trouble with that strategy, at least with laptops, is you risk crappy build quality, so over the long run you on average out having had to tolerate relatively cheaply-made hardware.

---

