---
title: "Core 2 Quad Q6600 2.4 Ghz"
date: 2007-09-01
forum: The Cafe
---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Hi all, I'm planning to buy this processor.
However, I have some basic questions in my mind regarding the performance of this processor.

Currently I'm using Pentium D 3.4Ghz (2 cores). Disregarding the number of cores (only used for multitasking right?), do this processor core speed beat the Pentium D ?
If i see 3.4Ghz definitely a bigger number than 2.4Ghz. But the techie on the store, tells me that the Quad Core's 2.4Ghz faster than Pentium D 3.4Ghz, anyone knows how to calculate this (2.4Ghz > 3.4Ghz) , how ?

If it's core speed indeed faster than Pentium D, can anyone tell me how fast this Quad Core compared to my Pentium D (something like 100% faster or 2 times faster) ?

Also, does anyone have suggestion for the Motherboard (besides the Intel DP353PM), that surely tough enough for over clocking this processor to above > 3.0Ghz , while compatible with Feisty (or in the future, Gutsy), and preferably having on board sound card and LAN card.

My current setup:
- Pentium D 945 3.40Ghz
- ASUS P5LD2-VM SE
- 2GB DDR2
- GeForce 8400GS 256Mb PCI-E

My planned setup:
- Core 2 Quad Q6600 2.40Ghz
- Intel DP35DPM
- 2 x 2GB Kit DDR2 800Mhz
- GeForce 8400GS 256Mb PCI-E (I'll pull out from my old setup)


Any help, opinion or idea would be greatly appreciated.
Thank you.

---

### Post by ~LoKe on 2007-09-01
Different architecture, technology, everything.  It's just a way to measure.  a 2.4GHz AMD will run differently than an Intel 2.4GHz.  A Pentium D will run slower than a Core 2 Duo, and the Core 2 Duo will run slower than the Core 2 Quad.  The Quad Core will DESTROY a Pentium D.

---

### Post by starcraft.man on 2007-09-01
> **~LoKe said:**
> The Quad Core will DESTROY a Pentium D.

Seconded. The Q6600 is a great CPU. Make sure to get a good heat sink for overclocking. My current favourite is the Tuniq 120 from Sunbeam, it's a bit of a monster though. Don't take it far past 3.0, it won't give you as much benefit past that and you might run into stability issues.

The clock speed however isn't that important. What makes the C2D line better than the D is the architecture which is much more efficient and powerful and that's why it can do more with less.

I don't have a recommendation for a board right now, I'm waiting till the new year for the new pcie 2.0 line with the x38.

---

### Post by WastingBody on 2007-09-01
Pentium D:
Core 1 + Core 2 = 6.8 GHz

Core 2 Quad:
Core 1 + Core 2 + Core 3 + Core 4 = 9.6 GHz

I don't know if thats right or anything, but thats how I think of it.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
> **~LoKe said:**
> 
Different architecture, technology, everything. It's just a way to measure. a 2.4GHz AMD will run differently than an Intel 2.4GHz. A Pentium D will run slower than a Core 2 Duo, and the Core 2 Duo will run slower than the Core 2 Quad.
I see, so the x.x Ghz isn't comparable if the technology is different.

> **~LoKe said:**
> The Quad Core will DESTROY a Pentium D.
:shock: Is it that fast ?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
> **starcraft.man said:**
> Seconded. The Q6600 is a great CPU. Make sure to get a good heat sink for overclocking. My current favourite is the Tuniq 120 from Sunbeam, it's a bit of a monster though. Don't take it far past 3.0, it won't give you as much benefit past that and you might run into stability issues.
Great, I won't go further when I've buy and do over clock to this CPU.
Actually, if the performance is that great, I won't over clock this CPU.

---

### Post by starcraft.man on 2007-09-01
> **WastingBody said:**
> Pentium D:
Core 1 + Core 2 = 6.8 GHz

Core 2 Quad:
Core 1 + Core 2 + Core 3 + Core 4 = 9.6 GHz

I don't know if thats right or anything, but thats how I think of it.

Not that simple. A 2 Ghz Core 2 Duo chip could crush anything in the D line, it has to do with many factors and clock speed/core number is only really one part. If the application isn't threaded properly then the extra cores are useless, among other things...

> **Milk & Toast & Honey said:**
> I see, so the x.x Ghz isn't comparable if the technology is different.

That's the gist of it. The power of CPU is measured in lots and depends on many factors, not least of which is clock speed.

> :shock: Is it that fast ?
It is.

[Here is an article from tech report comparing core 2s to D line and AMD.]("http://techreport.com/articles.x/10351")

[Here is an article comparing today's (well a few months back) current CPU performance.]("http://techreport.com/articles.x/12772")

I think that should sum things up. Remember though one of the most vital things when it comes to 4 cores is to have an application that supports all cores via threading, as you will see in the second article (first one only illustrates core 2 duo performance I think).

I think that wraps up all the questions, have fun with the quad. Oh and darn it, I'm still on a p4... >.>.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
> **WastingBody said:**
> Pentium D:
Core 1 + Core 2 = 6.8 GHz

Core 2 Quad:
Core 1 + Core 2 + Core 3 + Core 4 = 9.6 GHz

I don't know if thats right or anything, but thats how I think of it.
I think this won't apply, because each core work independently for each job, but they never sharing one same job parallelly.

---

### Post by starcraft.man on 2007-09-01
> **Milk & Toast & Honey said:**
> I think this won't apply, because each core work independently for each job, but they never sharing one same job parallelly.

They can. To share the work load of an application though you need one that supports "threading". The term means the original application (like a video encoder) creates numerous smaller jobs within the whole thing (parts for each core, depending on how it was designated to thread). Then the cores work on them and if it's coded very well all 4 can be maxed out to cut the job time significantly.

The problem lies in the fact that many older applications (like games, even some newer ones) only support 1 or 2 cores. So you won't always see a performance boost, it depends on how the application in question is coded... if you look at the different tests I linked you'll see this illustrated well.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-03
Sorry for very belated reply, I started this thread, but I leave it, got something really sudden to do.

[QUOTE=starcraft.man]
...
I think that wraps up all the questions, have fun with the quad. Oh and darn it, I'm still on a p4... >.>.
[/QUOTE]
Yes, those articles really answer my question about these processor technology, thank you very much for the link.
I though you're already on the Quad Core, regarding your knowledge about this stuff. Don't be sad, P4 isn't that bad :) .

[QUOTE=starcraft.man]They can. To share the work load of an application though you need one that supports "threading". The term means the original application (like a video encoder) creates numerous smaller jobs within the whole thing (parts for each core, depending on how it was designated to thread). Then the cores work on them and if it's coded very well all 4 can be maxed out to cut the job time significantly.
[/QUOTE]
That's clear my mind now.

[QUOTE=starcraft.man]
The problem lies in the fact that many older applications (like games, even some newer ones) only support 1 or 2 cores. So you won't always see a performance boost, it depends on how the application in question is coded... if you look at the different tests I linked you'll see this illustrated well.[/QUOTE]

Yes, actually, I asked question to my self, do I really need this number of cores?
But then I think, I do need this for my job, I'm developing software (using Java), and it really hog the CPU (and my time) when the time comes to compile and running jboss, I really need fast machine to cut the compile time.
Btw, I do coding, compiling, testing on this one machine (that's include some VMWare's console for testing the software's behaviour on other OS). This Pentium D just won't make it for another year I think :p .

---

### Post by PmDematagoda on 2007-09-03
I know that this is not what you wanted Milk & Toast & Honey but as I'm interested in buying a Quad core processor could you tell me how much you paid for it?

---

### Post by Frak on 2007-09-03
You can never have to many cores/Hz. As long as the arch is good.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-03
> **PmDematagoda said:**
> I know that this is not what you wanted Milk & Toast & Honey but as I'm interested in buying a Quad core processor could you tell me how much you paid for it?
No problem :) .
This is a custom setup.
Here's the offer from the store:
[LIST]
[*]Core 2 Quad Q6600 2.4Ghz 8MB : $290
[*]Intel DP35DPM : $140
[/LIST]
I've converted the price to US $.

If you need any price for any other part that I will use, just ask me.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-03
> **Frak said:**
> You can never have to many cores/Hz. As long as the arch is good.
I beg your pardon?
Which arch? The OS or the other thingy in motherboard?

---

### Post by Frak on 2007-09-03
> **Milk & Toast & Honey said:**
> I beg your pardon?
Which arch? The OS or the other thingy in motherboard?
The architecture. P4's have a pretty bad architecture IMHO. Yet most of that was fixed with the Core 2's.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-03
> **Frak said:**
> The architecture. P4's have a pretty bad architecture IMHO. Yet most of that was fixed with the Core 2's.

Oh, that one, yes, I read that in one of the articles that starcraft.man gave me.

---

### Post by PmDematagoda on 2007-09-03
Thanks Milk & Toast & Honey, seems quite cheap, because in Sri Lanka rupees it's 43000 approximately, though it may be higher here. Might wait for some time for the price to go down though. By the way how much was the entire 4GB RAM? 

> Frak:-

The architecture. P4's have a pretty bad architecture IMHO. Yet most of that was fixed with the Core 2's.

What's wrong with P4, I have a P4 Hyper-threaded system and there weren't many problems except for the fact that the processor sucks up a lot of energy and heats up very frequently. I assume these were the problems you were talking about?:)

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-03
[QUOTE=PmDematagoda]Thanks Milk & Toast & Honey, seems quite cheap, because in Sri Lanka rupees it's 43000 approximately, though it may be higher here. Might wait for some time for the price to go down though. By the way how much was the entire 4GB RAM? 
[/QUOTE]
I'm choosing the 2GB Ram Kit (that's 2x1GB, packed to one), it cost $90 each kit, totaled to $180 :) , the 1 stick version of 2GB DDR2 still cost high in here, but I can't remember the price.
Couple months ago, the same store offer Core 2 Quad (same spec) for more than $400! So I think, this price is very good (for me at least) for now.

