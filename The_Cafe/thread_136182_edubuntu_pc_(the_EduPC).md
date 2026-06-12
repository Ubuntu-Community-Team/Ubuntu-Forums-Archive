---
title: "edubuntu pc (the EduPC)"
date: 2006-02-25
forum: The Cafe
---

### Post by glug101 on 2006-02-25
I have an idea for a project that I will be working in my garage on.  The EduPC.  The idea is to make a system that is inexpensive, small, versital, runs edubuntu with little or NO configuration by the end user, can be locked down by parents to keep their children from accessing questionable content, and has low power consumption and heat generation.

Specs for the EduPC (speculative):
1gig VIA C3 processor
4 USB 2.0 connectors
1 firewire 400 connection
~60 gig hard drive (or whatever can be gotten cheaply)
512 MB Ram
Choice of slot loading optical media (cd, cdrw/dvd, dvdrw, none)
Choice of case (cheap standard itx case, or I am designing a wooden case)

    I look at it right now as a hobby that can be much more AND as a way to give back to the linux community a small portion of what I have gotten by finding new users.  The setup is also flexible enough that it would be ideal for diskless clients on an ltsp boot, which I would like to support later if there is anybody that is interested in it.  
    So that is my idea.  Any constructive comments or tweaks are appreciated, and I would like to know your opinions of the slot loading drives.  They are more expensive, but I figure children will break the trays more often.  The price that I am looking at currently is low enough that $30 cheaper is significant, so I am also looking for ways to make a less expensive device, but still leave it durable enough.

---

### Post by xequence on 2006-02-25
> 1gig VIA C3 processor

You mean 1Ghz =P

---

### Post by majikstreet on 2006-02-25
sounds cool :D

---

### Post by Iandefor on 2006-02-25
Price estimates?

---

### Post by WildTangent on 2006-02-25
Mini-ITX tends to get quite expensive to build actually, have you checked out the prices on some of those things? You'd be better off geting with a bigger solution using an AMD Sempron.

-Wild

---

### Post by glug101 on 2006-02-25
Sadly, the min-itx stuff is a bit over what I was hoping for.  ~$300-$500 US (depending on options), and $300 is admitedly optimistic.  However, if I go with the larger form factor, I would lose some appearance points, and the low power consumption.  The motherboards that I'm looking at are only ~$140-$170, including processor, video, sound, ethernet, and the better ones have pcmcia and compact flash.  The real price seems to come in getting low profile ram, and slimline optical devices.
    I've priced some of it, and I'm not overly happy with everything.  I'm still in the planning stages with this, and I plan on actually asking some friends of mine that fall in the target audience what features they would like.  Thanks for the constructive comments all.
    Would anybody know of an atx, or mini-atx case that would work well for this? (sturdy, small, professional looking, inexpensive?)  Most of the cheap cases I find look ugly as hell to me and unproffesional.  There is a mini-atx motherboard that is also VIA C3 on pricewatch for <$100.  Listed as a 2000+ processor (whatever that might mean).  Might do the job...

---

### Post by Leo_01 on 2006-02-26
drop the 60 gb hd for a 20 gb one if you wanna save cost..
drop the 512 ram too... 256 mb of ram runs nicely.
why don't you drop me a e-mail or something i got some really nice idea for it.
my contacts are in the sig.
Really hope this idea takes off...
It is so much better then the hand-cranked laptop.

---

### Post by commodore on 2006-02-26
I think 20gb is not enough, but I don't now crap about what people need.

I think the parents aren't very smart either. It would be great if someone would write a manual for them to protect their kids and use the computer. I could help you with the design.

---

### Post by majikstreet on 2006-02-26
[QUOTE=commodore]I think 20gb is not enough, but I don't now crap about what people need.

I think the parents aren't very smart either. It would be great if someone would write a manual for them to protect their kids and use the computer. I could help you with the design.[/QUOTE]
umm.. what's there to protect?

---

### Post by Iandefor on 2006-02-26
[quote=glug101]Sadly, the min-itx stuff is a bit over what I was hoping for. ~$300-$500 US (depending on options), and $300 is admitedly optimistic. However, if I go with the larger form factor, I would lose some appearance points, and the low power consumption. The motherboards that I'm looking at are only ~$140-$170, including processor, video, sound, ethernet, and the better ones have pcmcia and compact flash. The real price seems to come in getting low profile ram, and slimline optical devices.
 I've priced some of it, and I'm not overly happy with everything. I'm still in the planning stages with this, and I plan on actually asking some friends of mine that fall in the target audience what features they would like. Thanks for the constructive comments all.
