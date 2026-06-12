---
title: "Hardware Recommendations Please, and other Help"
date: 2007-11-22
forum: The Cafe
---

### Post by codypumper on 2007-11-22
Our desktop computer is continuously dying, and rather than buying a new configured one,  I would like to look into building our own.

I have little hardware experience (I have replaced RAM, and drives, but thats where it ends), and I actually don't know where to start.

Do I find a really good motherboard and find a case for it, or do the reverse?

Do I find a really good processor and find a motherboard for it, or do the reverse?

What are good processors, motherboards, cases, drives, and etc.?

I don't know all the limitations In compatibility, so any suggestions are appreciated. I would really like to learn.

---

### Post by prodigalson666 on 2007-11-26
I dont know where you live but ask around and find the best computer store in your area, good computer shop is like a good mechanic, word of mouth gets around. Check google and do some research, its often a matter of personal choice. I build computers in my spare time for extra cash. I personally prefer AMD over intel, I find intel has been playing catch up to amd, and amd is more affordable, for me they take a beating and keep on ticking. Good processor is important. Good motherboard is next, Asus tend to lead the pack for a very good reason. The case is irrelevant, what is important is a good power supply under the hood, 450w or better. Ram is at an all time low to buy, even the cheap no name stuff runs well and has good longevity, the bonus of a better brand name like corsair or ocz is they have excellent warranties and better heat sinks to avoid over heating. I stick with nvidia for the same reasons as amd and they work much easier than ati when dealing with linux. Hope that helps.

---

### Post by ARhere on 2007-11-26
I think a reason you may not be getting great responses to this thread is because building a good PC is more from plain experience then anything else.  Putting together a normal PC (*I define normal as one that is used for basic email, web, light gaming*) is very straight forward as all the parts are made to fit together easily.  I can give you $0.02 worth of advice to help you on your way.

1. Decide what you are going to do with this Box.  Are you going to be a serious gamer?  Normal use?.  What you decide will have the biggest impact on how much you spend.  For the list below, I am going to assume you need just a regular PC.  (*I defined that above*)  You **should** spend most of your time _**reading_** up on key hardware pieces.  Make sure there are good drivers for the hardware you want, and for the OS you want _before_ you buy!

2.  Choose a motherboard.  Great place for good reviews on PC hard ware is [HardOCP.com]("http://www.hardocp.com") or [tomshardware.com ]("http://www.tomshardware.com")
The MB is arguably the most important piece of the PC, not the processor.  Your motherboard will also define what processor and RAM you get so I repeat, spend a LOT of time reading up on motherboards.  Personally I enjoy ASUS with AMD hardware as they give me the best bang for my buck.  JMO.

3.  Choose a video card.  If you plan to use Ubuntu with this box, I would stick with Nvidia and search these forums to weed out the troublesome cards.  Stay clear of embedded graphics unless you have evidence it works with your OS.

4.  Choose your HDD array.  If you are just buying a single 250GB HDD, then no worries.  If you want to do something fancy like RAID 0,1, or 5.  Make certain your RAID controller, *IF you need one* is supported by the OS.  Most motherboards come with FakeRAID controllers, and if you want to do RAID mirroring using one of those, I always suggest to turn off the RAID in the BIOS and use software RAID built in Linux instead.

5.  The rest is just icing, like keyboard, mouse, monitor, case, whatever.

I am not trying to be mean, but just honest.  If you have never put your own PC together, I would just seriously buy one from a vendor.  The reason I say this is if you have a passion for PC hardware, you would already be reading up on the latest and greatest chipset/whatever.  If not, then I honestly think you are setting yourself up for a massive head-ache due to lack of knowledge on the subject.

-ARhere

P.S.  I forgot about the Power Supply, which usually comes with the case and is important.  Most supplies above 500watts should do just fine and are rock solid, except I caution you not to buy the cheapest available as a bad supply can take out everything, literally.

---

### Post by jinx099 on 2007-11-26
> **ARhere said:**
> 
I am not trying to be mean, but just honest.  If you have never put your own PC together, I would just seriously buy one from a vendor.  The reason I say this is if you have a passion for PC hardware, you would already be reading up on the latest and greatest chipset/whatever.  If not, then I honestly think you are setting yourself up for a massive head-ache due to lack of knowledge on the subject.

