---
title: "HOWTO: Build an energy-efficient Ubuntu box"
date: 2009-06-06
forum: Tutorials
---

### Post by Bucky Ball on 2009-06-06
* Quick note and update: While this post is OLD and many of the components are outdated, the principles remain the same. The thrust of the thread is about saving energy, the environment and a few dollars by being responsible with how you compute. Please enjoy. ;)

[FONT=Comic Sans MS][SIZE=2]    [I]* For those of you wanting to leave a smaller environmental footprint and save a little cash whilst enjoying and exploring Linux computing ... 
* Skip to [/I][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]*the end of this post for a *[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]*list of *[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]*components used and a word on notebooks/netbooks.*  

**Disclaimer **
       I am not an agent of or employed by any company, organisation or component manufacturer. The thoughts contained in this post are mine alone and not endorsed by Canonical, Ubuntu, the Ubuntu Forums or staff.

        This post is in no way intended as a review of any particular component, nor is it a technical step-by-step on how to put the components in the box and connect them together. It is a guide for selecting energy efficient, environmentally responsible, quiet and cool components that will work with Ubuntu (and probably other Linux distros and Windows flavours, too). Hopefully it will inspire you to explore and expand on what I have discovered and share what you find with the community. 

**Short Rant ...**
A year (month, week, day?) is a long time in the world of technology and computing. I built this machine for under AU$1000, a more basic version could be cobbled together for around AU$700. You might be able to do it cheaper. Since this build at the end of February '09, newer versions of a couple of the components have appearred with design changes and improvements (notably the monitor). 

        In a few minutes this machine will be worth $50, like my old IBM Aptiva P3 sitting in the corner (well, maybe it's not worth that much)! So you may as well build something that is going to be functional for as long as possible. As we become armed with ARM processors and terabyte SD cards, this machine will become obsolete but still upgradeable and useful for some years. I'm hoping we can continue to update this thread with the greenest and most energy-efficient hardware as things progress and it becomes available.

I support manufacturers taking a responsible approach to the environment in design, energy efficiency, manufacture and disposal of their electronic components. Most computer users of whatever OS flavour will perhaps put some thought into energy efficiency, environmental friendliness and cost effectiveness over time when buying a washing machine, but rarely seem to think much, if at all, about these things when buying or building a new computer or upgrading components. It doesn't seem to compute that we can be pro-active in the way we use resources when we compute (and save money, a fact, surprisingly, people overlook). 

    So, those of you wishing to build an environmentally responsible box with components available right now, read on for some hints ... 
[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
**Preliminaries**
Putting everything in the box is pretty straightforward now. Just remember: stay relaxed, plan, take your time and do some research on what you are about to do and *read the component instructions*. This is especially applicable to the motherboard, the trickiest bit. There is a bit of connecting up to do, so find your way around the MB first.  If you're really not confident, don't try. There is nothing stopping you doing the research and getting the right components for your job, though. Order the parts and get someone who is confident to put it all together (factor this into your budget). You'll pay less for a purpose built machine that's built to last and cheaper to run than what you'd pay for an 'off the shelf' box only coming close to the same specs. (Not that you would get a machine like the one below off the shelf; it would be a custom build so add more $). You'll also get that glow of achievement each time you use it! If you've done your planning the machine will do exactly what you require, use only the required energy, have less impact on the environment and save you money. 

        [CENTER]***
[/CENTER]
        
**Where to Start**
        With a piece of paper and pencil. Write down *exactly* what you want the machine to do. Think of everything. Remember, you can add and upgrade components later, but *only* if you've planned ahead and your motherboard is ready for that 'next generation' processor or that second PCI-e graphics card. If you one day hope to buy a third internal SATAII hard drive and your motherboard only has two SATAII ports ... you are looking at an external USB drive. Whoops. Didn't think of everything! Avoid having to buy another motherboard every two years and replace everything. This is bad for budget, environment, resources, and totally inefficient when you could have spent $25 dollars more for a board that could be upgraded down the track with a new processor and more RAM (and another couple of SATAII drives).

        Once you have a list, you can do some research and match the hardware to your requirements.

The GreenMachine I was about to build would be required to:

 1/ Print LightScribe media
    2/ Capture and edit home movies
    3/ Capture/digitise LP vinyl records
    4/ Run Skype
    5/ Edit stills/Print in colour
    6/ Email and surf the net
    7/ Listen to music
    8/ Watch DVDs
    9/ Have plenty of storage for vid/pics/audio
    10/ Run Ubuntu only
    11/ Be switched on for long periods in Australian conditions (this can mean very hot).
    12/ Be cool, quiet, energy-efficient and environmentally responsible

        ... with a budget *limit* of AU$1000. We can do that.

        [CENTER]***

[/CENTER]
        **What's in the box?**
        I usually build two or three machines a year. This year I again researched long and hard for components that were both energy-efficient and environmentally responsible. To add another level of difficulty, the components also needed to work under Ubuntu, in this case Hardy 8.04.2. All components were sourced in Australia.

        When buying equipment (especially monitors), I always check for an 'Energy Star' logo or sticker. More info here:

[LEFT][http://www.energystar.gov/index.cfm?fuseaction=find_a_product.showProductGroup&pgw_code=CO](http://www.energystar.gov/index.cfm?fuseaction=find_a_product.showProductGroup&pgw_code=CO)
[/LEFT]
        [LEFT]
And likewise, I look for an RoHS stamp, a UK initiative which aims to limit the amount of toxic materials used in the manufacture of electrical equipment:

[/LEFT]
        [LEFT][http://www.rohs.gov.uk/](http://www.rohs.gov.uk/)

[/LEFT]
        [LEFT]Let's start from the beginning: [/LEFT]

**1/ The PSU and case **        [LEFT]To help you figure out what size PSU you are going to need, Antec have a very useful configurator, but first figure out what you want the machine to do and what hardware you are going to need to achieve it, choose your components then plug the data into this configurator:

[/LEFT]
        [LEFT][http://www.antec.outervision.com/](http://www.antec.outervision.com/)

[/LEFT]
        [LEFT](* *Note: the results of this configurator apply to Antec PSUs, not other brands whose specs may differ.*)

[/LEFT]
        [LEFT]Every machine needs a solid, cool, energy-efficient power supply as this is where it all starts or where it can all end in sparks, smoke and dead or damaged components. Currently there are 85%+ energy efficient PSUs on the market, a marked improvement on the 70% and under of a generic 'silver box' power supply. The result of the generic PSU's inefficiency is that electricity you pay for becomes heat instead of power for your machine. In other words, it's wasted (unless you use your computer as a heater; there are more efficient heaters). This added heat and work can shorten the lifespan of internal components *apart* from the PSU as high internal computer temperatures will heat the motherboard and CPU, forcing fans and the system to work harder which forces the PSU to work harder causing more inefficiency and ... a vicious circle. The generic, off-the-shelf PSUs may also not have appropriate safety switches and are, IMHO, a little unsafe. When they die, they rarely die alone, usually taking another component or two, or every component in the box out with them.[/LEFT]
        [LEFT]
Look for the 80+ logo on your PSU, and for more info on the 80plus Project, go here:

[/LEFT]
        [LEFT][http://www.80plus.org/](http://www.80plus.org/)

[/LEFT]
        [LEFT]** Note: The majority of PSUs currently on the Australian market are 70% efficient or under, even name brands. You need to be specific and persistent when hunting down 80+ PSUs in AUS.*

[/LEFT]
        [LEFT]* Final word on PSUs: When dazzled by the 4Gb of RAM and the 500Gb hard drive for only ?$ at the local computer store, think of that unreliable silver box that is probably inside and the pretty sparks when box goes bang. If you do find a good value deal 'off the shelf', ask about the PSU or factor in the price of a good replacement PSU. When I bought my case I replaced the brand new silver box that was in there immediately. It sits under my desk in case of emergency. 

[/LEFT]
        [LEFT]Some otherwise sweet cases come with inefficient and over-powered PSUs pre-installed, and more power is not always better. (Something about killing a mosquito with an elephant gun? Waste of bullets and gunpowder.) Sorry to rave on about PSUs, but when aiming for energy efficiency a good PSU is of utmost importance.

[/LEFT]
[CENTER]*

[/CENTER]
        [LEFT]I landed a good price on an Antec NSK6580. This case has Antec's EarthWatts 430Watt power supply pre-installed. Antec have a wide range of cool and quiet cases with and without PSUs from their 80+ EarthWatts range:

[/LEFT]
        [LEFT][http://www.antec.com/Believe_it/product.php?id=MzY=](http://www.antec.com/Believe_it/product.php?id=MzY=)

[/LEFT]
        [LEFT]** If you want to use the Firewire socket on the front of this particular case but have no Firewire on your MB, read on (1A) for a remedy. If not, skip to 2/ The Processor ...*

[/LEFT]
    **1A/ Digression - Antec Case and Front Panel Firewire**
[LEFT]As it turns out, the Antec NSK6850, as well as having audio sockets and two USB sockets on the front panel, also has a Firewire socket. The internal Firewire lead from the panel socket ends in a 10 pin female header which would normally connect to a Firewire header on the MB. Motherboard has no Firewire header onboard so obviously this wasn't possible. Solution? The Antec case manual informs me I can get an Antec adapter; fits the ten pin header and the other end is a regular Firewire plug. I order the adapter from a local computer shop and a PCI card with 4 x USB and 2 x Firewire external and an internal USB and Firewire socket. When the adapter arrives I put it all together, plug my DV camera in and front panel socket works fine. 

[/LEFT]
        [LEFT]"Why not use one of the two Firewire sockets on the card around back?" I hear you ask. Because there is a perfectly good socket conveniently placed by Antec designers on the front panel! Ludicrous question! :p [/LEFT]

**2/ Processor**        [LEFT]I chose the 45watt AMD 4850e:

[/LEFT]
        [LEFT][http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=426](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=426)

[/LEFT]
        [LEFT]This is more than adequate for the job and uses around 20Watts less (about a third) than its closest counterpart in the AMD line. Thus, cooler and requiring less energy. (Power consumption of ARM processors, as they become more powerful and common in laptops and desktops, will make 20W look massive. First steps: [http://www.slashgear.com/wistron-n900z-smartbook-sub-200-arm-netbook-0345776/](http://www.slashgear.com/wistron-n900z-smartbook-sub-200-arm-netbook-0345776/).)[/LEFT]

**3/ Motherboard        **[LEFT]I had been looking at ASUS motherboards, mainly because of the company's apparent ethical attitude. When I went to pick up the hard drives I asked if the store had any in stock and sure enough, they had something in the exact price range and one left, the ASUS M2N68CM:

[/LEFT]
        [LEFT][http://www.asus.com/Product.aspx?P_ID=KWQH5MxS6HH3nWjy](http://www.asus.com/Product.aspx?P_ID=KWQH5MxS6HH3nWjy)

[/LEFT]
        [LEFT]The only thing it didn't have was IEEE-1394 (Firewire). See 1A for a remedy specific to this case/MB combination.

Take note, there is an issue here that may or may not concern you. I wish I'd have researched this a little better rather than expecting there might be a work around. Built into this board is an SD chip which boots into a version of Linux, which is installed on this fragment of technology. Great, you might think. If you are not using Windows, think again. *This fast boot feature will not work with Linux, only with a Windows install.* They have a special name for the feature but I can't remember it. For the functionality of the feature? Who gives a toss, really. But for creating a situation where people are forced to use Windows to access it and therefore creating seperation and exclusivity, thumbs down from me and no more ASUS (apart from the optical drive that's also in this box!).

[/LEFT]
**4/ Storage        **[LEFT]I chose two Western Digital 500Gb GreenPower hard drives. WD claim these drives can use up to 40% less energy than their non-green counterpart (WD 500Gb Caviar). These drives are cool, quiet and efficient. I have one in my desktop and one in a fan-less Coolermaster X-Craft external case. It runs cold. Check the full GreenPower range here:

[/LEFT]
        [LEFT][http://www.westerndigital.com.au/en/products/products.asp?driveid=576](http://www.westerndigital.com.au/en/products/products.asp?driveid=576)[/LEFT]

**5/ Monitor        **[LEFT]The right monitor took some finding, main reason being there seems to be as many on the market as stars in the sky(!). Eventually I found the Acer X193HQ 18.5" 16:9 monitor. Acer's webpage tells us the monitor uses 17W on, less than a watt on standby, is Energy Star stamped and an all round sweet view. When I got the monitor, the spec in the manual is 27Watts but the 0.64W standby figure remains the same.  This could be time compressing again and Acer very well could have changed the spec on the latest model to 17W when I blinked. Drop 'em an email if you need to find out for sure.

[/LEFT]
        [LEFT][http://www.acer.com.au/acer/product.do?link=oln23g.redirect&changedAlts=&kcond5e.c2att92=901&CRC=2373534056](http://www.acer.com.au/acer/product.do?link=oln23g.redirect&changedAlts=&kcond5e.c2att92=901&CRC=2373534056)

[/LEFT]
        [LEFT]* *Update**: I was so impressed that I bought two of these monitors and the newer manual does indeed state they are 17w on, 0.64w stby. They are also TCO'03 labelled and passed now*:

[/LEFT]
            [LEFT][http://www.tcodevelopment.com/](http://www.tcodevelopment.com/)
[/LEFT]

**6/ Wireless Card        **[LEFT]Wireless was required because the distance from where the machine was going to live to the router was way too far for cable (and inconvenient). The main issue is getting a card that is going to work 'out of the box' with whatever distro you are using, and when it comes to Ubuntu, I am aware of the nightmare journeys people (myself included) have had getting wireless up. Thankfully, this situation continues to improve, but nonetheless, I researched this component diligently! To be on the safe side with the distance (and compatibility), I ended up going for the TP-Link TL-WN651G which claims to function over 200 metres:

[/LEFT]
        [LEFT][http://www.tp-link.com/products/product_des.asp?id=17](http://www.tp-link.com/products/product_des.asp?id=17)

[/LEFT]
        [LEFT]** These cards use Atheros chipset * *[/LEFT]
        
   [LEFT]**7/ Colour Printer**[/LEFT]
        [LEFT]When it comes to techno-gadget environmental footprints, colour printers leave a rather large one. They are not so bad in the electricity stakes, but they are resource hungry and feeding them causes problems to do with  chemicals, paper and getting both created and to the printer. An unfriendly beast, but required for this build. 

[/LEFT]
        [LEFT]HP seemed the choice here because of their history of support for the open-source community and their stance on environmental issues regarding manufacture. HP Colour Laserjet CP1215:

[/LEFT]
        [LEFT][http://h10010.www1.hp.com/wwpc/au/en/ho/WF05a/18972-18972-3328060-3328070-3328070-3422474.html](http://h10010.www1.hp.com/wwpc/au/en/ho/WF05a/18972-18972-3328060-3328070-3328070-3422474.html)

[/LEFT]
        [LEFT]The printer was bought separately and *not* included in the AU$1000 budget.[/LEFT]

* Note: Even though HP claim this printer works fine with Ubuntu, the Ubuntu Compatible Printer list is not so sure (and advises the foomatic driver rather than the HP one). When the owner got the computer to Melbourne and plugged it in, the printer wasn't working (although fine here). We have tried over the phone and with emails to fix itbut to no avail. See what I can come up with when I go over there next month and update then.

[LEFT]**8/ RAM & Optical Drive**[/LEFT]
            [LEFT]A 4Gb kit (2 x 2Gb) of Kingston RAM and an ASUS IDE LightScribe CD/DVD combo drive. With all the components amassed on and around my _kitchen table_, which was_ covered with a protective old towel_, I was ready to build and power up! How are you going so far ...?

[/LEFT]
    [CENTER]***[/CENTER]
                [LEFT]**Putting it all together**
After planning, researching and selecting components, you should have a good (and comprehensive) component list. Start purchasing what you are going to need or researching what you haven't yet nailed down in an attempt to get all the components in one place. This can happen in dribs and drabs or all at once. You might see something perfect when you are picking up something else. An item might pop up on special that you just happen to be looking for. You often find the best prices as you are researching the best components for the job. Make a bookmarks folder and put all the info in there for later refinement. I make a folder for the build and folders inside that for each component. Easy to forget which page was the one when you've looked at fifty.

[/LEFT]
        [LEFT]For me, from component list to having all the components in the one place usually takes at least two weeks. This involves tracking down the components and finding the best price, picking things up and receiving things in the mail. My own computer took about a month from component list to the magic moment when I had all the bits. You might like to build it as things arrive (usually depends on prices and availability). If so, *buy the case first* and add as things get there. I prefer to wait until it's all there and go for it. 

[/LEFT]
        [LEFT]I'm am not going into a 'How To ...' on the nuts and bolts of building a computer here. There are many sites that cover this better than I could. I am primarily going to cover my experiences with getting the hardware up in Ubuntu 8.04.2, and it was pretty much a breeze(y!) despite my wrestling with the monitor for four days before realising all was fine originally ...![/LEFT]

**1/ Install        **[LEFT]Once everything was in the box and connected, I booted into the BIOS a few times and let it sit for a couple of hours, checking the temperature, voltages and fan rpm every now and then. It is a good idea to boot into the BIOS and check the temperature until it is consistent (not getting higher for about half hour say), but the lengthy pre-install monitoring is not necessary. I like to make *really* sure all has gone okay with the heatsink on the CPU fan and the CPU.

I have a thing about internal computer case temperatures (get a life)! Usually I use Artic Silver thermal paste and a custom fan. This time I used the thermal *pad* on the AMD fan that came with the 4850e processor. One thing I can say is that it really shouldn't be sticky like that (the thermal pad, that is). You will find that Arctic Silver (and some other thermal pastes I believe) do not adhere; I've removed CPU fans without dislodging the processor underneath using the paste. Next time, I'll go for the usual with the custom fan and Arctic Silver. If you have the folding, AU$50 for a decent fan (or fanless, noiseless heatsink) is worth it. From experience I can say that it will take your CPU temperature down by anything from five to ten degrees (this depends on a few factors). The Arctic Silver thermal paste needs to get through about 50 heat cycles (max temperature to room temperature) before it reaches its full cooling potential. And less heat means ... ? I forgot, there will be questions ... :)

[/LEFT]
        [LEFT]Let me just mention at this point that after humming along for a couple of hours on a 30C degree day, admittedly just sitting at the BIOS screen, the MB temp is 35, the CPU is 37 and the fans are blowing out cool air! I can hear the birds and insects outside over the faint hum of the computer. This is a cool, quiet machine.

[/LEFT]
        [LEFT](* Edit: I have just dropped the same Antec Earthwatts 430W PSU in my wife's desktop and the MB temperature has dropped by about 16C, the CPU about 10C - I did give it a blow out with a can of compressed air while I had the side off to install the PSU so undoubtedly that helped a, too.)[/LEFT]
            [LEFT]Happy with the consistent temperatures, I popped the Ubuntu install CD in to the optical drive, checked the CD for defects, then hit 'Install'. The install was fine til right at the end when I was confronted with a blank screen rather than a 'Remove CD and reboot' message. Hmm. Rather than screwing around, I re-installed with the same CD. Installed fine this time and the machine is still humming along from all reports (it lives in Melbourne, about 750kms away). Go figure.

[/LEFT]
**2/ Configure Hardware        **[LEFT]* A quick word for *anyone with a fresh install* and using a wireless card: *Make sure you have an ethernet cable plugged in*to your computer *when you boot up first time!* *Setting up* the *wireless* will be a whole *lot easier*. 

[/LEFT]
        [LEFT]Hard drives, most CPUs, RAM, PSUs, optical drives generally work just fine with Ubuntu, so I will only cover the components that are known to be problematic with Ubuntu installs.

[/LEFT]
        [LEFT]Once at the desktop, I installed ubuntu-restricted-extras, I downloaded whatever updates were waiting and the wireless card was picked up. I was offered the restricted drivers for it, I accepted, installed and the card was up. Next, my AP (Access Point, my router) and another network were discovered. I selected my AP, was asked for my WEP key which I dutifully input. Done. From first boot to having the wireless card up in less than five minutes. It took me five months with a Broadcom card in 7.04 over a year ago (and I never did succeed) so this is definite progress (*Note: The Broadcom card now also sets up on a fresh install in about five minutes with Hardy 8.04 and B43).

[/LEFT]
        [LEFT]Confirmed: TP-Link likes Ubuntu. xxx

[/LEFT]
        [LEFT]I got the planning right. On first boot, I was online via the ethernet cable, was being offered updates and life was sweet. The widescreen was detected and filled correctly, but I became obsessed with the resolution. 

[/LEFT]
        [LEFT]The native resolution for the screen is 1366 x 768 but Ubuntu had defaulted to 1280 x 800. It looked okay but ... so I changed it to 1280 x 768 and it looked great. Not satisfied with near perfection, I literally spent four days ripping my hair out trying to get the correct resolution. I eventually did get 1366 x 768 and ... it looked terrible for some reason! So I changed back to 1280 x 768. Widescreen DVD looked fantastic so that was the main thing. Desktop looks normal, nothing stretched or distorted, so I was satisfied.

[/LEFT]
        [LEFT]Confirmed: Acer X193HQ monitor likes Ubuntu.

[/LEFT]
        [LEFT]* Odd thing: the two monitors I bought more recently were offered 1366 x 768 on one machine and 1360 x 768 on another first time I plugged them in. This would have something to do with the differences in the hardware and configurations of the two machines I guess, but maybe it has something to do with the newer monitor also.

[/LEFT]
        [LEFT]Lastly, the printer. After a bit of research, I installed HPLip (available in the repositories), followed my nose and the printer was up and running and printing a colour test page in no time. 

[/LEFT]
        [LEFT]Confirmed: HP CP1210 Colour Laserjet printer likes Ubuntu (but didn't like it after a 750km drive to Melbourne ,,,)

* Update: As mentioned earlier, the printer has since be problematic and I'll post a fix when I get over to the machine in a month or so and (hopefully) find one. It did work when it was here so I don't doubt it will once more.
. [/LEFT]
        [CENTER]***

[/CENTER]
        [LEFT]**Final Words ...**
[/LEFT]
        [LEFT]* Why don't manufacturers label their products as compatible with Linux when they are? There is no problem emblazoning products and websites with 'Compatible with Vista' and 'Works with Microsoft this, that and the other' or 'System Requirements: Windows or Mac OS'. There are no doubt complex (or simple?) reasons for this and that question is the subject of another post. Because of this anomaly, I found out most of this stuff works with Ubuntu and Linux not from the manufacturer's websites, most of which said little or nothing about Linux, but through research and users findings posted on the web. Thank goodness for community spirit, ay? And thanks to all of you for putting your experiences out there.

[/LEFT]
        [LEFT]* You may have noticed the absence of a PCI-E x16 graphics card in this machine. It wasn't required and can be added later if my mother-in-law decides to get into any heavy 3D gaming(!). Seriously, these chew up juice and no company has really managed to decrease the power requirements of a decent, powerful gaming/graphics card to date. Not sure one's even thought to do so. Gamers, animators and others may be able to enlighten me on this. If you have the RAM to share with it, onboard graphics chips are becoming more than adequate for most users. 

 [/LEFT]
        [CENTER]***

[/CENTER]
        [LEFT]As stated at the beginning, planning is key to getting your component selection right and saving some money and power. If you are running an optical combo drive, one SATA hard drive, two USB slots and a P4, you are hardly likely to need a 650W energy-guzzling silver box humming away in the corner most of the day. If this is your current situation, get the money somehow and replace your PSU with an 80plus 350W PSU immediately! Then check your next power bill. Oh, and try to dispose of the old PSU responsibly. (If you can't and it's working, give it away. By the time it dies,  a more effective way of disposal, reuse/recycling or burial may have been developed.)  :)

[/LEFT]
                [LEFT]I hope this thread inspires users to think about what goes in the box and the effects of their hardware choices. Components are toxic, dangerous, don't grow on trees, are difficult to dispose of and consume energy their entire lifespan, from mine-site to landfill. On the other hand, conditions and awareness improves and as consumers we can make a conscious effort to minimise the environmental impact of our computing. By doing so we also demonstrate our support to/for manufacturers that make some effort toward greener, environmentally responsible component manufacture and disposal.

[/LEFT]
        [LEFT]* Don't hesitate to post corrections, updates of green/eco-friendly/energy-efficient components, developments, comments and anything else you feel is relevant. This thread can be an online time capsule of computing hardware technology. It will be interesting to compare the machine described here with how we are computing in twelve months. 

[/LEFT]
        [CENTER]***
[LEFT]
[B]Afterthought: Building a Notebook/Netbook
[/B]About all there is to say regarding this is: Don't bother. Problematic to say the least. The parts are not easily available, if you can get them at all. Besides which, mobile computing is one area where manufacturers are making definite inroads into power saving for one very good reason: Batteries. New battery technology will one day explode on to the market with extremely long-life renewables and rechargeables (and possibly power-sources we hadn't imagined), but for now, how long you can go before recharging is  everything. 

[http://www.csiro.au/partnerships/LiBatteryPartnership.html](http://www.csiro.au/partnerships/LiBatteryPartnership.html)

[http://www.pcworld.idg.com.au/article/259749/hp_extends_laptop_battery_life_24_hours](http://www.pcworld.idg.com.au/article/259749/hp_extends_laptop_battery_life_24_hours)

Primarily, what has happened is batteries have improved a bit and the components have improved a lot. Manufacturers have a vested interest in how long their device will run before recharge; could be the difference between selling a machine or not. So components have become energy misers, out to squeeze the last second of power from your battery. Great news, because this technology can be used in other areas of computing.

As mentioned, ARM processors are creeping into netbooks extending battery life further and by the time an ARM has the processing grunt of an Atom, maybe twenty four hour turnaround will be old news; a week may not be unusual. Maybe we'll have a power source other than the conventional battery. If you couple a 2W dual-core ARM processor with a new power source, say four times more effecient than a 12V battery by today's standards ... and let's not forget the terabyte SSDs and SD cards. Is a month out of the question? Six ... ?

[http://www.osnews.com/story/21031/ARM_Shows_Prototype_Netbooks](http://www.osnews.com/story/21031/ARM_Shows_Prototype_Netbooks)

Basically when buying an energy-efficient laptop: Check how long the battery lasts before it needs recharging.  This will generally reflect the efficiency of the components inside the device (screen, drives, graphics). [FONT=Comic Sans MS]Do your research and find out times users and reviewers are getting as the manufacturer's guestimate is rarely correct in the real world.[/FONT] SSD instead of hard drive adds considerably to battery life, but there are other issues regarding this beyond the scope of this thread. Read more here:

[http://www.dvhardware.net/article6148.html](http://www.dvhardware.net/article6148.html)
[/LEFT]
 
***
[/CENTER]
        [CENTER]:)

[/CENTER]
[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]Late Feb 2009 - [/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]Green Machine Component List:                                        [LEFT]* Acer X192HQ 18.5" monitor
* TP-Link TL-WN651G wireless card
* 4Gb kit Kingston RAM
* Antec NSK680 case with Earthwatts 430Watt PSU pre-installed
* 2 x Western Digital GreenPower 500Gb hard drive
* USB/Firewire PCI card with internal USB and Firewire socket
* Antec adapter to connect front panel Firewire socket to internal header on PCI card
* ASUS M2N68CM motherboard
* ASUS DVD/CD combo optical drive

[/LEFT]
                [LEFT]... all amounting to a tickle under AU$1000.Then add:

[/LEFT]
        [LEFT]* HP CP1215 Colour Laserjet printer

HP make about fifty devices that need the HPLip package PLUS the hp-plugin. I would go for another HP which works 'out of the box' using HPLip rather than having to load the additional hp-plugin which has been problematic (which worked first up but since transporting and reconnecting, for now, we can't get working again). HPLip is installed as part of Ubuntu (but not hp-plugin) so when you plug in your HP, it should be recognised and setup automagically. 

Will update printer installation in a month or so when I am with the Green Machine and I can figure it out. If anyone has any suggestions regarding how to get this printer working again, please post here:

[http://ubuntuforums.org/showthread.php?t=1149560](http://ubuntuforums.org/showthread.php?t=1149560)

[CENTER]
[/CENTER]
[/LEFT]
[CENTER]
[/CENTER]
[LEFT][CENTER].
[/CENTER]
[/LEFT]
[/SIZE][/FONT]

---

### Post by Noahod on 2009-06-06
Cool post. 

Few things, 

Most of ATI's newer graphics cards do power-mode switching built in, eg, they underclock & undervolt when not used for 3D. They still chew a lot more than intel onboard though. 

Also switching to a caviar green drive may have been a bad compromise for a desktop, as Hard drives don't use that much power overall.. A caviar black uses a lot more power, but total power is still 8.4W (load) vs caviar green (5.4w) and caviar green is a lot slower for desktop use. 

As for stamping linux compatible on products, I think the main problem with that is the lifecycle of linux. If you certify your products for windows, you are certifying them once every 5+ years or so. For Linux, there's a new ubuntu every 6 months, and a new kernel every month or so. There's also so many different flavours of linux, which one would you certify? Then there's the problem of support.. 

Curious also why you chose a laser printer? Don't they use a lot more power than inkjet? The HP website lists it as 11W standby, and 290W! printing..

Wondering also if you have measured the standby power of any of this gear using a meter yourself?

Great post though, I'll have to look into these certifications I knew nothing about, 80+ etc. 

Thanks

---

### Post by Bucky Ball on 2009-06-07
Thanks for the input Noahod. No, haven't checked standby with a meter (not really my area).

I had nothing to do with the printer choice (apart from the compatibility issue). This was the one my M-in-law had the heart set on, so that was entirely their decision and not included in budget or my build. I added and setup after completion.

---

### Post by Ganesh Srinivas on 2009-06-07
Thanks for the post. I'm planning to build a new computer soon enough. Since I don't have a big budget, I'm willing to use a few parts from my current PC. Can you tell me which parts I should use and which ones I should not?

I'm very concerned about the presence of toxins in computer parts and other electronic goods. Can you please give me links to sites that talk about this issue and perhaps, talk about how to solve it?

Thank you so much. :)

---

### Post by Bucky Ball on 2009-06-07
Ganesh, you're welcome.

1/ As for parts, legislation varies wildly from country to country; from just throwing in a domestic bin (becomes landfill) to law with serious penalties for not disposing of correctly (usually a council collection centre for recycling). Find out what your options are.

This question is a double edged sword environmentally. On the one hand, it uses more energy whilst in use, on the other, if you replace, it may or may not be recyclable (and that uses energy too). 

In my opinion, if it's not broke, don't fix it. In other words, in all cases (except PSU and, if you are using a CRT monitor and can afford to swap, monitor), if you are happy with performance of a component, why change it? When it dies, dispose of responsibly and replace with something friendlier.

If components are working but you really do want to replace, see if you can make up a functional low-spec computer with your old bits and give it to a cousin, aunt, family member, friend, charity or somewhere that needs one so the parts can be used for as long as possible. Who knows; they may have some old parts too and between you, you might be able to make a half decent, usable box and give that to someone who needs it!

2/ Toxins in computer manufacture and disposal are a big problem, so your concern is definitely warranted. The RoHS link in the HOWTO is the one to start with. Hopefully, some of their policies will be internationally binding one day soon. The TCO Development link in the post you may also find of some use.

As in some other technologies, some manufacturers are taking on themselves to take a responsible attitude on this (rather than/before they are forced by legislation) and I advise going to component manufacturer's sites and seeing what their stand is on issues environmental (if they have one). Email them for more detail or with feedback on your findings. 

I hope this is of some help and good luck with the build when it eventually happens. :)

---

### Post by Noahod on 2009-06-07
Also, before you dispose of any computer gear, check if there are any recycling centers.. I was really surprised to find that there are so many here in Sydney, and no-one knows anything about them. 

Some will have special processes where they can actually recycle each individual component on a board.

---

### Post by Bucky Ball on 2009-06-07
Exactly Noahod. I was also surprised to find that if you have enough old stuff, there are places that will actually pay you for the privilege of picking it up to recycle what they can and sell it on. There's money to be made in them there recycling plants (And probably by digging through landfill!).

---

### Post by dawnlove on 2009-07-18
I have build a 12volt (i have a 12v solar stand alone system as well as a 3k grid intertie solar) computer. It's a atom x2 itx with 95% efficient power supply. I run xubuntu 9.04 (I understand 9.04 has atom kernel)
  I'm @ coffeeshop on my eeepc but if you want to see/hear more let me know

---

### Post by binbash on 2009-07-18
There is also WattOS, an ubuntu based less energy disto : 

[http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by Bucky Ball on 2009-07-19
Dawnlove, yea. Bring it on.

Binbash, will be looking at that link when I have a little more time.

Keep it coming, people. :)

---

### Post by anonymous_user on 2009-07-19
EVGA has a lower power 9600GT:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130485](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130485)

Also with Powermizer, NVIDIA cards run at lower speeds when idle (2D) anyways.

And one comment: I wouldn't quite agree that the Acer monitor likes Ubuntu. I mean it uses an odd resolution that you couldn't even get.

---

### Post by Bucky Ball on 2009-07-19
> **anonymous_user said:**
> 

And one comment: I wouldn't quite agree that the Acer monitor likes Ubuntu. I mean it uses an odd resolution that you couldn't even get.

Yes, but I think I mention in an update there that I bought two of the same monitors for my wife and I, plugged them in and ... they were automagically set at 1360-768! Go figure.

Funny, I am actually sitting at that very same GreenMachine right now and people have started posting on this thread for the first time in ages. I have been over in Melbourne for a week tweaking it for the in-laws and generally getting it to purr and giving them some tips. The machine and Ubuntu themselves are going well, it is mostly hardware issues they have been having (read incompatible purchases from before my mother-in-law went Ubuntu).

---

### Post by /usr/sbin on 2009-07-19
Nice guide, thanks

---

### Post by samden on 2009-08-12
I note that your primary consideration is electricity consumption while you are using the computer. You do not appear to consider the energy consumed during manufacture - which could be considerable. It is vital to consider the lifecycle environmental effects rather than the immediately visible effects.

Furthermore, for me in New Zealand, the majority of the electricity I use is generated through hydro, so is eco-friendly. But the majority of the electricity used to manufacture a computer in China or other countries is likely to be from coal. This exacerbates the effect even more.

The best way of having an eco-friendly computer is NOT to make a new computer at all - because the manufacture of all those new "eco-friendly" components for you is not particularly eco-friendly.

For example, an LCD screen may use less electricity. But because it has used a large amount of electricity and other resources to produce, if you want to have the minimum resource consumption you'd probably be better off actually using a second-hand CRT.

The same logic goes for all other consumer products - for example, you are far better off "recycling" a second-hand car for another 10 years than buying a new hybrid - sure your fuel consumption will be lower with the hybrid, but the total lifetime resource use will be much higher. You won't look like a cool "greenie" with a snazzy hybrid, but the reality is you are probably far more eco-friendly than the hybrid driver.

The big environmental benefit of Linux is therefore that it can keep older machines running for longer.

The net result of all this is that the cheapest option is usually the most eco-friendly. This is because the cost of something is roughly a measure of the resources used to produce it. A new computer (or car) is expensive to pay for the resources used to produce it - all the electricity, raw materials, labour etc. A second-hand computer is cheap because the previous owner paid for all that and you are getting it without causing any further consumption of resources.

Therefore the cheapest option (a second-hand computer or car) is far more eco-friendly than the more expensive "green" option (a new computer or car using snazzy efficient components) - despite the old computer being noisy and using more electricity, and the old car maybe producing a bit of smoke now and then.

---

### Post by Bucky Ball on 2009-08-13
Samden:

Hmm, I quote from the HOWTO. You might like to go to these websites and re-read them:

> [LEFT][FONT=Comic Sans MS][SIZE=1] I look for an RoHS stamp, a UK initiative which aims to limit the amount of toxic materials used in the manufacture of electrical equipment:

[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=1][http://www.rohs.gov.uk/](http://www.rohs.gov.uk/)

[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=1]*TCO'03*:

[/SIZE][/FONT][LEFT][FONT=Comic Sans MS][SIZE=1][http://www.tcodevelopment.com/](http://www.tcodevelopment.com/)[/SIZE][/FONT][/LEFT]
[SIZE=1]
[/SIZE] [/LEFT]
I make it absolutely clear that if you can't use your old components yourself there is always someone that can and you should attempt to give any operational hardware a good home. If you look it is easy to find folks that can use it. I agree, recycling is what you might call a 'last resort'. Why do people upgrade at all if their components are still working? Well, they do, and if they do they should attempt to do so responsibly (IMHO).

I just yesterday dropped back a machine to a family of five kids. It was blue screening in XP, doing odd things. They were going to throw it away and I said, "Give me three days with it." Turns out only needed new battery and re-install. Now dual-booting XP and 9.04 with all Edubuntu packages. An old Compaq EVO 51S; 80Gb drive, 512mb RAM, little flat-screen. Works a treat and is absolutely perfect for what they need. 

I've been thinking of getting some kind of club together where we make operational machines out of everyone's unwanted obsolete bits, whack on a flavour of Ubuntu and hand 'em out to those that needs 'em for eductation, employment skills, whatever!

Hydro-power? Half your luck. I'm all for hydrogen myself. :)


Chang_m33:

Yes, I have built quite a few now! Dive in and give it a try, and as wisely reiterated previously, work out what bits you can use, what bits no longer work and what you can give away or sell of your old rig before buying stuff. Good luck.


Thanks all for you comments. :)

---

### Post by samden on 2009-08-13
If you need a new machine, then by all means go for it and build to your specifications. It may well be more eco-friendly than some other new ones - but I thought I'd point out that an old one is even better. Glad you appreciate this already!

Hydrogen is not a way of generating power, only of STORING electrical energy (you need electricity to make hydrogen). You still come back to hydro vs coal vs nuclear vs wind etc. Then you can consider hydrogen vs batteries to store it. Hydro-power and hydrogen are two completely separate issues.

> I've been thinking of getting some kind of club together where we make operational machines out of everyone's unwanted obsolete bits, whack on a flavour of Ubuntu and hand 'em out to those that needs 'em for eductation, employment skills, whatever!
I've been thinking the same idea, but considering how I could make a sideline business out of it (donating some profits back to FOSS projects of course!). The margins would be pretty small though. Maybe your voluntary idea would fly more.

---

### Post by TheTank on 2009-08-14
Nice topic.
I have actually built up a similar machine, though with a different antec case, a gigabyte board, a scythe ninja cpu cooler (which can be cooled passively) and a samsung hdd.
In order to really get the system quiet I switched the antec fan against a scythe.

I had initially wanted to hook up my 2 monitors to the onboard card but this caused problems (the gigabyte I have has an ati) so I got a cheep passive geforce 7600 from ebay.

It is running cool and quiet with just two fans (psu and case).

---

### Post by matthewbpt on 2009-08-15
I built myself a nice new machine last week, while I didn't follow this guide as I just found it but I think it's quite energy efficient, I'm not sure about the PSU though. I bought a mini-ITX Zotac 9300 wifi (not the Zotac ION because I wanted a bit more processing power than the intel atom) with integrated nVidia graphics (VDPAU capable!), an Intel Pentium Dual core 5200, WD Green SATA HD, Sony Optiarc SATA DVD+/-RW, and a Morex 668 case with 200W PSU (cheapest mini-itx case I could find), 4 GB DDR2 Corsair Memory (2x2Gb for dual channel mode). 

It's the first PC I've ever built but it has turned out great. Oh I also got a Acer X233H, I think it's the same as yours just larger (23inch), I'm going to use this as an desktop/HTPC. Ubuntu installed on it flawlessly except for the wifi, but I quickly found a fix for that and had the wifi up and running in about 30 minutes so it wasn't any trouble, there's an open source driver for the card it just hasn't been included into ubuntu yet, but I found a deb for in online quite quickly. My old laptop which I've now sold was very inefficient energywise. An Hp dv9000, it was constanly running at very high heat (sometimes peaking at 90C!) had a battery life of about an hour, even undervolting didn't help much with the overheating. This new PC runs very cool and quiet I am very please =)

---

### Post by Bucky Ball on 2009-08-15
Nice job! There is nothing quite like sitting at and using a computer you put together yourself. Your story is proof that if you do a bit of pre-planning, read carefully, take your time and be careful, it is a pretty easy job at the end of the day and brings a lot more satisfaction than grabbing a box off the shelf which is usually not *quite* what you were looking for but close enough ... (not to mention you have a custom computer and usually save a bit of cash on the build).

Now you are ready to help your friends when they are after an upgrade or just want to re-configure their hardware. Nice job. :)

---

### Post by FiReSTaRT on 2009-09-03
Thanks for the guide. By the way, what sort of issues did you experience with the printer? We are thinking of getting a CP-1210 for colour printing. While I heard that HP is very linux friendly, this post is the only relevant post on this particular printer. Been using a Brother MFC7440n for b&w printing/scanning/faxing with great results. We just keep it off since we don't print often, but we print in huge batches.
A note on energy consumption. For home/SOHO use, you really don't print much, so the high energy consumption of a laser is not much of an issue. The benefits of it being more ink-efficient outweighs th minor increase in energy usage.

---

### Post by Bucky Ball on 2009-09-03
Hi, it was actually a CP1215 and once I got over to Melbourne and was able to have a look at it myself, I had it re-installed and running faultlessly in less than five minutes. Not sure what happened there as it was running fine when it left here five months prior. All good now. I imagine the CP1210 would respond in the same way as I think it requires the same additional add-on (which you are now invited to add on through HPs' new Linux driver installer - yay, HP!)

Hope that helps. :)

---

### Post by FiReSTaRT on 2009-09-04
Thanks both for the heads up and for the great writeup (even though I'm beginning to suffer from laptop addiction). I'll pray for it working identically to CP1215. Don't wanna end up with an expensive paperweight... Already got 2 Lexmarks (bought against my advice) in the office for that purpose ;) I'm glad that HP has a proper driver installer. They'll be the first our wallet-votes in the future.

---

### Post by Bucky Ball on 2009-09-04
I take it all back. Go here:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

There is no cp1210 listed, only the 1215. :(

This is the place to be for all things HP and open-source incidentally:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Hats off to 'em. My mother-in-law is very happy with the 1215 and it was about AU$200 in Feb '09. It superceded the 1210 as far as I know. Might pay to call or email HP. Good luck. :)

---

### Post by FiReSTaRT on 2009-09-04
Thanks again. I almost pulled the trigger on the buy. Back to the drawing board for me. Might just get an ink-jet instead as we don't do much colour printing (mostly the occasional map/profile for the report).

---

### Post by durand on 2009-09-09
Interesting read!

My notebook uses on average 30W with ubuntu and 23W with gentoo/crunchbang. For me, the power usage is more about energy efficiency rather than just conserving battery life since most of the time, I just leave it plugged in with the battery out. The only problem I really have with this notebook (Dell Vostro 1710, Nvidia 8600M GS) is that the hard drive is pretty slow (5400 RPM). I  mean, it's great for normal work and even data intensive tasks but it is a real bottleneck when booting up ubuntu. Gentoo and chrunchbang seem to be fine on that front.
Do you know if faster, more energy efficient disks exist for notebooks? I'm guessing that if I chose the 7200 RPM option when ordering, the power usage would increase by about 7W? I would love to swap it out for an SSD but I can't realy afford one on my student budget.

---

### Post by samden on 2009-09-09
If looking at a new drive, think carefully about whether your primary reason is performance or energy efficiency. 

If you need a better drive for performance reasons, go for it. 

But if you're chasing energy efficiency, you'll find that the cost of any item is roughly proportional to the resources used to create that item. Therefore although a new drive might use less electricity while running, it will have used more energy to build it (than if you just kept using your old one that has already been built). You are unlikely to ever recoup the purchase price in saved electricity, and likewise are unlikely to ever offset the higher energy usage during production through saved electricity.

Short version - a new drive, even a more "energy efficient" one, might give better performance, but will be both worse for the environment and worse for your bank balance, however much electricity you save.

---

### Post by durand on 2009-09-09
I gues you do have a point but if I do want a higher performance and more energy efficient one, would they exist? Or would SSDs be a better choise?

---

### Post by samden on 2009-09-09
Don't expect higher performance in practice from a SSD. Eventually they should get there but the current performance is similar or only fractionally better than a HD, e.g.
[http://www.computerworld.com/s/article/9080838/Performance_showdown_Flash_drives_versus_hard_disk_drives](http://www.computerworld.com/s/article/9080838/Performance_showdown_Flash_drives_versus_hard_disk_drives)

Furthermore, they may even use more electricity, although if you get the right one you can save power:
[http://www.tomshardware.com/reviews/ssd-hdd-battery,1955.html](http://www.tomshardware.com/reviews/ssd-hdd-battery,1955.html)

Their main advantage at the moment, as far as I can see, is safety if you drop the computer while the drive is spinning. 

If you're aiming to save money, save the environment, or boost your performance for an affordable price, don't go there yet.

---

### Post by durand on 2009-09-09
Hmm, good idea. My other thought was to use a CF card with an adapter for the /boot partition but I need to check if my laptop has a spare sata or ide connector.

---

### Post by Calmatory on 2009-09-13
I didn't read the whole thread, but given the hardware addict I am, all I can say is that keeping this kind of a thing up to date, with good bang for the buck and low power parts WILL be possibly an impossible task.

Good luck trying though. :)

> **samden said:**
> Don't expect higher performance in practice from a SSD. Eventually they should get there but the current performance is similar or only fractionally better than a HD, e.g.
[http://www.computerworld.com/s/article/9080838/Performance_showdown_Flash_drives_versus_hard_disk_drives](http://www.computerworld.com/s/article/9080838/Performance_showdown_Flash_drives_versus_hard_disk_drives)

Furthermore, they may even use more electricity, although if you get the right one you can save power:
[http://www.tomshardware.com/reviews/ssd-hdd-battery,1955.html](http://www.tomshardware.com/reviews/ssd-hdd-battery,1955.html)

Their main advantage at the moment, as far as I can see, is safety if you drop the computer while the drive is spinning. 

If you're aiming to save money, save the environment, or boost your performance for an affordable price, don't go there yet.


First of all, the article is almost 18 months old. SSD's are very fastly evolving area, anything older than a year can be considerd "old".

The thing with them is that they are expensive. Multi Level Cell(MLC) based drives are generally slower and cheaper than Single Level Cell(SLC) drives.

[http://www.guru3d.com/article/ocz-vertex-120-gb-ssd-review/](http://www.guru3d.com/article/ocz-vertex-120-gb-ssd-review/)

---

### Post by Bucky Ball on 2009-09-13
> **Calmatory said:**
> I didn't read the whole thread, but given the hardware addict I am, all I can say is that keeping this kind of a thing up to date, with good bang for the buck and low power parts WILL be possibly an impossible task.

Good luck trying though. :)

Hehe, know what you're saying. I figure I might update when I do a build (usually two or three times a year). That is when I generally spend way too much time researching what is current. I have a build coming up soon. 

It might also be interesting, in these times of rapid and accelerating technological change, to post a build once a year. A bit of a time capsule of technological advancement, evolving energy efficiency and methods of dealing with computer waste/obsolete technology (we hope).

Let's call this one 'Energy Efficient Build #1: 2009!'

---

### Post by gordintoronto on 2009-09-19
The CPU is no longer available in North America.  AMD has a single-processor 45 w unit, or up to a quad at 65 w.

A dual-processor Atom with the Ion video seems like the natural next configuration.

---

### Post by Bucky Ball on 2009-09-20
> **gordintoronto said:**
> The CPU is no longer available in North America.  AMD has a single-processor 45 w unit, or up to a quad at 65 w.

A dual-processor Atom with the Ion video seems like the natural next configuration.

Bring on the ARM I say!!

Thanks for the info and input. :)

---

### Post by FiReSTaRT on 2009-09-25
> **FiReSTaRT said:**
> Thanks again. I almost pulled the trigger on the buy. Back to the drawing board for me. Might just get an ink-jet instead as we don't do much colour printing (mostly the occasional map/profile for the report).
Just an update. I ended up buying a CP1215. Your best bet is to install is via the CUPS web interface. I had network printing via a print server set up within 5min on the first machine while I didn't know what I was doing and under 2min on the second machine. All that was needed was to specify the printer and the IP.
Compare that to the 2 Windoze boxes (XP and Vista).. Took me a few hours to figure out how it's done and another 60-90min to figure out that a reboot was necessary (printed the test page but no documents before the reboot).
Environmentally, a cheap laser printer might be your best bet if you only print occasionally. You won't be throwing out your cartridges as the toner will never go bad. If you leave it in there for years, all you need to do is to shake it up and it's good to go again.

---

### Post by Jammy4041 on 2009-10-28
Sorry to seemingly go off topic, but even Mac OS 9 has had a utiliuty to stop the hard drive platters from spinning, included in the OS. I put in a standard hard drive and I can choose to stop the platters when the hard drive is not doing anything. Is there not a utility to do the same in Ubuntu? And what are your opinions on this? Because some may argue that it actually uses more power in constantly having to stop and start the hard drive...

---

### Post by durand on 2009-10-28
I have an option to spin down hard drives in Power Management. I'm running karmic but I'm pretty sure it was in jaunty as well.

---

### Post by Jammy4041 on 2009-10-28
I'll eat my words then!

---

### Post by cascade9 on 2009-10-28
> **gordintoronto said:**
> The CPU is no longer available in North America.  AMD has a single-processor 45 w unit, or up to a quad at 65 w.

A dual-processor Atom with the Ion video seems like the natural next configuration.

Theres a new 45w TDP dual, triple and quad-core AMDs out now-

Athlon II X4 600e/Athlon II X4 605e (quad) Athlon II X3 400e/Athlon II X3 405e (triple) and Athlon II X2 235e/Athlon II X2 240e (dual). They only got released in the last few days (20th October 2009) so I'm not sure how avaible they are now, but they should be around soon if they arent already. 

I'm not sure about how the newer 'e' series CPUs would compare to the Atom, but I would guess that the Atom would use less if it was always at idle, and AMD would be better if you had much load. Thats just a guess though....

---

### Post by durand on 2009-10-28
The atoms only use about 5W at max load, I think...[http://en.wikipedia.org/wiki/Intel_Atom#Power_requirements](http://en.wikipedia.org/wiki/Intel_Atom#Power_requirements)

---

### Post by bribera on 2009-10-28
While choosing efficient hardware is very important, a lot can be done with *existing* systems -- in fact, you're likely to save more net energy by deferring your purchase of new components and sticking with an existing system.

Whatever you choose to do, you can eke out savings by monitoring how your software choices affect power consumption. A program like powertop (which I believe works on all platforms, even though the its website is Intel-centric) can help you figure out what potentially extraneous processes are causing power consumption. If you find something is unnecessary, you can uninstall it and save a little.

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by bribera on 2009-10-28
> **bribera said:**
> you're likely to save more net energy by deferring your purchase of new components and sticking with an existing system.

BTW, I'm talking about this sort of effect: [http://twitter.com/vkhosla/status/3307416184](http://twitter.com/vkhosla/status/3307416184)

---

### Post by Jammy4041 on 2009-10-28
Good points Bribera, but by going by that, most computers, if not, all computers, would not payback the energy released.
 
Then there's the carbon footprint for transport and the computers' ineviatble disposal. In my opinion it is better to reuse, and is part of the reason for buying unwanted processors and motherboards, and giving away computers on local initiatives for local people such as Freegle and Freecycle.
 
However the OP is doing the process from new parts - so is trying to be responsible in his computing choices.

---

### Post by Bucky Ball on 2009-10-30
> **Jammy4041 said:**
> Good points Bribera, but by going by that, most computers, if not, all computers, would not payback the energy released.
 
Then there's the carbon footprint for transport and the computers' ineviatble disposal. In my opinion it is better to reuse, and is part of the reason for buying unwanted processors and motherboards, and giving away computers on local initiatives for local people such as Freegle and Freecycle.
 
However the OP is doing the process from new parts - so is trying to be responsible in his computing choices.

It was a build from scratch, yes. Use what's working and only buy new if you have to, couldn't agree more. Talked about earlier in the thread also.

Thanks for all the input people.

---

### Post by cascade9 on 2009-10-30
> **durand said:**
> The atoms only use about 5W at max load, I think...[http://en.wikipedia.org/wiki/Intel_Atom#Power_requirements](http://en.wikipedia.org/wiki/Intel_Atom#Power_requirements)

Depends on what Atom your talk about. Atom D510s go to 13watt. I had to laugh, though, at this-

> Initially, all Atom motherboards on the consumer market featured the Intel 945G chipset, which uses 22 watts alone. As of early 2009, only a few manufacturers are offering lower power 945GSE-based motherboards to end users, paired with the Atom N270 or N280 CPU.
[http://en.wikipedia.org/wiki/Intel_Atom#Power_requirements](http://en.wikipedia.org/wiki/Intel_Atom#Power_requirements)

Which is why you see Atoms with tiny CPU heatsinks, and much bigger chipset heatsinks. Using TDP as a guide for power consumption isnt that bad an idea, but its go its issues-

> TDP values between different [manufacturers]("http://en.wikipedia.org/wiki/Integrated_device_manufacturer") cannot be accurately compared.

[http://en.wikipedia.org/wiki/Thermal_design_power](http://en.wikipedia.org/wiki/Thermal_design_power)

---

### Post by durand on 2009-10-30
22W for an integrated GPU? That surely isn't right. My laptop has an nvidia 8600M GS and the whole laptop uses about 40W at max load, 20W at minimum load. I can't see how the graphics card can use such a big proportion of the total power.

---

### Post by cascade9 on 2009-10-30
Its not just a graphics card, its also the memory and PCI-E interface and the connection to the southbridge. 

Just for a laugh, see this pic- 

[http://www2.multithread.co.uk/mtcshop/images/linitx.com/products/Intel_D945GCLF2_Dual_Core_1.6Ghz_ATOM_Mainboard__main.jpg](http://www2.multithread.co.uk/mtcshop/images/linitx.com/products/Intel_D945GCLF2_Dual_Core_1.6Ghz_ATOM_Mainboard__main.jpg)

The Atom CPU is under the little passive cooler at top. The active cooler is for the chipset LMAO.

---

### Post by Bucky Ball on 2009-10-30
The issue of graphics cards is something that will be turned on its head when ARM processors eventually hit the netbook world. The graphics is part of the processor and they use more like 1-2 watts (for now). Expect twenty four hour and beyond battery goodness.

---

### Post by Spiritof76 on 2010-01-04
While I fully intend on leaving as big of a carbon footprint as I possibly can, because the energy companies give me a paycheck. I did find the need to build a couple low power low cost systems ( a Server and Desktop.) I used the Intel D945GCLf2. I put 2 gigs memory and and 1 terra byte drives 
I unit had a dvd burner the other just a reader.  Both units with cases and PS cost $600us the 330 Atom id pretty fast at 1.6 Gig cause of the hyperthreading and duo Atom chip.  the 20 inch 9/5 Samsung was $105.  

It doesn't use much power and the board assy is leadfree.  I will just have to figure out another way to do my part to warm up this freezing planet. but I do have a pretty nice green desktop server combination.

---

### Post by Bucky Ball on 2010-01-06
> **Spiritof76 said:**
> While I fully intend on leaving as big of a carbon footprint as I possibly can, because the energy companies give me a paycheck. I did find the need to build a couple low power low cost systems ( a Server and Desktop.) I used the Intel D945GCLf2. I put 2 gigs memory and and 1 terra byte drives 
I unit had a dvd burner the other just a reader.  Both units with cases and PS cost $600us the 330 Atom id pretty fast at 1.6 Gig cause of the hyperthreading and duo Atom chip.  the 20 inch 9/5 Samsung was $105.  

It doesn't use much power and the board assy is leadfree.  I will just have to figure out another way to do my part to warm up this freezing planet. but I do have a pretty nice green desktop server combination.

Like the way you think ... ;)

---

### Post by pk_m on 2010-06-02
I liked this post.
I just had few questions.

Why only Ubuntu OS?

Is there any difference between Windows 7 and Ubuntu 10.04 for going green?

Does Ubuntu utilizes less power than Windows 7?

---

### Post by Bucky Ball on 2010-06-02
That is an excellent question!

No, makes no difference as far as hardware. Energy efficient hardware is just that. The main point of this post is that the hardware is energy efficient AND works with Linux. All of the hardware will work 'out of the box' with a Ubuntu OS. Buy a machine off the shelf and that is DEFINITELY not a guarantee.

If you were to build and energy efficient Windows box, you wouldn't need to be so specific about hardware. The deceptive thing is, of course, that hardware often comes with 'Window & Mac ready' and all that guff, but not Linux ready. Generally, things work just fine with Linux also but best to be careful. You don't want to fork out for a top of the range vid card only to find you have spent two months trying to get the thing to work.

If you want to run Linux and you're building a machine to do it, best to do your research rather than find yourself up s**t creek without a paddle.

Glad you liked the post! It is about time I updated it I think cos things move pretty quick in the world of technology and some of this is outdated. (LED monitors are MUCH more energy efficient that even LCD). ;)

---

### Post by Jammy4041 on 2010-06-03
The software used is also important, in my opinion, as it may be needed to enable the energy saving modes of the hardware. For example, hard drives can stop their platters from spinning using software and in windows, processors undervolt and down clock themselves using software.

The paradox is, you need the hardware to be able to support the power saving mode in the first place. 

One question for you Bucky, if you had to build your energy efficient build today, what would it be? Just out of interest that's all...

---

### Post by Bucky Ball on 2010-06-03
> **Jammy4041 said:**
> One question for you Bucky, if you had to build your energy efficient build today, what would it be? Just out of interest that's all...

'Nother great question! I have some holidays starting now so get back to you on that one. I would definitely look at the LED options for starters. Not sure if there's been much improvement from the WD GreenPower drives as far as efficiency goes.

Will have a sniff over the next few weeks and update the post. Cheers everyone! :)

---

### Post by corrytonapple on 2010-11-07
This is a great post. It will make building a server for home/web much easier. But I saw you said that you bookmark all of your builds. I have done that, but once you bookmark it you cannot have a copy of it in another folder. You may think, "Why have a copy of it in another folder?". Well, what if you want to use the same RAM as if often do need to on more than one build? See? I use my build parts in a HTML file for each build. I am attaching the code and what it would look like. There are instructions to view your result as well.
What is a good, small case for a server that runs three or four small websites and is a home server for backups and a photo/music server? 
Thanks!
:guitar:   On!

---

### Post by Bucky Ball on 2010-11-07
Thanks for the kind comments and the html file tip. This thread needs to be updated so might do some research over the Christmas break.

As for the server; I saw a mini-server (but didn't realise it was actually a 2.5 inch enclosure) a few months ago. Just a small enclosure which plugs into the router, give it an IP, and away you go! Doubt it would use much energy at all. BUT ... don't know if you can get a terrabyte 2.5 inch drive. Never used 'em in an external case so have no knowledge of that.

There's a start. If you want something you can cram with a few hard drives, though, an energy efficient PSU, as always, is the place to start. From there, the case is up to you. Keep It Simple! The more PCI cards, etc, you jam in there, the more power it will use. Motherboard? As basic as you can get. It won't even be running a screen after all!

Processor is going need to fit the MB, naturally, so take that into consideration as you should pick the processor that is going to cover the job FIRST then match the MB to that. (Do some research on the lowest power CPU that covers what you want to do.)

As for the case itself? Give yourself some room! Unless the case is a 'just slip 'em in and slip 'em out' design, you are going to need to get elbow deep while plugging cables. 

I have not researched what you're after but there could be pre-existing boxes out there, you just add the hard drive, so I'd have a look around there, too (Antec might be a place to start but energy-efficient boxes 'off-the-shelf' become more common, and pre-made server boxes are prime for energy savings as they tend to be on 24/7 so savings are more noticable for domestic and especially business users).

You no doubt know a lot of this, but you might pick up a new idea, never know. Good luck with it. :)

PS: Still waiting on that ARM 2.1Ghz processor!

---

### Post by knifemonk on 2011-02-27
i like the mini-itx boards, they are small and power efficient and still  grunty enough for a well placed linux system to run very well and  preform all the necessary tasks.

speaking in terms of hardware,  there are all kinds of hardware that can be, and should be used in place  of heavier counterparts as they are more efficient - they -should be-  cheaper than the heavier desktop systems that essentially give the same  user experience.

the implementation of hardware from the  perspective of the kernel itself is really where linux users and  enthusiasts can make the most immediate difference, and the great thing  about that is differences can be made which effect not only the  performance and power consumption of a machine positively, but can also  effect the lifespan of a machine positively as well.

aside from  giving the fans routine cleanups and lubrication, removing dust from the  heat-sinks and ensuring ideal environmental factors here are some of  the programs in linux that can improve the performance, power usage and  life-span of a machine -

:idea:

cpufreqd
fully configurable daemon for dynamic frequency and voltage scaling

cpufrequtils
tools to switch between frequency modes, availability depends on your  kernel: conservative, ondemand, or performance modes exist.

cpudyn
It  saves battery, lowers temperature, and can put the computer disks in  standby mode if a given period has passed without any I/O operation.

powertop
finds  the software component(s) that make your {system} use more power than  necessary while it is idle. - (this one is really smart)

upower
an abstraction of the power controls present in HAL which are now officially obsolete... not yet fully implemented(?).

cpulimit
limits the cpu usage of a process, good when something is causing an overload or simply to reduce the load.

procmeter3
my  fav system monitor- temp, load, usage,  in, out, average, etc. cpu,  gpu,  hdd, network. if it gives a reading, this little beastie will pick  it up and give you the facts.

pm-utils
suspend / hibernate... this is what you want to know about for these functions.

bum / rcconf
these let you disable the things that lurk in the background eating power and resources.

---  in the kernel source itself there are sections for device support like  thermal sensors and motherboard specific power-saving features that  sometimes have to be compiled in. From hardware to kernel, building a  system with all the right features and switches specific to the needs of  its application, and easily accessible, will bring multiple benefits in  the matter of power/performance.

when a material has an amount  of energy passing through it and that wave-length becomes variable so  does the energy consumption and the thermal byproduct change  accordingly.

the computers desired byproducts= data, output. can  easily be achieved with very little resistance and energy: how? with the  right variables of course!

---

### Post by *^kyfds( on 2011-12-04
i'm actually planning to build a new PC sometime in the future.

thanks for this thread, keep it open and i'll report back when (or if) i finish :D

my friend's PC has an EPU utility that seemed pretty good for saving power 

[http://event.asus.com/epu/](http://event.asus.com/epu/)

---

### Post by will1982 on 2012-10-08
Sounds cool, will refer to it in the future :)

---

### Post by 577 Jersey on 2012-11-13
Wow,,
 Thanks for taking the time to go through all of that.Very usefull info,,a wealth of knowledge.Im going to remove my CPU heatsinks,clean off all the old thermal paste and re-apply the Arctic Silver that you mentioned.

I am a two way radio tech by trade,,we use thermal compound on our transistors,FETS,and regulators,,I never thought to check out the old PC.

 Take care

  Tommy

---

### Post by gbrowning on 2012-11-13
how about basing an ubuntu machine on a Raspberry Pi?  The board is $35 US.  Or paralleling two or more RaspPi? Much less processing power than a desktop but also requires much less power than a desktop. Think about a dedicated video transcoder which may take more than a day to transcode your movie but can sit in the corner churning away without costing much.  I'll bet you can get up and running (assuming you already own the TV or Monitor on which you watch your movies) for less than $100.

---

### Post by bcschmerker on 2013-02-18
If ye're able to land them in your country, the following components can be used to build as energy-efficient a system as I've been able to discover, with sufficient power reserves for expansion at a later date:

[VIA® pc3500 Platform]("http://www.via.com.tw/en/initiatives/empowered/pc3500_platform/index.jsp") (C7-D or Nano X2 or X4 CPU; CN896 chipset; planar Chrome9 GPU)
[Antec® Earthwatts&#8482; 650 Platinum&#8482;]("http://www.antec.com/product.php?id=704513&fid=11") (20*max* A@+3.3VDC; 18*max* A@+5VDC; four 30*max*A@+12VDC rails)

The pc3500 is already fully supported by LinUX Kernel 3.3, the X.org Unichrome GPU server, and the ALSA snd-intel audio driver; the onboard PCI-Express x16 slot allows for SCSI or high-performance video at a later date, the legacy PCI 2.0 slot a variety of multimedia options.

---