Would anybody know of an atx, or mini-atx case that would work well for this? (sturdy, small, professional looking, inexpensive?) Most of the cheap cases I find look ugly as hell to me and unproffesional. There is a mini-atx motherboard that is also VIA C3 on pricewatch for <$100. Listed as a 2000+ processor (whatever that might mean). Might do the job...[/quote] 

A really good Mini-ATX chassis is the Foxconn TLM-487. It ran me about $30, and is really great. It looks good (at least to me), is cheaper than dirt, and works excellently for such a cheap chassis. Using it brought the cost of my computer down to about $350.

Newegg product page:
[http://www.newegg.com/Product/Product.asp?Item=N82E16811153036](http://www.newegg.com/Product/Product.asp?Item=N82E16811153036)

---

### Post by glug101 on 2006-02-26
[QUOTE=Leo_01]drop the 60 gb hd for a 20 gb one if you wanna save cost..
drop the 512 ram too... 256 mb of ram runs nicely.
why don't you drop me a e-mail or something i got some really nice idea for it.
my contacts are in the sig.
Really hope this idea takes off...
It is so much better then the hand-cranked laptop.[/QUOTE]

Thanx for the suggestions Leo_01!  256 might be sufficient memory, and I will likely try both when I actually build a prototype.  My biggest fear with giving someone 256 is that I want them to have a good experience with this machine and Linux, and since I'm aiming for a low end proc, I don't want the system to go to swap much.

The hard drive I don't think I'm going to budge on.  Since a 20 gig is going for $20, and 3x the size for $40.  I'll try to drop you an email later to hear your ideas.  Thanx!

---

### Post by glug101 on 2006-02-26
[QUOTE=commodore]I think 20gb is not enough, but I don't now crap about what people need.

I think the parents aren't very smart either. It would be great if someone would write a manual for them to protect their kids and use the computer. I could help you with the design.[/QUOTE]

I am planning on having extra documentation geared toward Windoze junkies actually in the menus, giving them help with basic stuff.  Like my wife says, Linux is scary to the average person.

You are right that most parents are clueless when it comes to the internet.  An educational pamphlet (PRINTED, not electronic) could be very useful.  If you have any ideas, or would like to help with the documentation, it is very much appreciated.  

Thanx for the suggestions everyone, I'm getting a lot of good ideas.

I'm still in the process of pricing the system with mini-atx.  It's looking to be a bit cheaper, and to have a lot more power under the hood.

---

### Post by Brunellus on 2006-02-26
[QUOTE=WildTangent]Mini-ITX tends to get quite expensive to build actually, have you checked out the prices on some of those things? You'd be better off geting with a bigger solution using an AMD Sempron.

-Wild[/QUOTE]
as someone who just put a Mini-ITX together, I can concur.  The main benefits to Mini-ITX are the form factor...cost really isn't one of them.

As far as edubuntu, I'd be happier if schools & libraries picked up a firebreathing Edubuntu server, and then used that to serve up thin-clients donated by the communities.  Old PC plus $40 bootable NIC, and you're good.

---

### Post by glug101 on 2006-02-26
[QUOTE=Brunellus]as someone who just put a Mini-ITX together, I can concur.  The main benefits to Mini-ITX are the form factor...cost really isn't one of them.

As far as edubuntu, I'd be happier if schools & libraries picked up a firebreathing Edubuntu server, and then used that to serve up thin-clients donated by the communities.  Old PC plus $40 bootable NIC, and you're good.[/QUOTE]

I agree 100%.  Where I would like to go with the EduPC is into an Edubuntu server with ltsp etherboot thin clients.  That's were the real benefits of the software lie (IMHO).  About a year ago I did an (informal) price comparison between an office full of Windows boxes and one full of linux thin clients booting to ethernet on a very nice server.

Assuming a top of the line Dual Opteron server (with a half terrabyte Raid 0+1) and a windows workstation price of $500 per unit, there was a direct price advantage starting at only 10 workstations.  And that's not counting lower power requirements OR lower cooling costs in the summer.

All I have to do is find a sucker to trust me with $15,000 to $20,000 in hardware to prove it ;)

---