-ARhere

I disagree.  I put together my first PC without much real hand-on experience with PCs.  Getting it running was very rewarding, and I have not bought a pre-built PC since.

Just do your research on the hardware.  Obviously you want to make sure your motherboard, CPU, and RAM are all compatible types.  I recommend a dual-core CPU, they are cheap these days anyway.

Do extra research on the hardware if you plan to install linux!  This means paying close attention to the motherboard especially.  Pretty much any CPU and RAM will work with Linux so don't worry about those.

---

### Post by Linuxratty on 2007-11-26
Linux compatable hardware:

Auses or Biostar MB

Hard drive (ive not moved to Sata yet.)

Lite On DVD/cd recorder player.

1 gig RAM.

---

### Post by Lostincyberspace on 2007-11-26
just make sure the hard ware is compatible. try using new egg to build it in a wish list then you can change it to what you like. the good thing of doing it this way is you can check it easily I built my comp with out much hassle, but I have always thought that hardware was easy to figure out.

---

### Post by x0as on 2007-11-26
I agree with jinx099, build it yourself.  It gives you better options to upgrade in the future.  

Personally I'd go for a Intel core2duo, AMD has been playing catch up to Intel but still falls short of catching Intel.

---

### Post by jinx099 on 2007-11-26
> **Linuxratty said:**
> Linux compatable hardware:

Auses or Biostar MB

Hard drive (ive not moved to Sata yet.)

Lite On DVD/cd recorder player.

1 gig RAM.

ASUS and Biostar make many different motherboards using different chipsets.  I'm sure some, but not all ASUS and Biostar motherboards support linux.  

The hard drive and CD-ROM drive should work no problem with linux, but the associated SATA or IDE controllers may not.  My SATA drives work no problem on a Gigabyte 965P-DS3 motherboard.  My DVD Burner has been flakey recently.  It used to work fine, but it seems with 2.6.23 kernels it does not work well anymore.  Take this with a grain of salt because I've not really investigated the problem much yet!

In general, I've been dissatisfied with Jmicron controllers.  The past 2 motherboards I've owned, I've had issues with at first due to jmicron drivers being slow to get into kernels.  I don't have much faith in jmicron's linux drivers.

---

### Post by inversekinetix on 2007-11-26
Let me ask you a simple question?

what do you intend to do with this computer?

that's the most important question.

---

