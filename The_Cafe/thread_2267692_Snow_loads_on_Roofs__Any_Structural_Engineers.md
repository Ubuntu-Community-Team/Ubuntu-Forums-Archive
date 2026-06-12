---
title: "Snow loads on Roofs | Any Structural Engineers?"
date: 2015-03-03
forum: The Cafe
---

### Post by vtpoet2 on 2015-03-03
So, I'm a builder by trade and got into a friendly discussion. Boston has gotten several feet of snow and some roofs have collapsed. I have an in-law who got unreasonably panicky about the amount of snow on his roof. Contractors down there are charging upwards of thousands of dollars to rake roofs (though not all). He doesn't/didn't have the money or couldn't find a cheaper one. So, one panicky morning he climbed onto the roof and cleared one side. The other half is a two story fall and he is mildly scared of heights.

That got me thinking. Would it have been better to leave the snow on both sides, structurally? Does having all that weight on one side introduce more troubling structural stresses? To be honest, this may be theoretical. I've never seen his roof and it may have a ridge beam. But let's say it doesn't. It's probably rafters. But what if it were a truss system? I can see it both ways, but I'd be interested to hear a structural engineer's opinion. :popcorn:

---

### Post by tgalati4 on 2015-03-03
If you know the pitch of the roof, you can calculate the side load by using some trigonometry.  Most of the load will be vertically down if the roof has a steep pitch, so the side loads will be smaller.  A few links show that most 20 lb/square foot roofs can handle about 4 feet of dry snow.  So if your in-law has 3 feet of dry snow on the roof, and there is another storm coming, I would consider clearing the entire roof.  If you have 1 foot of wet snow, then that could be 20 lbs/square foot and require clearing.  

Take some snow off of the roof and weigh it.  Make it a kid's science project and let them decide what to do.

The asymmetric loading would more critical for dynamic loading--during an earthquake, for instance.  So as long as you don't have any earthquakes, you should be OK.

