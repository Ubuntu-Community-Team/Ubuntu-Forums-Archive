---
title: "Why the major move to webkit?"
date: 2009-08-12
forum: The Cafe
---

### Post by Jimleko211 on 2009-08-12
It seems that a lot of the major browsers (and the new browsers being developed) are going towards to webkit.  Why?  I just did a benchmark on my machine, and it took Arora (a webkit browser) over 60 seconds to render [www.cnn.com](www.cnn.com) completely.  It took Firefox(which I believe uses Gecko) 2-3 seconds.

---

### Post by Regenweald on 2009-08-12
Programmers seem to prefer it because it has a better design, is structured to follow international standards and in general is easier to code for. it also has a very large developer/testing base. Gecko is much older and kind of evolved into what is is today. Although is does render very well ( i know because Epiphany Gecko gives better performance than it's webkit twin) it seems to be very difficult to code for. Hence the exodus to webkit. programmers are future proofing their browsers.

I'm not a programmer, this is just how i understand it.

---

### Post by mrgnash on 2009-08-12
Performance-wise, I find that Google-Chrome outclasses every other browser I've come across. From my understanding, Webkit does have major advantages over Gecko, but both probably depend on how well they are actually implemented in any given browser as well.

---

### Post by gradinaruvasile on 2009-08-12
Try Chromium:

[http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/](http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/)

grab the latest build, unpack it and launch it with the --enable-plugins command line option

It took a few seconds to load that page...

---

### Post by juancarlospaco on 2009-08-12
*eLinks kick *** the rest *:)  ---->this is a joke

this is serious, and a problem:
Just like the SQLite ported to Mono/C# its 6 times slower than his twin, 
and in the future you get these things on Backends/Engines/Databases,
Slowing Down your system, resource hog, freezing, crashing, buggy.

Simply the True...

---

### Post by DownTown22 on 2009-08-12
eLinks???

I think most of us enjoy seeing webpages with more than just text.

---

### Post by Skripka on 2009-08-12
> **mrgnash said:**
> Performance-wise, I find that Google-Chrome outclasses every other browser I've come across. From my understanding, Webkit does have major advantages over Gecko, but both probably depend on how well they are actually implemented in any given browser as well.

Outclasses-only in speed.

---

### Post by directhex on 2009-08-12
Webkit is a million times nicer to embed and bind than Gecko.

Xulrunner is an obscene mess to try and deal with

---

### Post by mamamia88 on 2009-08-12
> **Skripka said:**
> Outclasses-only in speed.

and simplicity.  i love google chrome and once i figured out how to use it with flash in ubuntu i ditched firefox 3.5.

---

### Post by juancarlospaco on 2009-08-12
**[Web pages are coded in a terrible way]("http://validator.w3.org/")**

**[Web browsers are coded in a terrible way]("http://acid3.acidtests.org/")**

Test it yourself...
:)

---

### Post by schauerlich on 2009-08-12
> **Jimleko211 said:**
> It seems that a lot of the major browsers (and the new browsers being developed) are going towards to webkit.  Why?  I just did a benchmark on my machine, and it took Arora (a webkit browser) over 60 seconds to render [www.cnn.com](www.cnn.com) completely.  It took Firefox(which I believe uses Gecko) 2-3 seconds.

CNN loaded near instantly in Safari. Sounds like either your tubez were momentarily clogged, or Aurora sucks.

---

### Post by SunnyRabbiera on 2009-08-12
> **juancarlospaco said:**
> **[Web pages are coded in a terrible way]("http://validator.w3.org/")**

**[Web browsers are coded in a terrible way]("http://acid3.acidtests.org/")**

Test it yourself...
:)

Yes but the biggest issue I see with webkit is both Apple and adoptability.
I am unsure if Webkit will ever be a contender to gecko because gecko browsers are more supported then webkit ones.
I would like to see if its possible to run firefox with webkit though

---

### Post by Max Uglee on 2009-08-12
> **mamamia88 said:**
> i love google chrome and once i figured out how to use it with flash in ubuntu i ditched firefox 3.5.
 
