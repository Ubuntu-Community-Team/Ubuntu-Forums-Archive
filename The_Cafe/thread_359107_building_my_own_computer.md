---
title: "building my own computer"
date: 2007-02-11
forum: The Cafe
---

### Post by rbprogrammer on 2007-02-11
i'm looking to build my own computer, but the problem is that i'm not familiar with what hardware is compatible with linux ( pretty much just ubuntu is what i care about ).

what kinds of companies are compatible with ubuntu? what i'm thinking i would have problems with is a motherboard, graphics card, cpu, ram (not sure if ram would be a factor in this).....

i think everything else (ie. keyboard, mouse, cd/dvd drive, hard drive) i wouldnt have a problem with...

correct me if i'm wrong, but if i get a compatible graphics card, then a monitor would not be a problem, right?

thanks for any help........

---

### Post by %hMa@?b&lt;C on 2007-02-11
well, what is your price range? pretty much any NVidia card would work.  For Mobo, pretty much I would need your price range.

---

### Post by Jussi Kukkonen on 2007-02-11
Graphics card is *probably* the only thing that you need to worry about. Motherboards pretty much all work, but I still suggest choosing a popular one just make sure. Also, if you are going to need suspend (or other more esoteric motherboard functions) you should try to find out if it works on the MB before buying it... WLAN cards are another problem area.

Monitors just work, and in my experience so do the other devices you mentioned.

---

### Post by Yossarian on 2007-02-11
> Originally posted by **jeffc313**
well, what is your price range? pretty much any NVidia card would work. For Mobo, pretty much I would need your price range.

I'm the same boat as the original poster.  What would spending more money on a motherboard get you?  I want a fast workstation for CAD, and I want to run Windows/Solaris/Ubuntu etc on it, but I have zero interest in computer games.

---

### Post by Polygon on 2007-02-11
make sure that if you are going to have a wireless card, make SURE its supported. nothing worse then having to battle to get your wireless internet working

and also the video card, if your not going to be doing any gaming/cad/3d work or whatnot, you can get a good quality cheap card and it will work fine. Im playing games at like 30 fps with my ati radeon 9800 that i bought like 3 and a half years ago.

and also ive heard complaints that some features on certain mother boards dont agree with linux very well

just as a rule of thumb, read reviews on everything you buy and if a lot of people have problems with it then i would steer clear of it.

---

### Post by rbprogrammer on 2007-02-11
> **jeffc313 said:**
> well, what is your price range? pretty much any NVidia card would work.  For Mobo, pretty much I would need your price range.

well, price isn't too much of an issue.  but i do plan on installing windows in a SMALL partition to use for games.  now as far as compatibility with NVidia, i figured i'd be getting one of those graphics cards, but i think i will search for a post of something where some people said the same card definitely works in ubuntu..... i mean i don't want to shell out a couple hundred and find out its not compatible .

---

### Post by ~LoKe on 2007-02-11
Any card will work.  If you're really not sure, get something from the 6 or 7 series.  Make sure it's an eVGA card.

As for the motherboard...all JMicron controller issues should be resolved by now.  Hard drive, ram, cpu, sound card = not important.  Wireless internet...possible problem.

---

### Post by Detonate on 2007-02-11
I just put in a sizable order from Newegg myself.  One thing I've learned, when you go to these computer parts suppliers, and you are deciding what to order, don't put too much trust in those "customer reviews".  You don't really know who wrote them.  Check the specs, google the part and see if you can find a review, visit the linux hardware compatibility sites, then hope for the best.  For my linux box, I tend to buy hardware that's been around for at least a few months, hoping someone has built a driver for it.  Usually, everything I buy works out of the box.

---

### Post by mips on 2007-02-12
Just about any nVidia card will work, I would not worry to much about that.

The only area where you might have issues is the motherboard. Sometimes there are small problems (no unresolveable) with the HD controller or LAN chipset.

Go online and pick your components. Once you have a list of everything you want post it here for comments. People will let you know if there are any known issues with certain hardware or not.

---

### Post by blueturtl on 2007-02-12
If I were building a new system with Ubuntu in mind I would probably pick:

- An ASUS motherboard with an Intel chipset
- (and thus) Intel Core Duo
- nVidia video card (best performance)