[http://www.nationsroof.com/SnowLoads_2006.pdf](http://www.nationsroof.com/SnowLoads_2006.pdf)

[http://condoengineer.com/2011/02/24/how-much-does-snow-weigh/](http://condoengineer.com/2011/02/24/how-much-does-snow-weigh/)

[http://building.cdaid.org/images/Handouts/Shovel%20Roof%20Snow.pdf](http://building.cdaid.org/images/Handouts/Shovel%20Roof%20Snow.pdf)

Of course, if you in-law's house survives the winter then you will know the answer.  One test is worth a thousand expert opinions.

Sounds like a useful phone app to integrate the Metro Boston snowfall amounts and conditions (wetness) with the roof building codes by city block.  If your home is in the Red Zone, then you need to clear it.

One article said that there were 150 roof collapses, so if there is a map available of those incidents, you could use StreetView in Google Maps to get an idea of roof pitch and type versus collapse.  This would make a nice Google Summer of Code project.

---

### Post by MartyBuntu on 2015-03-03
How steep is the pitch of the roof?

---

### Post by MartyBuntu on 2015-03-03
P.S. I'm also in the building trades and I like to apply Linux and open-source solutions to problems and aspects of my business.

---

### Post by vtpoet2 on 2015-03-03
> **MartyBuntu said:**
> How steep is the pitch of the roof?

Just got home from another job site. :-) In answer to your question: I've only been to the house a couple of times, but I remember it being a shallow pitch, so prob'ly somewhere between 5/12 and 7/12? Shallow enough to stand on when removing snow.

---

### Post by vtpoet2 on 2015-03-03
Wow. That's really interesting stuff.

> **tgalati4 said:**
> If you know the pitch of the roof, you can calculate the side load by using some trigonometry.  Most of the load will be vertically down if the roof has a steep pitch, so the side loads will be smaller.

In his case, I remember it being a fairly shallow pitch, see above. In the meantime, he found a contractor who removed the snow on the other side (so it's academic at this point). At the time, I advised that it might have been better to leave the snow on both sides, rather than one (if the choice is only to remove one side or nothing); but then as I began to think about it, I could see it both ways. That's why I was curious to see if there were any Structural Engineers with opinions? At worst, it would prob'ly put extra stress on the opposite side (cleaned side) rafter and plate/bird mouth connection. So, if it's not well nailed (which it seldom is), then that might cause problems? If it's a truss, then it probably doesn't matter?

  > **tgalati4 said:**
> Sounds like a useful phone app to integrate the Metro Boston snowfall amounts and conditions (wetness) with the roof building codes by city block. 

Actually, I think it could be a very useful app, but one ought to also know whether the roof is rafters, trusses, or rafters and roof beam, and pitch, etc...

> **tgalati4 said:**
> One article said that there were 150 roof collapses, so if there is a map available of those incidents, you could use StreetView in Google Maps to get an idea of roof pitch and type versus collapse.  This would make a nice Google Summer of Code project.

Yes, it would. Would be interesting to know.

---

### Post by tgalati4 on 2015-03-03
Well, the risk of collapse due to weight from a low pitch is much, much greater than asymmetric loading from only one side being cleared.  Yes, without hurricane tie plates holding the roof rafters down (required in Florida), nails can easily pull out with dynamic loading such as strong winds or shaking in an earthquake.

You want to know the roof construction:  2x6 or 2x8 rafters, 16" or 24" on center, 1/2" sheeting, 3/4" sheeting?  Then look up in the handbooks what that type of construction is rated to:  20 lbs/sqft, 30 lbs/sqft, 40 lbs/sqft.  Then estimate the roofing:  1 layer of shingles, 2 layers of shingles, 3 layers of shingles?  Most buidling codes will allow up to 3 layers of shingles, but not to exceed 10 lbs/sqft.  The 50-year shingles I put on my house 2 years ago weighed 330 lbs per square (10ft x 10ft) so that is 3.3 lbs/sqft.  40-year shingles typically weigh 2.4 lbs/sqft.  

Estimate the quality of the snow, wet, very wet, or dry, then add the weight of the snow with the roofing type to calculate the total roof load.  If you are near the design load, then it's time to clear the roof--right away!

---

### Post by vtpoet2 on 2015-03-04
So you would argue that it's better to clear the snow on one side. I can see it that way, but earlier this morning I did some hard core Googling Check this out:

[http://engineernh.com/homeowners/snow-choices-hazards-unbalanced-loading/](http://engineernh.com/homeowners/snow-choices-hazards-unbalanced-loading/)

This was written by a professional engineer. Here's the nub of what she has to say:

"We agree that unbalanced loading can be a significant issue and lead to  breakage, leaning, and/or collapse.  This is particularly true if the  home is old and constructed as post and beam, a newer home that already  has unbalanced roof loading by configuration (e.g., New England Cape),  poor fastening of roof framing, undersized framing, and/or added  appurtenances (e.g., solar panels)."

This appears to confirm my first suspicion. My in-law's house is an old house with a shallow pitch and probably built with rafters and no ridge beam.

And [here's]("http://www.structuremag.org/wp-content/uploads/2014/09/C-CSSnowDec06p10-111.pdf") an article describing how to calculate unbalanced snow loads -- a bit above my pay grade, but something for an app possibly. And here's a brief paragraph from [here]("http://www.proflossadjuster.com/blog/bid/57562/Finding-Nemo-Avoiding-Snow-Load-Collapse"):

"Unbalanced snow load from drifting and sliding snow. When snow  accumulates at different depths in different locations on a roof, it  results in high and concentrated snow loads that can potentially  overload the roof structure."

So, right now, I'm thinking that it's better to avoid an unbalanced load, given a shallow pitch and older roof (if there are known un-knowns, if you know what I mean). Interesting stuff.

---

### Post by tgalati4 on 2015-03-04
I grew up in New Hampshire, so I had my share of shoveling snow off of the roof.  If a roof is old, then it needs to be de-rated from it's new construction design loading.  A 20 lb/sq ft roof may now only support 10 lbs/sq ft.  The article also highlights how asymmetric loading can cause collapse during a dynamic event, like a wind storm.  Put some tie plates in the attic to hold the peak together and tie the roof rafters to the top plate and that should help with asymmetric snow loads as well as dynamic loads like Nor'Easters.

---

### Post by HermanAB on 2015-03-05
First of all, use a safety harness.  Secondly, he need not clear everything right up to the edge.

---

