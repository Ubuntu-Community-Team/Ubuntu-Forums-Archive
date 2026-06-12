---
title: "Cool $90 tiny PC"
date: 2007-12-01
forum: The Cafe
---

### Post by Mateo on 2007-12-01
[http://www.norhtec.com/products/index.html](http://www.norhtec.com/products/index.html)

I like the first one, the MicroClient JrSX.  The only thing is that it says it can't run OSes that require "floating point support", what is that exactly?

I guess you'd have to put PuppyLinux or DSL on the compactFlash disc to run... still this could be cool to have.  I might think about a possible set up in my living room to hook this bad boy up to my TV.  Then I could buy a wireless keyboard/mouse and compute from my couch.  Laziness rocks.

---

### Post by n3tfury on 2007-12-01
that would look like *** on your tv.

---

### Post by Mateo on 2007-12-01
why do you say that?

---

### Post by n3tfury on 2007-12-01
something that small is unlikely to support a decent resolution for your set.  stick with a 17" monitor.

---

### Post by murt on 2007-12-01
That is not true, just look at the mac mini.

---

### Post by n3tfury on 2007-12-01
> **murt said:**
> That is not true, just look at the mac mini.

you're going to compare a $400 device to a <$100 one?  do you REALLY expect to get decent video quality out of it?

---

### Post by Mateo on 2007-12-01
Spec page says its VGA is: XGI Z9S with 32MB DDR2.

I don't know what that means as far as resolution.  I'd be happy if it could do 800x600.

---

### Post by n3tfury on 2007-12-01
i'm sure it could probably do that, but on your tv which (typically) is quite a bit bigger than your monitor, it will be hard to look at.  buy it and try it though or maybe use the pc you have now and hook it up to your current set and see if you'd like it.

---

### Post by mellowd on 2007-12-01
Floating points are pretty essential. They are the "fractions" floating points meaning the point could float from say 100.00 to 10.000 and so on. Floating points support a much larger number bse than regular numbers.

---

### Post by Mateo on 2007-12-01
hmm, would simply hooking up my current PC and setting the resolution to 800x600 be an anagulous test?

That's the only scenario where I would consider buying this thing.  if I need a monitor it sort of defeats the purpose of getting it (cost, portability).

By the way, there's another similar computer (different company) that's a bit more expensive but can run on solar panels and has a 10" inch monitor.  It's pretty cool as well, but at that price you might as well get the Eee PC.

By the way, no one answered what "floating point support" is... anyone know?

---

### Post by Mateo on 2007-12-01
> **mellowd said:**
> Floating points are pretty essential. They are the "fractions" floating points meaning the point could float from say 100.00 to 10.000 and so on. Floating points support a much larger number bse than regular numbers.

ahh, ok, I'm vaguely familar with this from databases.  However, I don't understand what this means in terms of hardware... hardware determines what types of math problems you can do?

---

### Post by mellowd on 2007-12-01
I just did

---

### Post by mellowd on 2007-12-01
> **Mateo said:**
> ahh, ok, I'm vaguely familar with this from databases.  However, I don't understand what this means in terms of hardware... hardware determines what types of math problems you can do?

It will be up to the CPU, as it's this which does the calculations

---

### Post by mellowd on 2007-12-01
> 486SX compatible processor (no floating point)

I haven't heard that name in years

---

### Post by teet on 2007-12-01
I bet they could make a killing on computers like this if they could make them run mythfrontend.  Most of the "mac-mini-esque" machines I have seen thus far have been like $400 or something.  That's way too much, considering that's about what I payed to build my main mythbackend box.

-teet

---

### Post by Mateo on 2007-12-01
It only has VGA-out, so even if the hardware could run a DSL/mythfrontend set-up (which I doubt it could) you'd have no good way of hooking it up to your tv or sound systems.

---

### Post by wieman01 on 2007-12-01
> 486SX compatible processor (no floating point)
My god... it won't be of any use if the really use an old 486SX processor. What could you do with it nowaways? It's no good for any application I could think of including video streaming and office suites. I looks quite nice though.

---

### Post by quinnten83 on 2007-12-01
> **mellowd said:**
> Floating points are pretty essential. They are the "fractions" floating points meaning the point could float from say 100.00 to 10.000 and so on. Floating points support a much larger number bse than regular numbers.

And now in English (or newbs!)

---

### Post by mellowd on 2007-12-01
> **quinnten83 said:**
> And now in English (or newbs!)

It's kind of hard to describe. You can get an in-depth example here: [http://en.wikipedia.org/wiki/Floating_point](http://en.wikipedia.org/wiki/Floating_point)



Thing is, modern OS's and software use floating point operations heavily, especially things like 3D graphics. Granted you won't be running Quake on this box, but as far as I know all current OS's use floating points. (I could be wrong, I really have no idea)

---

### Post by quinnten83 on 2007-12-01
> **mellowd said:**
> It's kind of hard to describe. You can get an in-depth example here: [http://en.wikipedia.org/wiki/Floating_point](http://en.wikipedia.org/wiki/Floating_point)



Thing is, modern OS's and software use floating point operations heavily, especially things like 3D graphics. Granted you won't be running Quake on this box, but as far as I know all current OS's use floating points. (I could be wrong, I really have no idea)

Dude that link is great,
Thanks to you guys I learn something new everyday.

---

### Post by popch on 2007-12-01
> **quinnten83 said:**
> And now in English (or newbs!)

Once upon a time, computers and most especially their processors were much simpler than those you can buy and use today.

For quite some time, the arithmetic done by the processors was restricted to 'integer' numbers. Integer numbers are 0, 1, 2 etc as well as -1, -2 and so on. Depending on the kind of processor the range of numbers they could process were about +/-32767 for 16-bit processors and +/-2147483647 for 32-bit processors. The processors did not 'process' numbers such as 3.12 or 3.12E-4, i. e. ***Floating Point Numbers***. Every program which had to use and produce this kinds of numbers had to use special software which performed those 'higher' operations on the 'simpler' hardware.

In the course of time, PCs were first equipped with additional chips which could perform calculations on such numbers. The main processor of the PC had the product##  80286, 80386, 80486. The additional chip performing the floating point calculation used to be called Floating Point Co-Processor and used to have the product##  80287, 80387 and 80487. You used the 80287 with the 80286 and so on.

Later in 'ancient history' the floating point unit was incorporated into the computer's main processor chip, and the term floating point co-processor fell into disuse. So did the floating point libraries which performed those calculations in software.

Is that English enough?:)