Ah, one note, if you're buying the Quad Core, make sure you choose the one with G0 stepping, not the B3. The G0 produce less heat and consume less power. I read it somewhere, but I can't remember that. I think in some overclockers forums somewhere.

[QUOTE=PmDematagoda]
What's wrong with P4, I have a P4 Hyper-threaded system and there weren't many problems except for the fact that the processor sucks up a lot of energy and heats up very frequently. I assume these were the problems you were talking about?:)[/QUOTE]
I think after we buy the Quad, we'll know the difference :)

---

### Post by PmDematagoda on 2007-09-03
Thank you for giving me the prices Milk & Toast & Honey and thanks also for your advice, i'll remember it when I go to buy a Quad Core processor.:) 

So all in all the total amounts to about 51,000Rs. if that is I use my old GeForce 6200 256Mb VGA PCI-E.  Which is quite expensive.:(

---

### Post by Frak on 2007-09-03
(Early Model, excluding late model HT's) We're very hastily constructed and are not very efficient for the power it uses. They overheat and can slowdown by a glitch in the "Self Preservation" mode.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-04
Hi all, finally the Quad Core and the Intel DP35DPM arrived this afternoon. But the 4GB DDR2 still on the way, maybe it'll arrive the day after tomorrow, at most.

After moving all the drives, RAM and the video card, finally I boot into this new *shinny* machine ;p .

Some minor problem (in case you're buying the same setup):
[LIST]
[*]The BIOS can't boot into my Seagate SATA 80GB, but it do detect my drives.
But I can boot from the Feisty's Live CD, and choose to boot from the drive, it works. Tried to update with the latest BIOS, but the updater freeze, and I just have to reset, maybe later I'll try other BIOS version (kinda lazy now).
[*]The network card doesn't work at all, I have to download the latest e1000 driver from Intel website, and manually "make install" from the source (doesn't hard at all anyway).
[*]The sensors can't detect the temperature or fan, already tried "sensors-detect" and adding the output to "/etc/modules", but still no change, well, this is minor however, maybe Gutsy will handle this in the coming October :) .
[/LIST]

Everyone, thank you for your idea, suggestion, I really appreciate it.
startcraft.man, thank you for the links, the charts in the article really give me the picture of processor performance.

PmDematagoda, I think this processor is great, well, it hasn't 2 hours I use this computer, but I can tell you, this processor really fast. And I'm sure, when the DDR2 800 arrived, it will give more performance boost.

---

### Post by PmDematagoda on 2007-09-05
Thanks for the heads up Milk & Toast & Honey, I can't wait till the day I get a quad core processor.:lolflag:

---

### Post by insane_alien on 2007-09-05
> **PmDematagoda said:**
> Thanks for the heads up Milk & Toast & Honey, I can't wait till the day I get a quad core processor.:lolflag:

ahh but you just know that as soon as you do there will  be octocores.and then the 1337 hexadecacores and so on.

---

### Post by PmDematagoda on 2007-09-08
> insane_alien:-

ahh but you just know that as soon as you do there will be octocores.and then the 1337 hexadecacores and so on. 


Yeah I know, the world changes so fast these days, about 50 years ago it would take about 5 years to advance in computer technology, but these days, it just takes a matter of a few months, and the speed is increasing. 

But I would like to enjoy something while it's still useful. One thing I would really enjoy even though I know it won't be the last thing is Quad Core for Laptops.:)

---

### Post by slimdog360 on 2007-09-08
You should look at how many instructions per cycle it can handle. Hence why back in the day AMD ruled intel with a slower clocked cpu, now intel rule AMD with a slower slower clocked cpu. Funny eh.

---

### Post by nowshining on 2007-09-08
my p4 no hyperthreading runs okay with just one fan...

---

### Post by PmDematagoda on 2007-09-08
> nowshining:-

my p4 no hyperthreading runs okay with just one fan...

That's good for you nowshining, because my particular P4 with hyper-threading needs 3 fans to keep it under the proper temperature before which it overheated 2 times. So I need to monitor core temperatures constantly.

---

### Post by nowshining on 2007-09-08
I was wondering what HT was like and was wishing it to be on mine, I for one am using Dells if you see my sig.. however the thing-a-ma-bob whatever it is called - pipe - big green thing covers the heatsink over as to help it keep kool, but no matter what it's going to be hot..



a link i found detailing internals of the P4 and why it sucks or so..



[http://www.emulators.com/docs/pentium_1.htm](http://www.emulators.com/docs/pentium_1.htm)

---

### Post by PmDematagoda on 2007-09-08
Well I don't know about others but here is my testimonial on HT, it's good because of the fact it makes the system work better by making it think that there are two processor cores instead of one, but it's not a very good investment because for me as you know my processor which is Pentium 4 HT sucks a lot of energy and give of so much heat that hell itself would be cooler. The price of the amount of electricity this processor sucks up in one month is about equal to that used up by a Quad core in 4 months. 

And the other problems is that when it works it usually heats up enough to make the Cooling system increase the speed of the cooling fans which means that 3 fans working hard is not a very relaxing song:guitar:. The sound is so loud that it makes me miss my old P2 with MMX which was very much quieter, used less energy and gave off less heat. 

This is also why I want to move to Quad core as soon as possible.:)

---

### Post by nowshining on 2007-09-08
well I don't know if My dell 4600i will accept a custom cpu myself nor would it work on the motherboard these series came out in 2003 so prob. not... hope u well when u get ur new cpu..

---