### Post by jgedeon on 2006-02-26
Ubuntu does it agian!  My hat goes off to those that put the Edubuntu together.  I have just installed one in a classroom this last Friday, and all I can say is that I am completely impressed.

It looks as if I have finally found the project that I would really like to become part of!  Where do I sign?

Again Great work guys!

---

### Post by jgedeon on 2006-02-26
[QUOTE=glug101]All I have to do is find a sucker to trust me with $15,000 to $20,000 in hardware to prove it ;)[/QUOTE]

I don't think it would be as hard as you think.  The classroom that I am now working with their school system spent just under $18,000 for the CMS software that they are trying to use.

---

### Post by glug101 on 2006-02-26
OK, updated EduPC specs, this time with an Athlon Proc.  I feel better with this one.  Better upgrade potential, and much faster processor.  

Asus Pundit AE3 Barebones computer  $126

Sempron 2200+ w/cooling fan and heat sync $74

512 MB of Kingston Value Ram ($50)

60 gig HD 7200 ($40)

DVD RW DL ($40)

CDRW/DVD Combo ($30)

DVD-Rom ($20)

Totals:

w/o optical = $290
w/dvdrom = $310
w/cdrw/dvd combo = $320
w/dvdrw = $330

Hoping to have this thing hammered out into a useable form (including doucmentation and the works) in time for Dapper Edubuntu release. (by which time the hardware will be obsolete again ;) )

My head hurts, I'm going to bed.

---

### Post by Iandefor on 2006-02-27
[quote=glug101]OK, updated EduPC specs, this time with an Athlon Proc.  I feel better with this one.  Better upgrade potential, and much faster processor.  

Asus Pundit AE3 Barebones computer  $126

Sempron 2200+ w/cooling fan and heat sync $74

512 MB of Kingston Value Ram ($50)

60 gig HD 7200 ($40)

DVD RW DL ($40)

CDRW/DVD Combo ($30)

DVD-Rom ($20)

Totals:

w/o optical = $290
w/dvdrom = $310
w/cdrw/dvd combo = $320
w/dvdrw = $330

Hoping to have this thing hammered out into a useable form (including doucmentation and the works) in time for Dapper Edubuntu release. (by which time the hardware will be obsolete again ;) )

My head hurts, I'm going to bed.[/quote] Corsair's Valueselect RAM is cheaper, and should work just as well. 512 MB of Valueselect on Newegg runs about $35.

---

### Post by Leo_01 on 2006-02-27
WOW!
I love the updated specs!
still a little too costly...
maybe it will be cheaper if the projects takes off and the hardware makers can sell you at a bulk price.
Why don't install ubuntu on it?
it is much better if it can be a home PC (which seems fine if it is a home PC)

---

### Post by glug101 on 2006-02-27
[QUOTE=Leo_01]WOW!
I love the updated specs!
still a little too costly...
maybe it will be cheaper if the projects takes off and the hardware makers can sell you at a bulk price.
Why don't install ubuntu on it?
it is much better if it can be a home PC (which seems fine if it is a home PC)[/QUOTE]

As for the RAM, thaks for the tip.  I wanted to go with Kingston because I've been burned by cheap ram before. (works in one computer and not the other)  Obviously, the cheapest that will work is the best option.

I plan on setting up at least one user account that will have su enabled on it and should be able to access everything even if it's turned off for the student account.  With Edubuntu installed, the system should be a fully functioning Ubuntu desktop with a few educational apps added and a some handy ways to lock it down (thanx to the edubuntu developers).  There is no reason why it couldn't be used as a full linux pc.  

As far as hardware makers giving me bulk pricing, I can only dream at this point that I will have that kind of demand.  I would LOVE to spin this off into a full time business, but I have to play it low key and be realistic.  The real advantages of this technology really do lie in the scale of it.  1 or 2 pcs running linux wouldn't save a company or individual much (if anything), but an entire office or company running linux would save a ton.

---

### Post by majikstreet on 2006-02-27
jesus christ! 18,000 dollars on a freaking CMS!?!?

anyway, I hope to see these in stores soon, I can see the full page ads!

---

### Post by glug101 on 2006-02-27
[QUOTE=majikstreet]jesus christ! 18,000 dollars on a freaking CMS!?!?

anyway, I hope to see these in stores soon, I can see the full page ads![/QUOTE]

Where might these suckers... err, I mean investors... live?

---