Reason: AMD, VIA and ATI poorly support Linux and as a result, in my current system USB 2.0 ports don't work, hibernation / sleep doesn't work. Intel is an open supporter of Linux, nVidia while not exactly open-source friendly does provide best closed source video drivers and performance. Can't think of other parts that wouldn't work.. CD/DVD writers and hard-disks are pretty much standard hardware. If you don't pick an Intel mobo with integrated LAN/WLAN you may have to look into the compatibility of those before purchase. Especially WLAN cards can be troublesome if the manufacturer doesn't support Linux.

---

### Post by wh0rd on 2007-02-12
You can check out the following websites, they have a list of hardware vendors specifically for Linux:
[http://www.linux.org/hardware/]("http://www.linux.org/hardware/")

[http://www.phoronix.com/lch/]("http://www.phoronix.com/lch/")

[http://www.linuxcompatible.org/compatibility.html]("http://www.linuxcompatible.org/compatibility.html")

I WOULD DEFINITELY NOT GET AN ATI GRAPHICS CARD!

Prism Wireless Card, for security reasons ;).

---

### Post by mips on 2007-02-12
> **blueturtl said:**
> 
Reason: AMD... poorly support Linux

FUD

---

### Post by ExtremeRc on 2007-02-12
What is the current issue with ATI cards.  I know from a quick search of their site, I found drivers for just about every XK1 card and older cards as well.  Not really sure why ATI wouldn't be good.  I would think that either and ATI card or Nvidia card would be fine.  As far as staying away from AMD and going intel, you are basically saying buy a Chevy and not a ford.  It seems its the good old debate on which one to get.  Neither CPU needs drivers so that wouldn't be a problem what so ever.

---

### Post by ~LoKe on 2007-02-12
Getting ATi drivers to function under Linux has always been a hassle for a lot of people.  I'm not saying it's impossible, because it certainly isn't.  Just saying that you'd definitely have better luck with an nVidia card.

---

### Post by Anthem on 2007-02-12
Yeah, AMD works great with Linux.  ATI, not so much.

What kind of gaming do you do?  It might be worthwhile to pick up a motherboard with integrated intel graphics.  Not only will it be cheaper, but it will actually run Linux very well due to the excellent driver support.

---

### Post by kvonb on 2007-02-12
I ran an ATI 9200se for over a year, while I got it working fairly well with both games and Beryl, the problem is the difficulty in driver installation.

I found the best driver is the default opensource driver supplied and already working on a default install of Edgy.  It's slower, but 3d works.

If you hit the "direct rendering No" problem with an ATI, you are in for big trouble.

The nvidia is far superior in terms of speed and ease of driver installation.

You might run into problems with some of the latest graphics cards, especially ATI, for nvidia go to their website and simply check their linux driver supported list.

As another person mentioned, some onboard network adaptors may have problems, so check the chip for compatibility.

If you are going to be gaming, or doing any sound work, I would suggest buying one of the mid range sound blaster cards.  I have a SBlive, it supports multiple sound channels, ie I can use TeamSpeak while playing a game at the same time.  Most onboard cards don't support this.

Webcams are a REAL pain, you will have to check the compatibility page, here is another good one:

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

Hope that helps, KEv :)

---

### Post by maniacmusician on 2007-02-12
> **ExtremeRc said:**
> What is the current issue with ATI cards.  I know from a quick search of their site, I found drivers for just about every XK1 card and older cards as well.  Not really sure why ATI wouldn't be good.  I would think that either and ATI card or Nvidia card would be fine.  As far as staying away from AMD and going intel, you are basically saying buy a Chevy and not a ford.  It seems its the good old debate on which one to get.  Neither CPU needs drivers so that wouldn't be a problem what so ever.
Sorry, but you're wrong on both fronts :) ATI cards have poor support. The official drivers **claim** to support a lot of cards, but in actuality, the drivers don't work on some of those cards. Even when they do work, hardware acceleration is not as good as you'd get with Nvidia. Furthermore, ATI supports DirectX more than OpenGL, whereas Nvidia tends to focus on OpenGL; basically, what it comes down to is that at the moment, Nvidia is the only sane choice for video cards on Linux (the intel GPU's are excellent as well, but aren't as powerful)

As for AMD vs. Intel, the argument you made would have been correct a couple of years ago. However, with the introduction of the Core Duos (and the Core 2 Duos, etc), Intel has sped ahead. It's not a matter of taking sides anymore...when you're looking for performance, Intel clearly has the upper hand. I'm fairly sure that none of the AMD dual core processors provide better or equivalent performance to their Intel counterparts at a similar price. AMD has simply been outdone. They might make a comeback with future generations of processors, but for now, Intel's the way to go for a new system.

---

### Post by Rodneyck on 2007-02-12
> **mips said:**
> FUD

I second that FUD!!!  AMD rocks and has always been my CPU choice for every computer I have built, rock solid and perfect for Linux.

---

### Post by mips on 2007-02-13
> **maniacmusician said:**
> 
As for AMD vs. Intel, the argument you made would have been correct a couple of years ago. However, with the introduction of the Core Duos (and the Core 2 Duos, etc), Intel has sped ahead. It's not a matter of taking sides anymore...when you're looking for performance, Intel clearly has the upper hand. I'm fairly sure that none of the AMD dual core processors provide better or equivalent performance to their Intel counterparts at a similar price. AMD has simply been outdone. They might make a comeback with future generations of processors, but for now, Intel's the way to go for a new system.


I think his response was to another poster above that said AMD does not support linux or work well with it (someting to that effect). As for performance I have to agree that right now Intel has the upper hand with their core 2 duos. 

At the same time it is important to look at price and if you are not going top of the line Intel you might find a comparable AMD at a better price. Another issue might be that you already have a AMD type socket MB which will happily accept a X2 amd processor and doing a MB+CPU+RAM to go the Intel could be an expensive option for those merely wishing to upgrade. I'm in that boat right now.

---

### Post by maniacmusician on 2007-02-13
I'm in that boat too, unfortunately. I'm just saving up little by little, because I still plan to go for a C2D. I want something that will at least last me for a couple of years to come. So I'm pretty much building another computer from scratch...reusing some of my old parts to save money, like the hard drives (of course), video card, monitor, cd/dvd drives. All I really have to buy is the processor and the motherboard, which will cost me around $450 US if I buy the stuff I want. I might actually get a new case too.

---

### Post by kerry_s on 2007-02-13
I've been saving up for this [http://www.compusa.com/products/product_info.asp?pfp=SEARCH&Ntt=acer&N=0&Dx=mode+matchall&Nty=1&D=acer&Ntk=All&product_code=341979&Pn=Aspire_ASL310_EC352M_Minitower](http://www.compusa.com/products/product_info.asp?pfp=SEARCH&Ntt=acer&N=0&Dx=mode+matchall&Nty=1&D=acer&Ntk=All&product_code=341979&Pn=Aspire_ASL310_EC352M_Minitower)
 
I want to use it as a starting point, i want to do a combination CF(4gb) & HD system. I'm planning on using the CF(using adapter) as the master drive holding the / and the HD will be for frequently written folders /home,/root,/proc,/dev,/tmp,/var. The rest is mostly read only so they'll stay on the CF. I will also tweak my setup for less writes to the HD.

What do you guys think? Can it be a mostly silent speedy system? Am i crazy? :)