### Post by LaRoza on 2007-11-26
Go to [http://www.newegg.com/](http://www.newegg.com/) and browse around to see what is available. Cases and motherboards should be no problem.

If I were to design a system, I would get an Intel Core 2 Duo (or Quad) processor and a motherboard that accepts it, and has room for 4 GB of RAM, although I wouldn't get that much to start with.

I would get WD hard drives, Maddog Multimedia DVD Burners, and Kingston RAM, because I like the prices, quality and my experience with these companies.

I would centre the computer around the CPU, find a motherboard to go with it, then get the case.

---

### Post by inversekinetix on 2007-11-26
everyone is suggesting expensive things without even asking what its going to be used for.

craziness

---

### Post by Crashmaxx on 2007-11-26
This should help you with the physical construction and give some useful tips:
[http://www.instructables.com/id/How-to-Build-A-Custom-PC%3a-The-Complete-n0ob_s-Guid/](http://www.instructables.com/id/How-to-Build-A-Custom-PC%3a-The-Complete-n0ob_s-Guid/)

Otherwise, this is the process I would follow for buying parts:

1. Decided what you want and need from it: What do you intend to do with it? Do you specifically want anything, like a small case, very quiet, RAID array, etc? How much would you like to spend?

2. Decide on a few key requirements from #1: Like you may decide you want a small case and a dual core processor, but otherwise want a cheap and moderate machine, that can be upgraded later. So then be able to say you need a Intel Core 2 Duo, a mini-ATX size board and case, and probably just want integrated graphics, but need DDR2 ram and a PCI-e slot, with a SATA drive. Just decided what specific features you want it to have here.

3. Find a motherboard that supports #2: So in this case, you would be narrowed down quite a bit and just need to find a good, cheap motherboard that has those features and good Linux support. This will make you really have a choice between just a few different models and all you need to do is choose the best value.

4. Buy the rest of the components: Now you are set with certain formats and just need to find the right size hard drive, decide how much RAM you're willing to buy now, and find a pretty case. Get the best processor you're willing to pay for, and get a DVD drive that does whatever you need.

5. Get any accessories you need: You may already have a keyboard mouse and monitor and want to use them. Otherwise, just get an LCD monitor of a size and price you like, and a keyboard and mouse that you like.

6. Put it all together: Now you're done buying stuff and just need to screw it all together. The guide posted above should explain all of this, but it close to self explanatory anyway. Start it and make sure the BOIS comes up, then install Linux.

And as far as Linux compatibility, pretty much the hard drive, DVD drive, RAM, processor, case, and power supply will work regardless. The motherboard will probably work most of the time, but some are better then others for having everything work, and the graphics and any wireless stuff will be the biggest hangups, make sure you get ones that will work. The monitor doesn't matter and nearly any keyboard and mouse will work, but many won't have the extra buttons and do-dads work, at least not out of the box.

The only other advice, is you probably want to get a barebones kit, which will have at least the case, power supply, and fans, but may also have a motherboard, processor, and even graphics or RAM. They are usually a good deal and come with other little bits you may need like cables and best of all you know everything in the kit will fit together perfectly. So they are a great thing to start with.

---

### Post by codypumper on 2007-11-30
I'm so sorry I haven't responded! I thought my thread was ignored and dead.

Thank you so much for the information.

A little more on my position:
I hope to build something within the same price range as an iMac, so a reasonable amount hovering at $1500.

Now, I do have passion for hardware. I know so, I just don't have much knowledge as of now. Although, I ensure you, its more than the average person.

Now, I've been on Newegg trying to (As Lostincyberspace had said, although I did it before I knew he had said.) get a list of parts, and continue tweaking the configuration until I'm completely happy. The tweaking hasn't really begun yet. I've been going to other sites (PCWorld, forums, cnet, and anything trusted that popped up on google.) and reading reviews on parts that are well rated in Newegg, and then end up picking one of the top part within the reasonable price range. Here's what I have so far:

-Motherboard:  ABIT IP35 Pro LGA 775 Intel P35 ATX Intel
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813127030](http://www.newegg.com/Product/Product.aspx?Item=N82E16813127030)
   I realize a couple of people recommended Asus motherboards, so any guidance in this category would be great.

-RAM-  G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231098](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231098)
  Some of the better RAM at a reasonable price, which is compatible with the mobo I picked out for now.

-Hard Drive- Western Digital
Western Digital Caviar SE WD800JD 80GB 7200 RPM 8MB Cache SATA 3.0Gb/s
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822135106](http://www.newegg.com/Product/Product.aspx?Item=N82E16822135106)
I didn't pick one with a lot of space, partly because we don't exactly have a huge media collection, and also because SSDs seem to be on a role right now. Correct me if I'm wrong please!

-Case (Seemingly less important, I know)  COOLER MASTER Centurion 5
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811119077](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119077)
I was aiming for cool and the ability to see the guts.

-Processor -  Intel Core 2 Duo E6700
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115002&Tpk=Intel%2bCore%2b2%2bDuo%2bE6700](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115002&Tpk=Intel%2bCore%2b2%2bDuo%2bE6700)
This one is questionable, but for the price it is really powerful, no?

Now I have not gotten to graphics cards, power supply, or Cd drive. For those, recommendations would be great. I was aiming for Nvidia with pci-e. 
As for power supply, thats the only part I don't understand as to compatibility.
The cd drive, I will just pick out a good brand dvd burner on sale.

Thanks, and sorry if anything I  just said sounds stupid/ridiculous!

Edit~ I hope to use it for moderate gaming, Internet, and hopefully some video editing, nothing major though. I'd rather it wasn't outdated to fast though.

---

### Post by codypumper on 2007-11-30
I take that processor part back. For about a hundred dollars cheaper I can get the E6600, which seems to be just as good.
Or, for 50 dollars less, I can get the [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103773](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103773)  AMD Athlon 64 X2 6000+ Windsor.
It claims to have more power, but I'll have to pick a different motherboard....

---

### Post by codypumper on 2007-11-30
I'm also considering:

Motherboard: 
 ASUS M2N-SLI Deluxe AM2 NVIDIA nForce 570 SLI MCP ATX AMD Motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131013](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131013)

