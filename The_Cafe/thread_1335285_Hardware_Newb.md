---
title: "Hardware Newb"
date: 2009-11-23
forum: The Cafe
---

### Post by Grant A. on 2009-11-23
Hi, I'm a bit inexperienced with hardware, but after looking through the HP website, it seems that I'd be able to add in a new graphics card. My Nvidia GeForce 6600 is getting on in years, and should probably be retired to my closet. Currently, I'm looking for an NVidia card that would bring me the best gaming experience in Windows, but also be fully compatible with Linux, and under $200 USD.

Does anyone have any recommendations?


P.S. I wanted to add this to the hardware forum, but that seems dedicated to issues regarding new Ubuntu installations. Sorry if this is in the wrong forum.

---

### Post by NoaHall on 2009-11-23
9XXX series, 9800 GTX works well, and affordable. Or get a old GT 2XX card.

---

### Post by Skripka on 2009-11-23
> **Grant A. said:**
> Hi, I'm a bit inexperienced with hardware, but after looking through the HP website, it seems that I'd be able to add in a new graphics card. My Nvidia GeForce 6600 is getting on in years, and should probably be retired to my closet. Currently, I'm looking for an NVidia card that would bring me the best gaming experience in Windows, but also be fully compatible with Linux, and under $200 USD.

Does anyone have any recommendations?


P.S. I wanted to add this to the hardware forum, but that seems dedicated to issues regarding new Ubuntu installations. Sorry if this is in the wrong forum.

What is the PSU in your machine rated at?  I saw "HP" in your post, hence I presume this is a prebuilt machine.

Assuming a low-output PSU, probably one of the 9000 series is what you'll have to pick from.  The GTX series needs 2 6pin power connectors to drive them.

---

### Post by KiraLexi on 2009-11-23
I personally use a GeForce 9600 GSO. My understanding is that its a rebranded 8800 with more texture memory. Runs Crysis somewhere between High and Very High at playable framerates... I figure that's good enough.

They cost in the $60 range.

---

### Post by blueshiftoverwatch on 2009-11-23
How can this [GTX 250]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130469&cm_re=GTX_250-_-14-130-469-_-Product") have faster RAM and more of it, not to mention a faster clock speed than this [GTX 260]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127426&cm_re=MSI_GTX_260-_-14-127-426-_-Product") and cost $60 less (after rebate) to boot?

The only difference between the two cards I see is that the GTX 260 has 216 stream processor cores while the GTX 250 only has 128. What exactly is a stream processor and how does it effect the graphics card's performance?

---

### Post by Skripka on 2009-11-23
> **blueshiftoverwatch said:**
> How can this [GTX 250]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130469&cm_re=GTX_250-_-14-130-469-_-Product") have faster RAM and more of it, not to mention a faster clock speed than this [GTX 260]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127426&cm_re=MSI_GTX_260-_-14-127-426-_-Product") and cost $60 less (after rebate) to boot?

The only difference between the two cards I see is that the GTX 260 has 216 stream processor cores while the GTX 250 only has 128. What exactly is a stream processor and how does it effect the graphics card's performance?

In short, it means you have a slower card.

---

### Post by blueshiftoverwatch on 2009-11-23
> **Skripka said:**
> In short, it means you have a slower card.
Well I already knew that, how though does it contribute to the card's overall performance for various tasks?

---

### Post by &#32 Greg on 2009-11-23
> **blueshiftoverwatch said:**
> Well I already knew that, how though does it contribute to the card's overall performance for various tasks?

GPU's are like CPU's in that they have multiple cores. Except instead of having 2 or 4 cores, modern ones have hundreds.

---

### Post by Grant A. on 2009-11-23
Thanks for all of the replies, so far.


> **Skripka said:**
> What is the PSU in your machine rated at?  I saw "HP" in your post, hence I presume this is a prebuilt machine.


Yes, it is a pre-built machine. How can I check the PSU rating?

---

### Post by Skripka on 2009-11-23
> **blueshiftoverwatch said:**
> Well I already knew that, how though does it contribute to the card's overall performance for various tasks?

More info than likely you were wanting:

