---
title: "Breakdown on electricity costs of running server hardware..."
date: 2009-01-01
forum: Server Platforms
---

### Post by handy on 2009-01-01
Here is a page from the FreeNAS on line help, revealing the costs of energy consumption of various components of a server:

***_[http://www.freenaskb.info/kb/?View=entry&EntryID=218](http://www.freenaskb.info/kb/?View=entry&EntryID=218)_***

---

### Post by samosamo on 2009-01-01
that was way too difficult to read

---

### Post by handy on 2009-01-02
> **samosamo said:**
> that was way too difficult to read

What was the problem?

---

### Post by MJN on 2009-01-02
The calculations are also **completely** wrong. Whoever wrote that article really doesn't have a clue.

As an example, let's take the redundant controller suggestion saving 5-10W. For the best case (10W) we calculate the annual running cost (and hence saving) as follows:

10 x 24 x 365 = 87,600 Wh

87,600 / 1000 = 87.6 kWh

87.6 x 9.95 (cents/kWh) = 871.62 cents

871.62 / 100 = **$8.72** per controller per year.

Yet the article calculates this to be **$45.50**. Bit of a difference don't you think?!

Another example, the 250W PC:

250 x 24 x 365 = 2,190,000 Wh

2,190,000 / 1000 = 2,190 kWh

2,190 x 9.95 = 21,790.5 cents

21,790.5 / 100 = **$219.91** per year

So how is keeping it off for 8 hours a day going to save **$503 **a year as claimed?! (it'll be more like $73)

The article really is a load of rubbish, which is a shame given the amount of other information available at the site which one has to suspect to be equally inaccurate.

Mathew

---

### Post by handy on 2009-01-02
I expected that this thread would attract some criticism of the educational kind. :-)

Thanks for your post.

As far as it being a load of rubbish, & tarring the whole site with the same brush is concerned:  I think you can very easily throw the baby out with the bathwater with such an attitude.

I have found extremely valuable technical help from that knowledge base.  

You must remember that the information has been made voluntarily by a variety of people, like a wiki.  What you could do, is go in there & edit the numbers & such to make it accurate.  Many people would benefit from such a positive action.

---

### Post by windependence on 2009-01-02
It depends on a lot of things. I have a full rack of servers and redundant UPS, redundant switches, etc, and my electric bill for the entire house is just $75 a month here in the winter. IMHO people get waaayyyy too excited about power consumption when most devices today are as green as ever. The press has people so screwed up about wasting power, it's easy to make people thing they consume too much. You most likely will see little difference unless you are running gaming machines and a lot of them at that.

-Tim

---

### Post by MJN on 2009-01-02
> **handy said:**
> As far as it being a load of rubbish, & tarring the whole site with the same brush is concerned:  I think you can very easily throw the baby out with the bathwater with such an attitude.True, true. It's just very worrying when you see such inaccurate information presented as fact that it makes you (me) worry what else might be right or wrong.

> What you could do, is go in there & edit the numbers & such to make it accurate.  Many people would benefit from such a positive action.I would if I knew how! I couldn't even find an easy way to contact the author.

Mathew

---

### Post by handy on 2009-01-03
> **MJN said:**
> True, true. It's just very worrying when you see such inaccurate information presented as fact that it makes you (me) worry what else might be right or wrong.

I would if I knew how! I couldn't even find an easy way to contact the author.

Mathew

Thanks for your kind offer. :-)

I will see if I can find a way in to that site, though really, your data will get so many more eyes on it in this forum.

If you could duplicate that page one way or another & post the numbers according to your calculations, here, it would do so many of us good?

In that event I shouldn't have much trouble getting  your post made sticky.

---

### Post by handy on 2009-01-03
> **windependence said:**
> 
It depends on a lot of things. I have a full rack of servers  

(I don't know what that means?) 

> **windependence said:**
> 
and redundant UPS, redundant switches, etc, and my electric bill for the entire house is just $75 a month here in the winter. IMHO people get waaayyyy too excited about power consumption when most devices today are as green as ever. The press has people so screwed up about wasting power, it's easy to make people think they consume too much. You most likely will see little difference unless you are running gaming machines and a lot of them at that.

-Tim

Sorry Tim, but I disagree with you on this one.

The total combination of what individual humans use, whether it is electricity or other power sources (I'm limiting the parameters) is the source of humanities environmental problems. 

No individual person, is the cause of the environmental degradation that shows up in the oft neglected (though hugely demonstrative) symptoms of mass animal extinction & river death.  (for example)

---

### Post by windependence on 2009-01-03
Well, that discussion is for another forum at another time. Wouldn't fit too well here I'm afraid. IMHO seriously inconveniencing oneself for benefit that is still debatable is not worth it. Of course YMMV. :)

I might add that through server virtualization, I have reduced my power consumption by over half. Much more significant, and no inconvenience on my part. My motive was of course selfish (energy bills), but that is I'm afraid the only way you will accomplish your lofty goal.

-Tim

---

### Post by MJN on 2009-01-03
> **handy said:**
> If you could duplicate that page one way or another & post the numbers according to your calculations, here, it would do so many of us good?I'm not so sure.

The author has not provided the actual power consumption of devices in many of their examples and so it would be impossible to correct those entries (instead requiring further research into average consumption of said devices) despite them all being so obviously incorrect.

Furthermore the premise in many cases is false, or at least does not take into consideration all the factors. For example, the suggestion to remove RAM appears to imply that its maximum power consumption will be immediately saved however this could instead merely lead to increased disk access, and associated power consumption, as a result of increased memory swapping.

Another example with suspect reasoning is the suggestion to replace two 250GB disks with a single 500GB drive. The calculation does not factor in the fact that the filesystem allocation would likely mean that one of these disks may not be required to be constantly active (e.g. it might just hold backups) and hence one should not expect to make as much savings compared to a disk in constant use (certainly not the $122 claimed which is frankly ridiculous).

It also suggests removing unneeded components. This sounds reasonable but then one must question whether or not removing a floppy drive would make any difference whatsoever compared to simply not using it... I strongly suspect not (and hence I think the claimed $45 saving is $45 out on this one).

All in the all the article is nothing more than inaccurate and misleading - and there is far more to power consumption, and savings, than simple calculations of maximum power rates and assumed constant usage, not least if one factors in the purchase of replacing components.

Mathew

---

### Post by handy on 2009-01-03
> **windependence said:**
> 
Well, that discussion is for another forum at another time. Wouldn't fit too well here I'm afraid.  

I agree, since the Backyard & all of the other names (& colours) Matthew gave that Ubuntu sub-forum (in vain attempts to save it) before it finally had to be put out of the mod's misery, removed the venue for such conversations. 

> **windependence said:**
> 
IMHO seriously inconveniencing oneself for benefit that is still debatable is not worth it. Of course YMMV. :) 