Processor:
 AMD Athlon 64 X2 6000+ Windsor 3.0GHz
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103773](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103773)

The Windsor X2 is substantially faster GHz wise, and has "HyperTransport"
It is also a bit cheaper. Although, it would run hotter, not a big concern though, is it?

If anyone has a graphics card that works fantastically (PCI-e), please let me know!

---

### Post by codypumper on 2007-11-30
So, maybe the heat of the Windsor is bad (read more reviews).
Supposedly, it really doesn't run that fast, so I'm thinking that the 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115029](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115029)
Intel Core Duo E6750 would be best with the Abit motherboard I had picked earlier.
I'd really like to hear some thoughts!

---

### Post by malangaman on 2007-11-30
If you are going to give the pc serious use, I prefer to build, because so much of the problems are caused by incompatible hardware. When you build your own, you know exactly what is in there and can change it if you must.
The opposite of this is to buy an appliance and forever rely on others for help. Dependency of this type gets expensive.
Google each individual component for linux compatability. The internet has become the greatest information resource in the history of the world. Use it.

---

### Post by codypumper on 2007-11-30
Yeah, I'm quickly finding that out.
I would just like some feedback from Ubuntu users on hardware they have or suggest.

On a side note:
 
Graphics Card: GeForce 7600GT 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062)
Its a good price, nothing to outdated or serious. What do you think?

Also, I think I'm going to go with a Hp Lighscribe:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827140025](http://www.newegg.com/Product/Product.aspx?Item=N82E16827140025)

Now, as mentioned earlier, how do I pick out a good, compatible PSU?
Is the size the only compatibility issue?

---

### Post by -grubby on 2007-11-30
> **codypumper said:**
> Yeah, I'm quickly finding that out.
I would just like some feedback from Ubuntu users on hardware they have or suggest.

On a side note:
 
Graphics Card: GeForce 7600GT 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062)
Its a good price, nothing to outdated or serious. What do you think?

Also, I think I'm going to go with a Hp Lighscribe:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827140025](http://www.newegg.com/Product/Product.aspx?Item=N82E16827140025)

Now, as mentioned earlier, how do I pick out a good, compatible PSU?
Is the size the only compatibility issue?

well, I searched google for site:ubuntuforums.org nvidia geforce 7600GT and didn't seem to have problems in recent threads.
P.S. there is kind of a "hidden" menu-thingy for NVIDIA cards which you can run from the terminal and type ```
gksudo nvidia-settings
``` at least with mine. (it's a geforce 6200

---

### Post by codypumper on 2007-11-30
Ah thats, good to know. Thank ya.

Now, the only thing I really have left is the PSU.
Any help would be great!

---

### Post by Crashmaxx on 2007-12-01
Couple things, first, I'd recommend a Seagate hard drive if for no other reason then they have a 5 year warranty. And I would get something bigger then 80GB, with them being so cheap, I see no reason not to spend $15 more and get a 250GB at least.

For the PSU, I hear Antec is one of the best brands. You probably want something like 400w-500w and the right shape to fit in the case. Just don't get a cheap piece of junk and you will be fine.

---

### Post by codypumper on 2007-12-01
Thank you Crashmaxx, I'm going to take your advice.

 Seagate Barracuda 7200.10 ST3250410AS 250GB
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148262](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148262)

Then the PSU:

 Antec earthwatts EA500 ATX12V v2.0 500W Power Supply
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371007)

Okay, review time:

PSU[RIGHT]Antec earthwatts EA500 ATX12V v2.0 500W[/RIGHT]
[COLOR="DarkGreen"]Motherboard[RIGHT] ABIT IP35 Pro LGA 775 Intel P35 ATX[/RIGHT][/COLOR]
Video Card [RIGHT]GeForce 7600GT [/RIGHT]
[COLOR="DarkGreen"]Processor[RIGHT]Intel Core Duo E6750[/RIGHT][/COLOR]
Dvd Drive[RIGHT]Hp Lighscribe[/RIGHT]
[COLOR="DarkGreen"]Hard Drive[RIGHT]Seagate Barracuda 250GB[/RIGHT][/COLOR]
RAM [RIGHT] G.SKILL 2GB SDRAM[/RIGHT]

Any problems you see with this configuration?

---

### Post by codypumper on 2007-12-01
No suggestions at all?

---