---

### Post by mellowd on 2007-12-01
Good explanation :)

---

### Post by Mateo on 2007-12-01
so basically the processor for this thing is really, really, really old.  huh, darn.  maybe it can't run DSL after all.

---

### Post by popch on 2007-12-01
> **Mateo said:**
> so basically the processor for this thing is really, really, really old.  huh, darn.  maybe it can't run DSL after all.

They claim that there are lightwight distros of Linux and BSD which can run on that thing. They even propose some ways of using it where using Linux makes lots of sense.

Does the Slug have float point arithmetic built in?

---

### Post by Mateo on 2007-12-01
> **popch said:**
> They claim that there are lightwight distros of Linux and BSD which can run on that thing. They even propose some ways of using it where using Linux makes lots of sense.

I'm sure they're technically right.  Linux has probably been around since before floating point, so i'm sure there are versions of linux which will run it. 

But as it says on the page, it's not a general use device.  It's really for standalone applications.  I can't think of any off the top of my head though.  MAME maybe?

---

### Post by Olav on 2007-12-01
> **n3tfury said:**
> i'm sure it could probably do that, but on your tv which (typically) is quite a bit bigger than your monitor, it will be hard to look at.  buy it and try it though or maybe use the pc you have now and hook it up to your current set and see if you'd like it.

TVs may be larger but typically do **not** have higher resolutions than PC monitors.

---

### Post by Mateo on 2007-12-01
Ok, they also sell a little more expensive device:

[http://www.norhtec.com/products/mcjr/index.html](http://www.norhtec.com/products/mcjr/index.html)

The "junior" doesn't say anything about floating point so perhaps it does have it.

---

### Post by Olav on 2007-12-01
> **wieman01 said:**
> My god... it won't be of any use if the really use an old 486SX processor. What could you do with it nowaways? It's no good for any application I could think of including video streaming and office suites. I looks quite nice though.
Would make a good web server!

---

### Post by x0as on 2007-12-01
The MicroClient Jr. looks more usefull, $57 shipping though :(

---

### Post by wieman01 on 2007-12-01
Frankly I would not even think about buying one if what they say the are using is a 486SX... 

A 486SX is probably a 25 Hz processor. Modern ones are... let me think... 1 GHz at minimum? Latest models reach 3 and more? Seriously... that thing is not an option at all.

---

### Post by popch on 2007-12-01
> **x0as said:**
> , $57 shipping though :(

Only for single units. They sell them in bulk, normally.:lolflag:

---

### Post by popch on 2007-12-01
> **wieman01 said:**
> Frankly I would not even think about buying one if what they say the are using is a 486SX... 

A 486SX is probably a 25 Hz processor. Modern ones are... let me think... 1 GHz at minimum? Latest models reach 3 and more? Seriously... that thing is not an option at all.

The specs are given. I seem to remember reading something like 300MHz. The speed of the processor is roughly comparable to what you buy in a modern laser printer.

---

### Post by Erik Trybom on 2007-12-01
But... Does it run NetBSD?

(Come on guys, you know the answer to that question!)

---

### Post by Whiffle on 2007-12-01
That would be an extremely useful device for things such as data logging (think tempuratures), maybe a firewall, and probably a few other things.

For that price though, I'd pick up something off of ebay or one of those $59 via development boards off of ClubIT.  Or an old laptop... I'm currently working on setting up a 166 MHz compaq laptop as a remote tempurature/humidity logging device.  Wee...

---

### Post by Mateo on 2007-12-01
Here's a guy who installed Debian on the Junior model:

[http://nicolas314.wordpress.com/norhtec-microclient-jr/](http://nicolas314.wordpress.com/norhtec-microclient-jr/)

---

### Post by mellowd on 2007-12-01
Would be useful as a tiny torrent box

---

### Post by n3tfury on 2007-12-01
> **Olav said:**
> TVs may be larger but typically do **not** have higher resolutions than PC monitors.

and where exactly did i say they did?  please point that out, kthx.

---

### Post by Warpnow on 2007-12-01
looks like a much worse version of the fit pc.

VGA resohelution will look fine on a tv...its the ability for the cpu to process fast enough that's the problem.

---

### Post by mips on 2007-12-01
> **Mateo said:**
> MAME maybe?

I doubt it.

---

### Post by popch on 2007-12-01
> **Olav said:**
> TVs may be larger but typically do **not** have higher resolutions than PC monitors.

> **n3tfury said:**
> and where exactly did i say they did?  please point that out, kthx.

How are we to understand, then:

> **n3tfury said:**
> something that small is unlikely to support a decent resolution for your set. stick with a 17" monitor.

Not nitpicking, just asking for information which you appear to be having and I do not.

---

### Post by n3tfury on 2007-12-01
when i've tried using a lower end vid card with a 32"+ teli, it looks like total crap.  on my 47" i'm not even going to bother.

---

### Post by Olav on 2007-12-01
> **popch said:**
> How are we to understand, then:

> something that small is unlikely to support a decent resolution for your set. stick with a 17" monitor.
Not nitpicking, just asking for information which you appear to be having and I do not.
I also wonder. A common 17" monitor will have an optimal resolution of either 800x600 or 1024x768. Higher resolutions may be possible, but text and icons will be very difficult to see for average users. A TV set has 768x576 (PAL) or 720x480 (NTSC). That should be well within the capabilities of even very modest SVGA cards, that are typically able to do 1024x768. Full resolution HDTV may be too much to ask, but such TV hardware should be able to interpolate a smaller input image nicely to the entire screen.

---

### Post by mellowd on 2007-12-01
I'm quite interested in getting the MicroClient Jr and set it up as a torrent box. Anyone done this yet? This thing only uses 8watts at load!

---

### Post by Tundro Walker on 2007-12-01
Things like this are usually used as thin-clients in a corporate environment.  Things like call centers, where you don't want folks having a full-blown comp that they can screw with, surf the net etc.  Let the server do all the grinding and just spoon-feed the visuals to the user for their input...that's all this is really designed for.

Well, some folks have taken them and created mini web-appliance comps with them, too.  I think there was another thread regarding a small Mini-8 (?) based comp like this that was a silent-running box which had no storage.  It had quite a few USB ports, so you'd toss a USB on it with your distro, a USB for storage (like for your home directory), and a wireless USB for your keyboard/mouse.  Had a connector for the monitor.  The idea was to use a quick-booting distro to fire up in like 10 seconds so you could just surf the net or use it as an email machine.  The folks at DSL offer their own version of comps like this, optimized to run DSL and do it fanless.  But the other one I remember was tailored for Puppy Linux.  The DSL folks are trying to sell theirs for like $300-400, but they have like an 800mhz processor in it (a bit more robust).  The Puppy Linux one was like $120 or so.

I've been toying with the idea of trying something like this out just to have a quickie fanless comp to surf with.  But, like someone else said, for these prices, you can just get an old laptop and toss X/K/Ubuntu on it, strip it down a bit and you'd have a portable, fanless comp just as easily.

---

### Post by Mateo on 2007-12-02
I did some research and this appears to be the same as the ebox 2300.

[http://www.embeddedpc.net/eBox2300/tabid/110/Default.aspx](http://www.embeddedpc.net/eBox2300/tabid/110/Default.aspx)

I'm seriously considering getting one of these to use as a web surfer in my bedroom.  It was look really nice having this tiny thing taking up no space on my desk.  My question for the hardware experts is whether 200 Mhz Vortex86 and 128 SDRAM is enough power to play a DVD (video)?

---

### Post by master_kernel on 2007-12-02
> **Mateo said:**
> I did some research and this appears to be the same as the ebox 2300.

[http://www.embeddedpc.net/eBox2300/tabid/110/Default.aspx](http://www.embeddedpc.net/eBox2300/tabid/110/Default.aspx)

I'm seriously considering getting one of these to use as a web surfer in my bedroom.  It was look really nice having this tiny thing taking up no space on my desk.  My question for the hardware experts is whether 200 Mhz Vortex86 and 128 SDRAM is enough power to play a DVD (video)?
Not really; especially for the graphics. It would melt before you got the DVD started.

---

### Post by gn2 on 2007-12-02
> **n3tfury said:**
> when i've tried using a lower end vid card with a 32"+ teli, it looks like total crap.  on my 47" i'm not even going to bother.

It all depends on what type of TV is being used.

A modern LCD TV has a far higher resolution than a conventional CRT TV.

LCD TV's don't all have the same resolutions, some are 768 pixels on the vertical, others are 1080.

---

### Post by Mateo on 2007-12-02
ehh, i suspected that.  Also, it uses USB 1.1, so that only makes matters worse.  Oh well, internet-only device it is!

---

### Post by srt4play on 2007-12-02
I recently got an [aopen minipc]("http://minipc.aopen.com/Global/spec.htm") to use as a media system.

It's hooked up to a 32" HDTV via VGA.  Not as cheap at around $200 for the barebones kit but craploads more powerful.

---

### Post by n3tfury on 2007-12-02
> **gn2 said:**
> It all depends on what type of TV is being used.

A modern LCD TV has a far higher resolution than a conventional CRT TV.

LCD TV's don't all have the same resolutions, some are 768 pixels on the vertical, others are 1080.

not everyone has an LCD for a main TV display.  also, good luck on finding something cheap for VGA>component.  from what i recall, that's not something you can do via cable only.

---

### Post by popch on 2007-12-02
> **n3tfury said:**
> not everyone has an LCD for a main TV display.  also, good luck on finding something cheap for VGA>component.  from what i recall, that's not something you can do via cable only.

Unless your TV has an RGB input, in which case it could be conceivable that the pinout and the signals on the VGA can be made to fit the TV's expectations.

---

### Post by n3tfury on 2007-12-02
> **popch said:**
> Unless your TV has an RGB input, in which case it could be conceivable that the pinout and the signals on the VGA can be made to fit the TV's expectations.

not sure about that. try finding a vga>component converter.  from what i understand, it's not as simple as just a cable.  

good luck anyway.

---

### Post by mips on 2007-12-03
> **n3tfury said:**
> try finding a vga>component converter.  from what i understand, it's not as simple as just a cable.  

good luck anyway.


Correct, not as simple as just finding a cable. Video conversion can be complex at times.

---