The simplest position against that argument is, that there is definitely much to gain, as opposed to potentially little to loose in that debate.

Would you rather be on the possibly winning side or the definitely winning side?

> **windependence said:**
>  
I might add that through server virtualization, I have reduced my power consumption by over half. Much more significant, and no inconvenience on my part. My motive was of course selfish (energy bills), but that is I'm afraid the only way you will accomplish your lofty goal.

-Tim

Why not choose to feel like you are benefiting me too?

---

### Post by handy on 2009-01-03
> **MJN said:**
> 
The author has not provided the actual power consumption of devices in many of their examples and so it would be impossible to correct those entries (instead requiring further research into average consumption of said devices) despite them all being so obviously incorrect. 

Could you give us/me the (I'm sure they are simple, but I'm a mathematical moron) equations for this stuff, I will do the best I can with them?

> **MJN said:**
> 
Furthermore the premise in many cases is false, or at least does not take into consideration all the factors. For example, the suggestion to remove RAM appears to imply that its maximum power consumption will be immediately saved however this could instead merely lead to increased disk access, and associated power consumption, as a result of increased memory swapping. 

No worries.

> **MJN said:**
> 
Another example with suspect reasoning is the suggestion to replace two 250GB disks with a single 500GB drive. The calculation does not factor in the fact that the filesystem allocation would likely mean that one of these disks may not be required to be constantly active (e.g. it might just hold backups) and hence one should not expect to make as much savings compared to a disk in constant use (certainly not the $122 claimed which is frankly ridiculous). 

I agree, the formulas for deductive purposes be great?

> **MJN said:**
> 
It also suggests removing unneeded components. This sounds reasonable but then one must question whether or not removing a floppy drive would make any difference whatsoever compared to simply not using it... I strongly suspect not (and hence I think the claimed $45 saving is $45 out on this one).

All in the all the article is nothing more than inaccurate and misleading - and there is far more to power consumption, and savings, than simple calculations of maximum power rates and assumed constant usage, not least if one factors in the purchase of replacing components.

Mathew

The formulas, if you don't want to be held responsible for the statements that they make, would be so helpful for us/me?

---

### Post by MJN on 2009-01-03
> **handy said:**
> Could you give us/me the (I'm sure they are simple, but I'm a mathematical moron) equations for this stuff, I will do the best I can with them?Sure... Let's do a walkthough:

To calculate the running costs of a device, at the most basic level, we need to know three things:

- Power consumption (measured in watts, W)
- Running time (measured in hours, h)
- Energy supplier cost (usually measured in cents per kWh)

So, for example, lets calculate the running costs of a 100W lightbulb left on for a whole year.

We start with the lightbulb power consumption, 100W, and must calculate how much energy it uses over the year. The energy usage is a function of power and time and usually expressed in kWh i.e. kW x hours.

So, for our bulb running for a year we calculate 100 x 24 (hours in a day) x 365 (days in a year) which gives us **876,000 Wh**.
We ideally want this in kWh (as that is what the energy companies charge in) so we must divide our result by 1000 i.e. 876,000 / 1000 = [B]876 kWh

[/B]If the energy company charges 9.95 cents per kWh (this is the figure used in the article and sounds reasonable) then we multiply our energy usage by this figure i.e. 876 x 9.95 = 8,716 cents or, in dollars (divide by 100), **$87.16**.

And that's it!

To summarise:

**100W** bulb, for a **year**, at **¢9.95** per kWh:

100 x 24 x 365 = 876,000 Wh
876,000 / 1000 = 876 kWh
876 x 9.95 = ¢8,716
8,716 / 100 = **$87.16**

Make sense?

This is easy for a simple lightbulb whose power consumption is known and consistent however it only serves as a rough approximation for something more complex like a PC as the power consumption at any one time varies depending on load and indeed is further effected by issues such as '[power factor](http://en.wikipedia.org/wiki/Power_factor)'. It is good enough for general comparison purposes though.

Mathew

---

### Post by handy on 2009-01-03
Thanks, I see that to extend this into computers only takes a little Scroogling, which I will do.

---