---

### Post by Omnios on 2007-02-13
Personally I will be doing a barebones hardware upgrade in about 4 moths. As a general rule I will be sticking to either a uases or Gigabite mother board  and a couple gigs of ram as it is fairly cheap now. As for a processor I will probably choose one that came out about 6 months previos as there is a huge price different though in 4 months or so this will be a dual core. My current box was about 6 months old compared to release date and I saved about a thousand though it was not a bare bones. This time I will be keeping my dvd-rw and hard drives etc.

---

### Post by Oki on 2007-02-13
It would be wonderful if there where **ONE** site where you could find out witch hardware that worked with Linux. I find it strange that it don’t are any yet. 


Here is the sites I have saved with info on working hardware(I  just paste the list, you have to see if all are relevant for you); 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
[http://www.linuxwireless.org/](http://www.linuxwireless.org/)
[http://intellinuxwireless.org/](http://intellinuxwireless.org/)
[http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix)
[http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)
[http://pvrhw.goldfish.org/tiki-page.php?pageName=pvrhw_tuners](http://pvrhw.goldfish.org/tiki-page.php?pageName=pvrhw_tuners)
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
[http://www.linuxcompatible.org/](http://www.linuxcompatible.org/)
[https://wiki.ubuntu.com/LaptopTestingTeam#head-ed3bfabb533fe8032b87405aab057e3f5835f724](https://wiki.ubuntu.com/LaptopTestingTeam#head-ed3bfabb533fe8032b87405aab057e3f5835f724)
[http://www.linux.org/hardware/](http://www.linux.org/hardware/)
[http://www.phoronix.com/lch/](http://www.phoronix.com/lch/)
[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)
[http://www.linux-usb.org/](http://www.linux-usb.org/)
[http://tldp.org/](http://tldp.org/)
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

If all where like IBM; [http://youtube.com/watch?v=KwEWxpOWOok](http://youtube.com/watch?v=KwEWxpOWOok)

---

### Post by mips on 2007-02-14
> **kerry_s said:**
> 
What do you guys think? Can it be a mostly silent speedy system? Am i crazy? :)


Am i crazy? Yes :)
Can it be a mostly silent speedy system? No
What do you guys think? Hmm,

Compact flash is not as fast as you think. A HD will outperform it. How are you going to implement this CF as you have no slot for it which leads me to believe you are going to use a sata/pata interface. Sorry to say but you will see a performance decrease with cf technology.

A better option would be to use technology other than CF. Look at,
[http://www.tomshardware.com/2006/09/20/conventional_hard_drive_obsoletism/index.html](http://www.tomshardware.com/2006/09/20/conventional_hard_drive_obsoletism/index.html)
[http://www.tomshardware.com/2005/12/05/hyperos_dram_hard_drive_on_the_block/index.html](http://www.tomshardware.com/2005/12/05/hyperos_dram_hard_drive_on_the_block/index.html)
[http://www.tomshardware.com/2005/12/05/hyperos_dram_hard_drive_on_the_block/index.html](http://www.tomshardware.com/2005/12/05/hyperos_dram_hard_drive_on_the_block/index.html)

As for the noise issue you could look in padding the inside of the case with acoustic absorbsion materials.
[http://www.acoustiproducts.com/en/acoustipack.asp](http://www.acoustiproducts.com/en/acoustipack.asp)
Use quieter fans for psu, cpu, gpu & mb.

Last, I would not buy that system. I would build my own to newer specs.

---

### Post by kerry_s on 2007-02-14
Ohh, i like the sound of that hyperdrive, but i don't think i can afford something like that.

The reason i'm going prebuilt is just for the price. I priced out all the parts i would need + shipping to hawaii and it is just no way in my budget. I also would prefer to buy locally and well thats the only decent mini i could live with.

I've been looking into that cf and hd, the difference should be seen in responsiveness, in the time it takes for the hd to spin up it would have already been found in the cf.

Your first link is a cf, it's just got the outer cover removed. I'm going to be using a adapter like these-> [http://www.acscontrol.com/Index_ACS.asp?Page=/Pages/Products/CompactFlash/IDE_To_CF_Adapter.htm](http://www.acscontrol.com/Index_ACS.asp?Page=/Pages/Products/CompactFlash/IDE_To_CF_Adapter.htm)

Of course i'm going to be stuck with hd at first till i save more for the cf and adapter. My original plan was to replace the hd altogether, but i've been reading about those new hybrid drives and was thinking that i could get the benefits of something like that but for far less cost. In the end it's just going to be a new toy for me to play with, i have my desktop for the real work. :)

---

### Post by mips on 2007-02-14
> **kerry_s said:**
> 
Your first link is a cf, it's just got the outer cover removed. []("http://www.acscontrol.com/Index_ACS.asp?Page=/Pages/Products/CompactFlash/IDE_To_CF_Adapter.htm")


Yes, but it has a normal pata interface. Another thing, not all CF are equal. 

Have you had a look at the asus pundit series yet ?

---

### Post by kerry_s on 2007-02-14
> **mips said:**
> Yes, but it has a normal pata interface. Another thing, not all CF are equal. 

Have you had a look at the asus pundit series yet ?

Yeah, i did but i can't find it locally and once again it comes down to cost for me. Hopefully someday my son will put some of that education to use and i can actually use some money for me. :(

---

### Post by mips on 2007-02-14
> **kerry_s said:**
> Hopefully someday my son will put some of that education to use and i can actually use some money for me. :(

Start laying on the guilt at an early stage ;)  "In my day we walked to school without shoes" and stuff like that comes to mind :)

---

### Post by kerry_s on 2007-02-14
> **mips said:**
> Start laying on the guilt at an early stage ;)  "In my day we walked to school without shoes" and stuff like that comes to mind :)

LOL, he still hates me for that, i made him walk to school everyday, a miles not that far. He now lives with his mama so he's gettin fat, damn mama spoils him, it's easy for her cause its my money she uses. :(

---

### Post by mips on 2007-02-14
> **kerry_s said:**
> LOL, he still hates me for that, i made him walk to school everyday, a miles not that far. 

I would have loved a mile walk every day compared to my 50min there & 50min back bus ride in sweltering heat. And then the bus also broke down a lot. Would have given me and extra 100mins surfing time every day.

---

### Post by flyinsquirrel992 on 2007-02-15
> **jeffc313 said:**
> well, what is your price range? pretty much any NVidia card would work.  For Mobo, pretty much I would need your price range.

Just dont get the Geforce 6200 **LE**, it has bad support even in Windows.

---

### Post by Yossarian on 2007-02-15
> Originally posted by **flyinsquirrel992**
Just dont get the Geforce 6200 LE, it has bad support even in Windows.


What's wrong with this card?  Is it all nvidia 6200 cards, or just the LE specifically?  I was thinking about getting a 6500 which is a slight variation on the 6200 model.  Maybe I'll consider a slightly better card.

I am also planning on building a PC, and here are the parts I've selected.  I would appreciate any criticism or comments on my list (I haven't chosen a power supply yet, I want to look for a good one):

Intel 975XBX2KR Intel Socket 775 ATX Motherboard

NVIDIA GeForce 6500 

Lite-On SH-16A7S Super Allwrite (SATA DVD Burner)

Intel Core 2 Duo E6400 2.13GHz Processor
Centon 2048MB Dual Channel PC6400 DDR2 800MHz Memory (2 x 1024MB)
Power Up Black ATX Mid-Tower Case 
Western Digital / Caviar SE 16 / 250GB / 7200 (SATA Hard disk)

Thanks

---

### Post by flyinsquirrel992 on 2007-02-16
> **Yossarian said:**
> What's wrong with this card?  Is it all nvidia 6200 cards, or just the LE specifically?  I was thinking about getting a 6500 which is a slight variation on the 6200 model.  Maybe I'll consider a slightly better card.

It is just the LE specifically (I used to have a regular 6200 that worked fine), I've had nothing but problems with it.  It ran right off the bat in Linux and in Windows, but just has some odd *qwerks* in it. I may just have a glitchy video card, but I had a heck of a time trying to get it to work with 3D and no graphical corruptions in Suse 10.1/10.2 (thats when i switched to ubuntu, then as a final touch KDE...then just Kubuntu). 

According to what I've seen online this happens to be one video card that just didn't have good support.


As for your parts, I'd say everything looks good there. I've heard the Core 2 duo's run insanely fast (I have an OC'd 805 myself (3.6 ;))). The only thing I'd look into is a better video card if you use it for gaming at all, I've seen some killer deals on Newegg you could look into.  I remember there was a 7800GT (I believe) that was on sale for 140 dollars plus a 50 dollar rebate, very nice deal, not sure if its there anymore though.

---

### Post by Yossarian on 2007-02-16
> Originally posted by **flyinsquirrel992**
As for your parts, I'd say everything looks good there. I've heard the Core 2 duo's run insanely fast (I have an OC'd 805 myself (3.6 )). The only thing I'd look into is a better video card if you use it for gaming at all, I've seen some killer deals on Newegg you could look into. I remember there was a 7800GT (I believe) that was on sale for 140 dollars plus a 50 dollar rebate, very nice deal, not sure if its there anymore though.


Thanks for the help.  I think I'm going to get a 6600 instead.  256 mb is enough for me and my modest 3d needs.  I could actually get a 512 mb card for the same price (about 100 CDN) but it would be a bottom of the barrel 512 card, wheras I think a think a higher quality but lower memory card fits my useage better.  I really just want something to give me DVI output and some light 3D (CAD, old games, etc).

---

