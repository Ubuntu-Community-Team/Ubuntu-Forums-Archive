---
title: "Upgrading my computer, can I get some input?"
date: 2009-01-15
forum: The Cafe
---

### Post by Oplix on 2009-01-15
Alright, so my graphics card recently overheated and needed to be replaced.

I'm running an ASUS M2N32-SLI Deluxe with an Athlon 64 x2 dual core (4200+).

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16814130339]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814130339")

This is the card I'm thinking of getting. But my power supply wont support it, so I'm thinking of upgrading the power supply to this:

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16817703015]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16817703015")

I've never built a computer, but I've done as much reading as I've been able to in making sure this is all compatible.

I was just hoping someone with a bit more experience than me could give it a quick look over to make sure I wont have any issues when I hook it all together.

Specs for my motherboard:
[http://www.asus.com/products.aspx?modelmenu=1&model=1163&l1=3&l2=101&l3=0]("http://www.asus.com/products.aspx?modelmenu=1&model=1163&l1=3&l2=101&l3=0")

Specs for my CPU: 
[http://computers.pricegrabber.com/processors-retail-box/m/20173454/details/st=product_tab/]("http://computers.pricegrabber.com/processors-retail-box/m/20173454/details/st=product_tab/")

Thanks for taking the time to help. I don't want to order this card and power supply only to learn that it wont work with my system for some little reason I overlooked. I can't wait to get off my laptop!

---

### Post by Murrquan on 2009-01-15
What's wrong with laptops? ^.^

I haven't built my own computer before, but one thing you might want to do is run a few Google or Ubuntu Forums searches to make sure that your video card is compatible! If it's not well-supported by Linux drivers, you may run into some problems.

---

### Post by Oplix on 2009-01-15
> What's wrong with laptops? ^.^

It's a MacBook, and I'm a PC user.

Good idea to check for the Linux compatibility though, I was so desperate to get my desktop back I almost overlooked Linux XD

---

### Post by Skripka on 2009-01-15
> **Oplix said:**
> Alright, so my graphics card recently overheated and needed to be replaced.

I'm running an ASUS M2N32-SLI Deluxe with an Athlon 64 x2 dual core (4200+).

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16814130339](http://www.newegg.ca/Product/Product.aspx?Item=N82E16814130339)

This is the card I'm thinking of getting. But my power supply wont support it, so I'm thinking of upgrading the power supply to this:

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16817703015](http://www.newegg.ca/Product/Product.aspx?Item=N82E16817703015)

I've never built a computer, but I've done as much reading as I've been able to in making sure this is all compatible.

I was just hoping someone with a bit more experience than me could give it a quick look over to make sure I wont have any issues when I hook it all together.

Specs for my motherboard:
[http://www.asus.com/products.aspx?modelmenu=1&model=1163&l1=3&l2=101&l3=0](http://www.asus.com/products.aspx?modelmenu=1&model=1163&l1=3&l2=101&l3=0)

Specs for my CPU: 
[http://computers.pricegrabber.com/processors-retail-box/m/20173454/details/st=product_tab/](http://computers.pricegrabber.com/processors-retail-box/m/20173454/details/st=product_tab/)

Thanks for taking the time to help. I don't want to order this card and power supply only to learn that it wont work with my system for some little reason I overlooked. I can't wait to get off my laptop!

Just about any graphics card you buy now will fit your motherboard.  GPUs have been standardized to be PCIe2.0 x16 rails; and they are backwards compatible to PCIe 1.0 x16 rails too.  That really isn't a worry.

Looking at the one you linked to-it should be up to the task, with enough 6pins for the task; it also has much more than the needed Amps on the +12V.  It should work from a hardware standpoint--it should plug together and run.  It looks like that card is covered by the Nvidia 177.80 driver which is in the Ibex repos.   Know that if you ever want to do any SLi insanity, you'll want a PSU with still bigger cajones.

With a card that fast, know that your bottleneck will likely be your CPU.

---

### Post by Bucky Ball on 2009-01-15
[http://www.antec.outervision.com/index.jsp](http://www.antec.outervision.com/index.jsp)

Calculate your requirements. Unless you are using crossfire 500W may be overkill, but not as much as 800w! They are for the days when PSU's were -70 rather than 80+. What am I saying, I think they still sell the generic silver box PSU's that take out most of your components when they overheat and explode!

[http://www.antec.com/usa/productDetails.php?lan=us&id=27500](http://www.antec.com/usa/productDetails.php?lan=us&id=27500)

There are others but whatever you get, make sure it has 80Plus certification and follows RoHS suggested standard concerning use and disposal of toxic materials if you want to do that extra bit enviornmentally. So many computer builders (including Linux builders) don't really think about either of these things. Also take note of the safety switches built in. As manufacturers get better at producing the goods, there is absolutely no reason not to use them (competitive pricing and benefits down the track - environmentally and on your pocket when you calculate your yearly power bill - especially if your box is on a lot).

Check my post here, I am building a machine at the moment (I usually build two or three over christmas break for friends and family and every year when I research the products become leaner, greener and more energy efficient):

[http://ubuntuforums.org/showthread.php?t=1040615](http://ubuntuforums.org/showthread.php?t=1040615)

I could probably get away with a 380w PSU even.

---

### Post by MaxIBoy on 2009-01-15
If you want to replace only the , don't invest too much in your graphics card, because your CPU will just slow it down. Try a Radeon HD 3xxx series or equivalent. 



However, I've learned the hard way that it is a better idea not to band-aid older equipment, and to start over instead. If I'd known that from the beginning, I'd be at least $200 richer right now.

---

### Post by Bucky Ball on 2009-01-15
> **MaxIBoy said:**
> 
However, I've learned the hard way that it is a better idea not to band-aid older equipment, and to start over instead. If I'd known that from the beginning, I'd be at least $200 richer right now.

How true.

---

### Post by Noblacktie on 2009-01-15
If you're going to go with the 9800GTX, make sure it will fit in your case.

The newer nVidia powerhouse cards are ginormoous. I know I had some knuckle scraping sessions when I got my 8800. Didn't look so big in the box but freakin' thing is huge.

---

### Post by Skripka on 2009-01-15
> **Noblacktie said:**
> If you're going to go with the 9800GTX, make sure it will fit in your case.

The newer nVidia powerhouse cards are ginormoous. I know I had some knuckle scraping sessions when I got my 8800. Didn't look so big in the box but freakin' thing is huge.

More detail-they are about 10.5 inches long, measured from the slot cover to the front of the card.  The fit perfectly in a Lian Li ATX midtower-I mean perfectly, no space to spare between GPU and HDD cage.


The Newer ATi powerhouse cards are bigger.  My brother just got a 4850X2 card, the beast is 11.25 inches long....and it took him an hour of grinding at the HDD cage in his Lian Li to get it to fit.

---

### Post by stmiller on 2009-01-15
And consider sound, if that matters to you. There are silent passively cooled video cards with no fan. Dead silent. :) Of course they are not as powerful as the big honking cards though.

I have a quiet Shuttle box I have to put my head down to listen if it is on. ahhh.... :)

---

### Post by Oplix on 2009-01-16
Some great advice there, thanks!

Although some questions still regarding this advice.

> If you want to replace only the , don't invest too much in your graphics card, because your CPU will just slow it down

See, another person I spoke to told me the opposite, that it was better to have the bottleneck in your CPU than your graphics card, because then you're getting full use out of the CPU because it's not waiting on the graphics card (that was my understanding of what he was telling me).

So I was under the impression that having a card that was faster than your CPU wouldn't really be a bad thing, and would be better than if my card was slower.

> However, I've learned the hard way that it is a better idea not to band-aid older equipment, and to start over instead.

Yes, normally I wouldn't even be looking at an upgrade, but as it stands now, I have no graphics card at all, so I do need one, and I'm not buying a whole new machine just because I was an idiot and allowed my graphics card to overheat and cook itself. Power supplies are fairly cheap, so I figure if I can get a better card in there, and all I need to do is upgrade the power supply, I'm getting a new card anyways, so I may as well get something that was a bit better within reason.

> If you're going to go with the 9800GTX, make sure it will fit in your case.

My 8800GTS fit with several inches to spare. I remember the first time I opened my PC and saw the card in there. It was so big I thought "Wow, motherboards must be really looking fancy and sleek these days...". Then I saw the motherboard behind it, "Hmmm. Wow.".

I'll definitely look for a lower watt power supply, but I need to find that +12v/24A that the card requires. That's the only reason I need to upgrade the power supply. I currently have an Antec SmartPower 450, and it looks like, judging by the Antec Power Supply Calculator, that I should still be able to get away with 450W, but it doesn't have the +12v/24A which is why I'd need to upgrade.

So you're saying that with my CPU, the card might not be worth purchasing compared to a lesser, cheaper card? And possibly one which wont require me to upgrade my power supply? This definitely gives me something to think about.

---

### Post by nick09 on 2009-01-16
I'd stay to the safe side and go to 610Watts, like this PSU:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817703005](http://www.newegg.com/Product/Product.aspx?Item=N82E16817703005)

If you don't believe me then open your motherboard manual to page 29 and it will say it needs at least a 500W ATX 12V Specifcation 2.0 PSU to power the following:
CPU: AMD FX-62
Memory 1024 MB DDR2-800 (x4)
Graphics card: PCI Express x16 NVIDIA 7900GTX
Serial ATA device: SATA hard disk drive (x2)
Optical drives: DVD-RW

The PSU that I have suggested has plenty room for expandability when you want to push the computer for a few more years before buying a entire new system.

---

### Post by stefangr1 on 2009-01-16
Just curious... but why do you buy such an expensive gaming card like the NVIDIA 9800GTX? And why doesn't your PSU support this / some graphic cards?

Your system will be really unbalanced if you build it like this. You 're combining a hypermodern high end GPU with a CPU from two generations back, which will not give you a very fast computer. Then: do you already have the RAM (and how much?).

On the other hand: $280 isn't enough to buy something like a new IO-board + 4GB RAM + Intel E8400 + NVIDIA 9500GT, which would cost you something like $400.

So what I would recommend you is to either replace everything (and then maybe sell the parts of your old computer), or just buy a GPU somewhere in the midrange.

Then there's another thing. You said your last GPU overheated. The NV9800GTX also produces a lot of heat, that might cause trouble.

EDIT: 620W might be on the save side for a dual socked quad core motherboard with a few fast GPU's in SLI mode, but it's really an overkill here. I suppoze 350W would already on the save side, especially if you buy a quality PSU. With those $20 things you can have issues with a maximum on some voltage lines, but about every decent PSU will do the job.

---

### Post by Bucky Ball on 2009-01-16
If you have a completely inefficient -70 efficiency psu which creates more heat than energy, your motherboard manual may be right, but these specs require nothing like 610watts. If you are intending to beef the machine to a full-blown gaming box, maybe. Sheesh, suck up as much energy as possible why don't we. Forget sleek and economical. Money to burn.

---

### Post by handy on 2009-01-16
> **Murrquan said:**
> What's wrong with laptops? ^.^ 

The major problem with notebooks, is that you are very limited in what you can upgrade on them & if they fail they are very expensive to have repaired, because the parts are not freely available outside of the distributorship.  So you have to pay top dollar for new parts & a very expensive hourly rate for the R&R.  Also, notebook batteries are not cheap.  All this is the price you pay for the convenience (often essential) of computing mobility & a space saving design. 

Desktop computers on the other hand, allow you the freedom (within your budget) to upgrade & modify (if you are so inclined) to your hearts content. 

This you can do without having to pay someone else for doing the easiest work there is on computers.  Again; if you are so inclined. :-)

---

### Post by Oplix on 2009-01-16
My last GPU overheating was sort of my own stupid fault. I guess I didn't clean the dust out of it well enough because several (4-5?) months later, it overheated because of all the dust that was in there.

I feel like an idiot for that one :mad:

Lesson learned. More frequent dust cleaning, blow from the opposite direction I was going, and stop taking advice from store employees.

> Just curious... but why do you buy such an expensive gaming card like the NVIDIA 9800GTX? And why doesn't your PSU support this / some graphic cards?

I like gaming, and the card was recommended to me given my specs as being a good choice for an upgrade. I'm assuming my PSU wont support this card because on the spec list, it says that it requires +12V/24A. My PSU has about +12V/17A. So I assume if it doesn't meet minimum requirements, that's a problem. I don't game on consoles, and got a pretty bad tv that was given to me that's using rabbit ears, so my computer is my whole entertainment system, I don't mind investing a little more in it if it makes sense, and from the information I had gathered, I thought that card made sense to upgrade to.

I don't have much experience with determining hardware compatibility and what's a good choice for which system, and I've been having a hard time finding a straight answer to "what's everything I need to consider when choosing computer parts", even google hasn't given me a straight answer. So I'm just trying to ask questions and learn along the way while still getting my desktop back.

So yes, excuse any confusion my beginner mistakes may have caused :)

---

### Post by Skripka on 2009-01-16
> **Oplix said:**
> 

See, another person I spoke to told me the opposite, that it was better to have the bottleneck in your CPU than your graphics card, because then you're getting full use out of the CPU because it's not waiting on the graphics card (that was my understanding of what he was telling me).

So I was under the impression that having a card that was faster than your CPU wouldn't really be a bad thing, and would be better than if my card was slower.



FYI-there was an argument/thread on the-buy-full-out-new versus upgrade paths-and you're getting some of that here.  I won't derail your current thread by saying more.

For most general purpose computing, you don't "need" a powerful GPU-i.e. an Nvidia 8500GT is more than "enough".  OTOH, buying newer and more mid/top of the line keeps you from being obsolete and legacied so soon.

As far as PSUs go, it is better to have room for more than you need-as if you have less, you get system instability.

---

### Post by stefangr1 on 2009-01-17
Well, as I see it then your psu has only enough power on the 12V line for the NVIDIA 9500GT, whereas the 9600GT already draws to much. So then you would indeed need to buy a new PSU.

I'm just thinking that it might be a disappointment if you're spending quite a lot of money while your system hasn't become really that fast.

---

### Post by handy on 2009-01-17
It is my understanding that the 9 series of nVidia GPU's use less energy per GPU output than the 8 series.  I believe the 9's use a finer die.

---

### Post by Oplix on 2009-01-17
Alright, I guess the main question is, how much of an upgrade would this really give me? I realize that it wont make my computer much faster, but will it be able to handle the graphics much better than my 8800GTS? Would there be games I could max the settings out on that I wasn't able to before?

Or does it all really fall down to my CPU being too slow to get that sort of use out of it?

I didn't have my heart set on that card or anything, it was just what was recommended to me.

I use the computer for photo editing, bit of graphics design, as well as flash, and regular internet stuff, but I also use it for gaming. I'm not the biggest gamer out there or anything, but I've been really getting into some of the newer games that have been coming out thanks to their graphics and game physics (3D animation is something I've dabbled with and had some interest in, so it's cool to see what the developers are coming out with in their games).

I'm really not inclined to sell my old hardware and get a new computer at the moment. My computer can still run these games, so I'm not ready to replace it, and they're probably the most system demanding thing I do regularly. I just figured since I didn't have a graphics card, and needed a new one, an upgrade wouldn't be a bad idea since my card was somewhat older and an upgrade wouldn't be top of the line prices..

---

### Post by handy on 2009-01-17
Stick the graphics card you want into your machine, if it runs reliably great.  If it doesn't run reliably then go & grab a more suitable PSU.

[I][U][http://www.anandtech.com/printarticle.aspx?i=3413](http://www.anandtech.com/printarticle.aspx?i=3413)

[http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html](http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html)
[/U][/I]

---

### Post by Oplix on 2009-01-18
Before I go and do that, just to make sure, that doesn't pose any risk of damaging any part of the computer does it? Trying to demand more from the PS than it was designed to deliver or anything like that?

Not accusing you of giving me bad advice, I just want to be aware of any potential risk I may not know about before I put my money down and end up gambling with my hardware or anything like that.

I'm going to look for some reading on putting a system together and choosing parts, so hopefully in the future I'll be the one giving answers and not asking questions. Thanks for the help in the meantime though.

---

### Post by jrusso2 on 2009-01-18
> **Oplix said:**
> Alright, so my graphics card recently overheated and needed to be replaced.

I'm running an ASUS M2N32-SLI Deluxe with an Athlon 64 x2 dual core (4200+).

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16814130339]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814130339")

This is the card I'm thinking of getting. But my power supply wont support it, so I'm thinking of upgrading the power supply to this:

[http://www.newegg.ca/Product/Product.aspx?Item=N82E16817703015]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16817703015")

I've never built a computer, but I've done as much reading as I've been able to in making sure this is all compatible.

I was just hoping someone with a bit more experience than me could give it a quick look over to make sure I wont have any issues when I hook it all together.

Specs for my motherboard:
[http://www.asus.com/products.aspx?modelmenu=1&model=1163&l1=3&l2=101&l3=0]("http://www.asus.com/products.aspx?modelmenu=1&model=1163&l1=3&l2=101&l3=0")

Specs for my CPU: 
[http://computers.pricegrabber.com/processors-retail-box/m/20173454/details/st=product_tab/]("http://computers.pricegrabber.com/processors-retail-box/m/20173454/details/st=product_tab/")

Thanks for taking the time to help. I don't want to order this card and power supply only to learn that it wont work with my system for some little reason I overlooked. I can't wait to get off my laptop!

Only thing I am not sure about is the Video card. Seems people were having problems with that model on Linux but it might be fixed by now.

---

### Post by handy on 2009-01-18
> **Oplix said:**
> Before I go and do that, just to make sure, that doesn't pose any risk of damaging any part of the computer does it? Trying to demand more from the PS than it was designed to deliver or anything like that?

Not accusing you of giving me bad advice, I just want to be aware of any potential risk I may not know about before I put my money down and end up gambling with my hardware or anything like that.

I'm going to look for some reading on putting a system together and choosing parts, so hopefully in the future I'll be the one giving answers and not asking questions. Thanks for the help in the meantime though.

You won't hurt your system, it will work fine or it will fail, it may boot straight into the graphics card's alarm, or it may fail under heavy load on the GPU.  If it doesn't run properly, replace the PSU, & that should be it.

---

### Post by Bucky Ball on 2009-01-18
[quote=Oplix]I'm going to look for some reading on putting a system together and choosing parts, so hopefully in the future I'll be the one giving answers and not asking questions. Thanks for the help in the meantime though.[/quote]

[http://ubuntuforums.org/showthread.php?t=1040615](http://ubuntuforums.org/showthread.php?t=1040615)

As I mentioned before, that is a start. Just beef up the PSU and the GPU. It is a good idea before building a box, to figure out what it is going to be used for. If you are never going to use Crossfire, SLI with 8 hard drives, 12 USB ports rocking at once and three optical drives, there is not much use for a 1200watt PSU, if you follow what I am saying.

Work out the components you are going to use now and the components you will realistically want to use in the future (and you are limited to some degree by the motherboard in this), use a power calculator (a reliable one, not one that is trying to sell you a bigger, more expensive PSU) and calculate your dream machine (what the MB is capable of producing), then buy a good, energy efficient PSU to fit the bill. This item is the heart of the machine, trust me. If it blows and there are no safety switches, goodnight Dick. If that happens when you are not home ...

Just get a really good one to fit the bill, no need to go bonkers and paranoid. 50 - 80watts over what you require should be plenty ... only if you have an efficient PSU that is, not a generic silver box.

Good luck with it, and keep asking questions ...

---