I love google chrome as well.  How are you running it in Ubuntu?  Wine?  If so, is it still really that fast?  If so, even with flash?

---

### Post by Skripka on 2009-08-12
> **EDavidBurg said:**
> CNN loaded near instantly in Safari. Sounds like either your tubez were momentarily clogged, or Aurora sucks.

No it sounds like Arora was loading all the ads on the CNN page.  Apples and Oranges.

I run Arora through Privoxy, as well as Firefox-and Arora completely out does Firefox on CNN.com with no ads.  Arora=6 seconds, Firefox=10 seconds: on my overpowered box....including download time.

---

### Post by mamamia88 on 2009-08-12
> **Max Uglee said:**
> I love google chrome as well.  How are you running it in Ubuntu?  Wine?  If so, is it still really that fast?  If so, even with flash?

no i got google chrome from a .deb file and used this guide to enable flash [http://webupd8.blogspot.com/2009/08/google-chrome-for-linux-adds-plug-ins.html](http://webupd8.blogspot.com/2009/08/google-chrome-for-linux-adds-plug-ins.html)  might as well give it a go and see for yourself.  the worst that can happen is you uninstall it

---

### Post by schauerlich on 2009-08-12
> **SunnyRabbiera said:**
> Yes but the biggest issue I see with webkit is both Apple and adoptability.

Why is Apple an issue? It's FOSS.

---

### Post by phrostbyte on 2009-08-12
Arora loaded CNN pretty fast for me. Maybe you need take your modem for an oil change. :P

---

### Post by mrgnash on 2009-08-12
> **juancarlospaco said:**
> **[Web pages are coded in a terrible way]("http://validator.w3.org/")**

**[Web browsers are coded in a terrible way]("http://acid3.acidtests.org/")**

Test it yourself...
:)

100/100 here (Chrome) :P

---

### Post by Jimleko211 on 2009-08-12
I'm thinking the problem might be IPv6.  It was enabled in Firefox and it made it go pretty slow until I turned it off, but I don't know how to turn it off in Arora...

---

### Post by phrostbyte on 2009-08-12
> **mrgnash said:**
> 100/100 here (Chrome) :P

Firefox 3.5 got close, 93/100

---

### Post by starcraft.man on 2009-08-12
> **Skripka said:**
> No it sounds like Arora was loading all the ads on the CNN page.  Apples and Oranges.

I run Arora through Privoxy, as well as Firefox-and Arora completely out does Firefox on CNN.com with no ads.  Arora=6 seconds, Firefox=10 seconds: on my overpowered box....including download time.

Ten seconds???!! Firefox ain't that slow, try again or else somethings wrong with your settings on that hardware. I load CNN in 1-2 second, period. I disabled adblock and noscript.

As to topic, I don't have any problems with Firefox's rendering time. I find the slowest thing I face is server trouble and just getting it down fast enough.

---

### Post by Skripka on 2009-08-12
> **starcraft.man said:**
> Ten seconds???!! Firefox ain't that slow, try again or else somethings wrong with your settings on that hardware. I load CNN in 1 second, period. I disabled adblock and noscript.

I might be able to afford a nice box--but I can only afford 1.5Mbit/sec DSL.

---

### Post by starcraft.man on 2009-08-12
> **Skripka said:**
> I might be able to afford a nice box--but I can only afford 1.5Mbit/sec DSL.

Ah, that's a bummer, a slow connection. One day the people will rise up against our terrible ISP overlords and their tiered pricing. I know they'll get their deserts that day.

---

### Post by gnomeuser on 2009-08-13
there are many reasons:

1) The API is infinitely newer to work with compared to XULrunner, the Webkit guys really take that stuff seriously whereas Mozilla are only working to get something out for their next Firefox and think little of how other developers might want to embed the code in their programs. It truly is a horrid experience.