[http://www.tomshardware.com/reviews/geforce-gtx-260,2286.html](http://www.tomshardware.com/reviews/geforce-gtx-260,2286.html)

---

### Post by blueshiftoverwatch on 2009-11-23
> **  Greg said:**
> GPU's are like CPU's in that they have multiple cores. Except instead of having 2 or 4 cores, modern ones have hundreds.
So what does it mean if one GPU has a less cores but higher clock speed and another has a slower clock speed but more cores?

---

### Post by &#32 Greg on 2009-11-23
> **blueshiftoverwatch said:**
> So what does it mean if one GPU has a less cores but higher clock speed and another has a slower clock speed but more cores?

It depends on what the GPU is being tasked with. If for some reason you decided to use Cuda to bruteforce the factorial operation, than more cores. If only one non-parallel task, higher clock speed. I'd guess that in most situations, the 260 would perform better.

---

### Post by Skripka on 2009-11-23
> **Grant A. said:**
> 
Yes, it is a pre-built machine. How can I check the PSU rating?

Pop open the box, and look on the sides of the PSU itself--there should be a sticker somewhere-that should tell you something.

Also check what kind and how many power connectors you have coming off your PSU snake.  At a bare minimum you'll be wanting at least ONE 6pin connector, and if you want to run a GTX you'll need TWO 6pin connectors, or ONE 8pin connector.  As the number of connectors on the PSU increases so does the likely wattage.

It is unlikely that a stock PSU from a prebuilt machine will have much in the way of cajones.  It is possible though.

EDIT:  You CAN get molex connector to 6/8pin adapters...but you're tempting fate unless you know you have a strong PSU.

---

### Post by Grant A. on 2009-11-23
> **Skripka said:**
> Pop open the box, and look on the sides of the PSU itself--there should be a sticker somewhere-that should tell you something.

Also check what kind and how many power connectors you have coming off your PSU snake.  At a bare minimum you'll be wanting at least ONE 6pin connector, and if you want to run a GTX you'll need TWO 6pin connectors, or ONE 8pin connector.  As the number of connectors on the PSU increases so does the likely wattage.

It is unlikely that a stock PSU from a prebuilt machine will have much in the way of cajones.  It is possible though.

EDIT:  You CAN get molex connector to 6/8pin adapters...but you're tempting fate unless you know you have a strong PSU.

I have four (one available) of these:
[img]http://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Molex_female_connector.jpg/800px-Molex_female_connector.jpg[/img]

And I have 2 of the things in the middle:

[img]http://upload.wikimedia.org/wikipedia/commons/thumb/a/a1/Molex.JPG/800px-Molex.JPG[/img]

I can't make quite out what it says on the label, but I saw tons of different wattages. Underneath "output", though, it said "250W MAX"


Is this any good?

---

### Post by Skripka on 2009-11-23
> **Grant A. said:**
> I have four (one available) of these:

I can't make quite out what it says on the label, but I saw tons of different wattages. Underneath "output", though, it said "250W MAX"


Is this any good?

FYI-the first pic is a molex connector.

FYI(2)-from left to right, ATX (motherboard) power 20pin+4, another power connector for some HDD devices, and molex

EDIT-Usually a PSU sticker will tell you in detail what the wattages ratings are on each rail...which is quite useful info when worrying about building a system.

For comparison, Nvidia recommends at least a 500W PSU to drive their GTX cards.

What it boils down to is that you don't have much PSU to spare...and unless you either use a molex->6pin adaptor (you're pusing your luck using only one, forget about two); or get a beefier PSU...you're confined to a gfx card that is bus powered (i.e. does not need separate power inputs).  HP skimped on your PSU, and it is likely the cheapest thing in your box.

Unfortunately just about any current gen card needs at a minimum ONE 6pin connector.  I'm not certain about the low end 9000 series, so you'll have to look to be sure.

---

### Post by blueshiftoverwatch on 2009-11-23
> **  Greg said:**
> It depends on what the GPU is being tasked with. If for some reason you decided to use Cuda to bruteforce the factorial operation, than more cores. If only one non-parallel task, higher clock speed. I'd guess that in most situations, the 260 would perform better.
So for playing 3D action games the higher clock speed is preferable to more cores.

---

### Post by Grant A. on 2009-11-23
> **Skripka said:**
> FYI-the first pic is a molex connector.

FYI(2)-from left to right, ATX (motherboard) power 20pin+4, another power connector for some HDD devices, and molex

What it boils down to is that you don't have much PSU to spare...and unless you either use a molex->6pin adaptor (you're pusing your luck using only one, forget about two); or get a beefier PSU...you're confined to a gfx card that is bus powered (i.e. does not need separate power inputs).

Unfortunately just about any current gen card needs at a minimum ONE 6pin connector.

I see, thank you so far.

Is it possible to get a new PSU onto a pre-built computer? If so, how much would one cost?

---

### Post by Skripka on 2009-11-23
> **Grant A. said:**
> I see, thank you so far.

Is it possible to get a new PSU onto a pre-built computer? If so, how much would one cost?

Depends on how fancy one goes.  You can get something to get you by for now for $50-75USD...or you can get a 2000W nuclear reactor PSU for $100s of USD.

Lots of choices on NewEgg. Love the Antec units myself.  Look for 80+ certified units to keep your electric bills down.


It is quite easy to swap out PSUs

---

### Post by &#32 Greg on 2009-11-23
> **blueshiftoverwatch said:**
> So for playing 3D action games the higher clock speed is preferable to more cores.

I'm going to tentatively say no- there's a lot going on when you're playing a game. For instance, smoke might be rising; the pattern at which it does so is calculated with the PhysX engine. Don't take my word on it though- I'm no expert.

---

### Post by ciborium on 2009-11-23
[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=58&name=Power-Supplies](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=58&name=Power-Supplies)

i'd get at least 600 watts, and count the connectors.

For the most part, if you have a tower or mini tower you wont run into problems with it fitting the case, unless you see a bunch of people complaining about i in the feedback.

---

### Post by Skripka on 2009-11-23
> **ciborium said:**
> [http://www.newegg.com/Store/SubCategory.aspx?SubCategory=58&name=Power-Supplies](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=58&name=Power-Supplies)

i'd get at least 600 watts, and count the connectors.

For the most part, if you have a tower or mini tower you wont run into problems with it fitting the case, unless you see a bunch of people complaining about i in the feedback.

Yep.  Everything is keyed, and only plugs in one way.  The art comes in making it tidy for the sake of airflow.  Kittens cry themselves to sleep, if you leave you PSU cabling a rats' nest.

Unplug the old one, pull it out.  Put in the new one, and plug it in, and zip tie it.  PS-modular PSUs are far easier to keep tidy, as you only have the cabling in your box that you use, they are more coin though.

---

### Post by blueshiftoverwatch on 2009-11-23
> **  Greg said:**
> I'm going to tentatively say no- there's a lot going on when you're playing a game. For instance, smoke might be rising; the pattern at which it does so is calculated with the PhysX engine. Don't take my word on it though- I'm no expert.
I was thinking of that in terms of one game running = one process. But that defiantly sounds plausible. I guess a lot of it would also have to do with how the individual game was programmed to take advantage of a GPU.

---

### Post by Grant A. on 2009-11-24
Thank all of you very much for the help. I guess I'll go out and buy a new PSU when I go get my graphics card. :)

---