### Post by Leo_01 on 2006-02-28
[QUOTE=glug101]As for the RAM, thaks for the tip.  I wanted to go with Kingston because I've been burned by cheap ram before. (works in one computer and not the other)  Obviously, the cheapest that will work is the best option.

I plan on setting up at least one user account that will have su enabled on it and should be able to access everything even if it's turned off for the student account.  With Edubuntu installed, the system should be a fully functioning Ubuntu desktop with a few educational apps added and a some handy ways to lock it down (thanx to the edubuntu developers).  There is no reason why it couldn't be used as a full linux pc.  

As far as hardware makers giving me bulk pricing, I can only dream at this point that I will have that kind of demand.  I would LOVE to spin this off into a full time business, but I have to play it low key and be realistic.  The real advantages of this technology really do lie in the scale of it.  1 or 2 pcs running linux wouldn't save a company or individual much (if anything), but an entire office or company running linux would save a ton.[/QUOTE]

why don't you get the final specs ready and have a poll to check if ubuntu users want to buy it if given the chance to?

---

### Post by glug101 on 2006-02-28
[QUOTE=Leo_01]why don't you get the final specs ready and have a poll to check if ubuntu users want to buy it if given the chance to?[/QUOTE]

Capital idea Leo!  I think I might take it one step further, by including options like better hard drives or a driveless network booting version.  Ram sizes might be a good option also.  (Maybe a MythTV option?  Would be popular, but would require beefier hardware and a lot more configuration)

For the beginning I only want to have 1 basic model of the EduPC available with some basic options.  This a concession for the moment because I can only afford 1 prototype, and my wife and I will have to get creative to come up with enough to build the first few units.

What would you consider a fair charge for building the things?  10%? 15%?  I understand that Apple gets a profit somewhere in that range, so I would like to do better than them at least.  (and by better I mean cheaper ;) )

Does anybody know where to find Ubuntu logos for download?  I fired up the Gimp last night and couldn't find a 1 of them.

Here is a (very crude) prototype of the label:

---

### Post by glug101 on 2006-02-28
I'm posting a lot today, but I'm too lazy to look for this right now.  Does anybody know a good mac (or, I suppose ppc-unix) program for editing an svg image?  My last x86 pc just kicked the bucket.

---

### Post by Iandefor on 2006-02-28
As for the logo, the wiki keeps a page for logos in png and svg:

[https://wiki.ubuntu.com/Artwork/Official](https://wiki.ubuntu.com/Artwork/Official)

---

### Post by majikstreet on 2006-02-28
inkscape? (dunno if it works on mac tho)

---

### Post by eriqk on 2006-02-28
Inkscape works on 10.3 and above.

Groet, Erik

---

### Post by glug101 on 2006-02-28
I posted the final specs, and the poll can be found [here]("http://www.ubuntuforums.org/showthread.php?t=137803").  Hope everything goes well with it.  I did some guessing at the prices and I consider them an upper limit.  The final computer should be slightly cheaper than what is listed.

---

### Post by glug101 on 2006-02-28
[QUOTE=eriqk]Inkscape works on 10.3 and above.

Groet, Erik[/QUOTE]
Sweet!  I might look into it, but if there is a lot of interest in the project I might build the prototype earlier than I expected and just do development on that. (My poor powermac is a G3 350.  Plays dvds perfectly, but for many things it's depressingly slow ;) )

---

### Post by glug101 on 2006-03-02
Well, I put a poll up, but there doesn't seem to be too much action on it.  The data points seem to point to most users wanting the 512 MB RAM, the dvdrw, and Ubuntu installed.  

Personally I'm not overly surprised at the lack of interest toward it.  Most people on these forums can build their own system and cut out (me) the middle man.

Anyhow, I was curious if anybody here could think of a good open source project that might benefit from this?  I'm thinking about maybe donate $10 or so from the sale of each of these to help out a distro.  It's good plublicity, and giving money back to the community is probably the cheapest R&D in the industry;) (oh, and I'd be helping the starving programmers too;) )

I figure it would be pointless to setup a relationship with Ubuntu, seeing as how they are the pet project of an VERY wealthy man.  Edubuntu?  I looked at their site and there isn't the 'donate' link or instructions that I normally see on OSS web sites.

Any ideas?

---

### Post by mindaslab on 2007-09-11
Cool, I am trying to do the same in India. A cheap computer for Kids, whose economic background is poor. May you succeed in your effort.

---