2) Performance, the Webkit development is governed by the rule that things can only go faster. To this end they test their code with every commit against a performance and correctness suite. This means you constantly know what impact your changes have on those factors. As a user it means you will get a known quantity with every release. This also increased code quality as one if not inclined to introduce unpredictable hacks.

3) API specialization, as a developer you may be used to working with say GTK+, Webkit allows such porting to happen and lets life be easy for developers. When a developer doesn't have to learn a new way of programming and instead can rely on the rules he is used to in his environment the programs tends to end up more stable.

4) The Webkit people have not slighted us like Mozilla, for years and year Mozilla has basically ignored Linux, releasing with vast performance issues on our platform, repeatedly fails to take us into consideration when planning platform integration. Yet having been roughly the only good browser everyone has been forced to use it. This situation is not longer the case with Webkit and we see many people wanting to switch to an upstream that actively cares about us.

In short, Webkit has superior design, performance and are infinitely more likable bedpartners.

---

### Post by Jimleko211 on 2009-08-13
> **gnomeuser said:**
> 
In short, Webkit has superior design, performance and are infinitely more likable bedpartners.
Hmmm...I still don't see the superior preformance, but I installed Midori and it's infinitely better than Arora.  Too bad it's not a QT browser...'least I got QTcurve xD

---

### Post by Tibuda on 2009-08-13
> **SunnyRabbiera said:**
> Yes but the biggest issue I see with webkit is both Apple and adoptability.
So you also have a big issue with Common Unix Printing System? Do you have a printer?

---

### Post by Warpnow on 2009-08-13
Webkit browsers use alot less resources than gecko based browsers. Gecko is a very bloated engine. Its basically impossible to build anything bordering on lightweight with it.

---

### Post by Mr. Picklesworth on 2009-08-13
My love for Webkit was inflated two-fold when I discovered Webview.set_transparent()

It really is this easy:

slideshow_webview.set_transparent(True) #Woah, this works!
[ATTACH]124753[/ATTACH]

Don't worry, that isn't actually happening in that project, but I discovered it briefly there. With love, that option could be used for amazing things. Awesome technology, regardless.


The big benefit with Webkit is that it is designed as a lone content rendering engine, whereas Gecko is build as part of the Firefox web browser. Because of this, Webkit is lightweight, easy to embed and scalable. It is great for big web browsers, but also for small chunks of embedded HTML content in applications. It doesn't put a major strain on whatever happens to use it.

---

### Post by CharmyBee on 2009-08-13
> **Warpnow said:**
> Webkit browsers use alot less resources than gecko based browsers. Gecko is a very bloated engine. Its basically impossible to build anything bordering on lightweight with it.
If that hype is so true, then why isn't webkit usable at all on 4th/5th/6th gen computers? They work well with Seamonkey that has an old Gecko renderer that is considered bloated, working better than "super fast" Chrome on the same Pentium II computer.

---

### Post by Chemical Imbalance on 2009-08-13
> **mamamia88 said:**
> no i got google chrome from a .deb file and used this guide to enable flash [http://webupd8.blogspot.com/2009/08/google-chrome-for-linux-adds-plug-ins.html](http://webupd8.blogspot.com/2009/08/google-chrome-for-linux-adds-plug-ins.html)  might as well give it a go and see for yourself.  the worst that can happen is you uninstall it

The PPA is a better choice if you want the latest:

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by Warpnow on 2009-08-14
> **CharmyBee said:**
> If that hype is so true, then why isn't webkit usable at all on 4th/5th/6th gen computers? They work well with Seamonkey that has an old Gecko renderer that is considered bloated, working better than "super fast" Chrome on the same Pentium II computer.

I ran a pentium II machine for a while and found epiphany-webkit to be far more usable than normal epiphany. Firefox would not run at all, and seamonkey was outrageously slow. Midori, and Arora both ran fine. Though my favorite was Opera.

So, I'm afraid I don't know what you're talking about.

---

### Post by scottuss on 2009-08-14
I'm no major dev but it seems that they prefer WebKit for many reasons. Meh, who knows? :P

---

